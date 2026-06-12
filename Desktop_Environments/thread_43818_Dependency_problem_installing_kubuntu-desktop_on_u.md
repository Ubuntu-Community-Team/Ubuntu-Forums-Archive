---
title: "Dependency problem installing kubuntu-desktop on ubuntu"
date: 2005-06-23
forum: Desktop Environments
---

### Post by galeal on 2005-06-23
Hi all,

I'm trying to apt-get install kubuntu-desktop on ubuntu 5.04.. 
and I am getting a dependency problem with konversation..

konversation: Depends: kdelibs4 (>= 4:3.4.1) but 4:3.4.0-0ubuntu3.2 is to be installed

I'd be happy to just ignore konversation and install the rest.. any hints?

Thanks in advance

---

### Post by SGC on 2005-06-23
Add this line to the end of apt-get's the sources file (/etc/apt/sources.list):
```

deb http://kubuntu.org/hoary-kde341 hoary-updates main

```

Then do **apt-get update** and try to install kubuntu-desktop again.

---

### Post by galeal on 2005-06-23
Perfect!! Thanks. That worked great.

Is this in the FAQ somewhere?

---

### Post by SGC on 2005-06-23
No , Its a recent problem that just starts to happens after releasing kde 3.4.1

---

### Post by Rory on 2005-07-07
[QUOTE=SGC]Add this line to the end of apt-get's the sources file (/etc/apt/sources.list):
```

deb http://kubuntu.org/hoary-kde341 hoary-updates main

```

Then do **apt-get update** and try to install kubuntu-desktop again.[/QUOTE]

I initially installed Ubuntu, then did an apt-get install kde, but it only gave me 3.4.

I then realized if I added the  about repository and did an apt-get install kubuntu-desktop, it would move me up to 3.4.1.

I did this and everything seems to be working smoothly except synaptic hangs and then opens.  Removing and reinstalling doesn't help.  update-manager and update-notifier still works.

Here's the weird thing: if I do this from terminal:
sudo synaptic

It works!

If I just do from terminal:
synaptic

it says I need to be root, which makes sense.

So, why would it be working from terminal but not from the kde desktop.  

Any ideas?

Thanks,
Rory

---

### Post by jcohen on 2005-07-07
Grrr, stop telling people to do a massive system upgrade because of one damn broken package in backports! There was absolutely no reason for that user to install KDE 3.4.1 so he could install konversation 0.18 from backports. The problem is that backport's konversatoin requires KDE 3.4.1 which it shouldn't. Backports is meant to be used on a fresh Hoary installation. There is nothing wrong with Ubuntu's kubuntu-desktop package. Konversation should either be removed from backports or it should depend on KDE 3.4.0 libraries. Anyways, the solution is quite simple:

TO INSTALL KDE WITH BACKPORTS ENABLED FOLLOW THESE INSTRUCTIONS:

1) sudo apt-get install konversation=0.16-1ubuntu1
2) sudo apt-get install kubuntu-desktop

If you feel more comfortable with the synaptic graphical installer follow these instructions: 

Bring up synaptic and search for konversation. Highlight the konversation package and then select Package > Force Version from the menu and select 0.16-1ubuntu1 (hoary). After that, hit apply to install. Once that's complete you can install kubuntu-desktop or the kde meta-pacakge. In order to prevent synaptic or Update Manager from complaining in the future that it can't upgrade konversation, you can also lock the version to 0.16 by choosing Package > Lock Version after highlighting the konversation package. This needs to be done after konversation 0.16 has been installed.

It really is a shame that users are being told to upgrade to KDE 3.4.1 when the fix is so trivial. Installing KDE 3.4.1 may make upgrading to Breezy more difficult and it's also unnecessary.

---

### Post by SGC on 2005-07-08
[QUOTE=jcohen]
Installing KDE 3.4.1 may make upgrading to Breezy more difficult and it's also unnecessary.[/QUOTE]
 [-X 

Having the latest bug fixes is always a good idea, and installing kde 3.4.1 will NOT make upgradding to Breezy difficult.

In fact people does not **UPGRADE** to kde, people with this problem are those who try to **INSTALL** kubuntu-desktop from ubuntu.

By adding kubuntu.org repository they will get kubuntu-desktop with the latest version of kde instead of downloading an old version that known to be unstable and have some bugs, and then upgrading to a newer one.

---

