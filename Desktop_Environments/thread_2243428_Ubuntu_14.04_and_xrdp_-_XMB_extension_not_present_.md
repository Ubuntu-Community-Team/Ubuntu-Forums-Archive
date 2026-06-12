---
title: "Ubuntu 14.04 and xrdp - XMB extension not present on..."
date: 2014-09-08
forum: Desktop Environments
---

### Post by frankh on 2014-09-08
Ok, this is getting ridiculous...

I've been trying to get xrdp to work on Ubuntu 14.04, but it seems just about impossible to get the keyboard map to work.

I have the following setup:

Ubuntu 14.04, running xrdp and xfce4

I can connect to the xrdp session from a windows machine. But even though the Ubuntu 14.04 system has NO (no) keymap, the xrdp session has only US available.

If I go to the system settings while in the xrdp session, us is listed as the keyboard layout, and the "Add" button is greyed out. So I cannot add another layout.

I've googled myself blue, but absolutely everyone seems to insist that the solution is, while in the xrdp session, to run this command:

$ setxkbmap

However, this gives the following error:

XMB extension not present on :12.0

Now, I've searched for and installed all thinkable packages that looks like they have anything to do with this, but it still doesn't work.

In addition, NO ONE SEEMS TO HAVE EVER SEEN THIS SPECIFIC PROBLEM OR ERROR MESSAGE, judging from the non-hits on google. How is that even possible?!

Any help is appreciated!

---

