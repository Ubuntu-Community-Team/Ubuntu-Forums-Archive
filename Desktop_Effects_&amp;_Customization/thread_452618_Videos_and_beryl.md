---
title: "Videos and beryl"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by Gleep on 2007-05-23
Ever since I got Feisty Fawn i've been having problems with beryl. When I was using Edgy, I was using XGL, with the fglrx drivers, and that was fine, but then when I got Feisty Fawn, I tried to install it this way and whenever using Beryl, I was greeted with this sort of thing:

[IMG]http://img.photobucket.com/albums/v156/gleep/Screenshot.png[/IMG]

So instead I am now using it with Aiglx. This works fine, until I want to watch a video... then I get sound but just a black picture. When I move the window I can see the picture as I'm moving it but only at the edges. That's with VLC.
With Totem, I'm not getting any sound, just picture.

It's very frustrating =[ Any help would be much appreciated.

---

### Post by Gleep on 2007-05-23
In fact to add to that, that was a while ago, now VLC just won't play anything and shuts immediately. And that's with both Beryl and Metacity :(

---

### Post by Campingman on 2007-05-23
Hi,
There is a work around to the problems you have with no picture, it works in both Totem and VLC.
For Totem this fix by solicitus works
If you load a terminal and do a;
$ gstreamer-properties
in the Video tab there is a drop down box for Plugin. I had a similar issue and selected "X Window System (No Xv)" and that solved my issue.

For VLC this should do the job
In VLC if you go to settings/preferences/video/output modules click advanced options you can change the video output, I have tried X11 video output and Xvideo extension video output, both now display the video in VLC (a bit choppy though)
[http://ubuntuforums.org/showthread.php?t=415012](http://ubuntuforums.org/showthread.php?t=415012)

---

### Post by Gleep on 2007-05-23
> **Campingman said:**
> Hi,
There is a work around to the problems you have with no picture, it works in both Totem and VLC.
For Totem this fix by solicitus works
If you load a terminal and do a;
$ gstreamer-properties
in the Video tab there is a drop down box for Plugin. I had a similar issue and selected "X Window System (No Xv)" and that solved my issue.

For VLC this should do the job
In VLC if you go to settings/preferences/video/output modules click advanced options you can change the video output, I have tried X11 video output and Xvideo extension video output, both now display the video in VLC (a bit choppy though)
[http://ubuntuforums.org/showthread.php?t=415012](http://ubuntuforums.org/showthread.php?t=415012)
You legend =]

Solved both my problems thank you.

---

### Post by jackiecanev2 on 2007-05-23
what kind of video card do you have?

---

### Post by Gleep on 2007-05-23
> **jackiecanev2 said:**
> what kind of video card do you have?
ATI RV350 Radeon 9550

---

### Post by Campingman on 2007-05-23
No problem, pleased you sorted it

---

### Post by arish on 2007-05-24
Ok problem solved the way you described, however video quality is really bad when the option No-Xv is turned on...

so is there another solution to this issue? any update planned for this problem??

---

### Post by Gleep on 2007-05-24
> **arish said:**
> Ok problem solved the way you described, however video quality is really bad when the option No-Xv is turned on...

so is there another solution to this issue? any update planned for this problem??Yeah the quality is really bad for me too, but at least it plays. Totem works fine though, in my experience.

---

### Post by arish on 2007-05-27
> **Gleep said:**
> Yeah the quality is really bad for me too, but at least it plays. Totem works fine though, in my experience.

Well yeah, but i am having a hard time setting the subtitles with totem... that is why i prefer vlc...

---

### Post by birdsixone on 2007-05-30
Thank you! X11 video output works perfectly!

---

