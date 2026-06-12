---
title: "Can't log out to switch between Gnome and xfce"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Daniel Rehm on 2005-11-29
I was looking for a desktop environment that I could recommend for my roommate. We both use Ubuntu but since Gnome and KDE run a bit slowly on her laptop, I decided to take xfce for a test drive on my computer and see how it looked, how it ran, and so that I'd be able to let her know where to find things in case she had any questions.

I grabbed the Xubuntu metapackage from synaptic, and tinkered with xfce for an hour or two. Confident that it would probably satisfy her needs, I attempted to log out. That's when the problems started. The screen simply went blank and nothing happened. After 5 or 6 minutes I tried to kill X with ctrl-alt-backspace and nothing happened. Mutteringly angrily to myself, I powered down and restarted.

I logged into gnome and all was well for another hour or two before I decided to switch over to xfce to fiddle with it some more, this time for my own personal curiosity. 

When I attempted to log out of Gnome, I was dumped to a command line. Puzzled, I attempted to restart X. That worked, but it put me right back into gnome instead of a login screen. Obviously, I had to be logged in to tell X to start and X was just putting me where it thought I was "supposed" to be.

A couple of experiments have duplicated this behavior. If I'm in gnome, logging out dumps me to a command line. If I'm in xfce, trying to log out locks up the computer.

This behavior won't fly. Strictly speaking, I don't *need* to be able to log out, since I'm the only regular user on this computer... but at the same time it seems pretty ridiculous to have to power down to switch between desktop environments. However, I'm fairly new to linux and I'm not sure what my next step should be.

Any and all suggestions would be very welcome!

---

### Post by Xian on 2005-11-30
I would start by making sure you have gdm installed.
If it is, then do a reconfigure session.

$ sudo apt-get install gdm
$ sudo dpkg-reconfigure gdm

---

### Post by Daniel Rehm on 2005-11-30
[QUOTE=Xian]I would start by making sure you have gdm installed.
If it is, then do a reconfigure session.

$ sudo apt-get install gdm
$ sudo dpkg-reconfigure gdm[/QUOTE]

I know that I have gdm installed because, when I restart, I do get a log on screen. I simply can't switch environments after I log into one or the other.

---

### Post by taurus on 2005-11-30
Did you pick XFCE4 as your session before you type in your login name and password???

---

### Post by Daniel Rehm on 2005-11-30
[QUOTE=taurus]Did you pick XFCE4 as your session before you type in your login name and password???[/QUOTE]

/sigh

Yes. I am able to log into xfce *just fine*.

The problem isn't getting *into* one session or the other. I have no problem getting into gnome or xfce. The problem is that I cannot *log out* of either one once I am in it. This is forcing me to restart the computer everytime I want to change desktop environments.

---

### Post by almahtar on 2006-02-06
I think you missed the whole "dpkg-reconfigure" part of that one guy's post.  He's saying if you reinstall and reconfigure gdm, perhaps it'll all be ok.  If it is, SWEET.  If it isn't then it looks like you have the same problem as the three of us in this thread:

[http://www.ubuntuforums.org/showpost.php?p=535267&postcount=1](http://www.ubuntuforums.org/showpost.php?p=535267&postcount=1)

Check it out, perhaps there's some info in there that will help you, even if it hasn't helped us yet :-)

---

