---
title: "Dell Mini 9: Firefox won't start / Navigation icons don't appear after update."
date: 2009-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sandy Stephens on 2009-01-12
I had a very similar problem on Saturday, only Firefox wouldn't open at all. I tried the above fix and now Firefox opens, but I still don't have bookmarks, setting, forward/back arrows or the ability to play video's within the browser.  I've worked on this issue for hours and it is frustrating to the point of making me want to wipe Ubuntu off the machine and install XP.  Help?

---

### Post by ugm6hr on 2009-01-12
Your issue is clearly completely different.

In Terminal, give the output from:
```
df /dev/sda2
ls /var/cache/apt/archives
free
```

---

### Post by Sandy Stephens on 2009-01-12
Ok...here are the values...

emily@emily:~$ df /dev/sda2
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              3555040   3380796         0 100% /
emily@emily:~$ 
emily@emily:~$ ls /var/cache/apt/archives
acpid_1.0.4-5ubuntu9netbook1_lpia.deb
anacron_2.3-13ubuntu2.1_lpia.deb
app-install-data-commercial_9.2_all.deb
belmont-config-travel_0.42_all.deb
belocs-locales-bin_2.4-2.2ubuntu7netbook1_lpia.deb
bluez-audio_3.26-0ubuntu6netbook1_lpia.deb
bluez-cups_3.26-0ubuntu6netbook1_lpia.deb
bluez-gnome_0.25-0ubuntu2~804um1msg10_lpia.deb
bluez-utils_3.26-0ubuntu6netbook1_lpia.deb
capplets-data_1%3a2.22.1-0ubuntu4.1usg4_all.deb
cheese_2.22.3-0ubuntu1usg7_lpia.deb
dbus_1.1.20-1ubuntu3.1netbook0belmont1_lpia.deb
dbus-x11_1.1.20-1ubuntu3.1netbook0belmont1_lpia.deb
deskbar-applet_2.22.3-0ubuntu1_lpia.deb
desktop-file-utils_0.15-1ubuntu4netbook0belmont1_lpia.deb
desktop-switcher_0.3.0_lpia.deb
eject_2.1.5-6ubuntu1_lpia.deb
eog_2.22.3-0ubuntu2_lpia.deb
esound-common_0.2.40-0ubuntu1~netbook1_all.deb
evolution_2.22.3.1-0ubuntu1netbook8_lpia.deb
evolution-common_2.22.3.1-0ubuntu1netbook8_all.deb
evolution-data-server_2.22.3-0ubuntu2_lpia.deb
evolution-data-server-common_2.22.3-0ubuntu2_all.deb
evolution-exchange_2.22.3-0ubuntu2_lpia.deb
evolution-plugins_2.22.3.1-0ubuntu1netbook8_lpia.deb
firefox-3.0_3.0.3+build1+nobinonly-0ubuntu0.8.04.1netbook2build1_lpia.deb
firefox-3.0_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_lpia.deb
firefox_3.0.3+build1+nobinonly-0ubuntu0.8.04.1netbook2build1_all.deb
firefox_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_all.deb
firefox-3.0-gnome-support_3.0.3+build1+nobinonly-0ubuntu0.8.04.1netbook2build1_lpia.deb
firefox-3.0-gnome-support_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_lpia.deb
firefox-gnome-support_3.0.3+build1+nobinonly-0ubuntu0.8.04.1netbook2build1_all.deb
firefox-gnome-support_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_all.deb
firefox-launchpad-plugin_0.2_all.deb
flashplugin-nonfree_9.0.152.0ubuntu0netbook1_lpia.deb
f-spot_0.4.3.1-0ubuntu1netbook1_lpia.deb
gcalctool_5.22.3-0ubuntu0.1netbook1_lpia.deb
gdebi_0.3.8netbook1_all.deb
gdebi-core_0.3.8netbook1_all.deb
gdm_2.20.7-0ubuntu1.1netbook3belmont2_lpia.deb
gimp_2.4.5-1ubuntu2netbook2_lpia.deb
gimp-data_2.4.5-1ubuntu2netbook2_all.deb
gimp-gnomevfs_2.4.5-1ubuntu2netbook2_lpia.deb
gimp-python_2.4.5-1ubuntu2netbook2_lpia.deb
gnome-about_1%3a2.22.3-0ubuntu1_lpia.deb
gnome-app-install_0.5.2.8-0ubuntu1netbook0belmont1_all.deb
gnome-cards-data_1%3a2.22.3-0ubuntu2netbook3_all.deb
gnome-control-center_1%3a2.22.1-0ubuntu4.1usg4_lpia.deb
gnome-desktop-data_1%3a2.22.3-0ubuntu1_all.deb
gnome-games_1%3a2.22.3-0ubuntu2netbook3_lpia.deb
gnome-games-data_1%3a2.22.3-0ubuntu2netbook3_all.deb
gnome-panel_1%3a2.22.2-0ubuntu1.1netbook2belmont1_lpia.deb
gnome-panel-data_1%3a2.22.2-0ubuntu1.1netbook2belmont1_all.deb
gnome-power-manager_2.22.1-1ubuntu4usg2_lpia.deb
gnome-session_2.22.1.1-0ubuntu2netbook1belmont2_lpia.deb
gnome-system-monitor_2.22.3-0ubuntu2_lpia.deb
gnome-system-tools_2.22.0-0ubuntu9usg3_lpia.deb
grub_0.97-29ubuntu21netbook2_lpia.deb
gstreamer0.10-alsa_0.10.18-3netbook2_lpia.deb
gstreamer0.10-gnomevfs_0.10.18-3netbook2_lpia.deb
gstreamer0.10-plugins-base_0.10.18-3netbook2_lpia.deb
gstreamer0.10-plugins-base-apps_0.10.18-3netbook2_lpia.deb
gstreamer0.10-tools_0.10.18-4ubuntu1netbook1_lpia.deb
gstreamer0.10-x_0.10.18-3netbook2_lpia.deb
gtk2-engines_1%3a2.14.3-0ubuntu2_lpia.deb
gtkhtml3.14_3.18.3-0ubuntu2_lpia.deb
gtkpod-aac_0.99.12-1ubuntu1_lpia.deb
gvfs_0.2.5-0ubuntu2_lpia.deb
gvfs-backends_0.2.5-0ubuntu2_lpia.deb
gvfs-fuse_0.2.5-0ubuntu2_lpia.deb
hal_0.5.11~rc2-1ubuntu8.2netbook2_lpia.deb
hal-info_20080508+git20080601-0ubuntu0.8.04netbook1belmont1_all.deb
initramfs-tools_0.85eubuntu39.2netbook1_all.deb
iproute_20071016-2ubuntu2_lpia.deb
language-installer_0.1-0netbook17_all.deb
libavcodec1d_3%3a0.cvs20070307-5ubuntu7.1_lpia.deb
libavutil1d_3%3a0.cvs20070307-5ubuntu7.1_lpia.deb
libcamel1.2-11_2.22.3-0ubuntu2_lpia.deb
libck-connector0_0.2.3-3ubuntu5belmont1_lpia.deb
libclutter-0.6-0_0.6.0-2netbook1_lpia.deb
libdbus-1-3_1.1.20-1ubuntu3.1netbook0belmont1_lpia.deb
libdrm2_2.3.0.16-0ubuntu2~804um3_lpia.deb
libebook1.2-9_2.22.3-0ubuntu2_lpia.deb
libecal1.2-7_2.22.3-0ubuntu2_lpia.deb
libedata-book1.2-2_2.22.3-0ubuntu2_lpia.deb
libedata-cal1.2-6_2.22.3-0ubuntu2_lpia.deb
libedataserver1.2-9_2.22.3-0ubuntu2_lpia.deb
libedataserverui1.2-8_2.22.3-0ubuntu2_lpia.deb
libegroupwise1.2-13_2.22.3-0ubuntu2_lpia.deb
libesd-alsa0_0.2.40-0ubuntu1~netbook1_lpia.deb
libexchange-storage1.2-3_2.22.3-0ubuntu2_lpia.deb
libgdata1.2-1_2.22.3-0ubuntu2_lpia.deb
libgdata-google1.2-1_2.22.3-0ubuntu2_lpia.deb
libgimp2.0_2.4.5-1ubuntu2netbook2_lpia.deb
libgksu2-0_2.0.5-1ubuntu5.2_lpia.deb
libglib2.0-0_2.16.4-0ubuntu3_lpia.deb
libglibmm-2.4-1c2a_2.16.4-0ubuntu1_lpia.deb
libgnome2-0_2.22.0-0ubuntu1netbook1_lpia.deb
libgnome2-common_2.22.0-0ubuntu1netbook1_all.deb
libgnome-desktop-2_1%3a2.22.3-0ubuntu1_lpia.deb
libgnome-window-settings1_1%3a2.22.1-0ubuntu4.1usg4_lpia.deb
libgstreamer0.10-0_0.10.18-4ubuntu1netbook1_lpia.deb
libgstreamer-plugins-base0.10-0_0.10.18-3netbook2_lpia.deb
libgtkhtml3.14-19_3.18.3-0ubuntu2_lpia.deb
libgtksourceview2.0-0_2.2.2-0ubuntu1_lpia.deb
libgtksourceview2.0-common_2.2.2-0ubuntu1_all.deb
libgvfscommon0_0.2.5-0ubuntu2_lpia.deb
libgweather1_2.22.3-0ubuntu2_lpia.deb
libgweather-common_2.22.3-0ubuntu2_all.deb
libhal1_0.5.11~rc2-1ubuntu8.2netbook2_lpia.deb
libhal-storage1_0.5.11~rc2-1ubuntu8.2netbook2_lpia.deb
libid3tag0_0.15.1b-10_lpia.deb
libldap-2.4-2_2.4.9-0ubuntu0.8.04.1_lpia.deb
libmetacity0_1%3a2.22.0-0ubuntu4.netbook2_lpia.deb
libmp4v2-0_1%3a1.6dfsg-0.2ubuntu1_lpia.deb
libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.5_lpia.deb
libnss3-1d_3.12.0.3-0ubuntu0.8.04.4_lpia.deb
libpanel-applet2-0_1%3a2.22.2-0ubuntu1.1netbook2belmont1_lpia.deb
libpoppler2_0.6.4-1ubuntu3.1_lpia.deb
libpoppler-glib2_0.6.4-1ubuntu3.1_lpia.deb
libpostproc1d_3%3a0.cvs20070307-5ubuntu7.1_lpia.deb
libpurple0_1%3a2.4.3-0ubuntu1~hardy1netbook3_lpia.deb
libsmbios1_0.13.10-1ubuntu1.1netbook1_lpia.deb
libsoup2.4-1_2.4.1-1ubuntu1_lpia.deb
libusplash0_0.5.19netbook3_lpia.deb
libwnck22_2.22.3-0ubuntu1_lpia.deb
libwnck-common_2.22.3-0ubuntu1_all.deb
libxine1_1.1.11.1-1ubuntu3.1_lpia.deb
libxine1-bin_1.1.11.1-1ubuntu3.1_lpia.deb
libxine1-console_1.1.11.1-1ubuntu3.1_lpia.deb
libxine1-ffmpeg_1.1.11.1-1ubuntu3.1_lpia.deb
libxine1-misc-plugins_1.1.11.1-1ubuntu3.1_lpia.deb
libxine1-plugins_1.1.11.1-1ubuntu3.1_all.deb
libxine1-x_1.1.11.1-1ubuntu3.1_lpia.deb
libxslt1.1_1.1.22-1ubuntu1.2_lpia.deb
linux-image-2.6.24-19-lpia_2.6.24-19.41netbook11_lpia.deb
linux-restricted-modules-2.6.24-19-lpia_2.6.24.13-19.45netbook5_lpia.deb
linux-restricted-modules-common_2.6.24.13-19.45netbook5_all.deb
linux-ubuntu-modules-2.6.24-19-lpia_2.6.24-19.29netbook16_lpia.deb
lock
lsb-base_3.2-4ubuntu1netbook1_all.deb
lsb-release_3.2-4ubuntu1netbook1_all.deb
maximus_0.4.2netbook0belmont1_lpia.deb
metacity_1%3a2.22.0-0ubuntu4.netbook2_lpia.deb
metacity-common_1%3a2.22.0-0ubuntu4.netbook2_all.deb
module-init-tools_3.3-pre11-4ubuntu5.8.04.1_lpia.deb
nautilus-sendto_0.13.2-0ubuntu2_lpia.deb
network-manager-gnome_0.6.6-0ubuntu3usg6_lpia.deb
oem-config_1.37.2netbook9belmont2_lpia.deb
oem-config-gtk_1.37.2netbook9belmont2_lpia.deb
partial
pciutils_1%3a2.2.4-1.1ubuntu5_lpia.deb
pidgin_1%3a2.4.3-0ubuntu1~hardy1netbook3_lpia.deb
pidgin-data_1%3a2.4.3-0ubuntu1~hardy1netbook3_all.deb
pm-utils_0.99.2-3ubuntu10belmont2_all.deb
poppler-utils_0.6.4-1ubuntu3.1_lpia.deb
procps_1%3a3.2.7-5ubuntu3_lpia.deb
python2.5_2.5.2-2ubuntu4.1_lpia.deb
python2.5-minimal_2.5.2-2ubuntu4.1_lpia.deb
python-gobject_2.14.2-0ubuntu1_lpia.deb
rhythmbox_0.11.5-0ubuntu8netbook1belmont3_lpia.deb
system-config-printer-common_0.7.81+svn1976-0ubuntu9netbook1_all.deb
system-config-printer-gnome_0.7.81+svn1976-0ubuntu9netbook1_all.deb
totem_2.22.1-0ubuntu2netbook0belmont3_all.deb
totem-common_2.22.1-0ubuntu2netbook0belmont3_all.deb
totem-gstreamer_2.22.1-0ubuntu2netbook0belmont3_lpia.deb
totem-mozilla_2.22.1-0ubuntu2netbook0belmont3_all.deb
totem-plugins_2.22.1-0ubuntu2netbook0belmont3_lpia.deb
tzdata_2008e-1ubuntu0.8.04_all.deb
ubufox_0.5-0ubuntu1belmont6_all.deb
ubuntu-gdm-themes_0.29usg6_all.deb
ume-config-belmont_0.101.4_all.deb
ume-config-belmont_0.77.3_all.deb
update-manager_1%3a0.87.30netbook0belmont2_all.deb
update-manager-core_1%3a0.87.30netbook0belmont2_lpia.deb
update-notifier_0.70.9netbook1_lpia.deb
update-notifier-common_0.70.9netbook1_all.deb
usplash_0.5.19netbook3_lpia.deb
usplash-theme-ubuntu_0.18ubuntu0netbook1_lpia.deb
webfav_1.0ubuntu5_all.deb
xdg-user-dirs_0.10-1ubuntu1netbook0belmont2_lpia.deb
xscreensaver-data_5.04-4ubuntu1netbook1_lpia.deb
xscreensaver-gl_5.04-4ubuntu1netbook1_lpia.deb
xserver-xorg-video-intel_2%3a2.2.1-1ubuntu13.6_lpia.deb
xserver-xorg-video-psb_0.16.0+repack-0ubuntu1~804um5netbook1_lpia.deb
xsltproc_1.1.22-1ubuntu1.2_lpia.deb
xulrunner-1.9_1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1_lpia.deb
xulrunner-1.9_1.9.0.5+nobinonly-0ubuntu0.8.04.1netbook0build1_lpia.deb
xulrunner-1.9-gnome-support_1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1_lpia.deb
xulrunner-1.9-gnome-support_1.9.0.5+nobinonly-0ubuntu0.8.04.1netbook0build1_lpia.deb
yelp_2.22.1-0ubuntu2.8.04.3.1netbook1_lpia.deb
emily@emily:~$ 
             total       used       free     shared    buffers     cached
