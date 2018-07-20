## Android Recovery Minimal Manifest
---
Minimal repo manifest for compiling android recovery

### Requirements
- Ubuntu 16.04 [Recommended]
- Common packages for both, 32-bit and 64-bit systems
```
bc bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk3.0-dev libxml2 libxml2-utils lzop maven openjdk-7-jdk pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev
```
- Additional packages for 64-bit systems
```
g++-multilib gcc-multilib lib32ncurses5-dev lib32readline6-dev lib32z1-dev
```
- Repo tool
```
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
$ export PATH=$HOME/bin:$PATH
```

### Getting Started
- Initializing repository

    `repo init --depth=1 -u https://github.com/vedant-y/android-recovery.git -b cm-13.0`
- Downloading source code

    `repo sync`

### Compiling
- Compiling single module, recovery
```
$ source build/envsetup.sh
$ breakfast surnia
$ make recovery
```

### Additional
- Installing OpenJDK 7 on Ubuntu 16.04
```
$ add-apt-repository ppa:openjdk-r/ppa  
$ apt-get update   
$ apt-get install openjdk-7-jdk
```
- Adding ~/bin to default $PATH
```
$ nano ~/.profile

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```
- Local manifests
```
# Create a directory inside .repo
$ mkdir -p .repo/local_manifests
```
```
# Create any xml file, default roomservice.xml
$ nano .repo/local_manifests/roomservice.xml

<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <remove-project name="CyanogenMod/android_kernel_motorola_msm8916" />
</manifest>
```

### Reference
- [LineageOS Wiki](https://wiki.lineageos.org/devices/surnia/build "Build for Surnia")
