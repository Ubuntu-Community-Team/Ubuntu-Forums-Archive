---
title: "Sansa fuze refuses to connect via usb 2.0 AND where did ehci_hcd module go?"
date: 2009-05-05
forum: General Help
---

### Post by ninotsmindelivar on 2009-05-05
Sorry to revamp a closed thread, but this is persisting in the release version of jaunty, out of beta. 

I recently updated to the jaunty and discovered some problems that I hadn't seen in intrepid with my sandisk sansa fuze mp3 player -- it was mounting exclusively via usb 1.1 (or so the transfer speeds and lsusb reported).

Now, I know I can get usb 2.0 speeds, as my various pendrives, my girlfriend's ipod nano, and my WD Passport drive all mount via usb 2.0, according to the perceived speed and lsusb's report. Still, the sansa fuze will only connect over usb 1.1, unless the fuze was plugged in and THEN the computer booted.

BUT... 

There used to be a different workaround if you're already loaded of unloading and reloading the usb 2.0 ehci_hcd module (sudo rmmod ehci-hcd; sudo modprobe ehci-hcd). 

So I tried this as I used to do on intrepid and seem to find that although my various non-sansa devices connect via 2.0 and get those speeds, ehci-hcd isn't present on my system....?

this is the terminal output if I try to unload/reload the module:


Quote:
rodya@rodya-laptop:~$ sudo rmmod ehci_hcd
[sudo] password for rodya: 
ERROR: Module ehci_hcd does not exist in /proc/modules

rodya@rodya-laptop:~$ sudo modprobe ehci_hcd
FATAL: Module ehci_hcd not found.  

Where did ehci_hcd go, and if it's no longer managing usb 2.0, what is?

Any help? Let me know if you need more info to figure this out. I'm surprised at the relative quiet about this -- aren't there a number of us fuze owners out there, being that sandisk reports linux support?? :)

Hoping to get a conversation together here to figure this out or at least hear what info I need for this to file a bug report, and likely with which component it should be filed. 

Or has this been fixed already??? Thanks!

Thanks in advance!

---

### Post by ninotsmindelivar on 2009-05-05
No ideas? Trying to deduce where the problem is and even HOW/where to report it.

---

### Post by wiijii on 2009-05-11
I'm having the same issue with a Sansa clip. 

Is the ehci_hcd module now compiled directly into the kernel?! 

I have no solution but just a note to say this seems a reasonably widespread issue - I don't think the Sansa players were the only devices that needed an unload/reload of the ehci_hcd module to get them working at USB2 speeds. 

Thom

---

### Post by ninotsmindelivar on 2009-05-11
> **wiijii said:**
> I'm having the same issue with a Sansa clip. 

Is the ehci_hcd module now compiled directly into the kernel?! 

I have no solution but just a note to say this seems a reasonably widespread issue - I don't think the Sansa players were the only devices that needed an unload/reload of the ehci_hcd module to get them working at USB2 speeds. 

Thom

hmm, looks like ehci_hcd IS now a part of the kernel. Great. No more rmmod...

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710)

This is pretty lousy -- stuck choosing between ext4 and usb 2.0. I'll probably keep the speed offered in getting access to ext4, but this is a huge shame. 

Perhaps I'll go get one of those 16gb microsdhc cards so I don't have to sync my stuff often, just keep it all on the player... 

But really, why can't we find the error here? :(

---

### Post by ninotsmindelivar on 2009-05-21
In troubleshooting an unrelated issue with ext4, I discovered that using the most recent 2.6.29 generic kernel from the ubuntu mainstream kernel repo, this issue is fixed. So, the issue lies either in some of the Ubuntu patches (somehow I doubt, considering that other distros have this issue), or in the 2.6.28 and earlier kernels across the board. 

If you don't need any of the ubuntu proprietary driver patches on your computer, then this might be a good option to upgrade to 2.6.29. Presumably (and hopefully) this will remain fixed when/if jaunty puts out its own flavor of the 2.6.29 kernel in the repos.

---

### Post by icheyne on 2009-06-20
I wrote some Sansa Clip instructions [here]("https://help.ubuntu.com/community/SansaClip"). Let me know if they work for the Fuze.

---

### Post by e.m.fields on 2009-11-22
> **icheyne said:**
> I wrote some Sansa Clip instructions [here]("https://help.ubuntu.com/community/SansaClip"). Let me know if they work for the Fuze.

Hi guys. 
I haven't been able to get Ubuntu to detect my Sansa Fuze.  Have any of you found a solution yet?

@ icheyne: Thanks for posting those instructions to the wiki, people really need to do more of that instead of wasting all this energy on the forums.  The instructions for the Sansa clip didn't work for the Fuze.

If someone finds a solution, please repond and I'll put it on a "Solved" thread.

---

### Post by brodiewells on 2010-06-24
I was having all kinds of problems mounting mine.  I just found that if I re-format from the device it works.

---

### Post by forbajato on 2010-12-02
I just went into the settings mode on the Fuze and set USB mode to MSC and that seems to have worked.

forbajato

---

