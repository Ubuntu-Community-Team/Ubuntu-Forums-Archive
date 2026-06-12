---
title: "User-switching problems"
date: 2005-12-17
forum: Desktop Environments
---

### Post by kmonihen on 2005-12-17
I'm having problems using the fast user-switching mechanism in KDE 3.5.  I am using a version of Ubuntu Breezy that has been upgraded to Kubuntu by installing the kubuntu-desktop package.  I am also using KDM and am trying to switch between two KDE sessions.

Here is how I attempt to switch users:
1. KDE-Menu->Switch User->Start new session
2. Log in as new user at the KDM screen
3. Then KDE-Menu->Switch User->username: kde: (:0, vt7)
4. Find myself back at the KDM screen, login as "username" and it starts a brand new instance of KDE.

I've tried using ctrl-alt-F7/F8 etc. to switch users, but doing this will sometimes take me back to KDM or take me to a non-graphical login prompt.  I have never gotten it to successfully switch users like Windows XP does.

Thanks in advance for any help with this problem.

- Keith

---

### Post by mlomker on 2005-12-18
It might be a video driver issue.  Fglrx, for example, doesn't support it right now because the second desktop requires another instance of the driver and they won't play nice.

You could try switching to VESA for one bootup to see if that works.

---

### Post by kmonihen on 2005-12-19
I switched to VESA, but then it would just boot straight to the non-graphical login.  I guess I should just be happy that I found a Linux distribution that is useable on my Dell PC.  My next PC will definitely by "Linux compatible."

Thanks for your time.

---

