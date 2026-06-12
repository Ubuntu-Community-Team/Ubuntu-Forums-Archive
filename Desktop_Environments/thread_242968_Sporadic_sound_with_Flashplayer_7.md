---
title: "Sporadic sound with Flashplayer 7?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by christian.convey on 2006-08-24
Anyone know why I'm experiencing this?:

When I watch videos on sites like jibjab.com, which use Flash for the movies, sometimes I get sound and sometimes I don't.

I haven't been able to clearly detect a pattern.  I've tried:
[LIST]
[*]disabling sound from the Gnome menus and reloading the page with the video
[*]doing the same, but re-enabling the sound before reloading the page with the video
[*]The two attempts listed above, but also running "killall esd" from the command line before reloading the video.[/LIST]I can't figure out what I'm doing that makes the Flashplayer sound go away and come back.

Sometimes I think that causing a system beep (by doing something silly on a command-line, for instance) causes Flash sound to come back, but I'm not sure.

Any ideas?

Thanks,
Christian

---

### Post by x64Jimbo on 2006-08-24
Are you attached to the Linux flashplayer? You can run the Windows version of firefox through wine and install the flash plugin there. It works better for me than the linux version ever did.

---

### Post by christian.convey on 2006-08-24
Yeah, I'm using the Linux version.

Thanks for the Wine tip.  Are there any inconveniences with your approach compared to running it all native Linux?

---

### Post by x64Jimbo on 2006-08-24
None whatsoever. If you have wine installed, it's as simple as running the windows installer.

---

### Post by arsenic23 on 2006-08-24
I do this:

$killall esd

Then I start or restart Opera/firefox/etc

When your done just start esd back up.  Works every time for me.

---

