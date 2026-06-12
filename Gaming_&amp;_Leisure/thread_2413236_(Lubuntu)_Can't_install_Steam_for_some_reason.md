---
title: "(Lubuntu) Can't install Steam for some reason?"
date: 2019-02-22
forum: Gaming &amp; Leisure
---

### Post by otto+van+chotto on 2019-02-22
So I finally decided to install Linux on my main PC and after making sure everything is up to date, you know the classic: ```
sudo apt update && sudo apt upgrade
``` I decided to install Steam but for some reason Discover gives me the following error when I try to install it: dependency resolution failed. Just wondering how can I get Steam working, thanks!

---

### Post by oldrocker99 on 2019-02-22
The way, in fact the only way, to install Steam is this:
```
sudo apt install steam
```
This will pull in all the dependencies, and you should be all set.

---

### Post by 1s3ct0wn on 2019-02-24
Lubuntu 18.04 for some reason steam uninstalled it self I couldn't run it with command: steam

Re-installed it with sudo apt-get install steam, and it worked, logged it and all of the games that were installed previously were showing as not installed.
For some reason I though its good idea to delete the folder manually of steam and reinstall it again, went in .local/share and deleted .steam it was about 50 Gbs, next thing I did sudo apt-get remove steam and then sudo apt-get install steam.
Now this is the error I get:
pc@PC:~$ steam
tar: This does not look like a tar archive
xz: (stdin): File format not recognized
tar: Child returned status 1
tar: Error is not recoverable: exiting now
find: &#8216;/home/pc/.steam/ubuntu12_32/steam-runtime&#8217;: No such file or directory


Thanks for taking the time to read.

---

### Post by 1s3ct0wn on 2019-02-24
Running this command solved the issue for me:
> mkdir /home/$USER/.steam/ubuntu12_32/steam-runtime

---

### Post by wsmith198729 on 2019-02-24
Use the command sudo apt install steam-installer in terminal

---

### Post by TechnoJunky on 2019-03-09
None of your previously installed games will show installed because you haven't redownloaded and installed them on the new system.  The only way your previously installed games will show up as installed on a new installation of Linux is if you have a separate /home partition that you never format, and install your games there.  Then if you decide to reinstall Linux or switch distros, remount /home (DO NOT FORMAT), and bingo bango, your Steam games are preinstalled, after in reinstall Steam.  But installing Linux for the first time, no games available till you install them.

---

### Post by flyn633 on 2019-03-15
Check **[this article]("https://linuxflips.com/install-steam-on-ubuntu-linux-and-play-games/")** to install steam on Ubuntu. Also make sure your device meets the Hardware Requirements.

---

