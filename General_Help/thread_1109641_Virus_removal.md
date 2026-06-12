---
title: "Virus removal"
date: 2009-03-28
forum: General Help
---

### Post by THdragon on 2009-03-28
I currently have Viruses on my hardrive and various other places on Ubuntu.

What program can remove the viruses or how can i remove them?

(Yes, I'm a noob)

---

### Post by jo4hnc on 2009-03-29
Clam AV. Go to Accessories>add/remove and look for virus scanner.

---

### Post by THdragon on 2009-03-29
> **jo4hnc said:**
> Clam AV. Go to Accessories>add/remove and look for virus scanner.

I just got the error when I tried to download it.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by gmatt on 2009-03-29
Wow, how do you get viruses under linux? I thought they didn't exist, or at least were very very rare. From my understanding, most viruses under linux are simply experimentations and not intended to spread, you would have to explicitly search it out on the web, download it and run it.

---

### Post by THdragon on 2009-03-29
> **gmatt said:**
> Wow, how do you get viruses under linux? I thought they didn't exist, or at least were very very rare. From my understanding, most viruses under linux are simply experimentations and not intended to spread, you would have to explicitly search it out on the web, download it and run it.

Well....things have been happening to my comp, such as errors when booting as well as audio suddenly going off, making me have to restart my comp. I tried running a virus scan on my XP OS but it showed that there were no viruses.

---

### Post by spike_naples on 2009-03-29
> **THdragon said:**
> Well....things have been happening to my comp, such as errors when booting as well as audio suddenly going off, making me have to restart my comp. I tried running a virus scan on my XP OS but it showed that there were no viruses.

Download ClamAV. It is just about the only one for Ubuntu as these types of programs are not really essential for Linux/Ubuntu.

Or you might have a hardware problem that is surely bound to get worse... If later on that you just can't boot up anymore you might want to suspect and accept that it is a hardware problem.

---

### Post by spike_naples on 2009-03-29
> **THdragon said:**
> Well....things have been happening to my comp, such as errors when booting as well as audio suddenly going off, making me have to restart my comp. I tried running a virus scan on my XP OS but it showed that there were no viruses.

You might have hardware problems. Virus attacks in Linux, Ubuntu for this matter is one in a billion. Go check your hardware configuration. Consider also the age of your equipment. They are bound to conk out after at least 3 years of daily use.

I had a similar experience where I found out that my motherboard was the culprit. I replaced it and got my Ubuntu running back to better (faster as it was a newer mobo) than normal.

Cheers! Hope this helps you.

---

### Post by jo4hnc on 2009-03-29
> **THdragon said:**
> I just got the error when I tried to download it.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

You might want to go into Synaptic and see if you can get it there. In the search box on the top type in clam. When you get clamav also get clamtk. It's the user interface for the program.

---

### Post by gmatt on 2009-03-29
> **THdragon said:**
> Well....things have been happening to my comp, such as errors when booting as well as audio suddenly going off, making me have to restart my comp. I tried running a virus scan on my XP OS but it showed that there were no viruses.

A virus scan under windows won't identify a virus under linux (unless the software explicitly says it will.) The converse is also true. Most likely the underlying cause is not a virus, as viruses under linux are exceedingly rare (but not impossible.) Please attach the file found on your computer at ```
/var/log/dmesg
``` People might figure out whats wrong just by looking at that. Refrain from making any hasty conclusions.

---

### Post by SunnyRabbiera on 2009-03-29
Yeh slowdowns and such in ubuntu are not viruses, there are no real viruses out there for linux (a good percent of them are concept though, most are non threats) that Ubuntu can fully contract because it disables the root account.
I would report the issues you have to us and we will see if we can fix them, there are a few bugs here and there on Ubuntu but most can be fixed.

---

### Post by THdragon on 2009-03-29
Well......when booting and closing down the comp, I get this:

usb 3-1 device descriptor read/64, error -110 

There are various numbers that appear before this in brackets. It also happens multiple times before ubuntu is booted or closed.

---

### Post by dcstar on 2009-03-29
> **THdragon said:**
> I just got the error when I tried to download it.

E: dpkg was interrupted, you must manually run **'dpkg --configure -a'** to correct the problem. 
E: _cache->open() failed, please report.

Then do what the system explicitly tell you to do:

```
sudo dpkg --configure -a
```

---

### Post by mb_webguy on 2009-03-29
Viruses on Linux are essentially non-existent.  You likely have a better chance of winning the lottery than you do of getting a virus on Linux.  Only a few dozen Linux viruses have ever been identified, and most of these were created in a lab as proofs-of-concept.  And security patches to the Linux kernel tend to be released fairly swiftly once a virus is identified. 

However, if you perform a virus scan using ClamAV or some other virus scanner, it's entirely likely you'll find some "viruses".  This doesn't mean you're actually infected.  Virus scanners scan for Windows viruses as well, and if you've downloaded a file that contains a Windows virus (which can't infect Linux), it will show up in a virus scan.  Furthermore, the occurrence of false positives are fairly high.  

Your problems are almost certainly not virus-related.  Errors when booting or problems with sound are likely either system configuration problems or hardware failures.

---

