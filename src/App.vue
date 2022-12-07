<script setup lang="ts">
import { appCacheDir, appConfigDir, appDataDir, appLocalDataDir,
  appLogDir, audioDir, basename, resolveResource, cacheDir, configDir,
  dataDir, desktopDir, dirname, downloadDir, documentDir, executableDir,
  extname, fontDir, homeDir, isAbsolute, join, localDataDir, pictureDir, publicDir,
  resolve, resourceDir, runtimeDir, templateDir, videoDir } from '@tauri-apps/api/path';
import { message } from '@tauri-apps/api/dialog';

// 获取 App 缓存路径信息路径是否为绝对路径
async function getAppCachePathInfo() {
  const result = await appCacheDir(); // /home/zsf/.cache/com.tauri.dev/
  await message(`App Cache Path: ${result}`, {title: "App 缓存路径信息"});
}

// 获取 App Config 路径信息
async function getAppConfigDirInfo() {
  const result = await appConfigDir(); // /home/zsf/.config/com.tauri.dev/
  await message(`App Config Path: ${result}`, {title: "App Config 路径信息"});
}

// 获取 App Data Dir 路径信息
async function getAppDataDirInfo() {
  const result = await appDataDir(); // /home/zsf/.local/share/com.tauri.dev/
  await message(`App Data Path: ${result}`, {title: "App Data 路径信息"});
}

// 获取 App Local Data Dir 路径信息
async function getAppLocalDataDirInfo() {
  const result = await appLocalDataDir(); // /home/zsf/.local/share/com.tauri.dev/
  await message(`App LocalData Dir: ${result}`, {title: "App LocalData Dir Info"});
}

// 获取 App Log Dir 路径信息
async function getAppLogDir() {
  const result = await appLogDir(); // /home/zsf/.config/com.tauri.dev/logs/
  await message(`App Log Dir : ${result}`, {title: "App Log Dir Info"});
}

// 获取 Audio 路径信息
async function getAudioDirInfo() {
  const result = await audioDir(); // /home/zsf/音乐
  await message(`Audio Dir: ${result}`, {title: "Audio Dir Info"});
}

async function getBaseNameInfo() {
  const resourcePath = await resolveResource("~/test/apps.py"); // resolveResource 函数获取资源路径名，包括文件名和扩展名
  console.log(resourcePath);
  const base = await basename(resourcePath, ".py"); // 获取路径最后的文件名，第二个参数指定过滤调扩展名，如：.py，将会只获取文件名
  await message(`base : ${base}`, {title: "Base Info"});
}

async function getCacheDirInfo() {
  const result = await cacheDir();
  await message(`Cache Dir : ${result}`, {title: "Cache Dir Info"});
}

async function getConfigDirInfo() {
  const result = await configDir();
  await message(`Config Dir : ${result}`, {title: "Config Dir Info"});

}

async function getDataDirInfo() {
  const result = await dataDir();
  await message(`Data Dir : ${result}`, {title: "Data Dir Info"});
  
}

async function getDesktopDirInfo() {
  const result = await desktopDir();
  await message(`Desktop Dir : ${result}`, {title: "Desktop Dir Info"});

}

async function getDirNameInfo() {
  const appDataDirPath = await appDataDir();
  const result = await dirname(appDataDirPath);
  await message(`Dirname Dir : ${result}`, {title: "Dirname Dir Info"});
}

async function getDownloadDirInfo() {
  console.log("Hello,Tauri!");
  const result = await downloadDir();
  await message(`Download Dir : ${result}`, {title: "Download Dir Info"});

}

async function getDocumentDirInfo() {
  const result = await documentDir();
  await message(`Document Dir : ${result}`, {title: "Document Dir Info"});

}

async function getExecutableDirInfo() {
  const result = await executableDir();
  await message(`Executable Dir : ${result}`, {title: "Executable Dir Info"});
}

async function getExNamePathInfo() {
  const result = await extname("~/test/app.conf"); // 获取扩展名 conf
  await message(`ExName Path : ${result}`, {title: "ExName Path Info"});
}

async function getfontDirInfo() {
  const result = await fontDir(); // 获取用户字体目录 /home/zsf/.local/share/fonts/
  await message(`user's font directory : ${result}`, {title: "User Font Directory Info"});
}

async function getHomeDirInfo() {
  const result = await homeDir(); // 获取当前用户目录 /home/zsf
  await message(`Home user directory : ${result}`, {title: "User Home Directory Info"});
}

