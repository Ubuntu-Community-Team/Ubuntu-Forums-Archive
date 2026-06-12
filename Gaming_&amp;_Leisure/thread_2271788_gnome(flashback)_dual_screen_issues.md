---
title: "gnome(flashback) dual screen issues"
date: 2015-04-01
forum: Gaming &amp; Leisure
---

### Post by barkerson on 2015-04-01
Ok, long story short, gnome-flashback(ubuntu) does not want to cooperate with me.

I got myself a second monitor a couple of days ago and it won't work the way I intend it too, in the default mode in ubuntu a dual screen configuration for me gives me a 2-screen wide desktop that's multiplied by the number of workspaces. What I really need is the type I had the last time I ran dual screen on ubuntu many years ago, basically the ability to switch to one of four workspaces independently(one of the screens is locked to a workspace). I tried putting one screen on another "x screen" in nvidia-settings, but that just makes the newly formed x-screen black. I can still drag my cursor there though, but the cursor turns into a cross and there is no possibility to drag any windows there. I can't seem to get TwinWindow to work either, don't know about that one. I know this kind of setup is hard to get working but I figured it should at least be possible given I've done it before.

I'm running ubuntu 14.10 gnome, gpu is evga 970, screens are samsung-syncmaster-p2770(via hdmi) and a philips 24ie(new screen, via dvi).

help much appreciated
[edit]: also it somehow does strange things to my text

---

### Post by kerry_s on 2015-04-01
i'm not i sure understand. have you tried under display or are you only using nvidia settings.
i run gnome 3 & use the display settings.

---

### Post by barkerson on 2015-04-01
My display settings does not look like that, and that's in gnome shell too(I normally run flashback). Also, I mean that one screen can be locked to a workspace, the version you show in thumbnail is what's causing me problems.

Could the different display setings be because I installed normal ubuntu and then got gnome(and then removed everything unity)?

---

### Post by barkerson on 2015-04-01
welp, it appears gnome wasn't installed even though I installed it a couple of months ago, I'll get back when I find the "gnome-control-center" you have installed

[edit]: nope, still default options without any way off setting primary screen

---

### Post by kerry_s on 2015-04-01
post a pic what your settings look like. i've used everything so my memory is not that great, my last setup was unity, lubuntu, xubuntu, mate, gnome, unity 15.04, & now back to gnome but using 15.04 version. so the last time i used flashback been more than a few months.

sorry for late reply, have appointments today so i'm in & out for today.

---

### Post by barkerson on 2015-04-01
[ATTACH=CONFIG]261038[/ATTACH]This is basically what I see when I have the second screen on another x-screen, using single x-screen and xinerama gave me two desktops and the same type of menu(but it just makes my workspace be 3840px wide).

---

### Post by kerry_s on 2015-04-01
that's the same settings as in unity. 
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)

---

### Post by barkerson on 2015-04-02
ok, after waking up and trying a couple of things I can almost tell exactly what the problem is, it lies with the twinview settings. I can't enable it. I found out with the nvidia-xconfig command with the -A flag(all commands), it doesn't exist. trying to add it manually to my xorg.conf file so it would work with two monitors just makes my screens go black after rebooting(edited it back in tty1 with nano). I also found out that the xorg.conf file listed two GPU's and four screens for some unknown reason(I deleted the extra two), then I was able to boot into ubuntu again. I'm really out of ideas on this one.

---

### Post by muktupavels on 2015-04-02
> **barkerson said:**
> What I really need is the type I had the last time I ran dual screen on ubuntu many years ago, basically the ability to switch to one of four workspaces independently(one of the screens is locked to a workspace). I tried putting one screen on another "x screen" in nvidia-settings, but that just makes the newly formed x-screen black. I can still drag my cursor there though, but the cursor turns into a cross and there is no possibility to drag any windows there.

If you want separate x screens, then this is not possible anymore. As you already know - all you will get is black screen. Since GTK+ 3.10 multi screen support has been removed.

---

### Post by barkerson on 2015-04-02
I did not know that. Well, you were a big help. I think I'll try to downgrade gtk and see if that works for me, otherwise I'll have to try something else...

[edit]: Looks like the kind of dual-screen I want works in kubuntu, I will try to install the official ubuntu gnome before that though.

---

### Post by barkerson on 2015-04-03
Ok, legit gnome installed. Now I have the issue of the second monitor not being detected at all, 'xrandr -q' gives me this:
```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
Unknown-0 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0x1c1)  148.5MHz
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz

```
The 'Unknown-0 disconnected' is what I guess would be DVI-D-1(which I'm guessing is the digital output), this is what should be my secondary monitor, the 'disconnected' hdmi is my main output which actually gives a pretty solid 1080p 60hz output which works really well. Now, what might cause this and/or what fixes this issue? help is still very appreciated.

---

