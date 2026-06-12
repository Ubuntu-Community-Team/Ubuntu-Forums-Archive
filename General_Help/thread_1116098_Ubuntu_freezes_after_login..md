---
title: "Ubuntu freezes after login."
date: 2009-04-04
forum: General Help
---

### Post by KadirÖ on 2009-04-04
I just installed Ubuntu server edition.
Then it rebootet the computer.

I came to the login screen, where I typed my username and password.

Then it just stays at a brown-like background, and I can move my mouse, but can't anything else.

How could I solve this problem?

---

### Post by KadirÖ on 2009-04-04
Bumping the thread, because I need help fast :)

---

### Post by KadirÖ on 2009-04-04
Bump.

---

### Post by tkearn5000 on 2009-04-04
This problem happened to me also. It's a problem with your graphics card not being able to run the 3d desktop graphics.

After you login hit Ctr Alt F1 to get to the command prompt. You will be asked for your password again. Then enter the following commands:

sudo apt-get remove compiz (press enter)
sudo apt-get remove compiz-core (press enter)

You will again have to enter a password.

Then enter:

sudo shutdown -r now (press enter)

This will reboot your computer, and you should be able to use ubuntu. However you won't have the 3d desktop graphics. I'm currently trying to find out how to get my graphics card to support them. I'll let you know what I find out.
-TK

---

### Post by KadirÖ on 2009-04-04
Thanks for reply, I'll try. :)

EDIT: I just tried, but my keyboard is off when I login, so I can't get the command prompt to come up.

---

