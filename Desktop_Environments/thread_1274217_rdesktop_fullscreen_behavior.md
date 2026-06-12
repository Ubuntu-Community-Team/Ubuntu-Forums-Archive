---
title: "rdesktop fullscreen behavior"
date: 2009-09-24
forum: Desktop Environments
---

### Post by KagenoKaze on 2009-09-24
Hello Everyone,


Its been a while since I have posted on this trove of knowledge.  The problem I am having is this:

I have set up using Ubuntu 8.10 a dual monitor desktop setup for work with compiz-fusion.  I often use windows for some of the proprietary tools we have here including Adobe flash and dreamweaver as well as office and for testing purposes.  I have setup virtualbox using vrdp and have one big monitor that spans the length of the two I have setup (Ubuntu treats this as one big screen).  The problem is when I do this either the Gnome Panels are blocking parts of the rdesktop screen when not in full screen or when I put it in full screen it doesnt stay on the viewscreen I started it on and I cannot change to my Ubuntu tools easily.

Essentially what I am looking for is some way to either remove the gnome Panels on one viewscreen or force rdesktop to only display on one viewscreen.


Any Ideas?

---

### Post by Giblet5 on 2009-09-24
So you're running two monitors from one graphics rig in "TwinView" (one big screen on more than one monitor) mode. Correct?

Is there any reason you can't configure two Xscreens instead?

That would eliminate the problem you describe (and create some interesting new ones) as long as you start the rdc explicitly to the other screen eg, ```
myrdc -display :0.1
``` to start it on screen 1.

I can't think of an elegant way to do it in TwinView mode. Something (WM hints, etc) will always mess it up or limit your display abilities in almost-unpredictable ways.

You can configure separate X screens in xorg.conf or use one of the fontend apps like nvidia-settings.

You could try hardwiring your rdc's X resources too.

Other than that, I got nuthin.

---

### Post by themtx on 2009-09-24
I had similar issues w/an xrandr dual monitor setup.  2x20" widescreens, 3360x1050 total desktop area, 1 X screen w/4 virtual desktops.  I tried a bunch of different things to get an rdesktop dislplay to behave properly, but what ultimately worked for me was the simple route.  I created a .sh script in ~/Desktop/ that launches rdesktop to my desired host at half my X screen's total resolution, then moved that icon to the side opposite my xfce toolbar, conky, etc.

When I launch it from the desktop I want to be my "Windows" desktop, it anchors to that side, and the virtual desktops work as expected w/mouse scroll on the linux "side".

```
rdesktop -0 -D -g 1680x1050 -r disk:home=/home/username -r clipboard:CLIPBOARD -r sound:off -x l -P windowshost -u "username" -p password
```

That's the text in the .sh file I have on my desktop.  Hope this makes sense!

---

