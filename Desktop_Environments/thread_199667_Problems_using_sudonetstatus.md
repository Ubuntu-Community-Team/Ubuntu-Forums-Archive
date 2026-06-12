---
title: "Problems using sudo/netstatus?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Terazilla on 2006-06-19
*Short version*:  When I try to use sudo it never seems to do anything beyond ask for my password.  Is there I trick I'm missing?  Also, is there supposed to be a net status icon on the launch bar in Dapper Drake 6.06? Because I don't seem to have one.

*Long version*:

I suspect I'm doing something wrong here, but can't figure out what it is.  I installed Ubuntu 6.06 (from DVD, using the liveCD style installer) the other day onto a Compaq laptop.  It installed no problem and seems to have detected all the hardware correctly.  I plugged in a network cable and it got an IP address correctly, web browsing and so on is no problem.

From there I ran Easy Ubuntu to get mp3 playback and so on installed, which seems to have worked fine.  I went to Administration/Users and added a user and password for myself, configured as a regular user.  Satisfied, I ran "sudo oem-config-prepare" and followed its instructions.

Somewhere around here is where I hit a stumbling block, because I realized I hadn't tried the D-Link G650 PCMCIA 802.11g card I had sitting around.  I plugged in the card and browsed Device Manager to find it appeared to be properly detected and installed.  Cool!  Then I started looking to connect to my wireless network... and couldn't figure out how.  A number of web searches tell me I'm supposed to use a "network status" icon from the launch bar -- which doesn't seem to exist on this machine.  Huh, okay.  I look around in the menus and so on, and don't find it.

I eventually find a page that suggests using a program called NetworkMonitor, which sounds promising.  So I run Synaptic from the command prompt, and when it says it needs root I close it and run it again thus: "sudo synaptic".  It prompts me for a password, which I provide, then does absolutely nothing.  I try running a few other commands through sudo, and still nothing.

I log out and back in, and try again, and it still refuses to do anything that I can discern when I try to sudo.  Looking around through more forums I try using visudo to see what allowed sudoers list, and it tells me I don't have permission.

Am I doing something wrong here?  I'm starting to think I'm stuck and will never be able to get admin access for anything without a reinstall.

---

### Post by aur0ra on 2006-07-27
I had a similar problem. Althought I don't know *why* I had the problem, it can easily be resolved by doing the following:

%> su
   --enter root password--
%> visudo
.....
.....
root    ALL=(ALL) ALL
yourname ALL=(ALL) ALL
....
....

Then shift+wq to get out of vi and you will be good to go.

Hope that helps.

---

