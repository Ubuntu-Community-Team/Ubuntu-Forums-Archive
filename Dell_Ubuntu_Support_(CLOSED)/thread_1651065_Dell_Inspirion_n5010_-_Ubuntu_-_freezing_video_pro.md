---
title: "Dell Inspirion n5010 - Ubuntu - freezing video problem"
date: 2010-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nutshell555 on 2010-12-22
Hi,

I just bought new Dell Inspirion n5010 running Ubuntu 9.10. When watching AVI video, sound is OK but picture is freezing for a moment about every 2 seconds.

Watching flash videos on youtube using Firefox works just fine.

Some system info:

System info: Linux dell-desktop 2.6.31-22-generic #68-Ubuntu
Ubuntu version: Ubuntu 9.10
Video codec: XVid MPEG4
Movie player: Totem Movie Player 2.28.2
Xorg version: X.Org X Server 1.6.4
Pulseaudio version: pulseaudio 0.9.19

Video card in this Dell is: Intel GMA 4500MHD.

I would very much appreciate any help since I have searched for the solution but haven't found anything helpful so far.

Thnx in advance!

---

### Post by nutshell555 on 2010-12-26
Any idea, anyone? Maybe to try some update or another version of a software? My video problem is similar to "slow motion" video problems that were already posted on this forum but I've tried those suggested solutions and none of them worked for me :(

---

### Post by mikewhatever on 2010-12-26
So, are all AVI files lag in Totem? Are those HD videos?

Another thought, sometimes, desktop effects can cause these problems. Try turning them off when playing videos.

---

### Post by nutshell555 on 2010-12-27
Hi,

Thank you for your suggestions.

AVI videos are all played in Totem. I have also tried VLC but the same problem occurs.

Videos are not HD videos, resolution of the videos: 624x352.

Visual effects for desktop are set to None, by default.

Additional info, checking the compiz version produces:

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1366x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
compiz 0.8.4

I would really appreciate any further suggestions or thoughts on this issue, thank you!

---

### Post by mikewhatever on 2010-12-28
Inspiron n5010 is the new model with Intel's Core i3/5 cpus and integrated graphics, right? Was it from Dell with Karmic preinstalled? If that's the case, I think the graphics can't be Intel GMA 4500MHD, as these where used with previous generations of cpus.
[https://secure.wikimedia.org/wikipedia/en/wiki/Intel_GMA#GMA_X4500](https://secure.wikimedia.org/wikipedia/en/wiki/Intel_GMA#GMA_X4500)

You could verify that by looking at the output of the **sudo lshw -C display** command.

If the above is correct, you might want to try a more recent version of Ubuntu (running from cd/usb), since I suspect that Karmic only has partial support for these new chips. You'd have to upgrade anyway, as Karmic is reaching EOL at the end of April, which is in four months.

---

