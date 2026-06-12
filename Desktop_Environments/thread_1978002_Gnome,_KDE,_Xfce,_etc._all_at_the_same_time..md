---
title: "Gnome, KDE, Xfce, etc. all at the same time."
date: 2012-05-11
forum: Desktop Environments
---

### Post by 1clue on 2012-05-11
Hi,

I use lots of window managers, currently KDE.  My girlfriend uses the default 11.10 manager.  I want to be able to switch around until I find something that works nice.

I want a display manager (login screen) that plays nicely with everything.  If I use KDM then when the gf tries to quit her session she gets errors and doesn't even get logged out.  Similarly for me when I try to log out with GDM.

More, I use dvorak and she uses querty.  In 11.04 there was a keyboard selector right in the display manager.  I want it back.

I want a display manager that has these features:
[LIST=1]
[*]Works with Gnome, KDE, XFCE, anything and supports whatever these managers/desktops want.
[*]Has a keyboard selection right in the display manager.
[/LIST]

---

### Post by zombifier25 on 2012-05-11
The default LightDM works fine (for me). It works with whatever DEs installed and you can choose the keyboard layout.

---

### Post by GERGE on 2012-05-11
LightDM would work but you can try LXDM.

---

### Post by 1clue on 2012-05-11
How do you get the keyboard menu to show?

I'm using 11.10, it does not show up by default.

FWIW KDM causes the default session to crash on logout, and it doesn't log out.  I don't know for a fact that KDM will fail when I log out with LightDM but I would like to avoid it if it happens.

Back when you had your choice as long as it was XDM, I got into configuring it.  Now I don't even know how.

Thanks.

---

### Post by VanillaMozilla on 2012-05-11
Why are you doing it the hard way?  Just use separate accounts.  You can switch desktops on login if you want to.  You can set file permissions so you both have access to the same files.

---

### Post by 1clue on 2012-05-12
We have separate accounts.  Wouldn't have it any other way.

I'm after enabling either keyboard during the login process.  As far as I can tell, there is no keyboard selection available to enter login credentials.

I'm also after a display manager that won't crash or cause a crash when you log out.

---

### Post by VanillaMozilla on 2012-05-12
I don't understand.  The keyboard selection is made after you log in, and each user should have a separate preference.

The choice of desktops, etc. is made just before you log in.  Once you have logged in, you should have your own desktop that's completely separate from other users.  What am I missing about your problem?

---

### Post by sudodus on 2012-05-12
I recently made a system to test 12.04 like this.

I started installing vanilla Ubuntu.

Then I installed the other desktop environments
```
sudo apt-get install kubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop
```
and I can select the desktop environment at the log-in screen. I have tested it forwards and backwards, and there were no crashes at logout of KDE (but the gnome-3 environments were not complete, I had to install extra packages to make those run).

I'm afraid that you have to install the keyboard in your user session (that is you have to log in using the standard keyboard). But I have little experience of 11.10 because I skipped it. Maybe someone else knows how to select the keyboard at the log in screen.

---

### Post by VanillaMozilla on 2012-05-13
I don't have Precise in front of me, but the keyboard is part of your profile, and it's easily controlled with an indicator applet.  <Alt>right click to install.

---

### Post by VanillaMozilla on 2012-05-14
Did you find it yet?  It's under System Settings > Personal > Keyboard Layout.

---

### Post by 1clue on 2012-05-14
> **VanillaMozilla said:**
> I don't understand.  The keyboard selection is made after you log in, and each user should have a separate preference.

The choice of desktops, etc. is made just before you log in.  Once you have logged in, you should have your own desktop that's completely separate from other users.  What am I missing about your problem?

Yes, I know all about setting it with user preferences.

What I'm talking about is a menu on the **login screen** which allows you to select an alternate one for the **login screen only**, so I can type my password using dvorak and she can type hers using the one she wants.

11.04 not only did this, but it also remembered which one you used last time, so when you clicked on your entry in the login page it automatically switched layouts for you.

I went the upgrade route rather than reinstalling, so maybe it's gone because of some upgrade glitch.  You guys are saying it's gone completely.

---

### Post by VanillaMozilla on 2012-05-15
Sorry, I completely misunderstood what you were asking.  Also sorry, I don't have a clue.  I see it here on Natty, but you are versions beyond that.

