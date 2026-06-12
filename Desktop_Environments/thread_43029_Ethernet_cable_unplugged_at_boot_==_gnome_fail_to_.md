---
title: "Ethernet cable unplugged at boot == gnome fail to start"
date: 2005-06-20
forum: Desktop Environments
---

### Post by OwlManAtt on 2005-06-20
I just got one of those clamshell iBooks and put Ubuntu on it last night. I had no problems until this morning when I tried to use it without the ethernet cable plugged in.

When I logged in through gdm and GNOME started, it would give a bunch of errors about not being able to do something with the bonobo server. After clicking through three or four error boxes, I'd get an ubuntu-brown colored screen and a mouse pointer. I couldn't even logout through gnome, I had to restart gdm.

I put the network cable in and restarted networking, stil the same problem. I don't think that came up though, because apt couldn't resolve a bunch of domain names. Once I rebooted with the network cable in, everything was fine.

How do I fix this so GNOME works when I don't have a network connection at boot? This is a laptop, I'm not always going to be by an ethernet jack when I use it. Behavior like this is totally unacceptable in a laptop.

---

### Post by intangible on 2005-06-20
I've seen an error like that before when the /etc/hosts file didn't have an entry for the local computer, dunno how it would've gotten removed, but:

Make sure there's a line in /etc/hosts that says something like:

**127.0.0.1 localhost localhost.localdomain COMPUTERNAME**

Where COMPUTERNAME is your computer's hostname.

If you can give the exact error message, that would help.

---

### Post by OwlManAtt on 2005-06-20
I have that entry in hosts. I uninstalled Xfce, which I tried for about five minutes last night, too. 

Then I rebooted without the cable to get the exact error messages, and I find that I can't reproduce the problem. Weird.

But thanks. =)

---

