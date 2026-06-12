---
title: "Unreal Tournament 2004 Aborting"
date: 2006-08-15
forum: Gaming &amp; Leisure
---

### Post by harderthanjss on 2006-08-15
I've installed UT2004 on my computer but it keeps aborting on me for some reason. Running it in the terminal produces this:

Xlib: extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Signal: SIGSEGV [segmentation fault]
Aborting.

Any ideas? I'm running 6.06 if it matters.

---

### Post by Josh_b on 2006-08-21
I'm having the same problem. Can anyone help?

---

### Post by rs3 on 2006-08-21
My segmentation faults stopped when I applied the latest game patch.  Assuming you did that already, I am really unsure what else could cause it. :-k

---

### Post by Josh_b on 2006-08-22
Ok, I haven't patched it. I've got the patch for Windows (can't remember what file type, not at home right now). Is it the same one used on Linux?

Also, will that fix sound issues (sometimes sound just doesn't work)

---

### Post by bender888 on 2006-08-22
The windows and linux patches are different, here is a link to the latest UT2004 linux patch.
[http://download.beyondunreal.com/fileworks.php/official/ut2004/ut2004-lnxpatch3369-2.tar.bz2](http://download.beyondunreal.com/fileworks.php/official/ut2004/ut2004-lnxpatch3369-2.tar.bz2)

---

### Post by rs3 on 2006-08-22
> **Josh_b said:**
> Ok, I haven't patched it. I've got the patch for Windows (can't remember what file type, not at home right now). Is it the same one used on Linux?

Also, will that fix sound issues (sometimes sound just doesn't work)

If you get silence when you start UT2004, try this at a terminal:

[B]sudo killall esd
ut2004[/B]

---

### Post by Josh_b on 2006-08-22
> **rs3 said:**
> If you get silence when you start UT2004, try this at a terminal:

[B]sudo killall esd
ut2004[/B]

Yeah, I tried that and it works, but is there a permanent fix? The interesting thing is that it is only silent randomly.

---

### Post by harderthanjss on 2006-08-22
I've got the patch installed but it's still doing it. Oh well.

---

### Post by rs3 on 2006-08-22
From [http://www.3dgamers.com/dlselect/games/unrealtourn2k4/ut2004-lnx-demo3334.txt]("http://www.3dgamers.com/dlselect/games/unrealtourn2k4/ut2004-lnx-demo3334.txt"):

[I]Q: I get the following text on my console when I run the game:
Xlib: extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Is this a problem?
A: No. This means you aren't using an X server from Xi Graphics.
That message means we're looking for the X11 extension they use to
change screen resolutions, and having a non-XiG X server, you
don't have it. THIS IS NOT A UT2004 BUG. It's not a bug at all.
Xlib prints that "error", but we handle it gracefully.[/I]

I am going to guess that this is unrelated to your repeated segmentation faults, as I could find nothing linking the two anyway.  What kernel (x86, amd64) are you using?  And what video card?--I'm assuming you're running the proprietary driver if you're using either ATI or NVIDIA...

> 
Yeah, I tried that and it works, but is there a permanent fix? The interesting thing is that it is only silent randomly.

I'm not sure, frankly.  You can disable esd in System > Preferences > Sound by unchecking "Enable software sound mixing (ESD)" but I'm not sure if that's such a great idea.  Anyone know of a better way?

---

### Post by harderthanjss on 2006-08-22
x86 and NVIDIA GeForce4 MX 420

---

### Post by rs3 on 2006-08-22
> **harderthanjss said:**
> x86 and NVIDIA GeForce4 MX 420

Did you install the proprietary NVIDIA driver?  In Dapper, it's quite easy.

**sudo aptitude install nvidia-glx**

Then, modify your xorg.conf (/etc/X11/xorg.conf); replace Driver "nv" with Driver "nvidia"

I haven't tried running UT2004 with the bundled open source driver ("nv") but I imagine you'd not get desireable results, if any at all.

---

### Post by harderthanjss on 2006-08-23
Unfortunately I've tried that, to no avail. Thanks anyway, though.

---

### Post by Josh_b on 2006-08-24
> **rs3 said:**
> If you get silence when you start UT2004, try this at a terminal:

[B]sudo killall esd
ut2004[/B]

> **Josh_b said:**
> Yeah, I tried that and it works, but is there a permanent fix? The interesting thing is that it is only silent randomly.

Correction, that only works sometimes. If I quit (or it crashes) the sound will randomly work. What other fixes are there?

---

### Post by Josh_b on 2006-08-25
> **Josh_b said:**
> If I quit (or it crashes) the sound will randomly work.

***UPDATE*** If it crashes, I can get the sound working again by starting ESD and then closing it again, but it causes the game to stop even few seconds. grrr

---

### Post by crane on 2006-08-28
Try changing your desktop resolution and running the game. I remember this problem when UT was released but can't remember what fixed it.
 Do a search for the error  message as  well. I know the answer is here some where.

 G/L and let us know what happens.

---

### Post by Josh_b on 2006-08-29
Yeah, I'm going to uninstall it, reinstall it again (in the proper directory this time) and I'll fully patch it (with the megapack and stuff, if I can figure out how.:-k )

---

### Post by Perfect Storm on 2006-08-29
[http://ubuntuforums.org/showthread.php?t=244841](http://ubuntuforums.org/showthread.php?t=244841)

or

[http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63)

---

