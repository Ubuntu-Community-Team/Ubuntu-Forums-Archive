---
title: "Compiz and video playback"
date: 2010-02-03
forum: Desktop Environments
---

### Post by giantjoebot on 2010-02-03
I have been noticing in certain videos that I get choppy video and these weird distortion lines.  It turns out that when any visual effects or compiz is enabled that I get this issue.  I have tried several workarounds, including X11.  I've been searching on the forum, and googling the problem, and I don't seem to be the only one.  Also it would be nice to be able to use vdpau and compiz.  So does anyone have a solution to this problem?

I'm running Ubuntu 9.1 64bit

My video card is a nvidia 8600GT

---

### Post by Minsky on 2010-02-03
I had the same problem with VLC. I'm running Karmic 64 with an ATI card and with Compiz and Emerald enabled, and I experienced the same distorted video playback. The way I fixed it was to change the video output in VLC from X11 to OpenGL.

---

### Post by finlost on 2010-02-03
I am running Compiz in 32-bit 9.10 with a nVidia 8600GT card without the issues you are describing.  No solution, but saying I have a similar setup only in 32-bit.

---

### Post by giantjoebot on 2010-02-03
The X11 didn't work for me, and the vdpau gives a lot better quality playback.  There is a button I can install to turn compiz on and off.  I think I might just use that, and turn off compiz when I want to watch something.  At least until its fixed, or there is a better way to fix it.

---

### Post by Gemba on 2010-02-04
Here's how I fixed this:

Go to compiz config settings manager

'General Options'

'General'

Make sure that the 'Unredirect Fullscreen Windows' option is ticked.

Then I changed VLC's video output to X11.

---

### Post by giantjoebot on 2010-02-04
Holy crap, that actually worked, and best of all its working with vdpau in smplayer, vdpau as opposed to X11.  Still have problems with the default player, but thats okay, I like smplayer better anyways.  I noticed some flickering when going in and out of full screen, and when going down to the controls, but I can totally live with that.   

Also only fixes full screen, which is still something that I can live with

I wish there was a way to turn off compiz on just smplayer

---

