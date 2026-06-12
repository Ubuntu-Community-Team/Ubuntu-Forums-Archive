---
title: "GDM times out to WHITE screen"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by balance07 on 2007-10-25
I just upgraded to Gutsy (fresh install) but am experiencing an odd problem:

If one or more users are logged in, and then the current user chooses to "switch users", the screen goes to the GDM (as it should). If the PC isn't used at that point, after a few minutes, the screen goes completely white. Mouse cursor is there, and it's possible to move it around and see where a text input box is, but it's still all white. I have discovered that the screen that is white is the "locked" screen. The only way I have found to get rid of it is to type in the password for the last user who used the PC.

This is certainly not ideal, I'd love to see it fixed. I have nvidia graphics (restricted drivers) and desktop effects are enabled.

Best solution I have come up with is to tell all users to "lock screen" when done instead of "switch user", this puts the PC directly at the lock screen, where there is an option to switch user if needed.

Admittedly, I didn't think of hitting "Alt-S" at the white screen to try to get back to GDM, I'll replicate the problem and try that tonite.

Any ideas?

---

### Post by balance07 on 2007-10-26
UPDATE: when on the white screen, pressing "Alt-S" does take me back to the GDM login screen.

still not an ideal situation tho...

---

### Post by rsay on 2007-11-11
Same problem here. If I happen to know which user is logged in I can just type their password blindly instead of going to alt-s

Have you already filed a bug?

---

### Post by rykel on 2007-11-11
I am also struggling with this bug... quite serious, if you ask me, since a user would be freaked out, thinking that the PC has hanged...   :(

---

### Post by balance07 on 2007-11-11
i have NOT submitted a bug report, because i am... oh what's it called.. lazy.

also: i have no further updates. would still love to see it fixed :)

---

### Post by chrishutt on 2007-11-13
Same problem, again with nvidia and compiz.

---

### Post by bford16 on 2007-11-23
Similar problem here.  Again, Gutsy, nVidia, Compiz.  I also get the white screen when switching users sometimes.  I have tried disabling "sync_to_vblank" in gconf-editor, and disabling "detect refresh," with refresh rate set to 60 (the default rate of my monitor).  No change in behavior.

---

### Post by Series8217 on 2007-12-04
Same problem here, it happens when using "switch user" and then logging out of the second user. If i type my password on the white screen and hit enter, it logs back in.
The locked-screen dialogue apparently doesn't load correctly.

---

### Post by mortonato on 2007-12-05
Same problem, Once again with nvidia and compiz. :mad:

---

### Post by zachofalltrades on 2007-12-05
ditto

fresh install of Gutsy (64 bit), compiz on default settings, nvidia driver enabled (with dual monitors via twinview)

I reinstalled the whole system because I thought I had screwed something up with Automatix -- I did everything the "right way" via synaptic the second time around, but the problem is still there.

glad to hear there is a workaround with alt-s

has a bug actually been filed yet? I'm not even sure how...

---

### Post by Amaranth on 2007-12-08
There has been a bug filed but the problem is (once again) with the nvidia driver. The problem is that when you do Switch User it does a VT switch to a new X server before the screensaver window has shown up.

With the nvidia driver if you do a VT switch then try to create a new GL texture the texture does not get allocated (this is similar to the black window problem) so you end up with a white window. In this case it's a fullscreen window so you end up with a white screen.

---

### Post by Anubis on 2007-12-21
> **zachofalltrades said:**
> ditto
I reinstalled the whole system because I thought I had screwed something up with Automatix -- I did everything the "right way" via synaptic the second time around, but the problem is still there.

That reinstall was a waste of time.:confused:

Automatix does not break anything. 

Seems this misinformation will persist.

Carry on.:(

---

### Post by mirzmaster on 2008-02-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/160264](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/160264) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I think I've located the Launchpad bug for this issue.  It's being confirmed as an nvidia driver bug.

---

### Post by tranau151 on 2008-03-09
Does anyone know of a video card for Gutsy 64 that fully supports switching users?  This seems to be a problem common with all NVIDIA cards?  Any ATI-based vids being used out there supporting this function?

---

### Post by Amaranth on 2008-03-09
Well, ati and intel don't allow compiz with more than one X server (or 3D, even). Only nvidia lets you use 3D with more than the first user and it has this bug. Basically they all suck somehow.

---

