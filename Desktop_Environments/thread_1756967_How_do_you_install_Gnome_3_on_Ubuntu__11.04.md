---
title: "How do you install Gnome 3 on Ubuntu  11.04?"
date: 2011-05-12
forum: Desktop Environments
---

### Post by COMTIBoy on 2011-05-12
I would like to try Gnome 3 on my Ubuntu 11.04.

How can I upgrade my version 2 to 3 ?

I found a ppa on the gnome website for Ubuntu 11.04, but this didn't work

---

### Post by NormanFLinux on 2011-05-12
Be aware if you do, it will break Unity and unless you have an accelerated graphics card, you won't get the full benefit of GNOME 3 and you will be back-booted into the default GNOME 2 style environment.

---

### Post by akand074 on 2011-05-12
To install it:

```
[FONT=Arial]sudo add-apt-repository ppa:gnome3-team/gnome3 
sudo apt-get update 
sudo apt-get dist-upgrade 
sudo apt-get install gnome-shell[/FONT]
```

To remove it:

```
sudo apt-get install ppa-purge 
sudo ppa-purge ppa:gnome3-team/gnome3
```

Check [this]("http://ubuntuforums.org/showthread.php?t=1742343") thread for common issues/fixes.

---

### Post by COMTIBoy on 2011-05-12
Thanks.  I don't use Unity (don't like it) and I do have an accelerated graphics card. Thanks again.

---

### Post by COMTIBoy on 2011-05-12
> **akand074 said:**
> To install it:

```
[FONT=Arial]sudo add-apt-repository ppa:gnome3-team/gnome3 
sudo apt-get update 
sudo apt-get dist-upgrade 
sudo apt-get install gnome-shell[/FONT]
```

To remove it:

```
sudo apt-get install ppa-purge 
sudo ppa-purge ppa:gnome3-team/gnome3
```

Check [this]("http://ubuntuforums.org/showthread.php?t=1742343") thread for common issues/fixes.



Thanks!

---

### Post by COMTIBoy on 2011-05-12
> **COMTIBoy said:**
> Thanks!


Just did the upgrade to Gnome 3.0 .  Worked great!  Really appreciate your help.

---

### Post by COMTIBoy on 2011-05-12
After a very short lived upgrade, I decided to revert back to the earlier Gnome desktop. I think I'll wait an OS upgrade (or two) before trying gnome 3 again.  I really like the new interface, but it just runs too slow. I have an nvidia graphics card.  The gnome 3 graphics were great when running build 173 (latest), but caused the system to really poke....The recommended version nvida driver (recommended) made the fonts look really bad. 

Glad you gave me the uninstall steps.

---

### Post by akand074 on 2011-05-13
> **COMTIBoy said:**
> After a very short lived upgrade, I decided to revert back to the earlier Gnome desktop. I think I'll wait an OS upgrade (or two) before trying gnome 3 again.  I really like the new interface, but it just runs too slow. I have an nvidia graphics card.  The gnome 3 graphics were great when running build 173 (latest), but caused the system to really poke....The recommended version nvida driver (recommended) made the fonts look really bad. 

Glad you gave me the uninstall steps.

I used it too and liked it. Reverted back to Unity (which I also like) because it was far more useable. Gnome 3 for Ubuntu is far from perfect. Wait until 11.10.

---

### Post by Allavona on 2011-05-13
I actually like both because they are brand new! Everyone's a noob!!

---

