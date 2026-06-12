---
title: "Problems after installing kubuntu-desktop"
date: 2006-07-27
forum: Desktop Environments
---

### Post by bzarhands on 2006-07-27
I recently used Synaptic Package Manager to install *kubuntu-desktop* so that I could try out KDE.  Since doing so, however, I have had problems that would lead me to believe I somehow installed Kubuntu incorrectly.

The most obvious problem is an inability to access System > Administration > Login Window in a GNOME.  While it seems to begin with "Starting administrative application," nothing seems to result.

At boot, once I select Ubuntu from GRUB, I'm presented with the blue Kubuntu start up screens (rather than brown Ubuntu).  While this isn't at a problem, I was wondering why it's now Kubuntu by default.

What are the differences between using KDM and GDM to run KDE and GNOME sessions?  I assume that KDM is my default now, and it doesn't seem to have any problems running a GNOME session, but if I am going to be spending more time in GNOME, should I be using GDM?  If so, how do I go about changing it?

Thanks for any information you can offer up.  I am more than happy to answer any questions that might give you a better perspective on what is happening on my end.  :)

---

### Post by bzarhands on 2006-07-27
Also, is it normal for KDE apps to display in GNOME sessions, and vice-versa?    

I got curious to know if it matter which session I ran them in.  Trying to run GIMP in a KDE session locked up Firefox, and I'm therefore assuming I shouldn't do something like that again.  :sad: Is this right?  If so, is there any easy way I might hide KDE apps in GNOME and GNOME apps in KDE?

Again, thanks for any help/suggestions/information/links.  :)

---

### Post by svarma on 2006-07-29
I had similer problems, which were fixed by setting the permissions right on the kde configuration files. 

try something like ...

1. ```
chown -R myuserid .DCOPserver* .kde 
```
2. kill off any stuck instances of kdialog.
3. start your app

---

### Post by Joey French on 2006-07-29
Yes, you can run gnome apps in kde and vice versa, some distributions don't really make a big distinction (suse). The thing is, some of the apps may look a little out of place, is all. The firefox dying issue is not related to your use of gimp in kde (it's not specific to any particular desktop).

I used to remember how to switch from kdm to gdm, but now I don't remember. Hopefully someone else will chime in, cause it's really easy (checking a box or something).

Joey French

---

