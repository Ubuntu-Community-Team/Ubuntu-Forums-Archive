---
title: "Switch from ATI to Nvidia"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Niroth on 2005-10-25
Hey All-

My old ATI video card died a few days ago and I replaced it with an Nvidia card... i have been in windows (Must.. play.. AoE3 :-p) for the past few days and when i just went to boot into Ubuntu I (not surprisingly) came up to a good old fashioned login prompt with an Xserver unable to start error.  I tried doing some apt-cache searches to find an Nvidia driver but wasn't really sure how I should proceed to get X working again.. I probably need to remove some ATI packages as well?

Thanks,

---

### Post by migueljacq on 2005-10-25
Not entirely sure but maybe you need to run 

dpkg-reconfigure xserver-xorg

from the terminal and reconfigure the settings to nvidia.

when i installed ubuntu and my screen was all messed up, I used the guide to install the nvidia driver

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by Niroth on 2005-10-25
Was just thinking that from looking at a thread about upgrading drivers.. will try that

---

### Post by Niroth on 2005-10-25
I tried running an dpkg --configure xserver-xorg and was told that it is already configured.. i tried using -reconfigure and --reconfigure but it says the command can not be found, how else would i go about reconfiguring xserver?

---

### Post by migueljacq on 2005-10-25
Are you sure you put dpkg-reconfigure, with no spaces?

---

### Post by Niroth on 2005-10-26
[QUOTE=migueljacq]Are you sure you put dpkg-reconfigure, with no spaces?[/QUOTE]

Yup, sorry, I am a completely fool.. i was thinking it was a typo that there was no space before reconfigure, silly me.  Thanks!  Got GNOME to come up and was able to install the Nvidia drivers easy as pie, excellent.

---

### Post by migueljacq on 2005-10-26
That got me the first time too :-) Glad to hear it's working

---

