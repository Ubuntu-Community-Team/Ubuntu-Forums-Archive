---
title: "Kde 4.2 ?"
date: 2008-11-15
forum: Desktop Environments
---

### Post by armageddon08 on 2008-11-15
How do I install KDE 4.2 on Ubuntu Intrepid ? I want a base minimal install.

---

### Post by sonicb00m on 2008-11-15
Add this to your sources

deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) intrepid main

and sudo apt-get install kde-nightly

log out and change the session.

It will along side 1.4.3 so it's quite safe to install

---

### Post by armageddon08 on 2008-11-15
Thanks....I'll be installing it now.

---

### Post by ACMiller on 2008-11-15
Just out of interest, how has the installation gone for you armageddon08? I'm interested in trying out KDE4, and wondering if this is the best way to do it.
Thanks

---

### Post by sonicb00m on 2008-11-15
I can tell that this worked flawlessly but the enviroment wasn't exactly very stable. A lot of missing widgets etc and other problems. I'd wait a bit longer before installing this.

I installed 4.1.3 from the unstable repo (just install kubuntu and enable unstable in synaptic) and it's much better. I am using it right now. I am very impressed with it. Despite sticking with Gnome over older K(rap)DE :D

---

### Post by doktormiod on 2008-11-15
Hi, I've just installed kde-nightly but when i try to login to new nightly session nothing happens :/. Login screen disappears, there's just the background picture, none error message pops up, any ideas?

---

### Post by awakatanka on 2008-11-15
> **doktormiod said:**
> Hi, I've just installed kde-nightly but when i try to login to new nightly session nothing happens :/. Login screen disappears, there's just the background picture, none error message pops up, any ideas?
It mostly helps to backup your ~/.kde dir to something like /.kdebckup and login.

---

### Post by doktormiod on 2008-11-16
Should I remove /.kde dir after making a backup?

---

### Post by awakatanka on 2008-11-16
> **doktormiod said:**
> Should I remove /.kde dir after making a backup?
Yes, but .... The neon version will make his own kde directory ~/.kde-neon, if you have problems with the neon version then backup that one and remove it, the same counts if you have troubles in normal KDE. If your problems still exist then it is something else.

---

### Post by doktormiod on 2008-11-16
Thank you, I found the solution. The problem was kde-neon's permissions. I changed owner to my user's name and now everything's ok :-)

---

### Post by brunomiguel on 2008-12-01
I've installed KDE 4 through this repo and changed .kde-neo's permissions, but I can't use it. Anyone experiencing the same problem?

---

### Post by kernelhaxor on 2008-12-02
> **sonicb00m said:**
> Add this to your sources

deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) intrepid main

and sudo apt-get install kde-nightly

log out and change the session.

It will along side 1.4.3 so it's quite safe to install

Any repo which has beta-1 and not the nightly builds?

---

### Post by gerbalblaste on 2008-12-04
From the Kubuntu page: 
The updated packages for Kubuntu 8.10 are located in the Kubuntu Experimental Software Personal Package Archive (PPA) repository. To update to KDE 4.1.80 (4.2 beta1), please follow these instructions:

   1. Follow the Kubuntu Repository Guide to enable Recommended Updates and add the following to your 'Third-Party Software' tab:
      ```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
```
   2. You can now update any existing KDE 4 installation to the most recent version using the Adept Updater tool in your system tray.
   3. Now log out and press Alt + E to restart X. When you log in you will have KDE 4.2 Beta 1. Enjoy.


see:
[http://www.kubuntu.org/node/58](http://www.kubuntu.org/node/58)

---

### Post by kernelhaxor on 2008-12-04
> **gerbalblaste said:**
> From the Kubuntu page: 
The updated packages for Kubuntu 8.10 are located in the Kubuntu Experimental Software Personal Package Archive (PPA) repository. To update to KDE 4.1.80 (4.2 beta1), please follow these instructions:

   1. Follow the Kubuntu Repository Guide to enable Recommended Updates and add the following to your 'Third-Party Software' tab:
      ```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
```
   2. You can now update any existing KDE 4 installation to the most recent version using the Adept Updater tool in your system tray.
   3. Now log out and press Alt + E to restart X. When you log in you will have KDE 4.2 Beta 1. Enjoy.


see:
[http://www.kubuntu.org/node/58](http://www.kubuntu.org/node/58)

Nice.  Looks like it was released today.  Anyone tried it out yet? How stable is it?

---

### Post by Skripka on 2008-12-04
> **kernelhaxor said:**
> Nice.  Looks like it was released today.  Anyone tried it out yet? How stable is it?

I tried out the preceding nightly--granted that was a nightly, but it was segfaulting left and right (just on login and logout)--my installed apps weren't even populated into the menu....Plasma seemed much better though-I liked what I saw and what worked there.  'Twas easy enough to remove the nightly though.  But that was the preceding nightly, and of course YMMV.

---