// 判断路径是否为绝对路径
async function getIsAbsoluteInfo() {
  const result = await isAbsolute("/home/zsf/test"); // 判断路径是否为绝对路径
  await message(`当前路径是否为绝对路进 : ${result}`, {title: "是否为绝对路径 Info"});
}

async function joinPath() {
  const home_path = await homeDir();
  const result = await join(home_path, "test", "tauri", "main.rs"); // 连接路径 /home/zsf/test/tauri/main.rs
  await message(`路径 : ${result}`, {title: "生成的路径 Info"});

}

async function getLocalDataDirInfo() {
  const result = await localDataDir(); // /home/zsf/.local/share/
  await message(`Local Data Dir : ${result}`, {title: "LocalData Dir Info"});
}

async function getPictureDirInfo() {
  const result = await pictureDir();
  await message(`Picture Dir : ${result}`, {title: "Picture Dir Info"});

}

async function getPublicDirInfo() {
  const result = await publicDir();
  await message(`public Dir : ${result}`, {title: "Public Dir Info"});

}

async function getResolveDir() {
  const appDataDirPath = await appDataDir();
  const path = await resolve(appDataDirPath, '..', 'users', 'tauri', 'avatar.png');
  await message(`Resolve Dir : ${path}`, {title: "Resolve Dir Info"});
}

async function getResourceDirInfo() {
  const path = await resourceDir();
  await message(`Resource Dir : ${path}`, {title: "Resource Dir Info"});

}

async function getRunTimeDirInfo() {
  const path = await runtimeDir();
  await message(`Runtime Dir : ${path}`, {title: "Runtime Dir Info"});

}

async function getTemplateDir() {
  const path = await templateDir(); // /home/zsf/模板/
  await message(`Template Dir : ${path}`, {title: "Template Dir Info"});
}

async function getVideoDir() {
  const path = await videoDir(); // /home/zsf/视频/
  await message(`Video Dir : ${path}`, {title: "Video Dir Info"});
}

</script>

<template>
  <div class="container">
    <h1>Welcome to Tauri!</h1>
    <button type="button" @click="getAppCachePathInfo">获取 App 缓存路径</button>
    <button type="button" @click="getAppConfigDirInfo">获取 App Config 路径</button>
    <button type="button" @click="getAppDataDirInfo">获取 App Data 路径</button>
    <button type="button" @click="getAppLocalDataDirInfo">获取 App LocalData 路径</button>
    <button type="button" @click="getAppLogDir">获取 App Log Dir 路径</button>
    <button type="button" @click="getAudioDirInfo">获取 App Audio Dir 路径</button>
    <button type="button" @click="getBaseNameInfo">获取 Base 路径</button>
    <button type="button" @click="getCacheDirInfo">获取 Cache Dir 路径</button>
    <button type="button" @click="getConfigDirInfo">获取 Config Dir 路径</button>
    <button type="button" @click="getDataDirInfo">获取 Data Dir 路径</button>
    <button type="button" @click="getDesktopDirInfo">获取 Desktop Dir 路径</button>
    <button type="button" @click="getDirNameInfo">获取 DirName Dir 路径</button>
    <button type="button" @click="getDownloadDirInfo">获取 Download Dir 路径</button>
    <button type="button" @click="getDocumentDirInfo">获取 Document Dir 路径</button>
    <button type="button" @click="getExecutableDirInfo">获取 Executable Dir 路径</button>
    <button type="button" @click="getExNamePathInfo">获取 ExName 路径</button>
    <button type="button" @click="getfontDirInfo">获取 Font 路径</button>
    <button type="button" @click="getHomeDirInfo">获取 Home 路径</button>
    <button type="button" @click="getIsAbsoluteInfo">路径是否为绝对路径</button>
    <button type="button" @click="joinPath">生成的路径</button>
    <button type="button" @click="getLocalDataDirInfo">获取 LocalDataDir 路径</button>
    <button type="button" @click="getPictureDirInfo">获取 PictureDir 路径</button>
    <button type="button" @click="getPublicDirInfo">获取 PublicDir 路径</button>
    <button type="button" @click="getResolveDir">获取 ResolveDir 路径</button>
    <button type="button" @click="getResourceDirInfo">获取 Resource 路径</button>
    <button type="button" @click="getRunTimeDirInfo">获取 Runtime 路径</button>
    <button type="button" @click="getTemplateDir">获取 Template 路径</button>
    <button type="button" @click="getVideoDir">获取 Video 路径</button>
  </div>
</template>

<style scoped>
.logo.vite:hover {
  filter: drop-shadow(0 0 2em #747bff);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #249b73);
}
</style>
