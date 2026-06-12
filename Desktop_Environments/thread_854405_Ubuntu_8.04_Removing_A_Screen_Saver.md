---
title: "Ubuntu 8.04: Removing A Screen Saver"
date: 2008-07-09
forum: Desktop Environments
---

### Post by tinker123 on 2008-07-09
Hi;

I'm using Ubuntu 8.04.   I like the random screen saver.  I don't like one screen saver in particular.  It takes random images on my hard drive and rotates them as a screen saver.   Cool Screen Saver, bad idea for a default.  Maybe there are some images people don't want flashing up on their screen while they are talking to people in their homes :).

Is there any way I can keep the random screen saver, but remove/disable just this one?

Thanks

---

### Post by werries on 2008-07-09
yes, theres a way to remove just one screensaver, and i have entirely forgotten how. >.<
edit: just found it.
```
sudo rm /usr/share/applications/screensavers/screensaver_name.desktop
```
where screensaver_name is where you put in the one you want to remove

---

### Post by tinker123 on 2008-07-09
> **werries said:**
> yes, theres a way to remove just one screensaver, and i have entirely forgotten how. >.<
edit: just found it.
```
sudo rm /usr/share/applications/screensavers/screensaver_name.desktop
```
where screensaver_name is where you put in the one you want to remove

Thanks!

FYI, the name of the offending screen saver is
personal-slideshow.desktop

What a *bad* idea to include that in the random list by default! :)

---

### Post by vayira on 2009-06-22
> **tinker123 said:**
> FYI, the name of the offending screen saver is
personal-slideshow.desktop

What a *bad* idea to include that in the random list by default! :)

I too was a bit horrified to see my private photos poping up on the screen without warning. I shall delete it now!

In 9.04 Jaunty it is called pictures folder

---

### Post by tinker123 on 2010-11-28
> **tinker123 said:**
> Hi;

I'm using Ubuntu 8.04.   I like the random screen saver.  I don't like one screen saver in particular.  It takes random images on my hard drive and rotates them as a screen saver.   Cool Screen Saver, bad idea for a default.  Maybe there are some images people don't want flashing up on their screen while they are talking to people in their homes :).

Is there any way I can keep the random screen saver, but remove/disable just this one?

Thanks


I forgot about the existence of this issue and that I did something about it.  I rediscovered it 16 months later.  In other words the screensaver got reinstalled during an upgrade.

This is a potential security issue.

Someone can choose the option to display random screensavers not knowing this screensaver will display random pictures from their hard drive --- possibly to coworkers, a boss, guests etc.

I opened up a feature request to have it removed or at least not reinstalled.  If you agree with me please take the time to vote my feature request up:

**Idea #26580: Potential Privacy Issue: Screensaver personal-slideshow.desktop **
[http://brainstorm.ubuntu.com/idea/26580/](http://brainstorm.ubuntu.com/idea/26580/)

---

### Post by tinker123 on 2010-11-28
I discovered 3 things:

1. Removing the screensaver from the directory quoted earlier does not work.

2. This is a problem with GNOME/gnome-screensaver, not Ubuntu

3. I found directions in a FAQ on the GNOME web site for removing a screensaver from the list of screensavers.  Run the command in those directions logged in as a regular user, not root.  The command will only disable screensavers for that user.

[http://tinyurl.com/2632kld](http://tinyurl.com/2632kld)

HTH

---

