---
title: "Compiz stopped working"
date: 2010-07-23
forum: Desktop Environments
---

### Post by xtracool_protik on 2010-07-23
Hey guys,
 I'm using edgers ppa and its been really nice until now, this morning I updated as usual and to my surprise after restart compiz is not working anymore.
 compiz-check does not print anything wrong with my system.
 
 Can anyone tell me wats wrong over here?

 Thanks

---

### Post by linux18 on 2010-07-23
```
 compiz --replace 2>&1 > ~/err.log 
```
this will attempt to restart compiz and create an error log that you can post in case it doesn't work.

---

### Post by xtracool_protik on 2010-07-23
Thanks linux18, it does create err.log but file is empty.
If I do > cat err.log
There is absolutely nothing in that file, I thought it would take some time so I tried waiting, I tried executing same command few times (everytime deleting err.log) with same result

---

### Post by linux18 on 2010-07-23
if the log is empty then no errors are being produced. 
try this: 

> 

-choose recovery mode at grub
-drop to a root prompt
-type telinit 3 and login
-then type xinit 
-when xinit starts type: metacity &  - for ubuntu OR flux/openbox &  - if you have it OR fvwm & -  for xubuntu
-then type gnome panel & -for ubuntu OR xfce4-panel & -for xubuntu
-lastly type nm-applet & -for networking then open a terminal and type ```
 compiz --replace 
```did it work?

---

### Post by xtracool_protik on 2010-07-24
hmm looks like I'll have to restart and go through terminal (command line) will report again once I'm done restart :)

Thanks

---

### Post by vikas.sood on 2010-07-24
compiz-check script can identify compiz related issues. try it 
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by WinRiddance on 2010-07-24
Try installing the Compiz Fusion app from the software center. Easy as pie. After one of my recent updates I lost all of my window border decorations and they remained lost, causing me to restart them manually after every reboot. Once I installed the above app I went ahead and added the command under startup applications. After that everything was fine ... try it ...

---

### Post by hugmenot on 2010-07-24
Edgers broke compiz. Here too, I think two days ago. 

I just went to /var/cache/apt/archives and angled for the packages previous to 2010-07-21 and installed them. 

```
cd /var/cache/apt/archives/
ls -lrt *sarvatt* | grep "2010-07-2[123]" | awk '{print $8}' | cut -f1 -d_ | sort -u | while read line; do ls -lrt *$line* | grep -v "2010-07-2[123]" | tail -n1 | awk '{print $8}'; done
```



You can also use ppa-purge to remove all of xorg-edgers.

---

