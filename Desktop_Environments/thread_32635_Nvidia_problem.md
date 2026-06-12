---
title: "Nvidia problem"
date: 2005-05-08
forum: Desktop Environments
---

### Post by weaner on 2005-05-08
Hi,
     I have a small but (now that I have noticed it) annoying problem. After installing the Nvidia-glx graphics driver the KDE display seems to be too big for the monitor. The difference is only a couple of pixels but I have no idea how to fix it. I had the same problem with Suse but I was able to resize it using Sax, does Kubuntu have a similar app? I've tried using nvidia-settings but I couldn't a answer there.

Thanks in advance,

Weaner

---

### Post by Xian on 2005-05-08
SuSE places a monitor display size line in the xorg.conf file. You could do the same and see if there is any change. Or, you could just adjust the screen parameters via the monitor's hardware on-screen settings. If you append the xorg.file you will want to write something like this:

```
Section "Monitor"
  DisplaySize  312 234
  HorizSync    30-70
  Identifier   "Monitor[0]"
  VendorName   "CPQ"
  VertRefresh  50-140
</snip>
```

---

### Post by weaner on 2005-05-08
Thanks for the info I'll give it a go, I don't really want to change the size using the monitor as I dual boot and on the few occasions that I use XP it'll end up bugging me there instead  :smile: 

Cheers,

Weaner

---

### Post by Xian on 2005-05-08
[QUOTE=weaner]Thanks for the info I'll give it a go, I don't really want to change the size using the monitor as I dual boot and on the few occasions that I use XP it'll end up bugging me there instead [/QUOTE]
Okay, here's another idea. Adjust the parameters manually via the monitor settings while in Ubuntu, and then you could reboot & set the screen size in your Windows system properties dialogue since the Nvidia drivers should allow you to do this with the screen adjustment tab. Basically the idea here is to work the process in reverse. So instead of trying to adjust the configs in Linux you would instead be doing it in Windows, which will be easier and Sax-like with the Nvidia GUI that is available.

---

### Post by weaner on 2005-05-08
Has anyone told you that you are a genius!!! What a great idea  :grin: 

Thank you so much,

Weaner

---

### Post by Xian on 2005-05-08
[QUOTE=weaner]Has anyone told you that you are a genius!!! What a great idea  :grin: [/QUOTE]
Heh. It's only a great idea if it works. :)

---

### Post by weaner on 2005-05-08
It worked a treat, didn't even have to play with anything in M$. So I guess you are going to have to accept the title of genius after all   :wink: 

Cheers,

Weaner

---

### Post by crane on 2005-05-08
[QUOTE=Xian]Heh. It's only a great idea if it works. :)[/QUOTE]

Yea if it doenn't work your a..... well you know :smile: 


Just kidding!

---

