---
title: "All users disappeared.  Can't login."
date: 2008-12-10
forum: General Help
---

### Post by nc_jed on 2008-12-10
From what I can tell, all my users suddenly and abruptly disappeared.  I am trying to start up and I get errors in the startup messages that it cannot find user 'gdm' for instance.  There are others before that, but they flash by.  When I 'enter' through the 'Can't start GDM' error, I am dumped to a shell login on TTY1.  It won't recognize my regular username/password combo.  I assume /etc/passwd or /etc/shadow is fried.

I periodically have issues on start up and have to run fsck (finds tons of orphaned crap), but it has honestly been a while (a few clean reboots) since this has happened, so I don't think that's it.

So anyway, what to do?  I'd assume reboot with the livecd.  is there a rescue option there, or all my data gone?

- Jed

---

### Post by louieb on 2008-12-10
> **nc_jed said:**
> Feriodically have issues on start up and have to run fsck (finds tons of orphaned crap),

Sounds like your being warned the hard drive is about to die. 
If it were me I boot to a live CD and get whatever data you can copied off.

---

### Post by nc_jed on 2009-01-03
long time between posts, I know, but here is what I've found out.  


A few nights back, I pulled the drive from the laptop after weeks of literally the same behavior.  I mounted it into a USB enclosure to pull my files off of it before it really did die.  To my surprise, the drive installed fine, was recognized by the host (another Xubuntu installation (on a desktop)), mounted and I pulled the files off.  It has been live ever since, leading me to believe that the drive may not be really the problem.  the Laptop is quite old and has been having problems periodically.  perhaps it is "scrambling" data (the battery doesn't work and it runs off AC 100% of the time, for instance).

Anyway, to my real post, since I have the drive mounted, shouldn't I just be able to copy over a few files from the desktop to the laptop drive (mounted as a USB drive), (like /etc/passwd and /etc/shadow) and be back in business?

I'd really like to avoid reinstalling and am interested in any suggestions you have for a patch job.

- Jed

---

### Post by nc_jed on 2009-01-03
Edit: I just discovered there is no /etc/passwd file on the USB (Laptop drive).  Guess that explains why no users are present...

I'll see what I can find out about rebuilding on the Google.

Thanks.

- Jed

---

