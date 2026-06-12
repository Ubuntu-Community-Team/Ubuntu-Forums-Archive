---
title: "System tray icons, KGPG"
date: 2013-01-15
forum: Desktop Environments
---

### Post by alnilamski on 2013-01-15
I installed KGPG on Lubuntu 12.10 (it's a GUI frontend for GnuPG).
The first time I ever ran it, I could successfully see the GUI. Hooray!
Then I restarted.

Now, when I try to run it, I can't get to the GUI. I'll break it down into the three things that might happen, depending on how I try to open it.

[LIST=1]
[*]**I run KGPG from the launcher menu**. I get a dialog box that says"*The use of GnuPG Agent is enabled in GnuPG's configuration file (/home/billy/.gnupg/gpg.conf). However, the agent does not seem to be running. This could result in problems with signing/decryption. **Please disable GnuPG Agent from KGpg settings**, or fix the agent.*" So it seems like KGPG should be running, and it even shows up after "ps -e", but I can't get to the GUI! The bolded part makes me think that this dialog box thinks I'll be able to get into the GUI, though, because it's telling me I can mess with the KGpg settings.
[*]**I run KGPG from terminal**. It returns "QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave." This repeats twice. Again, KGPG appears to be a running process, but I can't get to the GUI.
[*]**If I try to run it while the process is already running, nothing happens.**
[/LIST]

The searching I've done so far tells me this:
**KGPG is supposed to start minimized in the system tray (if that's the right term - what I mean is the little tray with the clock, volume icon, wifi, etc.). But I don't see it down there. All I see is volume, battery, wifi, clock, and shutdown.**

In one solution I found online, the poster said, in short, "Silly me! All I had to do was expand the system tray and the icon was hidden there all along." In my system tray, I don't see any way to expand it to show more icons. I thought about trying to open something else that keeps an icon down there, to see if I can see THAT icon, but I don't know of any such programs.

Any help is appreciated, thanks!
**Also, I'm open to recommendations of other GPG frontends that are compatible with Lubuntu. I used to use regular Ubuntu, which came natively with a key-manager, but Lubuntu doesn't. Or does it?**

edit: I'm posting this in "Desktop environments" because I'm unfamiliar with LXDE, and so my assumption was that it's a problem with the system tray, or with my understanding of the sys tray. But it may just as well be that KGPG isn't running right, in which case maybe I posted in the wrong sub-forum.

edit2: Since posting this, I've found that the key manager I was used to is called Seahorse, and it IS possible to install in Lubuntu. Even though it's supposed to be for gnome. But, I still need to be able to run KGPG to encrypt/decrypt/verify files, unless there's another way to do it.
Can someone point me to some reading on what exactly Gnome/KDE/LXDE means? I think I don't fully understand what it means to be running LXDE as my environment. Some things were designed for Gnome, but can still run in KDE or LXDE - true?

---

### Post by offgridguy on 2013-01-28
KDE, here.

[http://en.wikipedia.org/wiki/KDE](http://en.wikipedia.org/wiki/KDE)

Gnome, here.

[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

Lxde,  here.

[http://en.wikipedia.org/wiki/LXDE](http://en.wikipedia.org/wiki/LXDE)

---

### Post by johnmuir on 2013-05-22
Hi alnilamski,

I've got the same problem, did you find a solution?

---

### Post by johnmuir on 2013-05-22
I found that starting kgpg with the option -d (editor) or -k (key manager) solved the problem. I'm using Unity and it doesn't support the system tray, so the solution is to force KGpg not to start minimised.

---

