---
title: "All I want is amaroK on GNOME!"
date: 2005-12-09
forum: Desktop Environments
---

### Post by rskovacs on 2005-12-09
I just installed amaroK the other day, and it's great!  But KDE isn't, IMO.  So I was wondering if someone could help me figure out the bare minimum of packages needed to run amaroK on GNOME (never on KDE) and how to actually uninstall those packages (without uninstalling the packages needed for amaroK as well).  Is this even possible, or do I really have to keep an entire display manager just to run one program?

(P.S. Sorry, this should probably be in the newbie section, but I thought maybe it was a little too complicated.)

---

### Post by angkor on 2005-12-09
just do:

sudo apt-get install amarok amarok-xine

apt will figure out the dependencies for you. It will not install packages not needed for amarok to run.

---

### Post by rskovacs on 2005-12-09
haha i knew it was easy!

thanks! (and thanks to aysiu for his thread on uninstalling kde first)

---

### Post by earobinson on 2005-12-09
I think its important to note that amaroK will load up a bunch of kde packages with it this could cause performance problems.

NOTE THE SECOND: this should be fine in most cases, Just dident want you to be worried when you had a lot more processes running. Also load time may be a bit longer than in kde

---

### Post by denisesballs on 2005-12-09
[QUOTE=earobinson]I think its important to note that amaroK will load up a bunch of kde packages with it this could cause performance problems.[/QUOTE]

I'd like to note that I use K3B and Amarok on Gnome every day with no problems. :) 

Don't be discouraged!

---

### Post by earobinson on 2005-12-09
this is true, could cause performance problems was my point.

but denisesballs is correct, you have nothing to lose by trying, and in most cases this will work with no problems. (I will edit the post to not that in most cases this will be fine)

---

