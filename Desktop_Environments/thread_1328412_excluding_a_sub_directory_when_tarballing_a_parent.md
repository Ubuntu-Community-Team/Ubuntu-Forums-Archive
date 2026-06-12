---
title: "excluding a sub directory when tarballing a parent directory"
date: 2009-11-16
forum: Desktop Environments
---

### Post by rgagnon on 2009-11-16
Trying to make a backup tarball of my home directory, but I want to exclude the music sub directory in my home directory. I have Ubuntu 9.04 and I've tried the following...

cd /home

tar czvf /tmp/home_backup.tgz --exclude=home/music          I also tried exclude=home/music/*.*  It still backs up the music directory. Can someone help me out?

---