---

### Post by sudodus on 2012-05-15
I'm afraid it was a feature of Gnome 2, and it is probably not implemented (yet?) in Gnome 3 and or whatever software has replaced the software containing keyboard switching at the log in screen.

Gnome 2 is neither developed nor supported any more. There is fork called Mate, that is replacing Gnome 2. Maybe Mate has the feature you request. Linux Mint Debian has a Mate flavour. I don't know how it works to run Mate in Ubuntu. You can read more about Mate browsing the internet.

---

### Post by marco07 on 2012-05-15
> **sudodus said:**
> I recently made a system to test 12.04 like this.
 
I started installing vanilla Ubuntu.
 
Then I installed the other desktop environments
```
sudo apt-get install kubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop
```
and I can select the desktop environment at the log-in screen. I have tested it forwards and backwards, and there were no crashes at logout of KDE (but the gnome-3 environments were not complete, I had to install extra packages to make those run).
I'm afraid that you have to install the keyboard in your user session (that is you have to log in using the standard keyboard). But I have little experience of 11.10 because I skipped it. Maybe someone else knows how to select the keyboard at the log in screen.
 
Hello, I am interested to try this. But i could not figure out what you mean by a "vanilla Ubuntu." Would you elaborate? Which and what version of Ubuntu?
Thanks!

---

### Post by VanillaMozilla on 2012-05-15
Marco, he started with Ubuntu.  That means Ubuntu, not Kubuntu, Lubuntu, or Xubuntu.  It means the Gnome desktop with Unity.  Then he added the KDE, LXDE, and XFCE desktops, i.e., Kubuntu, Lubuntu, and Xubuntu.  You can choose which one you want at login time.

You should know that there is a problem with this, though.  You will get three or four of everything.  For example, you won't just get Nautilus.  You'll also get PCMan, maybe Konqueror, and something else.  Your Applications menu will be stuffed with lots of programs that you don't need.  The system may also be kind of confused.  For example, whether you are you running a screensaver, and which one.  You can sort it out easily, but your computer will probably be a bit messy.

---

### Post by marco07 on 2012-05-15
> **VanillaMozilla said:**
> Marco, he started with Ubuntu. That means Ubuntu, not Kubuntu, Lubuntu, or Xubuntu. It means the Gnome desktop with Unity. Then he added the KDE, LXDE, and XFCE desktops, i.e., Kubuntu, Lubuntu, and Xubuntu. You can choose which one you want at login time.
 
You should know that there is a problem with this, though. You will get three or four of everything. For example, you won't just get Nautilus. You'll also get PCMan, maybe Konqueror, and something else. Your Applications menu will be stuffed with lots of programs that you don't need. The system may also be kind of confused. For example, whether you are you running a screensaver, and which one. You can sort it out easily, but your computer will probably be a bit messy.
 
Thank you! I lost my interest and gave up.
So, it seems it would be better to install, for example unity and kubantu, each on a separate partition, if one desires to have them both. Right?

---

### Post by 1clue on 2012-05-15
> **marco07 said:**
> Thank you! I lost my interest and gave up.
So, it seems it would be better to install, for example unity and kubantu, each on a separate partition, if one desires to have them both. Right?

IMO the answer there is no.  The only real difference between Kubuntu, Lubuntu, Ubuntu and any of the others is which desktop package is installed.

As most of you guys probably know, I'm "suffering" from this very scenario, with 4 or more of everything.

I think it's a PITA, the default setup should only install apps into the desktop which matches it unless you specify otherwise.  I would like to have a semi-pristine example of  each setup so I can switch at will.

Nonetheless, having an entirely different partition with everything the same but the desktop is a total waste of space and a total PITA for maintenance.

---

### Post by VanillaMozilla on 2012-05-15
I think there are limited packages that don't install the whole works.  (I forget the details, and I'm not on the right box right now.  You can search for it.)  Also, you can uninstall anything and everything, but it's a pain.  Both the Software Centre and Synaptic keep history, so you can see what was installed when.  Keep some notes.

Realize, of course, that you can run KDE programs from a Gnome desktop, etc., if that's what you want to do.

If you really just want to look at a desktop, without much possibility of installing or modifying very much, you can always just boot from a live CD.

We're kind of getting away from the original question, though.

---

