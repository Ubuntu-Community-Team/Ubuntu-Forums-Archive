---
title: "Getting the default kubuntu desktop"
date: 2005-04-08
forum: Desktop Environments
---

### Post by Stephen-I-M on 2005-04-08
My home directory had a .kde directory from a previous distro. I'd like to rename it to something different and get the default kubuntu settings for the appication menu, taskbar, desktop, etc., and then copy over information bit-by-by.

What's the best way to do that?

Stephen

---

### Post by m29389 on 2005-04-08
Hi
I don't know if this is the best way ;) but...

Log out of kde - "End Current Session"
When at the login screen switch to terminal - "Ctrl+Alt+F1 and login"
When in terminal enter - "mv .kde .kde.backup"
Exit terminal and return to login screen - "Alt+F7"
Login to your default kubuntu setup as usual... A new .kde will be created to default spec...

I just tried it to check before posting and it worked for me, hope it does for you too :)


EDIT:

just for fun I tried it again by deleting .kde while logged in to kde then logging out.  On logging back in I got a nice new default-settings kubuntu desktop... In the past though I'm sure that kde has written to .kde on logout so stick with my more long winded method for that really nice, shiny, new feeling! :)

---

### Post by Stephen-I-M on 2005-04-08
Thanks for the post! I'll give it a shot when I'm back home.

Stephen

---

### Post by m29389 on 2005-04-08
That's ok.

I just remembered though... A few settings for fonts, backgrounds, etc(?) are stored in .kderc (settings for what part of kde i'm not sure).  So you may want to do to that what you do to .kde

---

