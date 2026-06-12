---
title: "No desktop after logging in"
date: 2009-02-15
forum: Desktop Environments
---

### Post by SynDaily on 2009-02-15
Hello,

I've been faffing a bit and think I may have screwed up my user profile.

After logging on, my desktop background is shown along with the mouse cursor and then nothing else happens.

No key combinations apart from ctrl-alt-backspace seam to work.

Looking in /var/log/Xorg.0.log, there are no errors and I am typing this request for help from another users profile.

All suggestions on what to try next greatly received.

Cheers

Si

---

### Post by ajgreeny on 2009-02-15
Try renaming your username *~/.gconf* folder to *~/.gconfbak* and login under your own name again.  You will have lost all your desktop icons and chosen wallpaper, etc but the standard gnome panels should be back, and you can then set up your preferences again.

Just out of interest, what do you think you were you doing to mess things up so much, or was it rather a surprise to you that this happened?

---

### Post by SynDaily on 2009-02-15
> **ajgreeny said:**
> Just out of interest, what do you think you were you doing to mess things up so much, or was it rather a surprise to you that this happened?

well... I was backing up my preferences for compiz and created ~/cube.profile via the ui, and I notice ~/.profile. Thinking it was a duff file I'd created on a previous occasion, I deleted it :oops:

A day passes... And said problem rears its ugly head. 

I've looked at the .profile of other users and since realized it was a bash script that sets up your terminal preferences from .bashrc. I've cp'ed one over to no success.

Also, I've:```
 #mv .gconf .gconf.bak.2009.02.15
``` and now I get the same hang except I'm looking at the hardy heron rather than a honda fireblade. Doh! I then tried hiding .gconfd in the same way. still no luck unfortunately.

Cheers for the help though as we now know it must be something after gnome that's causing the problem.

p.s. I've always changed the name of things by moving them due to advice back when I used suse. Is this the convention with ubuntu as well?

---

### Post by SynDaily on 2009-03-01
bump.

---

