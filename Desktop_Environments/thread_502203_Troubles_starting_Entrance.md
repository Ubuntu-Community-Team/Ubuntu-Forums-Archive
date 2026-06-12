---
title: "Troubles starting Entrance"
date: 2007-07-16
forum: Desktop Environments
---

### Post by hybernate20 on 2007-07-16
I already checked out all of the other posts containing hte word entrance, and nothing helped.

I have everything configured correctly I believe.....I installed entrance, removed gdm from my runlevels with the update-rc.d command, and made sure that entrance was set to start at the default runlevel. Looking good so far. I checked /etc/X11/default-display-manager and it said /usr/sbin/entranced....which I assume is correct because if it isn't that it tells me that Entrance isn't the default display manager. I boot up, and I end up at the command line. I try running sudo /etc/init.d/entrance start, and it says "becoming entrance", tries to start, and I end up back at the command line. 

I know that entrance and e17 and all of that stuff is alpha, but it's still fun to play with.


Any ideas?

---

### Post by gspearing on 2007-07-16
I just ran this:

sudo dpkg-reconfigure entrance

switched to enance, and it worked.

---

### Post by hybernate20 on 2007-07-16
I still end up at the command line....

---

### Post by gspearing on 2007-07-17
> **hybernate20 said:**
> I still end up at the command line....

I've got nothing... :(

I installed everything by Synaptic and didn't 'fiddle about'. I use the following repo:
[http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu)

---

### Post by TravMan63 on 2007-07-31
hmmm - I'm having an issue as well - I have a gray 'dotted' screen with a grey x....

e17 and e16 installed...

any ideas?

TM

terminal reports:
root@laptop:/home/dad# dpkg --configure entrance
dpkg: error processing entrance (--configure):
 package entrance is already installed and configured
Errors were encountered while processing:
 entrance

maybe becuase it is 'installed and configured'...

entranced - shows the gray screen with the X...

---

