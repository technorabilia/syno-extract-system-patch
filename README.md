# Introduction
The latest Synology pat files cannot be extracted using the `tar` command anymore and require special handling.

Based on https://github.com/pocopico/tinycore-redpill.

# How to use
Git clone this repository.
```
git clone https://github.com/technorabilia/syno-extract-system-patch.git
```
Build the image.
```
cd syno-extract-system-patch
docker build --tag syno-extract-system-patch .
```
Place the pat file you want to extract in `~/data/in`.
```
$ ls ~/data/in
DSM_DS723+_42962.pat
$
```
Execute the following command.
```
docker run -it --rm -v ~/data:/data syno-extract-system-patch \
  syno_extract_system_patch \
  /data/in/DSM_DS723+_42962.pat \
  /data/out/.
```
The extracted pat file will be in `~/data/out`.
```
$ ls ~/data/out
bios.ROM                 grub_cksum.syno  indexdb.txz   rd.gz               updater
checksum.syno            GRUB_VER         model.dtb     synohdpack_img.txz  VERSION
DiskCompatibilityDB.tar  H2OFFT-Lx64      packages      Synology.sig        zImage
expired_models           hda1.tgz         platform.ini  texts
$ 
```
