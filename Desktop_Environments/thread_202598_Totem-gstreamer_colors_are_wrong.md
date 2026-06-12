---
title: "Totem-gstreamer colors are wrong"
date: 2006-06-23
forum: Desktop Environments
---

### Post by stinerman on 2006-06-23
Howdy,

I'm starting off with a fresh install of Totem and the colors are incorrect.  To be precise, the Blue and Red channels are swapped.  A screenshot is provided.

This happens regardless of the codec used.  Also, any thumbnail preview of a movie gets the colors right, but reverts to the swapped colors as shown in the screen shot.

I have an ATI X1600 Pro, using the fglrx drivers.  My xorg.conf is also provided.

Thanks for any help you can give.

---

### Post by masterjonny on 2006-06-23
Try using a different media player (such as VLC) and see if you still get the problem, this way you can pinpoint if its totem or your card causing the problems...

---

### Post by stinerman on 2006-06-23
It works fine with mplayer ...

(odd that I replied to yours and you replied to mine :D)

---

### Post by floguy on 2006-06-25
Same exact problem here: totem is rendering bluish and all other media players work fine.  ATI X1800XL here running fglrx 8.25.18

---

### Post by pertti on 2006-08-06
Same problem here with totem-gstreamer, in a laptop with an ATI x1400. However, mplayer doesn't have this problem.

I have another computer with the same version of totem and flgrx (the latest from the repositories), with an ATI 9600 Pro, which plays videos without this problem.

Could this be a problem with the support of the ATI x1_00 cards?

---

### Post by pertti on 2006-08-09
I switched to vesa driver and all videos played fine, so I guess it has something to do with the fglrx driver.

I also played around a bit with gstreamer-properties, and found that testing SDL or Xv would crash it. Here's the error message for SDL:

```
The program 'gstreamer-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 25 error_code 2 request_code 141 minor_code 19)
```

And for Xv:

```
The program 'gstreamer-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 52 error_code 2 request_code 141 minor_code 19)
```

I switched to 'No Xv', and the colors on the videos where right, but they looked a bit ugly when stretched (that's what Xv is for, right? ;).

Another thing I noticed is that new thumbnails of video files always look ok, even when using Xv.

Here's the Device section on my xorg.conf, though there's not much to look at:

```
Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection
```

---

### Post by shoffman11 on 2006-08-09
Not to hijack your thread, but I'd like to add that I have the same problem as you when watching video in mythtv and totem.  Mplayer looks correct.  The colors are swapped.  I'm also using the fglrx driver.  I have the same problem with the version in Synaptic and the one I downloaded from ati.com.  I have an x1400 as well.
Just letting you know it's a problem with fglrx and not the media player.

Edit: forgot to mention the colors display correctly in mythtv and totem with the vesa driver.

---

### Post by autrui on 2006-08-27
> **pertti said:**
> 
Could this be a problem with the support of the ATI x1_00 cards?

i have the same problem with ATI x1300pro.

weird...  i'm gonna check out VLC.

autrui

::edit:: vlc looks fine.  i used it when i was on windows xp, and though i never found the interface as intuitive and awesome as media player classic, it always played just about every format i've ever heard of.  if we get no solution to the totem problem, i recommend vlc.

---

### Post by pertti on 2006-08-28
Yeah, right now I'm using mplayer for video playing, which can play any file I've thrown at it and have lots of options, but also a couple of annoyances (like restarting the video when I change the audio track, or having to select a different aspect ratio for my widescreen display when going fullscreen (and then restarting again)).

Furthermore, last week I installed XGL+Compiz (I can't find the link now), and video run fine on Totem on a XGL session, but crashed on a normal session. Then I went back to regular X.org, and colors where wrong again. Some of the packages that I upgraded when I installed XGL where xorg-something, but I can't remember if any of those was related to ATI.

---

### Post by pertti on 2006-11-06
*Bump*

I was wondering if this problem has been resolved in Edgy Eft. I haven't updated yet because I also have concerns about my "wonderful" Dell 1380 wifi card ;).

---

### Post by hackeron on 2007-02-14
Hmm, having same problem in feisty - anyone have a solution?

---

### Post by rjcroy on 2007-02-16
I have this same problem but I occurs whichever media player I use: totem, VLC, mplayer.
I have an ATI Radeon X1300 and are using fglrx 8.33.6 on Edgy.

---

### Post by Deus42 on 2007-03-15
I'm having the same problem with Feisty, 

What's strange is the problem didn't show up until I got DRI working with fglrx.

Try disabling dri (your video framerate will suffer!) and see if that fixes the problem.

---

### Post by desync0 on 2007-03-17
I'm also having this problem with mythtv playing live tv/recorded tv, but mplayer plays other movies fine.

I had this problem before but I can't remember the fix.

---

### Post by desync0 on 2007-03-17
Found the fix for this problem if you're using an Ati video card....

check out** [this link]("https://launchpad.net/ubuntu/+source/mythtv/+bug/73102") ** near the bottom somone attached a recompiled libmyth that fixed it for me.

 Or you can recompile myth with the options they talk about.


Good luck guys!

Chris

---

### Post by Mr Frosti on 2007-04-20
Has anyone filed a bug for this issue?

---

### Post by pertti on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/93144](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/93144) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Mr Frosti said:**
> Has anyone filed a bug for this issue?

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/93144]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/93144") .

---

### Post by Mr Frosti on 2007-04-21
A  bug for this issue labelled as "status: confirmed" is located at the address below:

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/79559](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/79559)

