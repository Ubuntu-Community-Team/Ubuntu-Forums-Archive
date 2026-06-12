---
title: "Switching from GNOME to KDE in Ubuntu"
date: 2008-04-22
forum: Desktop Environments
---

### Post by RevolutionMaster on 2008-04-22
Is there a way to switch from GNOME to KDE, while keeping Compiz and not reinstalling with Kubuntu?

---

### Post by marwansherin on 2008-04-22
YES, you can install KDE on Ubuntu without installing Kubuntu
just open the terminal and type:
sudo apt-get install kde

it will download it from the internet,so make sure you have an internet connection, after setup is finished.
you can then choose KDE or GNOME at the login screen.

---

### Post by robertsaron on 2008-04-22
Now that hardy is out, I am using Gnome in 8.04

If I were to install KDE 4.0.2 or what ever it is, would the process be the same as above? 

What would be the ramifications for stability and package updates? Would it cause the system to become unstable to use 2 desktop environments or not?

---

### Post by tedt on 2008-04-22
They can be installed next to one another with out a great degradation IMHO.  They are complied to work in the Ubuntu universe so that the underlying libraries and such aren't different versions.  You can get in to trouble if you start installing bleeding edge software that requires a brand new library for the compile which can cause problems with backward compatibility.  Installing things just from Ubuntu repos should keep one safe.

---

### Post by russo.mic on 2008-04-22
> **marwansherin said:**
> YES, you can install KDE on Ubuntu without installing Kubuntu
just open the terminal and type:
sudo apt-get install kde

it will download it from the internet,so make sure you have an internet connection, after setup is finished.
you can then choose KDE or GNOME at the login screen.

Could be wrong, but I think your better off with sudo apt-get install kubuntu-desktop.  

Just typing KDE would install the stock KDE, but I think Kubuntu-desktop meta package is ubuntu specific.

Russo

---

### Post by robertsaron on 2008-04-22
for hardy 8.04 will that install the kubuntu desktop KDE 4.0.0.2 or what ever kde 4 is?

More than anything I want to give it a test run. I have 4-5 hard drives, but dont feel like setting up a partition just to run the Kubuntu desktop, already had enough nightmares getting vista installed.

---

### Post by Uber-Noob on 2008-04-23
You can get the pkg from synaptic as well, it's under KDE. That is what I did, and I have not had any problems yet. :KS (It has only been a few weeks though).  

I think you will have to wait for the official release of Hardy before you get KDE 4. (You might get it sooner if you go to settings -> repositories -> updates(tab) then enable pre-release, but I don't know that for sure. If anybody knows better, feel free to correct me on this).   

Related Question: Does any one know how I can configure the login script so that some users can  start GNOME and others start KDE by default? :confused: My whole family uses the same computer, and we don't all like the same DE.

---

### Post by russo.mic on 2008-04-23
> **Uber-Noob said:**
> You can get the pkg from synaptic as well, it's under KDE. That is what I did, and I have not had any problems yet. :KS (It has only been a few weeks though).  

I think you will have to wait for the official release of Hardy before you get KDE 4. (You might get it sooner if you go to settings -> repositories -> updates(tab) then enable pre-release, but I don't know that for sure. If anybody knows better, feel free to correct me on this).   

Related Question: Does any one know how I can configure the login script so that some users can  start GNOME and others start KDE by default? :confused: My whole family uses the same computer, and we don't all like the same DE.

kubuntu-desktop metapackage, I'm fairly certain, will install the supported kubuntu desktop, so KDE 3.5.  you can install KDE 4 now by executing 

sudo apt-get install kde4

However,  I very much recommend you "Try Out" kde4 via the kubuntu remix CD Live.  After a few days of having it installed, I found it to be really cool, but really buggy.  If your mileage varies, then by all means!  

Just a word of advice.

Russo

---

### Post by lemurian on 2008-04-23
If you want to get the equivalent desktop to what you would get with a fresh kubuntu install you want to install the kubuntu-desktop package for KDE3.5  If you want KDE4 you need to install the kubuntu-kde4-desktop package.  Installing only kde or kde4 will not give you the full desktop experience.

I've tried KDE4 a few days ago.  It is crashy and has much less functionality than KDE3.5.  (I'm talking about *actual* functionality, not potential.  KDE4 has more potential but it is mainly theoretical at this point.)  I've searched in forums where long time KDE users were giving their opinion of KDE4 and most are saying people should wait for 4.1 at the very least.

---

### Post by natman on 2008-04-24
I did the exact same thing for gusty KDE ontop of Ubuntu gnome, was the worst thing i ever did, all the little things like sounds in programs like k3b no longer worked ( unless i deleted the .gnome dirctory ) and the wireless profile manager really got confused with settings in kde and gnome.

If you really want both desktops ( which is more work also,learning where things are in both gets confusing ) partition and install KDE and speratly gnome and then perhaps try sharing the files for things like photos,music, just leave the settings alone to each desktop env.

---

### Post by albertoramirez on 2008-04-24
Can KDE be removed from a prior apt-get installation typing

apt-get remove kde

?

---

### Post by markjensen on 2008-04-24
> **Uber-Noob said:**
> ...
Related Question: Does any one know how I can configure the login script so that some users can  start GNOME and others start KDE by default? :confused: My whole family uses the same computer, and we don't all like the same DE.Just install it.   Per-user is already automatically tracked and set when you use gdm to change your session.

I use fluxbox.  My kids use XFCE.  There is no need to manually select each time.  Nor is there a need to set up a custom configuration script for this.  It just already works like you describe. ;)

---

### Post by russo.mic on 2008-04-25
> **natman said:**
> I did the exact same thing for gusty KDE ontop of Ubuntu gnome, was the worst thing i ever did, all the little things like sounds in programs like k3b no longer worked ( unless i deleted the .gnome dirctory ) and the wireless profile manager really got confused with settings in kde and gnome.

If you really want both desktops ( which is more work also,learning where things are in both gets confusing ) partition and install KDE and speratly gnome and then perhaps try sharing the files for things like photos,music, just leave the settings alone to each desktop env.

I can't say I've ever had that many issues with it.  I have both KDE and Gnome installed usually, and everything seems to work fine for me.

Russo

---

### Post by anachreon_ on 2008-04-25
I've got KDE, Gnome and KDE4 all installed on the same (originally) Kubuntu install, and haven't really had any problems with it.  I've settled back on KDE 3.x after playing around with Gnome and KDE4.  Gnome just wasn't to my taste, and as another poster has said, KDE4 has tons of potential but I'd wait for 4.1 at the very least before really building a computer around it.

---

