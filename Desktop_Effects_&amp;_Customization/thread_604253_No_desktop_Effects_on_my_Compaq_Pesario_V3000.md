---
title: "No desktop Effects on my Compaq Pesario V3000"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by waggygee on 2007-11-05
I managed to install Gutsy on my Latop (intel core2 duo 1.5ghz, 2gb ram, 160gb HDD etc)... After sometime I found this thread that helped me to get my wireless working [http://ubuntuforums.org/showthread.php?t=405990&highlight=firmware+broadcom+43xx+chipset+family](http://ubuntuforums.org/showthread.php?t=405990&highlight=firmware+broadcom+43xx+chipset+family)
After I got this out of the way, I noticed that my desktop effects didnt work, I installed the Advanced Desktop Effects Settings (using my WLAN :) ) but still, I dont get any desktop effects (I did enable restricted drivers)

---

### Post by smartboyathome on 2007-11-06
What Video Card do you have? Yours may be one of the few which are blacklisted.

---

### Post by waggygee on 2007-11-06
> **smartboyathome said:**
> What Video Card do you have? Yours may be one of the few which are blacklisted.

Im not sure of the exact model but I know it's intel. Do you know a command that I can run inorder to find out the exact model?

---

### Post by Forlong on 2007-11-06
> **waggygee said:**
> Do you know a command that I can run inorder to find out the exact model?
```
lspci | grep VGA
```
And also post the output of ```
compiz
``` in a terminal.

---

### Post by syncmasta on 2007-11-06
Well you're in luck, I happen to be a new V3000 user as well and I got mine working fine. 

1. open terminal and type 

> compiz

It will complain that Xgl isnt installed and that you can type something below to download and install it. xgl-xserver or something, can't quite remember. 

reboot. 

You should be able to pick high settings after that. You can get the latest version of compiz-fusion to add more effects. Everything worked fine on mine, even the water droplets on the desktop with video!

---

### Post by waggygee on 2007-11-06
> **Forlong said:**
> ```
lspci | grep VGA
```
And also post the output of ```
compiz
``` in a terminal.

georg@georg-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
georg@georg-laptop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 



So I guess this means my graphics card is blacklisted? Is there a way to "unblacklist" it?

---

### Post by Forlong on 2007-11-06
> **waggygee said:**
> So I guess this means my graphics card is blacklisted? Is there a way to "unblacklist" it?
Yes, but keep in mind it has been blacklisted for a reason.

So let's just try this (in a terminal): ```
SKIP_CHECKS=yes compiz
```

---

### Post by waggygee on 2007-11-06
> **Forlong said:**
> Yes, but keep in mind it has been blacklisted for a reason.

So let's just try this (in a terminal): ```
SKIP_CHECKS=yes compiz
```

Blacklisted for a reason? What reason may that be? the out put of that command is as follows

georg@georg-laptop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

After closing the terminal, I get wobbly windows and such but no cube or windows borders :(

---

### Post by Forlong on 2007-11-06
> **waggygee said:**
> Blacklisted for a reason? What reason may that be? 
AFAIR it has something to do with video playback. So if you want to watch a video, you may have to disable Compiz.
> **waggygee said:**
> After closing the terminal, I get wobbly windows and such but no cube or windows borders :(
Don't worry, it was just a test. Did you have window boarders before closing the terminal?

---

### Post by waggygee on 2007-11-06
> **Forlong said:**
> AFAIR 
Don't worry, it was just a test. Did you have window boarders before closing the terminal?

Yes there were borders, after a few minutes I noticed that the cube started working... Let me try restarting again

---

### Post by Forlong on 2007-11-06
> **waggygee said:**
> Yes there were borders
Alright than do this:
```
gedit ~/.config/compiz/compiz-manager
```
Put the command in there:
```
SKIP_CHECKS=yes
```
and save.

Afterwards, just use *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects*


To get the cube working, see [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).

---

### Post by waggygee on 2007-11-06
> **Forlong said:**
> Alright than do this:
```
gedit ~/.config/compiz/compiz-manager
```
Put the command in there:
```
SKIP_CHECKS=yes
```
and save.

Afterwards, just use *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects*


To get the cube working, see [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).

Windows borders go transparent and the computer freezes... I had to wait for the battery to die to switch it off :(

---

### Post by joshuachad on 2007-11-07
I am pretty sure thats the wrong file. At least on my system it is ~.config/compiz-managerrc

though i comiled from source so it might just be different.

---

### Post by Forlong on 2007-11-07
> **joshuachad said:**
> I am pretty sure thats the wrong file.
Trust me, it's the right one. Here's the part of the compiz-wrapper that uses it:
```
if [ -z "$XDG_CONFIG_HOME" ]; then
	test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager
else
	test -f $XDG_CONFIG_HOME/compiz/compiz-manager && .  $XDG_CONFIG_HOME/compiz/compiz-manager
fi
``` (I'm working on this right now to make it work properly with Kubuntu and Xubuntu, that's why I'm certain)

But even if it wasn't, the file itself can't be the cause of a system freeze.

What happens now, when you boot Ubuntu again?

---

### Post by waggygee on 2007-11-07
> **Forlong said:**
> 
What happens now, when you boot Ubuntu again?

It boots up normaly as if I had never put those commands in

---

### Post by waggygee on 2007-11-07
Ok, when I run compizfusion... everything runs smoothly but my windows boarders are transparent (meaning I can't see the boarders but the writting is still there) and when I try watch a video, the video propram crashes :(

---

