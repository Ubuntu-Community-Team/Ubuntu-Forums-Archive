---
title: "Kubuntu Startup Problem"
date: 2008-03-15
forum: Desktop Environments
---

### Post by z|x on 2008-03-15
Ok, everything was fine till I uninstalled KDE 4.

Here's what I did, I wanted to try out the new kubuntu 4.02 and so, I installed kde4-core through adept. There were many applications that were not working correctly and so I decided decided to uninstall it. I uninstalled kde4-core through adept but it only uninstalled the core packages and not the packages that came along with the core package. So, I searched for all the applications containing kde4 in the name and uninstalled them. I started noticing some problems with the startup menu in KDE 3 and even in dolphin. So, I reinstalled the kde4-core packages so that the kde4 application would be reinstalled. Reinstalling them made no effect with the errors I was facing. I then decided to reboot, but after rebooting I was not able to log into KDE.

After selecting Ubuntu as the OS (I am dual booting with Vista), I get the kubuntu loading screen and then all I see is a blank black screen with a blinking cursor. 

Please help me.

Thanks!!

---

### Post by z|x on 2008-03-16
Bump.. pls help..

---

### Post by zxscooby on 2008-03-16
will it load in recovery mode?

---

### Post by z|x on 2008-03-16
> **zxscooby said:**
> will it load in recovery mode?
Yep.

---

### Post by zxscooby on 2008-03-16
thats a start lol , im not sure about restoring your kde.
I know its a bad idea to use the recovery mode full time because it defaults to root.

---

### Post by samwyse on 2008-03-16
try installing kubuntu-desktop.

---

### Post by z|x on 2008-03-16
> **samwyse said:**
> try installing kubuntu-desktop.
how?

---

### Post by samwyse on 2008-03-16
> **z|x said:**
> how?

If it boots in recovery mode: "sudo apt-get install kubuntu-desktop".

I'm not sure if it will do anything, but it will install packages that are missing. I've noticed that if you remove the kde4 oxygen icon theme, it removes some kde3 stuff too which might break things.

---

### Post by z|x on 2008-03-16
> **samwyse said:**
> If it boots in recovery mode: "sudo apt-get install kubuntu-desktop".

I'm not sure if it will do anything, but it will install packages that are missing. I've noticed that if you remove the kde4 oxygen icon theme, it removes some kde3 stuff too which might break things.
I cannot access the internet in recovery mode. And i think KDM got uninstalled. Is there any way in which i can connect to a network in recovery mode? or can I install kdm through another source?

---

### Post by angry_johnnie on 2008-03-17
You might still be able to install those things in recovery mode, since all the things you download from the package manager stay in your computer (unless you run apt-get autoclean).  So, the deb packages might still be there.

Did knetworkmanager get uninstalled, too?
Can you launch it via "run command"

I think it's also possible to add your installation cd to the repositories, and then you could select and install packages from it.

---

### Post by z|x on 2008-03-17
> **angry_johnnie said:**
> You might still be able to install those things in recovery mode, since all the things you download from the package manager stay in your computer (unless you run apt-get autoclean).  So, the deb packages might still be there.

Did knetworkmanager get uninstalled, too?
Can you launch it via "run command"

I think it's also possible to add your installation cd to the repositories, and then you could select and install packages from it.
Wait a minute.. I reached recovery mode through the boot up options, and not my entering the live cd. Also, the live cd that I have has ubuntu and not kubuntu. I only get a console like thing.

I dont think the knetworkmanager got uninstalled.

and how do i add the cd to the repos list?

---

### Post by angry_johnnie on 2008-03-17
> Wait a minute.. I reached recovery mode through the boot up options, and not my entering the live cd.
:-)  I know

> Also, the live cd that I have has ubuntu and not kubuntu. I only get a console like thing.

I dont think the knetworkmanager got uninstalled.

and how do i add the cd to the repos list?[


Ok, so when you login you don't have a desktop?  What happens if you type startx?
If your installation cd has ubuntu and not kubuntu, then maybe that's not what you need.
Try startx.
That should get you into gnome.
Then try to connect to the internet.
Hit Alt+F2
I think the command would be

```
nm-applet --sm-disable
```

And then see if you can install Kubuntu-desktop.

Also, go to System > Administration > Services

And see if either GDM or KDM is enabled.

---

### Post by z|x on 2008-03-18
Thank you so much!! It worked!! Thanks guys!!

---

### Post by z|x on 2008-03-18
pls delete this post.

---

### Post by z|x on 2008-03-18
pls delete this post too.

---