Mem:        505080     491372      13708          0      76232     170848
-/+ buffers/cache:     244292     260788
Swap:            0          0          0
emily@emily:~$

---

### Post by ugm6hr on 2009-01-12
Your problem:
```
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/sda2 3555040  3380796      0   100% /
```

You have filled your HD.

---

### Post by ugm6hr on 2009-01-12
Suggestions (cut and paste):

Delete Trash:
```
sudo chown -R emily ~/.local/share/Trash
rm -rf ~/.local/share/Trash/*
```

Copy update files from "/var/cache/apt/archives" to an external USB flash stick, then delete them:
```
sudo apt-get clean
```

Delete / backup any personal files (and re-delete trash as above).

Then:
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
```

Then post the output from:
```
sudo apt-get -s upgrade
```

---

### Post by Sandy Stephens on 2009-01-12
Ok...so I did all that. I think... 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
emily@emily:/var/cache/apt/archives$ 

My question is, I bought this machine for my teenage daughter form Christmas.  How did she fill the HD in 2 weeks?!

---

### Post by ugm6hr on 2009-01-12
> **Sandy Stephens said:**
> My question is, I bought this machine for my teenage daughter form Christmas.  How did she fill the HD in 2 weeks?!

You bought a 4GB HD version.  Unfortunately, Ubuntu takes about 3.5GB in itself (with all applications).  Hence, in the modern era of video / music etc on computers, it doesn't take much to fill it.  Plus, those downloads took about 200MB too.

Make sure you have some free space now:
```
df /dev/sda2
```

Ensure all the updates have definitely been installed correctly (this should do nothing):
```
sudo apt-get upgrade
```

Remove any residual upgrade files:
```
sudo apt-get clean
```

Then try and avoid filling the HD again in future.  Best to check how much free space you have before agreeing to updates in future.  Unfortunately, I think it was remiss of Dell to sell Ubuntu devices with a 4GD HD.  I would suggest storing all files on a separate SD card or a USB flash stick.

It is possible to remove any unused applications, although I suspect that won't make a great deal of difference.

Hope that sorts out your problems for now, anyway.

---

### Post by Sandy Stephens on 2009-01-12
Things are already a LOT better.  but..now I get this..
emily@emily:~$ sudo apt-get upgrade
[sudo] password for emily: 

Any idea what password its looking for?

You have been a huge help.

---

### Post by ugm6hr on 2009-01-12
> **Sandy Stephens said:**
> Any idea what password its looking for?

Did it not ask for a password any of the other times you used a "sudo" command?

It certainly should have done.  It will also have asked for a password when you tried to install the updates the first time around.

It is the password that you set up for "emily"

EDIT: I have just realised I made a small error with the deleting Trash command earlier.  It won't have done any damage - but you should repeat that process again using the new command in post #5.

---

### Post by Sandy Stephens on 2009-01-12
the first times it didnt.. Odd.. The password is ...snip... but its not responding to me typing numbers.

OK... I got it to work!  I have 82% of the hard drive free. Ive set firefox to always delete cache/history etc. which should help and I gave my daughter a thumb drive. 

You have been a tremendous help! Thank you so much!

---

### Post by ugm6hr on 2009-01-12
> **Sandy Stephens said:**
> the first times it didnt.. Odd.. The password is xxxxx but its not responding to me typing numbers.

Does it require a password to log in?  Or does it auto login?

PS: I used my moderator power to remove your password - it is best not to reveal such details on a public forum.

PPS: I have just realised I made a small error with the deleting Trash command earlier. It won't have done any damage - but you should repeat that process again using the new command in post #5 to ensure everything is returned to normal.

---

### Post by Sandy Stephens on 2009-01-25
So... I once again allowed my daughters mini to update and again firefox will not open.  I've tried everything here and this time it hasn't helped. the hard drive is NOT full.. so what should I do?

---

### Post by ugm6hr on 2009-01-26
Try this:
```
ls -l ~/.mozilla
```

It should reply (post your output back here if you don't understand):
```
drwx------ 3 user user 4096 2009-01-06 08:34 extensions
drwxr-xr-x 3 user user 4096 2009-01-23 07:04 firefox
lrwxrwxrwx 1 user user   29 2009-01-26 07:13 web browser -> /home/user/.mozilla/firefox
lrwxrwxrwx 1 user user   29 2009-01-10 10:05 web browser.bak -> /home/user/.mozilla/firefox
```

If there is no "firefox" entry in that list, then that is the problem.  Did you apply a "fix" to correct the loss of firefox bookmarks etc after the last update?  Unfortunately, this update was designed to fix the previous problem, but has made a mess agaian for some people who manually fixed things themselves.

If you renamed "firefox" to "web browser" the first time then you need to rename "web browser.bak" to "firefox"

If that isn't the problem - post your "ls -l ~./mozilla" here, and try running firefox from Terminal (and post output): 
```
firefox
```

---

### Post by ugm6hr on 2009-01-28
This is likely your problem too:

[http://ubuntuforums.org/showthread.p...08#post6628108](http://ubuntuforums.org/showthread.p...08#post6628108)

Read through and check posts 8-10 for a likely reason why things aren't working (and the solution).

---

