---
title: "mplayer won't go full screen"
date: 2005-12-07
forum: Desktop Environments
---

### Post by leetcharmer on 2005-12-07
Any video files played w/ mplayer will not resize nor go full screen, any ideas?

---

### Post by soulestream on 2005-12-07
preferences <- video <- xv

restart mplayer

soule

---

### Post by badtyprr on 2005-12-07
Make sure you have the libxv1 library installed. I think the command in terminal is:
```
sudo apt-get install libxv1
```
You can set Mplayer in the gui to use the xv output. To set it as your default video output, you can modify the conf file at /etc/mplayer/mplayer.conf. Another option might be to change to *zoom=yes* in the mplayer.conf file. This takes more CPU cycles than necessary, though. If you can get your hardware to do it, it's much better.

---

### Post by leetcharmer on 2005-12-07
didn't work :/

it works in gmplayer now, but not mplayer alone.

---

### Post by leetcharmer on 2005-12-07
yeah, changing to xv in mplayer.conf worked fine, thanks!

---

### Post by kingsidy on 2005-12-07
I never gave mplayer a fair shot because of the fact that I could not get it into fullscreen. I had the xv thing but never selected it. Thanks for the tip soulestream

---

### Post by e2k on 2005-12-20
[QUOTE=badtyprr]Make sure you have the libxv1 library installed. I think the command in terminal is:
```
sudo apt-get install libxv1
```[/QUOTE]
I have libxv1 installed, but still can't manage to get this working..
While trying to display videos with xv selected, I just get a:
```

==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [msadpcm] MS ADPCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 353,8 kbit/25,07% (ratio: 44229->176400)
Selected audio codec: [msadpcm] afm:msadpcm (MS ADPCM)
==========================================================================
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.
```
What's this? xvinfo says this:
```
$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
```

---

### Post by Gats on 2005-12-21
I have exactly the same problem with my Radeon 9600... Any help would be appreciated ;) 

[QUOTE=e2k]I have libxv1 installed, but still can't manage to get this working..
While trying to display videos with xv selected, I just get a:
```

==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [msadpcm] MS ADPCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 353,8 kbit/25,07% (ratio: 44229->176400)
Selected audio codec: [msadpcm] afm:msadpcm (MS ADPCM)
==========================================================================
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.
```
What's this? xvinfo says this:
```
$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
```[/QUOTE]

---

### Post by kaamos on 2005-12-21
What drivers are you using? If it is fglrx, then add this to your /etc/X11/xorg.conf device section:
>      Option "VideoOverlay" "on"
     Option "OpenGLOverlay" "off"
Restart X and try again.

---

### Post by Gats on 2005-12-21
[QUOTE=kaamos]What drivers are you using? If it is fglrx, then add this to your /etc/X11/xorg.conf device section:

Restart X and try again.[/QUOTE]

Thanks a million kaamos! That works well now! :smile: 

Can you just try to explain me a bit what those options are for? I wonder what was the problem exactly and what these options do.

---

### Post by Benedolt on 2007-05-22
> **kaamos said:**
> What drivers are you using? If it is fglrx, then add this to your /etc/X11/xorg.conf device section:

Restart X and try again.

Wow, over a year and about two Ubuntu releases later I am still having the same problem and am able to solve it using your tip, kaamos. Should this enter Launchpad?

---

