---
title: "multiple desktops"
date: 2006-10-14
forum: Desktop Environments
---

### Post by dpgrant on 2006-10-14
I have a fairly clean install of Ubuntu.  A few questions:

1) When I log in, it takes 2-3 minutes for after my password before my desktop is up.  What can I do to fix this.  Last week, when trying to get DVDs working, I found instructions to apt-get remove -purge gstreamer, which of course removed the ubuntu desktop.  I logged in via ssh, reinstalled ubuntu desktop, rebooted, and since then it takes a long time to get the desktop after a login.

2) This computer will not only function as a desktop for me, but will also be for the kids (their first).  I'd like to have my account log into Ubuntu, and the kids login to Edubuntu, with easy switching between.  How do I do this.

3) Finally, I'd like to be able to get a full GUI from my laptop (Windows), even if my kids are on the computer.  I've installed VNC, which isn't very satisfying, as it just takes over the screen.  I suppose I could do this with an X-window server on my windows box, and good free ones, and how to set it up to tunnel over ssh?

---

### Post by encompass on 2006-10-14
For number 3, I use an old lappy to xdmcp (look it up) to log into my big computer when the wife is on.  Depending on how old the kids are... you should be able to just use the same sofware packages from ubuntu to let them have all their games and other cool software.
As for your setup with the long boot, wow... something is really trying to think hard... does it read the harddrive alot?  is this during the boot or during the login?
You could drop to a console and see what is taking it so long.
Cntrl Alt F1 login and type top press q to quite and exit to logout.. then ctrl alt F7 to get back in.

---

### Post by dpgrant on 2006-10-14
The delay is after login.  There doesn't seem to be any hard drive access or anything.  It almost feels like it is waiting for something to time out.  I'll look at in a terminal window.  What should I use, top?

dg

---

### Post by dpgrant on 2006-10-14
As for the extended login, it took 3 minutes and 15 seconds, top showed a spike up to about 3-5% immediately after I entered the password (for about 2 seconds), and then a second spike of about 10% once the desktop actually came up, but was hovering at about 0 for the entire time in between.  tcpdump didn't show any traffic going in or coming out.

---

### Post by encompass on 2006-10-14
Here is what I would do...
create new account and see if it can login ok...
to creat the account...```
sudo adduser thingyname
```
then just go back to your gdm graphical login and see what happens.

Anything with your new account or the same problem.

---

