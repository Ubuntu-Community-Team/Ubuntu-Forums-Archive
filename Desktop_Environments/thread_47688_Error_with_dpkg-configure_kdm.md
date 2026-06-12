---
title: "Error with dpkg-configure kdm"
date: 2005-07-09
forum: Desktop Environments
---

### Post by ChodeNode on 2005-07-09
Hello,

I'm trying to switch over to KDM, but I'm getting an error when I run it:

> sudo dpkg-reconfigure kdm
 * Reloading K Display Manager configuration...                                                 [fail]
invoke-rc.d: initscript kdm, action "reload" failed.

I have no clue what is causing this. Is there something I can manually edit to get this to work?

Thanks,

Chode

---

### Post by pipodnmy on 2005-07-09
not sure what ur problem is, but from what i understood you are using something else right now (xdm, gdm) and you want to start using kdm?
is that right?
if so, remove the prev one that from running at start-up, and then add a link to kdm to run at start-up..
if you dont have kdm installed already, simply:
apt-get install kdm //not sure why you want to reconfigure it?!
all links to start-up programs are in /etc/init.d/

---

### Post by az on 2005-07-09
You obviously have a big problem with your kdm package.  The wrong way to fix it is to change a file by hand.

Where did you install kdm from?

---

