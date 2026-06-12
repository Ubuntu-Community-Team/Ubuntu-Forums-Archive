---
title: "Why do the same three windows open at startup?"
date: 2006-11-19
forum: Desktop Environments
---

### Post by wilberfan on 2006-11-19
When I boot to my gnome desktop, the same three windows open--almost like I told the session manager to 'save' my last session.  (In fact, the session manager is one of the windows that opens.)

"Automatically save changes to session" is NOT selected, though...  :confused:

---

### Post by gustolove on 2006-11-20
might i ask what the 2 windows are besides the session manager?

---

### Post by hashimoto on 2006-11-20
Actually, I had the same behavior yesterday: Three nautilus windows (my home folder in all of them) opening after log on. But this was only on my spare PC, not on my main one. Would be nice to know what happened as I didn't have those windows open when logging off last time and I don't have the sessions saved.

---

### Post by gatiba on 2006-11-20
Same problem here: 2 nautilus windows and one shell at startup!

---

### Post by Crooksey on 2006-11-20
From gnome run, Admin > Sessions, then see if you have startup programs listed.

---

### Post by wilberfan on 2006-11-20
> **gustolove said:**
> might i ask what the 2 windows are besides the session manager?

Well, things have changed a bit:   I decided to see what would happen if I checked the "Automatically save changes to session" button, and now my Home folder no longer opens.

One of my startup programs is "Mail-Notification"--which is set to open Thunderbird if it finds any mail.   At the beginning of every session I get an error message that says that an instance of Thunderbird is already running--so I wonder if TBird was one of the three windows that were opening when I originally posted?

---

### Post by CatKiller on 2006-11-20
I had this for a while too - the session seemed to have been saved at the point that I unticked the "Save Session" box in Session manager. So every time I logged in, it would open Session manager (and Nautilus, and a Terminal window, IIRC). The solution I found was to **untick the box**, **close everything**, then press **Alt-F2**, and then run **gnome-session-save**. This saved the session at the point where everything was closed, and all has been well since.

---

### Post by wilberfan on 2006-11-20
I don't know if it's related, but I was having trouble getting gdesklets to stay in the session manager:   [http://www.ubuntuforums.org/showthread.php?t=292228](http://www.ubuntuforums.org/showthread.php?t=292228)

---

### Post by wilberfan on 2006-11-20
I just did a restart--without any new mail present--and did NOT get the "thunderbird already running" error message, so that problem is most likely Mail Notification related.

I did NOT get any of the other windows opening, either... (ie, I got a normal startup this time.)

---

