---
title: "no gnome panel"
date: 2008-08-08
forum: Desktop Environments
---

### Post by Drone4four on 2008-08-08
I loaded Ubuntu for the first time in a week and after logging into my account, the gnome-panel doesn't load.  Since ALT + F2 doesn't work, I can't run the gnome-panel command.

Searching Google for no gnome panel, I came across one solution, to create a new user account.  I did that using the adduser command in a VT, but the new account doesn't have a gnome panel either.  

How do I get my gnome panel back?

I'm using the LiveCD to write this forum thread.

---

### Post by phidia on 2008-08-08
Type or enter > sudo apt-get update && apt-get install gnome-core gdm
 I think that will pull the packages you need.

---

### Post by Drone4four on 2008-08-08
This worked.  Thanks phidia.  How did you know this was the command I needed?  I ask because I want to do these things myself without asking questions.  I want to learn to fish, so to speak.

---

### Post by ad_267 on 2008-08-08
sudo runs a program as the root user
the && in the middle means run the second command if the first completed successfully.
"apt-get update" updates the list of packages
"apt-get install" installs a package

If you want to learn to fish there's just one command you need to learn. It's called "man". Try "man sudo", "man apt-get", "man apt-cache"

There's also plenty of tutorials out there about linux commands.

---

### Post by phidia on 2008-08-09
> **Drone4four said:**
> This worked.  Thanks phidia.  How did you know this was the command I needed?  I ask because I want to do these things myself without asking questions.  I want to learn to fish, so to speak.

I'm very glad it worked! :D

When I offer help here in the forums I often double check myself so that I don't give people the wrong instructions. I still make mistakes though but my main sources of double checking are the Ubuntu wiki (linked in my signature) man pages are also online and debian has an amazing amount of help at [their site]("http://www.debian.org/").
Other guides: [commands & shortcuts]("http://www.unixguide.net/linux/linuxshortcuts.shtml"), [command.org]("http://gd.tuwien.ac.at/linuxcommand.org/"), [tools/guides]("http://www.linuxtopia.org/online_books/gnu_linux_tools_guide/") and for dessert [the gnu project]("http://www.gnu.org/").

---

