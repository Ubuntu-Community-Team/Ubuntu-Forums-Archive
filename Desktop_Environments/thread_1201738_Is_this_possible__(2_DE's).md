---
title: "Is this possible?  (2 DE's?)"
date: 2009-07-01
forum: Desktop Environments
---

### Post by AoSteve on 2009-07-01
Alright, I was bored.. and I want something new to play with for a while, but I'm not sure if this is even possible.

Is it at all possible to install more than one environment like Gnome?

Let me rephrase it to better understand what I'd like to do, if it's possible.

My User Account ->  Gnome, standard from 9.04 install..

New User Account ->  KDE from repo's or whatnot without hurting my normal user account?

Is it possible to run two different user accounts with different desktop environments without potential problems?   Also, how difficult would it be to do?

---

### Post by Idefix82 on 2009-07-01
If you install another desktop environment then all your environments will be available to all users, no need for a new user if you want to use KDE. Just open the terminal, type in
```
sudo apt-get install kubuntu-desktop
```
provide your password and watch the installation firework. Now logout and choose under "Session" whether you want to boot into KDE or GNome. Repeat with
```
sudo apt-get install xubuntu-desktop
```
for even greater choice. Enjoy.

---

### Post by AoSteve on 2009-07-01
So I can switch any time I want?   I mean, I love Gnome and have only used KDE once..  I didn't really like it personally.    Any idea how big those downloads would be?  

I would rather have a new user account however being as I would like to leave this as it is.  It's perfect for my daily use! :)

---

### Post by Idefix82 on 2009-07-01
> **AoSteve said:**
> So I can switch any time I want?   I mean, I love Gnome and have only used KDE once..  I didn't really like it personally.    Any idea how big those downloads would be?  

I would rather have a new user account however being as I would like to leave this as it is.  It's perfect for my daily use! :)

You are free to create as many user account as you like but that has got nothing to do with the Desktop environment you use. Every time you login, you can choose what Desktop to use. That's the power of the modular structure of Linux. It's as if you wanted to create a new user to use a different office suite.

Having said that, what will change is that you will also be able to run KDE programs from GNome and they will show up in your menu. For that a separate user might be useful since you can then set up your menu e.g. to contain only KDE programs for one user and only GNome for the other, or a suitable mix, as you wish.

---

### Post by AoSteve on 2009-07-01
Nice...   I think I'll have to give it a try! :)  Thanks Idefix82!

---

### Post by AoSteve on 2009-07-02
So KDE is absolutely amazing compared to Gnome..  However, I noticed it takes a bit more.. umph from the system to run.  However, I have both installed so I can basically say I have a Ku-Ubuntu machine in there :D    I like it, not as much as gnome, but it is pretty full of some nice Eye candy.  steveKDE will be the KDE account of choice.  My wife seems to like it too.   Now to try Xubuntu's desktop.  :)   Thanks for the lead bud!  I appreciate it!

---

### Post by Idefix82 on 2009-07-02
You are welcome. Have fun!

---

### Post by XubuRoxMySox on 2009-07-02
You can have four or five DEs if you want (and you have room on your hard drive for all of them).

You might also want to try [LXDE]("http://lxde.org") (available in repositories) for use on low-resource machines. It uses much less RAM and CPU resources than any other DE. Great for laptops, older computers, and netbooks. They are not related, but LXDE looks like it could pass for "KDE's pretty little sister." Cute, graphical, very very simple (good choice for kids), very configurable and customizable.

Then there's E-17, omygosh... the *animated* desktop environment. Mind-bending animated wallpapers and stuff. Beautiful - and less resource-hungry than KDE!

Try 'em all! Have fun!!

-Robin

---

### Post by AoSteve on 2009-07-02
Sweet!   I installed Xcfe on the laptop last night.  I like it, interesting booting up with less than 150mb of 2gb used!  LOL

E-17 really sounds interesting!  I'll have to check into that!

---

