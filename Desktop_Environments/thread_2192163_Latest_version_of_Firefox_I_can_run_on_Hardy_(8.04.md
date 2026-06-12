---
title: "Latest version of Firefox I can run on Hardy (8.04)"
date: 2013-12-06
forum: Desktop Environments
---

### Post by mister_p_1998 on 2013-12-06
I dont want to go into why Im still running my outdated version of Ubuntu, but could anyone tell me whats the latest version of Firefox I can run on it? Im on Firefox v5.0. Yeah I know, the OS runs sweet, but Firefox is really starting to creak.

---

### Post by tgalati4 on 2013-12-06
Try installing the latest from [http://mozilla.org](http://mozilla.org).  It will install it to your home directory so that you will now have 2 copies of firefox, your old version and the latest (Version 25).  To run it, you can create a launcher to point to the local firefox.

Or, open a terminal:

```
cd
./firefox/firefox
```

Take note of error messages in the terminal.  I think I have version 23 running on an old Jaunty machine, so I know it is possible.  You can't do the same with Google Chrome, because of dependencies and how Chrome is packaged.

---

### Post by Dennis N on 2013-12-06
I have Firefox 16.0.2 in use on a Ubuntu 8.04 system. Firefox 17 should work as well. Versions 18 or later won't work because of the higher gtk+ version required for those.

---

### Post by mister_p_1998 on 2013-12-06
> **Dennis N said:**
> I have Firefox 16.0.2 in use on a Ubuntu 8.04 system. Firefox 17 should work as well. Versions 18 or later won't work because of the higher gtk+ version required for those.

Thanks Dennis,
Thats exactly the kind of reply I was hoping for, I get so sick of the 'you've GOT to upgrade to the latest distro!' comments.
Apart from the old version of Python that doesnt run the scripts I use (I do it on my Raspberry Pi) this is the first problem I've come across with running Hardy.

Steve

---

### Post by mister_p_1998 on 2013-12-09
Running v17 now, Wow! what speed!
V5 just sat there timing out half the time, I thought it was my router and restarted it a few times, but it seems it was the old Firefox. Superfast now on the 100mb fibre!!

Steve

---

### Post by whatthefunk on 2013-12-09
Running an unsupported browser on an unsupported OS?  Have fun....

---

### Post by buzzingrobot on 2013-12-09
> **whatthefunk said:**
> Running an unsupported browser on an unsupported OS?  Have fun....

Not something that I would do.  But, if potential security issues don't worry someone, then software that works will continue to work. (Although old code on new hardware will probably run slower than new code on new hardware because it can't leverage the new hardware capabilities.)

Risk can be mitigated, somewhat, by using a current kernel and manually installing newer versions of libs, apps, etc.  The latter is eventually limited, though, by the versions of core components like GTK, python, etc, whose replacement would amount to building a new distribution.

---

### Post by mister_p_1998 on 2013-12-12
> **whatthefunk said:**
> Running an unsupported browser on an unsupported OS?  Have fun....

Behind a hardwired firewall, Noscript, flashblock, Adblock, Image  Block, BlockSite and Ghostery, Java disabled, I think I've got it covered guys...

Around 95% of this machines time is running unattended, only use firefox on it 2 hours max a day...

---

### Post by kansasnoob on 2013-12-12
> **mister_p_1998 said:**
> Behind a hardwired firewall, Noscript, flashblock, Adblock, Image  Block, BlockSite and Ghostery, Java disabled, I think I've got it covered guys...

Around 95% of this machines time is running unattended, only use firefox on it 2 hours max a day...

With that old of a kernel I think you're seriously at risk, but it's your risk not mine or anyone else's ;)

---

### Post by mister_p_1998 on 2013-12-13
Its behind a Hard firewall & a soft one, I've been running Various Ubuntu's for 7 years, with zero problems. I dont see what the problem is with an old kernel. Still better than XP or Win7.

---

### Post by buzzingrobot on 2013-12-13
> **mister_p_1998 said:**
>  I dont see what the problem is with an old kernel.

Old kernels do not contain patches created to thwart potential attacks discovered since that kernel's release. Ditto any software. 

Being vulnerable to a threat because of an older kernel doesn't mean you'll be a victim, of course.  And the firewalls, etc., you use provide a degree of protection.

Skilled users can add patches to kernels. (The kernel in RHEL is still labeled as a 2.6 series kernel, but Red Hat keeps it updated by backporting patches.)

Newer hardware often performs better with newer kernels, too.

---

### Post by whatthefunk on 2013-12-14
After 10 seconds of Googling:
These security updates are only a small portion of those that you are missing: [http://threatpost.com/firefox-24-patches-17-security-vulnerabilities/102335](http://threatpost.com/firefox-24-patches-17-security-vulnerabilities/102335)
Small list of kernel vulnerabilities youre exposed to: [http://www.linuxtoday.com/infrastructure/2012011200639NWKN](http://www.linuxtoday.com/infrastructure/2012011200639NWKN)

I dont want to get into an argument (its your computer after all) but most computer problems arise from unsafe user practices, one of which is running out-of-date software.  Changing your OS could save you a massive headache in the future.  Anyway, Im done here.  Best of luck to you.

---

