---
title: "Desktop GUI broken by elves"
date: 2007-02-27
forum: Desktop Environments
---

### Post by Mark_in_Hollywood on 2007-02-27
While following instructions from a post on these forums:

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
and
sudo apt-get install linux-sound-base alsa-base alsa-utils

The next instruction was to reboot. Once that was done I no longer have a graphic desktop. 

The next instructions in the Guide said:

sudo apt-get install gdm ubuntu-desktop

which can't happen because I have ONLY the command line prompt, no way to access the net. I switched hard drive (I keep a spare Ubuntu for just these kinds of problems) and received advice to see  X troubleshooting page. [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)
The first command: sudo apt-cdrom add, returned an error message that no device was present -- or something like that.

and the next two commands

sudo aptitude update
sudo aptitude install ubuntu-desktop

both required the 'net, so again I was in trouble.

The harddrive with no GUI is now primary SLAVE. It is seen as hdb1 in a folder called /mnt/Drive2 by the primary master.

Where do I start to repair the problem? I'm completely lost.

---

### Post by ComplexNumber on 2007-02-27
> 
sudo apt-get install gdm ubuntu-desktop

which can't happen because I have ONLY the command line prompt, no way to access the net.it still mounts the network, so you can install gdm....unless there is something that you've forgotten to mention. you don't need a graphical interface to access the net.

---

### Post by Mark_in_Hollywood on 2007-02-27
> **ComplexNumber said:**
> it still mounts the network, so you can install gdm....unless there is something that you've forgotten to mention. you don't need a graphical interface to access the net.

What commands perform the chores of dialing the ISP and making a PPP connection and from then is it:

sudo apt-get install xxx-xxx-xxx ?

---

### Post by ComplexNumber on 2007-02-27
oh right. so you're on dialup. i can't remember the last time i ever used dialup, so i can't help im afraid. sorry. i've been on broadband for quite a few years now.

---

### Post by yamel on 2007-03-14
Good evening.

This is one of the threads that pops up when I'm searching for a solution to my lost gui.  I followed the exact same advice trying to get sound on a Gateway MX3414 (sudo apt-get --purge remove alsa-base alsa-utils.  Froze and lost everything a couple lines later).  I don't know what all is purged by that command, but I have nothing left but a command line.  Can't "apt-get install anything because I can't access a wireless network.

I've started a thread similar to this one that has seemingly dried up as this one did.  I'm curious to know if there is a solution that was found off the forum or if a complete reinstall is the next step.

Thanks

---

### Post by Cariboo1938 on 2007-03-15
> **ComplexNumber said:**
> oh right. so you're on dialup. i can't remember the last time i ever used dialup, so i can't help im afraid. sorry. i've been on broadband for quite a few years now.
So, how do I access the Internet (Broadband) without GUI?
Is there a list of most commonly necessary commands for a running a simple server? 
I just began to configure a server for my home network of three computers of family members who want to use one printer and one Internet connection.

---

