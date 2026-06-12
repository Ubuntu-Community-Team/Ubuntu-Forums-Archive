---
title: "using my old /home partition messes up Jaunty graphics"
date: 2009-04-29
forum: General Help
---

### Post by holdie on 2009-04-29
I recently upgraded to Jaunty after a long and annoying process (my CD drive doesn't work so I have to do everything with USB)...anyways, everything is working great with the new release, until I tell fstab to mount my old /home partition as /home.  Basically, everything looks the same appearance-wise, but now everything runs much less smooth, my external monitor is not detected, the screen flickers...basically stuff just doesn't work well...

I imagine this is due to an incompatibility with the graphics (I was using the ATI proprietary drive with Ibex, but it's not supported with my card in Jaunty).  Is there a way I can use all of the info stuff (ie desktop, firefox bookmarks, etc.) but start with a clean slate on the graphics settings?

---

### Post by cmnorton on 2009-04-29
Maybe there are dot (.) files that need to be updated and would be correct if you created a new user.  They'd probably be under .gnome or similar directory. 

Someone might know of a way to get these updated by the system, like perhaps deleting them, so when you log in the next time, gnome will update them.

Before you do anything rash, I strongly suggest researching this.

---

### Post by geirha on 2009-04-29
Hard to say what configuration in your home folder could cause that. Your best bet is probably to use the freshly created home directory, and copy/move the parts from the old that you need.

To get your firefox settings and bookmarks, copy the hidden .mozilla folder from your old homedir, to your new one.

---

### Post by holdie on 2009-04-29
OR (I just thought of this a second ago so bear with me), why couldn't I just copy the . files from my new /home and paste them into the old partition...that way any overlaps would be overwritten and I could still have my /home on the separate partition...

what do you think of this?

---

### Post by Thelasko on 2009-04-29
> **holdie said:**
> OR (I just thought of this a second ago so bear with me), why couldn't I just copy the . files from my new /home and paste them into the old partition...that way any overlaps would be overwritten and I could still have my /home on the separate partition...

what do you think of this?

No, it's likely extra files that are the problem.  Doing what you are proposing won't fix that.

However, you can rename "." folders so they aren't recognized, and Ubuntu will create new ones.  If that file wasn't the problem, simply delete the new one and change the name on the old one back.  It's a bit of trial and error, but I've done it before and it works.

P.S. To be honest, I can't understand what file it could be.  Xserver shouldn't be saving anything in the /home partition.  My next guess would be something with Gnome or Metacity.

---

