---
title: "Somebody please help"
date: 2006-10-06
forum: Desktop Environments
---

### Post by sheine on 2006-10-06
In the last couple of days, we were offered large upgrades which I foolishly accepted. Now I cannot get into the graphic mode. I have even tried xf86config and XF86Setup but they do not work with Ubuntu. Until the upgrades, Ubuntu was working well for me. I do not want to reinstall Ubuntu because I will lose files.

How can I get into gnome again?

---

### Post by towsonu2003 on 2006-10-06
you can try sudo dpkg-reconfigure xserver-xorg -that's what you do in ubuntu instead of xf86config. 

if that won't work, attach your /var/log/Xorg.0.log here. Hopefully it will give us a clue. 

What were the upgrades? I'm up to date and I'm still alive (knock on wood) :)

---

### Post by sheine on 2006-10-06
sudo dpkg-reconfigure xserver-xorg gives the message "xserver-xorg is broken or not fully installed".

I then tried dpkg -i xserver-xorg and got "cannot access archive: No such file or directory".

---

### Post by towsonu2003 on 2006-10-06
make sure you're connected to the web and do
sudo apt-get update
sudo apt-get reinstall xserver-xorg

if it asks you to remove packages, don't. paste output here.

---

### Post by sheine on 2006-10-06
Thanks to towsonu2003, I have made real progress. sudo apt-get install xserver-xorg got my gnome desktop back. 

There is still a problem that I did not have before. While the Opera browser seems to work, Firefox keeps closing down. When I restart Firefox, I get a message about Bon Echo failing and whether I want to restart the previous session or start a new session. Whichever I do, it fails again. I tried to reinstall Firefox with the synaptic package manager. I shall try to remove it and then reinstall it.

---

### Post by sheine on 2006-10-06
I uninstalled and then reinstalled firefox. It did not cure the problem.

I think that I will switch to Puppy until the final version of Edgy EFT comes out.

---

### Post by towsonu2003 on 2006-10-06
> **sheine said:**
> Thanks to towsonu2003, I have made real progress. sudo apt-get install xserver-xorg got my gnome desktop back. 

There is still a problem that I did not have before. While the Opera browser seems to work, Firefox keeps closing down. When I restart Firefox, I get a message about Bon Echo failing and whether I want to restart the previous session or start a new session. Whichever I do, it fails again. I tried to reinstall Firefox with the synaptic package manager. I shall try to remove it and then reinstall it.

Let firefox be your only problem :)

Three ways to fix (choose one): 
1. launch friefox from command line to see if you understand the output of the crash: ```
firefox
```
2. Try salvaging the existing Firefox:
a. launch the terminal to wirte commands :p
b. move your profile to see if it helps with ```
mv .mozilla .mozilla-backup
```
b. launch firefox from inside the terminal with ```
firefox
```
if it fixed stuff, your bookmarsk are under /home/yourusername/.mozillabackup/randomnumbersandletters.default/bookmarks.html
-----
if that crashes again, time for you to file a bug report by doing:
c. launch firefox with the following command ```
strace -o ~/Desktop/firefoxcrash.log firefox
```
don't input passwords, don't go to private web sites... if it crashes, file a bug report on launchpad.net and attach the firefoxcrash.log (it's on your desktop) to the bug

3. Getting a new firefox:
see [https://help.ubuntu.com/community/FirefoxNewVersion#head-26d21f8b635c06a9858f7bef322b3821c7545598](https://help.ubuntu.com/community/FirefoxNewVersion#head-26d21f8b635c06a9858f7bef322b3821c7545598) which should do the job for you temporarily.

---

### Post by sheine on 2006-10-07
I chose option 2. After doing mv .mozilla .mozilla-backup, firefox seems to have stopped crashing. I have found my old bookmarks in subfolders of ./mozilla-backup (not the ones in the previous post) but I cannot transfer them to .mozilla.

---

### Post by sheine on 2006-10-07
"The cat came back". I went to the Washington Post website and tried to view the Mars pictures. It required the installation of flash-player. As soon as I installed it, firefox started to crash again. I repaired the damage with mv .mozilla .mozilla-backup.

---

### Post by towsonu2003 on 2006-10-07
see [http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/) for flash installation. but remember **not** to follow the ```
FIREFOX_DSP="aoss"
``` reccomendation in that site. aoss makes firefox very very unstable (prone to crashes). when u can't hear sound in a flash site, and you need to hear the sound, launch firefox from command line with ```
aoss firefox
``` to visit that site (no need to close other running firefox instances afaik). 

as per the old bookmarks, copy them over to your desktop (using nautilus) and use the Bookmarks > Manage Bookmarks > File > Import in firefox to import the bookmarks.html you copied to your desktop. Bad news: when you did "mv .mozilla .mozilla-backup" the second time, I think you lost the old bookmarks.html you had. when moving (mv) or copying (cp) your profiles (to a backup), try to change the name of the new folder name. so you will have your backups usable for everytime you did a backup.

In the future, I think this link will be very helpful: [http://kb.mozillazine.org/Firefox_crashes](http://kb.mozillazine.org/Firefox_crashes) shows troubleshooting steps in a way much better way than I did :)

---

