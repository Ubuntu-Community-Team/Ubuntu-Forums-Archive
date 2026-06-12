---
title: "Steam for Linux failing to Download/Install Ubuntu 13.04 and 12.10"
date: 2013-05-10
forum: Gaming &amp; Leisure
---

### Post by mrkernalpanic on 2013-05-10
Hi, I am a gamer that usually has to boot into windows to game, Since this new Steam for Linux, ive been trying to install it! I am not a noob (relatively) But i havent been able to find a solution anywhere. When i try to install it begins, attempts to download gets to about 250kb out of 2.5mb and then gives me this error : "Failed to Download package files. Check your internet connection" Although my connection is fine, So i try to download the .deb directly and it fails. And in terminal with ```
 sudo dpkg -i steam-latest.deb
``` . Any ideas? I thought a dodgy repo but when i ```
sudo apt-get update
``` it completes with no errors.
 Thanks Ben

---

### Post by mrkernalpanic on 2013-05-10
HEY GUYS! I fixed it! All i had to do was install Curl and Jockey-Common which were dependencys. So i did ```
sudo apt-get install jockey-common
``` ```
sudo apt-get install curl
``` ```
sudo apt-get -f install
``` then it all worked!

---

