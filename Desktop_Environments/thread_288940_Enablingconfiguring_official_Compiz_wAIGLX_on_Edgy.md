---
title: "Enabling/configuring official Compiz w/AIGLX on Edgy w/ATI"
date: 2006-10-30
forum: Desktop Environments
---

### Post by Schluppy on 2006-10-30
Now that AIGLX and compositing are available by default and compiz is available in the official repositories, how does one go about configuring and enabling such without the use of third-party apps, libs, or repositories?

I could be wrong here but, with the release of edgy, the dozens of HOWTO's available appear to be pretty much outdated.

Assuming that they are outdated, and assuming all the necessary prerequisites are installed, how does one go about enabling and configuring compiz?

Is there a simple command or conf file to edit?

---

### Post by sciurus on 2006-10-31
I have a Radeon 9800 Pro and a clean install of edgy.
I installed compiz and compiz-gnome and added 

```

        Option "DRI" "true"
        Option "ColorTiling" "on"
        Option "EnablePageFlip" "true"
        Option "AccelMethod" "EXA"
        Option "XAANoOffscreenPixmaps"
        Option "RenderAccel" "true"

```
to my device section in xorg.conf.

I ran *compiz --indirect-rendering --strict-binding --replace gconf* but my window decorations disappeared. Then I ran *gnome-window-decorator --replace* as well, but my system slowed to a crawl so I restarted X.

I then ran gconf-editor. In /apps/compiz/general/allscreens/options/active_plugins I removed blur. Afterwards, the previous two commands gave me a speedy working compiz. The water/rain effects do not work.

---

### Post by Schluppy on 2006-11-02
Thanks for the tips. I haven't tried them yet, I have to ensure my machine is in a working state for the next day or two, but I intend to try again soon. 

It seems that all I was missing were the changes to xorg.conf and, being that one of my cards is a lowly 8500LE, disabling water, blur, and rain effects would, as you've suggested, probably be a good idea too. ;) 

Thanks! I'll post again with the results.

---

### Post by Sunn3K7aas on 2006-11-09
> **sciurus said:**
> 

I ran *compiz --indirect-rendering --strict-binding --replace gconf* but my window decorations disappeared. Then I ran *gnome-window-decorator --replace* as well, but my system slowed to a crawl so I restarted X.


Which command did you run first? Every time I try to run compiz, the window borders disappear and GNOME hangs. ](*,) :confused:

---

### Post by Sunn3K7aas on 2006-11-09
Wait, I figured out what was wrong with it. I feel kinda stupid about this, but I removed the fglrx driver from my computer completely and used the ati ones instead. Heheh :p

---

### Post by TeleTommy on 2006-11-13
Thank you for this howto - it works pretty good for me.
But what do I have to do to have this nice features after a reboot without hacking the commands in my console?

Thanks,
Thomas

---

### Post by neildarlow on 2006-11-14
Hi,

I have a Radeon-9250 card and found that **Option "AccelMethod" "EXA"** disables XVideo. You might want to stay with XAA.

---

### Post by jeremytaylor on 2006-11-14
I've tried following this and I don't get any window decorations. I'm using a radeon x600 mobility and on starting compiz I get an error, 

libGL warning : 3D driver claims to not support visual 0x4b

all the other swishyness works, wobbly windows and cube.

Any suggestions as to what I'm doing wrong?

thanks
Jeremy

---

### Post by neildarlow on 2006-11-14
Try starting Compiz like this:

**compiz --indirect-rendering --strict-binding --replace gconf && gnome-window-decorator --replace &**

Note the starting of gnome-window-decorator conditionally on compiz starting and that gnome-window-decorator executes in the background.

---

### Post by jeremytaylor on 2006-11-15
that works! brilliant. Thanks.
Jeremy

---

### Post by mtn on 2006-11-28
hey sciurus,

thanks for this, been trying to find out what this was all about for a couple of days and this worked great. feeling like my desktop has taken a trip!

---

### Post by zir0n on 2006-12-02
I got compiz running but my window decorations disappeared. Then I ran gnome-window-decorator like it said in the walkthough and ran gnome-window-decorator which restored my boarders. I actaully had it running ok but a little slow, so i tried some of the newer versions of compiz out, then when they didn't work i reinstalled this compiz package and it starts up again, but when i run the gnome window decorator it gives me this message...

> root@ubuntu:~# gnome-window-decorator --replace
bash: gnome-window-decorator: command not found

who do i get gnome-window-decorator back up and running? i have a feeling i uninstalled it with the other compiz package

---

### Post by Miguel on 2006-12-15
Try again with gtk-window-decorator instead. By the way, I've installed the backported compiz packages (all four, plus its libxcomposite1 dependency). 

My ATi works OK with the open "sauce" drivers. However, running compiz results in windowless applications, and gtk-window-decorator (no gnome-window-decorator is on my system) will not give the borders back to me.

Any idea?

PS: I'm heavily biased against using other repositories. I just won't use all these repositories advised in a thousand tutorials, even though I'll probably switch to Arch when Feisty hits the street.

---

