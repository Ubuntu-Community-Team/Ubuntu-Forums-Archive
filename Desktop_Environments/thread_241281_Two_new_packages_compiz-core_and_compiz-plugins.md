---
title: "Two new packages: compiz-core and compiz-plugins"
date: 2006-08-22
forum: Desktop Environments
---

### Post by oobuntoo on 2006-08-22
Has anyone installed them yet? What repo are they from? I'm afraid of installing these after xserver-xorg-core broke my display.

---

### Post by Saibot on 2006-08-22
I recommend waiting.  I was reading a little about it on the compiz forums and it seems Quinn is changing some stuff, but it might not be ready yet.  I did try the update on my guinea-pig system and lost compiz for the time being.  I'm sure it'll all get worked out and that's what my test system is for. :p 
You might want to check the compiz forums yourself for any news before updating.

---

### Post by dentaku65 on 2006-08-22
The new package broke my AIGLX/Compiz conf; seems that the new compiz-core pkg works for the moment only for XGL :evil: 

So I suggest to wait for the moment...

---

### Post by Erestar on 2006-08-22
I just installed them and now X is broken. Looking for a way to generate a fresh xorg.conf file. None of the backups I had are working.

---

### Post by Erestar on 2006-08-22
Oh...

[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by mdwuznik on 2006-08-22
If you upgraded xserver-xorg-core to 1.0.2-0ubuntu10.3, take one step back 
to 1.0.2-0ubuntu10.
That has just fixed my Xorg (ang Xgl too)

Cheeres
Michal

---

### Post by dentaku65 on 2006-08-22
Try to downgrade Xorg
[http://yep.it/?6q4v5y](http://yep.it/?6q4v5y)

---

### Post by oobuntoo on 2006-08-22
Whew! I almost got sucker punched :mrgreen: Thanks for the warning, guys.

---

### Post by oobuntoo on 2006-08-22
I decided to upgrade/install compiz-core and compiz-plugins after reading several posts on compiz.net. So far, everything is still working, even after reboot. But there's still no info on what's new about these packages.

---

### Post by llamakc on 2006-08-22
There should be a changelog in /usr/share/doc/NAMEOFPACKAGE

---

### Post by PathSpace on 2006-08-22
Has anyone tried the new compiz-vanilla and compiz-vanilla-gnome packages for AIGLX yet?

---

### Post by PathSpace on 2006-08-22
OK, I think I will go ahead and take the plunge, upgrading compiz-vanilla and compiz-vanilla-gnome.  But I would like to be sure that I know how to downgrade them in case something goes wrong.  How do I find out the exact version I am using now, so that I can re-install those versions if something breaks?

---

### Post by oobuntoo on 2006-08-23
> **PathSpace said:**
> OK, I think I will go ahead and take the plunge, upgrading compiz-vanilla and compiz-vanilla-gnome.  But I would like to be sure that I know how to downgrade them in case something goes wrong.  How do I find out the exact version I am using now, so that I can re-install those versions if something breaks?

To downgrade (using command line):

cd /var/cache/apt/archives/
sudo dpkg -i compiz-vanilla

hit Tab key twice and you will get a list of all packages with name starting with "compiz-vanilla" that were cached on your system. Just fill out the rest of the name of the package version you want.

---

### Post by Saibot on 2006-08-23
Looks like things have settled down now, I just upgraded two machines and compiz works fine on both now.  One update went without a hitch, but I got a couple errors on the other machine.  I ended up having to use Synaptic to repair 2 broken packages, but that took care of it and now all is fine.

---

