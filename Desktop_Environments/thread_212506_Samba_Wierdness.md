---
title: "Samba Wierdness"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Jivicin on 2006-07-10
I've been gradually migrating my computers from XP to ubuntu, and I have to say 99% of my problems I have been able to solve reading the forums/manuals.  This community is amazing.

However, the only thing keeping me from deleting my Windows partition is:

I want to share folders across my network using Samba.  My main rig has 6.06 up and running with samba installed.  My other rig has the latest xubuntu installed (it's only 800 MHz).  Using the GUI under System -> Administration -> Shared folders seemed to work.

Today I had the two computers running concurrently with samba and various shared folders and I was able to see them from a third computer.  I threw a small party when everything was working. :D 

The problem:  First, when I shut a computer off that has samba enabled, it takes between 5-10 minutes for the group to show that there are still computers connected under nautilus.  For example, right now if I click Places -> Network Servers then click windows network then MSHOME, I can see the computer that I'm using and my files.  When I shut down the other computer, my main one temporarily disappeared from this screen.  I have no idea why.  Yet when I type: ```
smb://mainrig/shares
```I can see the files anytime.  It also takes 5-10 minutes when I start the computers before they show under the screen.  Weird?

A side annoyance I have is a ton of extra entries showing up beneath Network Servers in the Places menu.  Old connections that I no longer wish to use.  Any idea on how to clean that out?

Thanks in advance!

---

### Post by scxtt on 2006-07-10
samba's kinda just "weird" like that ... i've never really gotten the whole "network neighborhood" concept working w/o minor issue - even in windows it isn't perfect ... there is a program called "linneighborhood", it might perform better ...

also, i've you're going "all *ubuntu" - consider using NFS instead, it performs better ...

---

### Post by Jivicin on 2006-07-10
Thanks for the info (and spelling tips... I need to stop posting after midnight).  I'd consider NFS, but I want to share files to a Windows box too.

Any thoughts on how to get the extra entries out from under the Network Servers list?

---

### Post by AZzKikR on 2006-07-10
Perhaps with the Configuration Editor in Gnome. It doesn't show up by default, but you can add it using the Alacarte Menu Editor if I recall correctly. I once removed share entries like that as well, but I can't recall how at this moment (I'm at work on my XP laptop).

---

### Post by Jivicin on 2006-07-10
I was hunting around inside the Configuration Editor and didn't see anything that looked like it would do the trick.

Anyone?

---

### Post by Jivicin on 2006-07-26
I ended up solving this by opening up the Network Services window and unmounting the servers by right clicking on them.

It's nice when the problem is simpler to solve than you anticipated. :D

---