I have referenced this bug to the bug posted above. It looks like a change is on the way...

---

### Post by pertti on 2007-04-22
> **Mr Frosti said:**
> A  bug for this issue labelled as "status: confirmed" is located at the address below:

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/79559](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/79559)

I have referenced this bug to the bug posted above. It looks like a change is on the way...

The last post on that bug is three months old and the fix hasn't already been released :(. Also, reading the associated upstream bug, it seems that it is a problem with the fglrx drivers on ATI X1xxx cards and not on GStreamer. Maybe the fix is about getting around that problem with fglrx.

---

### Post by willywongi on 2007-05-01
Still waiting for this fix to be seen in an update... btw, is there a way to use VLC mozilla plugins instead of totem plugins? This could resolve some of my issues..
Thanks

---

### Post by krizz on 2007-05-16
Same situation here in Feisty, ATI X1600,fglrx in Totem.

A **workaround** that worked for me is (Totem gstreamer):
[LIST=1]
[*]run **gstreamer-properties** from console
[*]go to tab **Video**
[*]select Default Output -> Plugin -> **X Windows System (No Xv)**
[/LIST]

I don't know if there are any performance issues by not using Xv. If anyone knows please tell

---

### Post by pertti on 2007-05-16
> **krizz said:**
> I don't know if there are any performance issues by not using Xv. If anyone knows please tell

I don't know either if there's any performance penalty, but scaled and full-screen videos don't look as smooth.

By the way, I can't seem to play videos with subtitles in Totem anymore - an error dialog appears when I try to play one. I'm not on my computer right now so I can't tell if it's related to Xv or not. Does anyone have the same problem?

---

### Post by Technoviking on 2007-05-16
This fix work for me, and no performance issue afterwards.

[LIST=1]
[*]Run gstreamer-properties
```
macbuntu:~$ gstreamer-properties
```
[*]Change the video output plugin to custom
[*]Change the video output pipeline to:
```
ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink
```
[/LIST]

---

### Post by krizz on 2007-05-16
> **Mike said:**
> This fix work for me, and no performance issue afterwards.

[LIST=1]
[*]Run gstreamer-properties
```
macbuntu:~$ gstreamer-properties
```
[*]Change the video output plugin to custom
[*]Change the video output pipeline to:
```
ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink
```
[/LIST]

Yeah!!! That's the trick! Mike's solution gives me more than 50%, less cpu utilization from not using Xv and beautiful colors. :D

Thanks

---

### Post by krizz on 2007-05-19
> **krizz said:**
> Yeah!!! That's the trick! Mike's solution gives me more than 50%, less cpu utilization from not using Xv and beautiful colors. :D

Thanks

The problem though, with this approach, is that movies with external subtitles wont work. Maybe it's relevant to this bug [http://bugzilla.gnome.org/show_bug.cgi?id=350299](http://bugzilla.gnome.org/show_bug.cgi?id=350299).

damn it was too close :(

---

### Post by Daedalus on 2007-10-24
This problem is solved with the new 8.42.3 fglrx drivers.

---

