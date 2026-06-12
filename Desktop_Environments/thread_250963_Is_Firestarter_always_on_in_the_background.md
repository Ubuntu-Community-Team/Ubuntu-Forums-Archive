---
title: "Is Firestarter always on in the background?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Gotou on 2006-09-04
Hi!  I installed firestarter, entered my settings and then clicked on the little "x" in the top corner to quit.  I noticed the blue circle and arrow icon up in the top right Gnome panel disappeared.  That means firestarter isn't running and now I don't have a firewall protecting my computer anymore?

Or...

Firestarter is just a frontend to manage the iptables.  Firestarter is not the actual firewall but just a way to make changes to the iptables and iptables are always running.  Correct?

Thanks!

---

### Post by powder on 2006-09-04
You can check if it's running by typing into terminal:

sudo /etc/init.d/firestarter status

---

### Post by orb9220 on 2006-09-04
You are correct you only need to run it when you want to make changes.
iptables is always running and is the actual firewall.

---

### Post by Gotou on 2006-09-09
Thanks powder and orb9220!

The command said that firestarter was running.

It's good to have a more experienced Ubuntu user confirm my semi-newbie conclusions.  That means I'm beginning to catch on as to how this Linux thing works.

Cool beans!:-D

---

