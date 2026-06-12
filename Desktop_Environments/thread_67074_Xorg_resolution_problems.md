---
title: "Xorg resolution problems"
date: 2005-09-19
forum: Desktop Environments
---

### Post by VyRuZ on 2005-09-19
For this problem i'm having i shall detail every bit of it so that you can help me.

The first pc i got was a Pentium II at 450MHz ... Yesterday my dad bought a Pentium III original HP and i put my HDD and my DVD-RW LITE-ON in it. 

SO the Configuration for it now is

CPU: Intel P3 at 1000MHz
HDD: 26GB Maxtor 
VIDEO: Cirrus Logic GD 5446
RAM: 256MB

When i started the machine, GDM and X.org wouldn't start because it wouldn't detect my *new* video card. So i did what i thought was right... Delete /etc/X11/xorg.conf so that it would probably reset it's configuration and get the new hw detected.

Good thing is it worked. Didn't detect my hw properly but after i updated the xorg version from auto-update the new graphics card would be properly detected and xorg.conf now is there and has correct data in it....

Problem is- Xorg won't read that config... Config says my pc supports 1024x768... but i only get 640x480..

I had an idea to do xorgconfig but i don't know much info about my hardware for all it asks.

Is there a way to *reset* or point Xorg to that config so i can get a more proper 1024x768 resolution ??

Thanks!

---

### Post by Freddy on 2005-09-19
Open up your xorg conf file, write sudo editor /etc/X11/xorg.conf in a console (editor= the editor of your choice) Take a look in the screen section, there you can find which modes you can use, make additions for those you wan't if you can't find those.

Maybe you need to change HorizSync and VertRefresh to, in that case take a look your monitor manual, it's crucial that you only use those written in your manual.

Try this first, there are other ways to, such as make yourself a new file with xorgconfig but thats not recommended and maybe there are other Debian/(K)ubuntu ways to do this, that I don't know but I think som hacking in your confile will correct your problem.  /// Freddan

---

### Post by VyRuZ on 2005-09-19
Thanks for answering my friend.
But the xorg.conf file is a configured as it can be. All modes are set correctly, as identified by X.org itself. Like i said, after i autoupdated it, it properly detected my hardware, but won't read that xorg.conf file....

---

### Post by Freddy on 2005-09-19
Ok there you lost me, I have never heard of a problem like that before. Are you really sure that your refresh rates a correct to, cause as  you explain it it's not even sure that it's gonna help to build a new one with xorgconfig. 

Well, I will have to leave this problem cause I have no other ideas of whats wrong, sorry  /// Freddan

---

### Post by VyRuZ on 2005-09-19
You were right. Not even a succesfull xorgconfig helps... Im still trapped in this 640x480. Is there no way to FORCE it to go 1024x768. The video card can do 1024x768 as my dad used that on Windows. 
The monitor also can do 1024x768 as it is the same one used on my last configuration, when i used 1024x768.

The only way i could make it would be to reinstall ubuntu/kubuntu. But this mobo won't boot cd's...

---

### Post by Xian on 2005-09-19
[QUOTE=VyRuZ]Is there a way to *reset* or point Xorg to that config so i can get a more proper 1024x768 resolution ??[/QUOTE]
1. Check this log file: /var/log/Xorg.0.log

You'll see a line that will tell you what config file is being used.
Here is my output:

(==) Using config file: "/etc/X11/xorg.conf"

2. Issue this command to see the supported resolutions:

```
$ xrandr
```

---

### Post by VyRuZ on 2005-09-19
Hmm guess X.org doesn't like the amount of memory on my video card... i found the problem... the config is good, but thanks to Xian's idea to check the log, i found the problem...  

(II) CIRRUS(0): Not using default mode "1024x768" (insufficient memory for mode)

But not even 800x600 works and im 110% 800x600 WORKS!!

---

### Post by fergie4000 on 2007-05-11
very sorry to bump such an old topic, but i too am having problems with a Cirrus Logic GD 5446 only running at 640x480 i get the same errors as mentioned above and am using basically the same setup P3 etc. just wondering if it has been resolved.

---

### Post by wgandhi on 2007-05-11
Guys

Have you tried using the command :

sudo dpkg-reconfigure   xserver-xorg

It will take you through all the X setup options. Make sure you select the correct driver and allow enough video RAM.

Hope this works..

-Wish

---

