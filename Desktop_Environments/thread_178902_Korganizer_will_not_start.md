---
title: "Korganizer will not start"
date: 2006-05-18
forum: Desktop Environments
---

### Post by kenklay on 2006-05-18
I have been using Korganizer for some time and now it will not start.  The problem started the day after I installed Konserve and included std.ics in a daily backup.  I had not closed Kontact at the end of my previous session so kde was also openning it while Konserve was trying to do its backups.  Konserve crashed with an error message about accessing /tmp/ directory.  Kontact now crashes if I click the calander icon.  If I try to start Korganizer in konsole the curser moves to the next line and nothing more happens.

In another thread I found a suggestion to remove lock files.  I removed 4 or 5 from the .kde/.../abc/lock directory.  But that did not help.

If I run "ps -A" in konsole after trying to start korganizer I will occasionly see "korganizer" listed and "korganizer <defunct>" listed.  Running "killall -9 korganizer" does not help.

I considered uninstalling korganizer so I could reinstall, but when I preveiwed that idea in Adept it also wanted to uninstall KDE desktop so I aborted that idea.  It would not unlink the two. 

This is my work system so any help will be greatly appreciated.

---

### Post by ltmon on 2006-05-18
Try removing all cache files, it sometimes helps.

This won't harm you system, as they are all temporary and will be regenerated on startup if missing:

```

rm -rf .kde/socket-<HOSTNAME>
rm -rf .kde/tmp-<HOSTNAME>
rm -rf .kde/cache-<HOSTNAME>

```

Logout and login again after you have done this.

L.

---

### Post by kenklay on 2006-05-19
That did it, it started up.  

Unfortunately my calander file got corrupted when the crash occurred, so Kontact or Korganizer would not start with it.  I had reanmed it before in my efforts to get Korganizer going and when I made it the std.ics, korganzier would not open.   In copying from the orginal to a new std.ics file, I have located the faulty data to be some where between lines 3998 and 4995.  Was out all with my son at technical school orientation and it is getting late now, so will continue tomorrow to pinpoint the bad data and then I will be back to work.

Thanks so much.

---

