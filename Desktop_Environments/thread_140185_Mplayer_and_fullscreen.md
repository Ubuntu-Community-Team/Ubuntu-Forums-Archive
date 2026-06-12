---
title: "Mplayer and fullscreen"
date: 2006-03-05
forum: Desktop Environments
---

### Post by Dearhell on 2006-03-05
I have installed mplayer-386 in my machine (what's the difference with mplayer-586?), also I have installed the win32 codecs and the mplayer-fonts.

I have followed this tutorial: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

But when I see any movie with the mplayer, I only can see it in the default size, and when I choose full screen mode or double size mode, the mplayer window gets larger, but the movie still goes in the default size. 

So, how can I see movies in full screen with mplayer?

With totem player I can see movies in full screen mode, but the sound it's not synchroniced

Anticipate thanks

---

### Post by jazzi on 2006-03-05
[SIZE="5"]That is the solution:
1.edit the config 
> [COLOR=Red]sudo gedit /etc/mplayer/mplayer.conf[/COLOR] add the following lines into it
> [COLOR=Red]zoom=yes[/COLOR] 2.if it still isn't work,add the same lines to the files you will open
> [COLOR=Red]gedit your_home_dir/.mplayer/config[/COLOR][/SIZE]

---

### Post by taurus on 2006-03-05
In ~/.mplayer/gui.conf, make sure you use "xv" instead of x11,

```

vo_driver = "xv"

```

---

### Post by Dearhell on 2006-03-06
> That is the solution:
1.edit the config
sudo gedit /etc/mplayer/mplayer.conf
2.add the following lines into it
zoom=yes

With this it works fine now, thanks

---

### Post by terje on 2006-03-06
Thanks for this, been having the same problem myself.

---

### Post by souteneur3190 on 2006-03-13
thanks a lot

---

### Post by Mr Green on 2006-03-14
For those with ATI garbage inside their computers:

Setting *vo_driver = "xv"* does not work at all, but *zoom=yes* does the trick.

---

### Post by jtp51 on 2006-03-27
I've followed the steps above and the two config files:

~/.mplayer/config
/etc/mplayer/mplayer.conf

are both set video out variable value "xv" and zoom=yes.

However, I just want my videos always set to double size as the default, how can I change this setting?

Thanks,

---

### Post by halfbaked on 2006-03-31
I too had the same issue with Mplayer. Setting the zoom=yes and the vo_driver=xv worked a treat. Cheers.

---

### Post by R-A-V-E-N on 2006-04-05
I am new to using mplayer, i have not had the zoom errors in mplayer, but my problem still has to do with the fullscreen mode. When i go into fullscreen mode the image stretches to the right size, but the image gets messed up, lines and flickering all over the place. I was wondering if there was anything I could do or need to install to fix this

---

### Post by taurus on 2006-04-05
[QUOTE=R-A-V-E-N]I am new to using mplayer, i have not had the zoom errors in mplayer, but my problem still has to do with the fullscreen mode. When i go into fullscreen mode the image stretches to the right size, but the image gets messed up, lines and flickering all over the place. I was wondering if there was anything I could do or need to install to fix this[/QUOTE]
What video card do you have and did you install the right driver for it?

---

### Post by R-A-V-E-N on 2006-04-05
I have a Radeon 9200 SE, I'm sure where to get the drivers for the card other than the cd, but im not sure if the cd works on linux

---

