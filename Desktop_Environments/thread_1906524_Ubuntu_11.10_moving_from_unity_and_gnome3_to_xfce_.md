---
title: "Ubuntu 11.10 moving from unity and gnome3 to xfce xubuntu"
date: 2012-01-09
forum: Desktop Environments
---

### Post by chicom9 on 2012-01-09
First I like to mention that I been using Ubuntu since 9.10. However, after release 11.04 with unity and gnome3 I became really disappointed. For once I felt that Ubuntu was pushing a UI that is driven to tablets and netbooks. I use my desktop at home for doing server/admin work. I hate to have to look or search for programs using a forced task bar which cannot be relocated.
Either way since I do not plan to move away from ubuntu, because I just love their package manager. I decided that my best bet was to use a different UI. The answer was pretty simple I did some searching and I found xfce. From the looks it seem like a real simple GUI and actually it turn-out to be just as great as gnome2. So here is the breakdown for those that will like to get back their Ubuntu simplistic GUI:
[INDENT]1.Backup you existing system. Home user Directory, plus any especial /etc/ configs. I like to backup the hosts, fstab, and X11 files (I'm Using dual monitors and I figure out how to get X to play nicely with out expanding my desktop across). [/INDENT]
[INDENT]2. Get xubuntu:
[ http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/11.10/release/]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/11.10/release/")[/INDENT]
[INDENT]3.Installing Compiz + Emerald in Xubuntu 11.10 Xfce is becoming popular as more and more people are migrating away from Gnome-Shell and Unity. As Xfce is desktop environment which is developed for high performance and low-end systems, so Xfce doesn&#8217;t include Compiz. If you want to migrate to Xubuntu and don&#8217;t want to miss eyecandy provided by Compiz than you can follow this tutorial. First you have to install Compiz, Compiz Settings Manager and Gnome Themes, to do so open terminal and paste following command:[/INDENT]
```
apt-get install compiz compiz-plugins-extra compiz-plugins-main compizconfig-settings-manager gnome-themes
```
[INDENT]4. Than you have to install Emerald but Ubuntu Repository packages of Emerald are not working, so you have to download libemeraldengine and Emerald Chose the correct architecture x86 or x64:[/INDENT]
[http://www.mediafire.com/?0sbu8bd27fca2cu]("http://www.mediafire.com/?0sbu8bd27fca2cu")
Extract the tar some where and either as root or as su - install the packages:
```
dpkg -i libemeraldengine0_0.8.8-0ubuntu0~malteworld1_amd64.deb
```
```
dpkg -i emerald_0.8.8-0ubuntu0~malteworld1_amd64
```
```
dpkg -i emerald-themes_0.2.1-0ubuntu1_all
```
After installing Compiz and Emerald go to
```
Menu> Settings> Settings Manager> Session and Startup> Application Autostart
```
and add Compiz and Emerald in autostart applications list
```
name: compiz
command: compiz --replace ccp
```
```
name: emerald
command: emerald --replace
```
After adding Emerald and Compiz make sure that under
```
Menu> Settings> Settings Manager> Session and Startup> General
```

Credit goes to the persons on these links below:

[http://it-diary.com/tutorials/install-compiz-emerald-xubuntu-11-10/]("http://it-diary.com/tutorials/install-compiz-emerald-xubuntu-11-10/")
[http://superuser.com/questions/348027/can-i-make-ubuntu-11-10s-desktop-look-like-11-04s-ubuntu-classic]("http://superuser.com/questions/348027/can-i-make-ubuntu-11-10s-desktop-look-like-11-04s-ubuntu-classic")

Now for those that enjoy compiz your desktop should be back. I did not try to restore my existing compiz configs, but it may work as well as it did in the gnome session. I did it as part of a clean start. 

You can restore your home directory and back to business. xcfe runs pretty nicely....

---

