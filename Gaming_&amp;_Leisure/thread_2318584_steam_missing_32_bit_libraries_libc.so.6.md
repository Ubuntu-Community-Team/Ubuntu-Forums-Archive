---
title: "steam missing 32 bit libraries libc.so.6"
date: 2016-03-27
forum: Gaming &amp; Leisure
---

### Post by bobby26 on 2016-03-27
So I just got Ubuntu 15.10.3 last week and tried to install steam. I got it from the site because it isn't available from synaptic, ubuntu software center, or the terminal. when i download it, it says it needs to install 
[h=2][SIZE=2]these additional packages: libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386[/SIZE][/h]
This process fails every time by saying they have no installation candidate and then when i leave the terminal it says I am missing libc.so.6.
          I have also tried reinstalling several times and have researched for quite a few hours and yet to find a solution. I tried following the advice given in this thread ([http://ubuntuforums.org/showthread.php?t=2317240](http://ubuntuforums.org/showthread.php?t=2317240)) but it said to reinstall from synaptic. However, once I uninstalled steam-launcher and steam:i386 they wouldn't show up in synaptic or on the terminal.
      Any advice is greatly appreciated!

---

### Post by MikeCyber on 2016-03-28
There are two steam packages. One from synaptic and the other download   from steam. I would remove all, including in your home the hidden steam   folder. 
cd ~
rm -rf .steam
Than try the other one. Also never use root unless you have to. So get rid of ~/.steam and try again.

---

