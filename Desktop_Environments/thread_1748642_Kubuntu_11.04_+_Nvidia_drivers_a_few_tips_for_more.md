---
title: "Kubuntu 11.04 + Nvidia drivers: a few tips for more stability"
date: 2011-05-03
forum: Desktop Environments
---

### Post by scorp123 on 2011-05-03
Hi out there,

I am posting this in the hope that it may be useful for anyone who may be searching for a solution for the following problems:

[LIST]
[*]You installed Kubuntu 11.04 because you wanted to escape from that horrible Kindergarten-interface they call "Unity" ... 
[*]you have a Nvidia card and use the proprietary Nvidia drivers from the repositories (e.g. because "Nouveau" won't work properly on your PC)
[*]with the desktop effects turned on KDE crashes very often
[*]whenever you play Adobe flash content (e.g. YouTube, Zattoo, etc.) full-screen you get a "black screen of death" soon afterwards and/or your desktop freezes hard
[*]whenever you play a movie via VLC or Dragon Player full-screen you also get a "black screen of death" and your KDE desktop freezes hard
[/LIST]

I was about to give up and abandon (K)Ubuntu altogether ... then I found the solution:

[LIST]
[*]Make sure ***"Sync to VBlank"*** is turned off in the Nvidia Settings Manager ...
[*]there are two places where you need to turn it off:
[/LIST][INDENT][LIST]
[*]*X Screen 0 > X Server XVideo Settings* ... turn ***"Sync to VBlank"*** off (leave everything else untouched)
[*]*X Screen 0 > OpenGL Settings*: turn ***"Sync to VBlank"*** off (leave the rest untouched)
[/LIST][/INDENT]

Then you have to turn it off in KDE too:
[LIST]
[*]*KDE Menu > Applications > Settings > System Settings* ...
[*]go to *Desktop Effects > Advanced ...* please make sure that ***"Use VSync"*** and ***"Suspend desktop effects for fullscreen windows"*** are both turned off!
[/LIST]


Since I did these minor changes the overall stability has drastically improved on my desktop PC (no more crashes or freezes so far!) and the "Black screen of death" after playing videos full-screen has completely gone.

I hope this posting proves useful for others too.

---

### Post by scorp123 on 2011-05-13
Addendum:

It also seems to help (at least it does in my case) to add the options ***"nolapic_timer clocksource=jiffies"*** to the GRUB configuration .... Details here:

[https://bugs.launchpad.net/linux/+bug/657990/comments/29]("https://bugs.launchpad.net/linux/+bug/657990/comments/29")


I hope this may help someone. :-k

---

### Post by azupan on 2011-06-03
Hey! The bloody thing works all of the sudden!

Thanxx, man! :biggrin:

---

### Post by Zorael on 2011-06-04
What cards does this happen with? My 580 works great with both vsync and fullscreen redirection enabled.

---

### Post by azupan on 2011-06-05
> **Zorael said:**
> What cards does this happen with? My 580 works great with both vsync and fullscreen redirection enabled.
GF104 [GeForce GTX 460]

The cheapest thing to hook dual monitors on I could get.

---

### Post by SeijiSensei on 2011-06-05
I have a 9500 GT, and Kubuntu 11.04 with nvidia-current has a strange problem for me.  If I try to move a window in KDE, the screen will sometimes become covered with sparkles, rather like what old analog TV viewers like me called "snow."  The only solution to this problem that I've found is rebooting.

I've reverted to 10.10 which doesn't display this problem whatsoever.

---

### Post by scorp123 on 2011-06-09
> **SeijiSensei said:**
> I have a 9500 GT, and Kubuntu 11.04 with nvidia-current has a strange problem for me.  If I try to move a window in KDE, the screen will sometimes become covered with sparkles  Yes, I also get that with KRDC (remote desktop client e.g. for VNC) as soon as I connect to a VNC remote desktop. No such problems though if I use any of the other VNC clients (tightvnc or xvnc4viewer).

I read something about the kernel being at fault for this!? So I upgraded my kernel ... the KRDC issue still remains, but the rest seems to perform better and is far more stable. I rarely experience any crash anymore.

What I did to upgrade the kernel is this:

- I upgraded to Kernel 2.6.39 following these instructions:
[http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0]("http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0")

- I then removed the GRUB options I mention above! e.g. the relevant line in /etc/default/grub now looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"

```

The last few bits there from "nomodeset ... " onwards fixed the boot splash for me. Details here:

[http://ubuntuforums.org/showpost.php?p=10721249&postcount=5]("http://ubuntuforums.org/showpost.php?p=10721249&postcount=5")

I now use this boot splash called "Earth Sunrise" ... It's beautiful:
[http://gnome-look.org/content/show.php/Earth+Sunrise+Plymouth+Theme?content=137171]("http://gnome-look.org/content/show.php/Earth+Sunrise+Plymouth+Theme?content=137171")

---

### Post by backlashforblow on 2011-08-13
It seems that your firewall is blocking the ports. Does krdc support 2 protocols ???? :KS

---

### Post by hug0b0ss on 2012-02-13
I had same issue, like couldnt even move a window if it was running video, ive a evga gtx560, to find someone that had same issue and posted same fix, well seams something is wrong in the normal nvidia drivers, ah btw im using Ubuntu 11.10.

> **scorp123 said:**
> Hi out there,

I am posting this in the hope that it may be useful for anyone who may be searching for a solution for the following problems:

[LIST]
[*]You installed Kubuntu 11.04 because you wanted to escape from that horrible Kindergarten-interface they call "Unity" ...
[*]you have a Nvidia card and use the proprietary Nvidia drivers from the repositories (e.g. because "Nouveau" won't work properly on your PC)
[*]with the desktop effects turned on KDE crashes very often
[*]whenever you play Adobe flash content (e.g. YouTube, Zattoo, etc.) full-screen you get a "black screen of death" soon afterwards and/or your desktop freezes hard
[*]whenever you play a movie via VLC or Dragon Player full-screen you also get a "black screen of death" and your KDE desktop freezes hard
[/LIST]

I was about to give up and abandon (K)Ubuntu altogether ... then I found the solution:

[LIST]
[*]Make sure ***"Sync to VBlank"*** is turned off in the Nvidia Settings Manager ...
[*]there are two places where you need to turn it off:
[/LIST]
[INDENT]
[LIST]
[*]*X Screen 0 > X Server XVideo Settings* ... turn ***"Sync to VBlank"*** off (leave everything else untouched)
[*]*X Screen 0 > OpenGL Settings*: turn ***"Sync to VBlank"*** off (leave the rest untouched)
[/LIST]
[/INDENT]Then you have to turn it off in KDE too:
[LIST]
[*]*KDE Menu > Applications > Settings > System Settings* ...
[*]go to *Desktop Effects > Advanced ...* please make sure that ***"Use VSync"*** and ***"Suspend desktop effects for fullscreen windows"*** are both turned off!
[/LIST]


Since I did these minor changes the overall stability has drastically improved on my desktop PC (no more crashes or freezes so far!) and the "Black screen of death" after playing videos full-screen has completely gone.

I hope this posting proves useful for others too.

---

