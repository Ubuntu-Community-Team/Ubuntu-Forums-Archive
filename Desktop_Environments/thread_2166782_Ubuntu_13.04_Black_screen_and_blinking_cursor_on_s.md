---
title: "Ubuntu 13.04 Black screen and blinking cursor on startup"
date: 2013-08-11
forum: Desktop Environments
---

### Post by snakeplizzken on 2013-08-11
I have Ubuntu 13.04 installed on a SSD and almost always the computer boots to a black screen and a blinking cursor.
There seems to be a timing problem related to lightdm.

I can still login by entering the password ("in the dark") or
pressing Ctrl-Alt-F1 to enter terminal mode and once logged in:
> sudo service lightdm restart

I thought the problem was solved by following the advise here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150)

#16:
Add sleep 2 to /etc/init/lightdm.conf

And it seemed to work but now I discovered that the problem is still there.
I don't have a graphics adapter - only a motherboard (Gigabyte Z77-DS3H) with integrated graphics.

It seems like the SSD is to fast for lightdm. What more can you do?
Any ideas?
This can't be an uncommon problem.

Ohhh... There is a bug report on this issue:
[https://bugs.launchpad.net/lightdm/+bug/1097521](https://bugs.launchpad.net/lightdm/+bug/1097521)

But it is from January and nothing happens...
Is it so uncommon to use an SSD as boot disk?

---

### Post by Rsxhawk on 2013-08-30
I have this problem as well as I use a 90 gig Kingston SSD as my primary OS drive but I'm running 12.04 LTS.  It doesn't happen all the time, and when it does it seems pretty harmless, i just login from the "terminal" like screen that appears since it gives me the opportunity to do so, and then I give the command "startx" and then it boots into the GUI just fine.  They do need to fix that.

---

