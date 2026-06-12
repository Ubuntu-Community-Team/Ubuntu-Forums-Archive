---
title: "Blinking panel elements and Plank on top and left screen edge"
date: 2018-07-28
forum: Desktop Environments
---

### Post by malysps on 2018-07-28
Hello all, I'm new here. I registered with hopes to finally solve this long lasting issue that I have. I'm trying to investigate it for some time now. I'm using  Xubuntu (currently 18.04) and I've noticed long time ago that Whisker Menu icon is blinking when I move  my mouse cursor on the left and top screen edges, but it behaves  normally when I drag it on the bottom and right edges. Not only panel  plugins/elements are affected by this strange behaviour, but also other applications, for  example Plank. And this occurs not only on Xubuntu.

You can see the issue on this video - [https://youtu.be/YXmFXFV_ONQ](https://youtu.be/YXmFXFV_ONQ)
EDIT: New video - [https://youtu.be/P8NVGl5DqGQ](https://youtu.be/P8NVGl5DqGQ)

  Issue occurs on Ubuntu 18.04 (GNOME), Xubuntu, Ubuntu MATE, Kubuntu and some  other distributions like Manjaro Xfce. Here are some other videos showing this issue:
Ubuntu MATE - [https://streamable.com/ee9sk](https://streamable.com/ee9sk)
Kubuntu - [https://streamable.com/dyqur](https://streamable.com/dyqur)
Xubuntu - [https://youtu.be/UY4ZuxsPifw?t=15s](https://youtu.be/UY4ZuxsPifw?t=15s)

Issue is visible on my desktop with NVIDIA GTX650Ti and on my laptop with NVIDIA NVS 3100M, but not only NVIDIA is affected, some users confirmed this issue on Radeon RX 460 and Intel integrated graphics. Please help me to kill that nasty bug, it's been on my system for a  year now, I've noticed it first on Xubuntu 17.04. I don't know where exactly  to submit this bug, I previously submitted it wrongly on the Xfce's  Bugzilla, but this issue is not Xfce specific, now I know that. Not sure if that's an important info, but issue doesn't occur in VirtualBox VMs.

 More details (and videos showing this issue) are here: [https://forum.xfce.org/viewtopic.php?pid=48257](https://forum.xfce.org/viewtopic.php?pid=48257)

Thanks for help.

PS: I posted this 2 months ago on Ask Ubuntu, but no one responded.
[https://askubuntu.com/questions/1034051/what-causes-an-issue-with-desktop-elements-losing-focus-when-i-move-my-mouse-cur](https://askubuntu.com/questions/1034051/what-causes-an-issue-with-desktop-elements-losing-focus-when-i-move-my-mouse-cur)

---

### Post by Autodave on 2018-07-30
Have you installed any drivers for the Nvidia cards? If so, what ones and where did you get them from?

---

### Post by malysps on 2018-07-30
Yes, I use proprietary NVIDIA driver (nvidia-driver-390) on my main machine (desktop PC) now, and nvidia-340 on my 1st laptop, both installed in GUI using "software-properties-gtk". I also tried Nouveau - issue still occurs. But I don't think it's a driver related issue, because I can see exactly the same behaviour on my 2nd laptop with integrated Intel graphics.

```
$ inxi -Gxxx
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller bus-ID: 00:02.0 chip-ID: 8086:2a42
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1280x800@59.98hz
           OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express version: 2.1 Mesa 18.0.5 Direct Render: Yes
```
```
$ inxi -Gxxx
Graphics:  Card: NVIDIA GK106 [GeForce GTX 650 Ti] bus-ID: 01:00.0 chip-ID: 10de:11c6
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia Resolution: 1440x900@74.98hz
           OpenGL: renderer: GeForce GTX 650 Ti/PCIe/SSE2 version: 4.6.0 NVIDIA 390.48 Direct Render: Yes
```

---

### Post by mc4man on 2018-07-30
Does this occur in plank when you aren't running your cursor on the tiny dock area, i.e when you run it thru the icons?

For both plank & the xubuntu icon, it seems like a semi contrived issue. Your placing your cursor where it's getting on, off, on, off, on the icon so  the highlighting is flickering on, off, ect.  Like a loose wire can cause a light to flicker.
Quite obvious in plank video, that's why you keep losing the dock.

---

### Post by again? on 2018-07-31
I see the same in xfce and other desktops with plank.
When on left side using autohide, plank seems to have a quirk where it will hide when the mouse is about a pixel away from the edge.
It's hard to replicate consistently but it's annoying enough that I don't use autohide.
It's as if whatever the mouse is over keeps losing and regaining the hover focus.
I find a permanently visible dock is more efficient anyway.

```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] inxi -b**
System:    Host: Bionic Kernel: 4.15.0-29-generic x86_64 bits: 64 Desktop: Xfce 4.12.3
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x serial: N/A BIOS: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) speed/max: 1438/3800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: X.Org 1.19.6 driver: nvidia Resolution: 1680x1050@59.88hz
           OpenGL: renderer: GeForce GTX 550 Ti/PCIe/SSE2 version: 4.6.0 NVIDIA 390.77
```

---

### Post by malysps on 2018-07-31
> **mc4man said:**
> Does this occur in plank when you aren't running your cursor on the tiny dock area, i.e when you run it thru the icons?
No, keep in mind that this issue occurs only  when I move my mouse cursor exactly on the screen edge (only top and left), not on Plank itself. This picture explains it: [https://i.imgur.com/OCuM2I0.jpg](https://i.imgur.com/OCuM2I0.jpg)
> **mc4man said:**
> For both plank & the xubuntu icon, it seems like a semi contrived issue. Your placing your cursor where it's getting on, off, on, off, on the icon so  the highlighting is flickering on, off, ect.  Like a loose wire can cause a light to flicker. Quite obvious in plank video, that's why you keep losing the dock.
Have to disagree with you. There's nothing contrived about this issue. And you can see on **[[B][COLOR=#000000]guber2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2063040")[/B]'s attachment that icons have nothing to do with that.

I've made a new video (on Xubuntu 18.10 with Nouveau, newest packages and kernel) showing that "autohide" on Plank doesn't have anything to do with the issue (it's disabled) and it occurs on many elements (not only icons), and that on bottom and right screen edge it's not occurring.

[https://youtu.be/P8NVGl5DqGQ](https://youtu.be/P8NVGl5DqGQ)

I think that the mouse cursor / pointer can be a culprit here. Is there any way to change how the mouse cursor is handled in Ubuntu/Xubuntu? Hardware or software? Maybe some xorg.conf entry? Any ideas how to investigate that?

---

### Post by again? on 2018-07-31
It's not the window manager because also see it in compiz.
Doesn't look to be an easy solution.
I only have a bottom panel using tint2 so don't really notice it.

---

### Post by molecularentropy on 2018-09-12
Same issue here. It does not allow me to reliably click the whiskermenu button.

---

### Post by malysps on 2018-10-03
More info about the issue - I did some testing on Kubuntu 18.04.1 and Latte dock (Qt app) doesn't flicker, but Plank dock (GTK3 app) does, so maybe it's a GTK-related issue?

---

### Post by malysps on 2018-10-24
OK, there's a workaround for this issue. This bug report tells a lot more about it - [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1795135](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1795135)

I put **export GDK_CORE_DEVICE_EVENTS=1** to */etc/X11/Xsession.d/56xubuntu-session* and my Xfce panel items aren't blinking any more, and that works with Plank too. Tested on Xubuntu 18.04.

---

### Post by Frogs Hair on 2018-10-26
I don't see this with Budgie though I did during the past 18.10 development cycle. The problem was resolved by the final release at least on my system. 

```
CPU:
  Dual Core: Intel Core i5-2540M type: MT MCP speed: 798 MHz 
  min/max: 800/3300 MHz 
Graphics:
  Device-1: Intel 2nd Generation Core Processor Family Integrated Graphics 
  driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.1 driver: i915 resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel Sandybridge Mobile v: 3.3 Mesa 18.2.2 



```

---

