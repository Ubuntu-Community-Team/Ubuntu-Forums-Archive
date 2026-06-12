---
title: "Nautilus failing to open"
date: 2008-02-23
forum: Desktop Environments
---

### Post by fishonadish on 2008-02-23
Hi,

Nautlius has decided to stop opening in my user account.

When I log in, the desktop image takes ages to load, but appears eventually.  However, I can't get a file browser to open at all.  Running 'nautilus --no-desktop --browser %U' and various permutations of it from the CLI does nothing; i.e. no output, no apparent activity at all.

This isn't affecting other user accounts, and seems to have just appeared overnight.  There don't appear t have been any relevant updates recently.

Any thoughts?

Fishonadish

---

### Post by gmaniac on 2008-02-23
do a
```
cat .xsession-errors
```after you try to run nautilus

---

### Post by fishonadish on 2008-02-23
Thanks for the reply.

There doesn't seem to be anything relevant in xsession errrors though:

```
Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
** Message: Not starting remote desktop server
evolution-alarm-notify-Message: Setting timeout for 43175 1203811200 1203768025
evolution-alarm-notify-Message:  Sun Feb 24 00:00:00 2008

evolution-alarm-notify-Message:  Sat Feb 23 12:00:25 2008

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
  PID TTY          TIME CMD
ERROR: decompression failed
```

That seems to be compiz related.

Further to the above, when I log in everything appears very slowly, i.e. panel icons and tray etc.  Also, the background doesn't appear at all now, unless I open the appearances app and reset it.

I'd really rather avoid having to make a new user account and lose my settings to get around this.  Any ideas would be appreciated.

Regards,
Fishonadish

Update: I've tried disabling compiz and logging in and out again to see if it was related, by the way, but the problem persists.

---

### Post by fishonadish on 2008-02-23
Another update...

This may be compiz related after all, I think.

With desktop effects on, the window list doesn't work - i.e. no 'bars' appear on it - as well as nautlius, but this is resolved with them off.  However, still no file browser.

Also, on logging in the panel icons etc. are displayed for a moment an then disappear and slowly return - I assume this is the point where compiz is turned on.

I have tried renaming all the config folders that seemed relevant to *_backup to see if I it helped, but no luck there (I changed .gnome2, .gnome, .gnome2_private, .gconf, .gconfd).

It's strange that it's only one user account that's affected - it must be caused by some setting in my home folder then, mustn't it?

Anyway, if anyone can come up with any suggestions I'd appreciate it.

Fishonadish

---

### Post by gmaniac on 2008-02-23
:confused:.
What ```
dmesg
``` has to say ?
Although i haven't tried it myself you can preserve your settings in a new account by copying all directories and files starting with a "." (dot). 
i.e something like sudo cp -R (old account)/.* (new account)/

Ps if after copying the files the new account fails maybe some customization you made has borked your profile

---

