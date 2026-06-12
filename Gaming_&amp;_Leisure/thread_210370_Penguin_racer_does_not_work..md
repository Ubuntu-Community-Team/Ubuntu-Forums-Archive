---
title: "Penguin racer does not work."
date: 2006-07-06
forum: Gaming &amp; Leisure
---

### Post by skale on 2006-07-06
I thought what the hell, installed the xgl/compiz thingy, thought it was gay, undid it according to the guide, and now Penguin Racer does not work. I got rid of it, installed it again, updated the drivers, did some other stuff, but it still doesn't work. It had worked on the computer yesterday. Tetris and Solitaire work fine. I love that game.
Any ideas?

---

### Post by dubnmike on 2006-07-06
What happened when you try to run it?  Have you tried running it in a terminal?  If so, what kind of errors are you getting?

---

### Post by skale on 2006-07-06
It just doesn't turn on.
> sameer@Sameer:~$ ppracer
PPRacer 0.3.1 --  [http://racer.planetpenguin.de](http://racer.planetpenguin.de)
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Success)


---

### Post by Lord Illidan on 2006-07-06
You might have to re-install nvidia drivers I think.

---

### Post by skale on 2006-07-07
I purged, installed the drivers and then Reinstalled ppracer. No luck. However, I did a google search and found that changing the color pixel depth from 24 to 16 would help. The xgl howto also mentioned the bpp and It might have been changed to 24. I could not find anything else, so I might try that. How do I change the bpp?

---

### Post by sgtBiafra on 2006-07-07
From the error message above, it looks as if Xorg is having a problem locating the glx module. I experimented with this at one point and seem to remember having to edit the /etc/X11/xorg.conf file and comment out a module (I believe it was dri). Perhaps you commented out glx as well or it may depend on dri.

(edited for spelling)

---

### Post by skale on 2006-07-08
> Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
I undid all that.

---

### Post by Burgresso on 2006-07-24
*Bump*

I'm having the same issues - any success here? If needed, how to I reinstall Nvidia drivers?

PS I think I'd rather have more upgradable/stable system then "the best" video drivers, if this means no Planet Pengiun Racer that's ok :) 

gracias

burgresso

---

### Post by Burgresso on 2006-07-28
Upgrading to the latest Nvidia drivers worked for me - look for the how to.

---

