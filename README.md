# Yocto kirkstone manifest

This repo for raspberrypi yocto (kirkstone) development.

#### Build environment setup

First we need to install the host packages by executing the below script.

```bash
git clone https://github.com/spikynavin/scripts.git
cd scripts
sh yocto-host-pkg-install.sh
```
It will install all the host packages.

Note: This script is used for kirkstone version and also supports ubuntu-18.04 & 20.04. depending on distro version it  will install the packages.

Once the environment setup done. we need to do repo init by using the below cmd.

#### Install repo tool
```bash
curl https://storage.googleapis.com/git-repo-downloads/repo > repo
chmod a+x repo
sudo mv repo /usr/bin/repo
```
#### Sync source
```bash
repo init -u https://github.com/spikynavin/yocto-manifest -b main -m manifest-raspberrypi.xml --repo-url=https://gerrit.googlesource.com/git-repo --repo-branch=stable --no-repo-verify
repo sync -c
```
Once source synced try the below cmd.

#### Yocto build for raspberrypi
```bash
cd workspace
source build.sh
bitbake core-image-minimal
bitbake core-image-minimal -c populate_sdk
```
Once the build done. check the image in
```bash
ls workspace/build-sdk1/tmp/deploy/image/
ls workspace/build-sdk1/tmp/deploy/sdk/
```
There we can find the image and sdk.