### Post by xtracool_protik on 2010-07-24
Thanks guys
 linux18: that didn't do any difference thanks for walking me through though 
 vikas.sood: > compiz-check does not print anything wrong with my system. that was my first post
 WinRiddance: I already have fusion-icon and I tried switching between metacity and compiz and then reloading windows manager few times but it didn't help
 Finally thanks a lot hugmenot for confirming that its an issue with edgers, I can wait 2/3 days - which is average time for them to release update. btw I did wat u pointed out in ur post not sure wat should I do next though. Does that automatically points to previous package? or do I need to change packages in synaptics and I used/use purge when I want to upgrade my version (Lucid -> Maverik) edgers r doing great for me (considering I've intel graphics) I don't want to purge(disable) them just because I can't use compiz for 2-3 days

---

### Post by hugmenot on 2010-07-24
There&#8217;s no way to tell if compiz will magically start working again with the next batch of xorg-edgers updates. It could take a while.

I didn&#8217;t want to stay stuck with metacity now so i rolled back all the packages that were installed in the last three days. And compiz started working again afterwards.

The command I gave just looks at all edgers packages that were installed during the last three days and then it prints the previous versions of those.

Let&#8217;s take a look at yours first to make sure it won&#8217;t do harm and if the set looks consistent.

Then you can just append

```
  | xargs sudo dpkg -i
```

to that command to downgrade all. I have no idea which precise package led to breaking compiz (there&#8217;s no debug output whatsoever). I just downgraded them all.

---

### Post by hugmenot on 2010-07-24
Here&#8217;s my list of packages that i downgraded:

```
libgl1-mesa-dev_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt_i386.deb
libgl1-mesa-dri_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt_i386.deb
libgl1-mesa-glx_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt_i386.deb
libglu1-mesa_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt_i386.deb
libglu1-mesa-dev_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt_i386.deb
libpciaccess0_0.11.0+git20100712.e5159771-0ubuntu0sarvatt_i386.deb
libpixman-1-0_0.19.1+git20100719.9897bb4e-0ubuntu0sarvatt_i386.deb
libpixman-1-dev_0.19.1+git20100719.9897bb4e-0ubuntu0sarvatt_i386.deb
mesa-common-dev_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt_i386.deb
xserver-common_2%3a1.8.99.905+git20100714.a2c13f0d-0ubuntu0sarvatt_all.deb
xserver-xephyr_2%3a1.8.99.905+git20100714.a2c13f0d-0ubuntu0sarvatt_i386.deb
xserver-xorg-core_2%3a1.8.99.905+git20100714.a2c13f0d-0ubuntu0sarvatt_i386.deb
xserver-xorg-video-intel_2%3a2.12.0+git20100720.7a4bfaf4-0ubuntu0sarvatt_i386.deb
xserver-xorg-video-vesa_1%3a2.3.0+git20100707.fa1fcd48-0ubuntu0sarvatt_i386.deb
```

you probably don&#8217;t have the -dev packages installed.

---

### Post by xtracool_protik on 2010-07-24
hmm I never assumed that would be the case.
So here is output from given script
> libgl1-mesa-dev_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt~lucid_i386.deb
libgl1-mesa-dri_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt~lucid_i386.deb
libgl1-mesa-glx_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt~lucid_i386.deb
libglu1-mesa_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt~lucid_i386.deb
libglu1-mesa-dev_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt~lucid_i386.deb
libpixman-1-0_0.19.1+git20100719.9897bb4e-0ubuntu0sarvatt~lucid_i386.deb
libpixman-1-dev_0.19.1+git20100719.9897bb4e-0ubuntu0sarvatt~lucid_i386.deb
mesa-common-dev_7.9.0+git20100720.bab484a5-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-apm_1%3a1.2.2+git20100707.0a7bb1b3-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-ark_1%3a0.7.2+git20100707.7cf934ad-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-ati_1%3a6.13.99+git20100720.593eff29-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-chips_1%3a1.2.2+git20100707.d8ce758f-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-cirrus_1%3a1.3.2+git20100707.ebb417ee-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-dummy_1%3a0.3.4+git20100707.51642de7-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-glint_1%3a1.2.4+git20100707.b2590514-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-i128_1%3a1.3.3+git20100707.ff026f65-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-i740_1%3a1.3.2+git20100707.897fee2e-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-intel_2%3a2.12.0+git20100720.7a4bfaf4-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-mach64_6.8.2+git20100707.6da9520f-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-mga_1%3a1.4.12+git20100707.306c46f6-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-neomagic_1%3a1.2.5+git20100707.77faeb22-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-nv_1%3a2.1.17+git20100707.0f220eb6-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-r128_6.8.1+git20100707.1936b9bb-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-radeon_1%3a6.13.99+git20100720.593eff29-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-rendition_1%3a4.2.4+git20100707.0bf606d1-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-sis_1%3a0.10.3+git20100707.75a8a7c5-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-sisusb_1%3a0.9.4+git20100707.43eab862-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-tdfx_1%3a1.4.3+git20100707.83661e56-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-trident_1%3a1.3.4+git20100707.b5d17329-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-v4l_1%3a0.2.0+git20100707.45a5eb8c-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-vesa_1%3a2.3.0+git20100707.fa1fcd48-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-vmware_1%3a11.0.1+git20100707.f307f77a-0ubuntu0sarvatt~lucid_i386.deb
xserver-xorg-video-voodoo_1%3a1.2.4+git20100707.e58d3158-0ubuntu0sarvatt~lucid_i386.deb


Let me know if I can switch back to previous version with no issues.
 And I suppose I should follow similar procedure in future if I face same problem with newer update right?

---

### Post by xtracool_protik on 2010-07-24
awesome that fixed it, Thanks again

---

