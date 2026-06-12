---
title: "My office full of dells, wont print or email with ubuntu"
date: 2007-06-21
forum: Dell  Ubuntu Support
---

### Post by jpuretz on 2007-06-21
The email system is compatible with Outlook, but how do I load old files onto it? I saved Outlook's files but I don't know where to put them so that this system will know to access and use them correctly.

I know how to put up a firewall and have done so, but what about a virus scanner or something to allow you to know when someone is trying to access your computer?

I have tried to set up the computer to print on a network, but even if I set it up properly, by filling in all the appropriate fields (windows network printer, hp laserjet2300, IP host address) I can't print. I've tried a couple other settings and it still won't work. I looked at an online tutorial as well and the controls I have on my computer are different even though we have the same version of Ubuntu (7.04, fiesty fawn). Maybe that person had the "expert" version?

How do I get the expert version or at least upgrade to it?


Thank you for your time
__________________

---

### Post by scrooge_74 on 2007-06-21
Hi, 

there is no expert version, you have to customize things for you to work, your Outlook files it would be best to first export them to Thunderbird from inside windows and then just load those files from the Linux version of Thunderbird.

As for printing you first set up your printer using CUPS (which comes pre-install) and then you setup a SAMBA server (so your PC appears in a windows network)

For firewall not really necesary to install one, Linux has a firewall inside the Kernel, you need one if you are planning to run a server or a webserver.  As for virus the scanners available (in the repositories) are only so you dont resend viruses to windows computers, your Linux box can't  get infected

A couple of sites to get you up to speed.

[http://www.psychocats.net/](http://www.psychocats.net/)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://www.samba.org/](https://www.samba.org/)
[https://www.cups.org/](https://www.cups.org/)

---

