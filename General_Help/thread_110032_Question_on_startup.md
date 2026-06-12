---
title: "Question on startup"
date: 2005-12-29
forum: General Help
---

### Post by buck8 on 2005-12-29
I'm a newbie to this. I loaded Ubuntu 5.10,; everthing seemed fine until reboot. FIRST during startup, I have a '**Temporary failure in name resolution**'         **FAIL**. HuH?

And, what do I do when:  ***root@myusername:~#***    pops up? What do I enter?

---

### Post by Zelut on 2005-12-30
Temporary failure in name resolution isn't a big deal.  Its just saying that it tried to connect to a central server to update the system time & was unable.  I get that from time to time but it doesn't affect my useability at all.

Uhm, as far as the prompt.. did you install the default or the 'server' version.  If you installed the basic 'server' you'll only end up with a prompt like that.  if you installed the default (which should include the Gnome Graphical Manager) it sounds like something wasn't installed correctly.

give this a try:

sudo apt-get update (enter your password)
sudo apt-get upgrade

See if that does anything..

---

