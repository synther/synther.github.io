---
layout: post
title: Restore And Mount Clonezilla *.gz Files (on Ubuntu 14.04)
---

### I Use NTFS

Install `partclone` at first.

```
sudo apt-get install partclone
```

Extract a large image from `*.gz.*` files.

```
cat sda1.ntfs-ptcl-img.gz.a* | gzip -d -c \
| sudo partclone.ntfs -r -s - -W -O restored.img
```

todo: explain every option

Mount this image easily.

```
sudo mkdir /mnt/restored
sudo mount -t ntfs-3g restored.img /mnt/restored
...do your work here...
sudo umount /mnt/restored
```

### I Use ext4

Install `partclone` at first.

```
sudo apt-get install partclone
```

Extract a large image from `*.gz.*` files.

```
cat sda2.ext4-ptcl-img.gz.a* | gzip -d -c \
| sudo partclone.ext4 -r -s - -W -O restored.img
```

Mount this image easily

```
sudo mkdir /mnt/restored
sudo mount restored.img /mnt/restored
...do your work here...
sudo umount /mnt/restored
```
