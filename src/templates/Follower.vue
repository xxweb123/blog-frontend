<template>
  <Layout>
    <div>
      <el-card shadow="never" style="min-height: 400px; margin-bottom: 20px">
        <div slot="header" class="clearfix">
          <span>{{ this.$page.strapiFollower.login }}</span>
          <el-button
            @click="$router.go(-1)"
            style="float: right; padding: 3px 0"
            type="text"
            icon="el-icon-d-arrow-left"
            >返回</el-button
          >
        </div>
        <el-row>
          <el-col :span="9" style="padding: 0px 10px 20px 0px">
            <img :src="this.$page.strapiFollower.avatar_url" style="width: 100%; border-radius: 5px" />
            <div style="padding: 10px">
              <font style="font-size: 26px; line-height: 40px; font-weight: 600"
                >{{ this.$page.strapiFollower.login }}
                <br />
              </font>
              <font
                style="
                  font-size: 20px;
                  font-style: normal;
                  font-weight: 300;
                  line-height: 35px;
                  color: #666;
                "
                >{{ this.$page.strapiFollower.login }}
                <br />
              </font>
              <font
                style="font-size: 14px; line-height: 20px; color: #606266"
                v-if="location"
              >
                <i class="el-icon-location-outline"></i>&nbsp;&nbsp;{{
                  location
                }}
                <br />
              </font>
              <font
                style="font-size: 14px; line-height: 20px; color: #606266"
                v-if="email"
              >
                <i class="el-icon-message"></i>&nbsp;&nbsp;{{ email }}
                <br />
              </font>
              <font style="font-size: 14px; color: #606266" v-if="$page.strapiFollower.html_url">
                <i class="el-icon-edit-outline"></i>&nbsp;&nbsp;
                <a :href=" $page.strapiFollower.html_url" target="_blank">{{ this.$page.strapiFollower.html_url }}</a>
                <br />
              </font>
            </div>
          </el-col>
          <el-col :span="15" style="padding: 0px 20px 20px 10px">
            <div
              style="
                width: 100%;
                min-height: 300px;
                border-radius: 5px;
                border: 1px solid #ebeef5;
                padding: 10px;
                font-size: 16px;
                color: #6a737d;
              "
              v-if="$page.strapiFollower.html_url"
            >
              {{ this.$page.strapiFollower.html_url }}
            </div>
            <div
              style="
                width: 100%;
                min-height: 300px;
                border-radius: 5px;
                border: 1px solid #ebeef5;
                padding: 30px;
                text-align: center;
                font-size: 30px;
                color: #dddddd;
              "
              v-else
            >
              <b>◔ ‸◔？没有简介</b>
            </div>
          </el-col>
        </el-row>
      </el-card>
    </div>
  </Layout>
</template>
<page-query>
    query($id: ID!){
      strapiFollower(id:$id){
        id
        login
        html_url
        blog
        avatar_url
      }
    }
</page-query>
<script>
export default {
  name: "followerdetail",
  metaInfo() {
    return {
      title: this.$page.strapiFollower.login,
    };
  },
  data() {
    return {
      githubUsername: null,
      name: null,
      avatarUrl: null,
      htmlUrl: null,
      blog: null,
      location: null,
      email: null,
      bio: null,
      followers: null,
      following: null,
      publicRepos: null,
    };
  },
  methods: {},
};
</script>