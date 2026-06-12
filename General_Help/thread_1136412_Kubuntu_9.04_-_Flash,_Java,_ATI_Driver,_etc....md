---
title: "Kubuntu 9.04 - Flash, Java, ATI Driver, etc..."
date: 2009-04-25
forum: General Help
---

### Post by AdamShumpisxXx on 2009-04-25
I don't know if anyone will recognize me from the Jaunty Release thread but here I am and I'm not happy.

I've been a Ubuntu user since 7.10 and since then I've become really fluent with how it works, how to troubleshoot, and how to solve any problems I have.

If you do remember me from the Jaunty Release thread you'll know that for 9.04 I was going to make the switch from Ubuntu to Kubuntu. MISTAKE! Just about everything I know about Ubuntu / Linux is completely useless here. I can't install flash for Firefox, I can't install Java for Firefox, I can't get the latest ATI driver, I can't find Cheese for my webcam...and any documentation I find to do these things with Kubuntu comes from 2006 or something.

Trying to use apt-get through Konsole to install flashplugin-nonfree comes up with a sweet "package not found" error. I'm not going to go through it all but basically that's the story with everything. Yes, I enabled all the repositories in Software Sources and no that didn't help.

Here's what it boils down to. It's pretty but it sucks. End of story.

The only redeeming quality so far was it had my Wireless N PCI Card installed on first boot with no configuration unlike the hell I went through in 8.10. But I expect that to be the same case for Ubuntu.

I don't know what I'm asking here and I don't expect someone to "save me". I basically wish time wasn't wasted on something I instantly hate.

This is a warning. Don't use Kubuntu. Hahaha.

---

### Post by Roryking on 2009-04-25
Ha ha, I made the switch during the 9.04 beta. I plan to reformat/reinstall with the official Kubuntu release.

Try sudo apt-get install ubuntu-restricted-extras. ubuntu-restricted-extras should give you all the goodies like Flash, Java, MP3 codecs, etc. As far as ATI goes - installing kernel-restricted-extras may give you the driver. Installing Envy will give you a pretty interface to do the same.

Good luck. Kubuntu definitely isn't as simple as Ubuntu, but I've found the enhanced user interface to be worth the learning curve.

---

### Post by AdamShumpisxXx on 2009-04-25
xxx@xxx:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

None of that works. I just got done burning the Ubuntu 9.04 CD. I'm outta' here!!!

---

### Post by AdamShumpisxXx on 2009-04-25
Well, would you look at that turn-around time?! I'm back on Ubuntu and everything is installed and configured! SOLVED!!!

Ubuntu was the solution the whole time! Hahaha!

:lolflag:

---

### Post by drleper on 2009-04-28
You need to install* kubuntu-restricted-extras* (from what I can see there's 3 restricted-extras packages, one each for ubuntu, kubuntu and xubuntu). That will put flash, mp3 playback, mostly everything you need. For some reason it doesn't install the firefox java plugin (on kubuntu 9.04), so I had to do;

sudo apt-get install kubuntu-restricted-extras sun-java6-plugin

To get all the extras and make java work in Firefox. No problems after that.

---

