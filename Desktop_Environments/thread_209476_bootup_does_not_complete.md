---
title: "bootup does not complete"
date: 2006-07-05
forum: Desktop Environments
---

### Post by jgv on 2006-07-05
Hello, I would be grateful for any guidance as my computer is presently not usable.

I have seen 2 different failure scenarios during bootup.

Here is one scenario:

[] the "loading ... " screen appears and as best I can tell, everything is OK except for "lLoading hardware drivers" and "Starting PCMCIA services" both of which "failed".  A considerable delay (minutes) occurs at the "Loading hardware drivers" step.

[] the next delay occurs at the "Configuring network interfaces" step after which the text changes from amber colored to white and the boot process appears to abort with the final messages being:

* Checking all filesystems ... [ok]
/etc/rcS.d/S40ifrename: line 12: /sbin/ifrename: No such file or directory
* Configuring network interfaces...
udevd-event[3180]: wait_for_sysfs: waiting for '/sys/devices/platform/i82365.0/bus' failed


Nothing else happens after that.

Here is a second failure scenario:

[] I get the logon screen where I enter a user/password and press enter.
[] Thereafter, a blank brown screen appears and nothing else happens.
[] Pressing ctrl-alt-F1 (something I gleaned from other forum postings) displays the following:
[17179604.708000] ppdev: user-space parallel port driver

The following may be helpful:

[] I am a linux novice, but I did use the previous "hoary hedgehog" release with no problems.
[] The computer was working with 6.06 until I used the system administration "networking" dialog tool to switch the wireless network encryption from disabled to enabled and back to disabled.  I have never directly edited any configuration files so if one is corrupted, the supplied GUI tools are suspect.


Thanks for taking the time to read my tale of woe.

-- jv

---

### Post by notepad on 2006-07-05
i dont have any answers for you jv but it may be some comfort to you that my system actually gives me the same bootup errors you described in the first instance. apart from that, my system mostly works besides from a terribly annoying dhcp issue im having which is why im here. i think this version of ubuntu while much prettier than any version before it, is functionally up the creek. who is developing ubuntu? dont they read this forum?

---

### Post by jgv on 2006-07-06
Does anyone have a suggestion on how to fix this?  My computer appears to be usable at this time.  Very bad!

-- jv

---

### Post by muffinhead on 2006-07-07
Btw, would you happen to have any onboard sound card, or onboard video?

I had the same problem with it stalling or freezing at "Loading Hardware Drivers" Whenever I tried to boot with my PCI Geforce FX 5500, and I solved it by blacklisting my paticular onboard video, with the /etc/modprobe.d/blacklist , file

Hope you can figure out how to solve your problem, who knows it might be as simple to solve, as mine was ;) . Make Sure if this is the problem, and if it is, Ask exactly what needs to be blacklisted, in that file that I mentioned, someone else might be able to help with that.

Btw, my onboard video, was Intel extreme graphics 3d, I solved my problem by adding:

blacklist agpgart  ", and"
blacklist intel_agp

to my /etc/modprobe.d/blacklist file, minus what I put in the quotes above, dont add the ", and" or else it won't work of course:)

---

### Post by jgv on 2006-07-08
Thanks for the feedback.

I have a very basic Dell computer -- basic graphics and sound cards that are standard on Dell machines.

As stated in my original posting, all was fine using Ubuntu 5.10 and even 6.06 worked till I enabled/disabled encription on the wireless router via the Ubuntu administration Networking GUI tool.  The computer has never rebooted since.

At no time have I ever manually edited any system configuration file.

I find this situation simply appalling.

---

### Post by muffinhead on 2006-07-08
Okay, so thats not your problem. Hopefully someone can help you, and find out what you need to do, to get it to work;)

I'm clueless as what your problem could be, so I probably can't help any more than I already did.

I wish I could help you more, I know what it's like to have a problem, and not get barely any replies or help, after bumping my thread continuously, I was able to finally get the help I needed, and my problem solved.

Good Luck getting it all to work again:D

---

### Post by jgv on 2006-07-08
Thanks for your reply.  I very much appreciate you taking the time to try to help.  Apparently, it is a difficult/unusual problem.  Happy computing.

---

