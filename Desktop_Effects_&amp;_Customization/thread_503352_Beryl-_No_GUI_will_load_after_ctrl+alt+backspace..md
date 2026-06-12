---
title: "Beryl- No GUI will load after ctrl+alt+backspace."
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by SerialSniper on 2007-07-17
Hello, Iam relatively new to linux & ubuntu so please bear with me.

I followed the follwing guide to try to install beryl on new instalation of Ubuntu 7.04. 

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#The_123_NoFile_Automatic_Installation_Method](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#The_123_NoFile_Automatic_Installation_Method)

I followed the steps and all went well apart from the end. ''3. Now Logout and then press [CTRL+ALT+BACKSPACE] to restart xorg''

Now I have read the warning at the bottom...it should be at the TOP imo...

''WARNING: THIS HAS BEEN KNOWN TO BREAK FEISTY IN SOME INSTANCES, BREAKING THE WHOLE GUI SYSTEM AND NOT ALLOWING THE UBUNTU GUI TO LOAD SINCE NVIDIA CANNOT LOAD THE KERNEL MODULE

LOAD THE NVIDIA DRIVERS SEPARATELY --THEN --Execute the script above. Some repositories have out-of-date nVidia drivers and the script above is really hard to get undone. ''

This is what happened to me. So my question is how do I ''...LOAD THE NVIDIA DRIVERS SEPARATELY --THEN --Execute the script above.''

Please help. Thanks (I realize I could reinstall ubuntu again but I want to learn as much as I can about linux) reinstaling is usually the only way to fix windows but i hear linux isnt supost to be like that. lol

PS: I tried to post this over at the beryl forums but for some reason I cant register an account.

---

### Post by SerialSniper on 2007-07-17
Ok...so from the terminal in recovery mode. I tried:

apt-get remove nvidia-glx

and removed it I think.

Then,

apt-get install nvidis-glx

nvidia-xconfig

and it replaced the xorg config file (I think)

but still the same poblem. Do I have to type that script from the guide in recovery mode? Is there a way to copy&paste? :)

---

### Post by SerialSniper on 2007-07-17
dpkg-reconfigure xserver-xorg did the trick! :)

Selected nv driver then it asks you 20+ questions. Reboot and all is good.

---

### Post by SerialSniper on 2007-07-18
I still can't install the nvidia drivers...I have a 8800GTS 320MB. I read the newer 88xx card are not supported, but this was april i think. Should I be able to install the drivers??

---

