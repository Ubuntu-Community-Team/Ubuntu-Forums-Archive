---
title: "Mail-Notification Pop-up"
date: 2009-05-28
forum: General Help
---

### Post by gruppler on 2009-05-28
No matter what i change the Expiration setting to in the Message Popups tab, i always get dialog box popups, as if i had set it to "Never."  The test messages work correctly, but when i actually get an email, i get the dialog box notifying me, rather than a popup in the corner as in the test messages preview.

I've tried other mail notification programs, but this one seems to be the best.  Others are either for a window manager other than Gnome, hog memory, or they don't use the new Ubuntu notification system.  I just switched from Fedora, and it was working fine there (though there are many more things that didn't work properly on Fedora that do in Ubuntu).  Is anyone else having this problem?

I've tried reinstalling and configuring with the Configuration Editor, but nothing has worked.

---

### Post by Bender2k14 on 2009-05-28
What mail notification program are you talking about?

---

### Post by gruppler on 2009-05-28
> **Bender2k14 said:**
> What mail notification program are you talking about?

The program called "mail-notification" located at /usr/bin/mail-notification.

---

### Post by rosswmcgee on 2009-05-28
Have you tried "revert in the browse part of properties? Instead of using usr bin.

---

### Post by arkusk on 2009-08-11
It is a known bug: [https://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/332767](https://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/332767)
The workaround posted on that page works for me, in short:
> To be nice, I should mention here that it is possible to disable the actions in gconf-editor as a horrible workaround :)
Look in /apps/mail-notification/popups/actions. (Just delete everything in that list).hth
Arian

---

### Post by migmruiz on 2010-12-17
this workaround works for me too. it's strange to have this bug in maverick...

---

