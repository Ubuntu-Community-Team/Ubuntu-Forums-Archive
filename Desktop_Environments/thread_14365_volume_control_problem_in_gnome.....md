---
title: "volume control problem in gnome...."
date: 2005-02-06
forum: Desktop Environments
---

### Post by mike_c on 2005-02-06
This is a strange problem and I can't seem to find the solution.  I just installed Ubunto on a VIA EPIA M10K system.  In the account I set up during the install, sound works fine, i.e. I can play audio CDs and mpgs without difficult (one minor issue was that I don't have an analog audio cable on my CDROM, so I have to use XMMS to play CDs directly, but no worries).

I'm setting this machine up as a GiantDisc music jukebox, so I added a user named "music" with home directory in /home/music.  That's where the problem begins.  User music apparently has no control over system volume settings, and in particular the volume control is set to zero, but only in usr music's account.  The gnome panel volume control remains pegged on zero no matter what I do when logged in as "music".  If "music" tries to run gnome-volume-control, he receives the "Sorry, no mixer elements or devices found" error.  Again, simply logging in as the original system user solves this problem, but that doesn't help in the "music" account where the GiantDisc server runs.  Likewise with aumix, which works well in my regular account but which returns the error "aumix: error opening mixer" in "music"'s account.

I presume this is a permissions issue, but I can't figure it out.  Permissions are wide open on /dev/dsp, so that's not it.  It's not a hardware issue-- sound works beautifully in "my" account.  

Any hints?

---

