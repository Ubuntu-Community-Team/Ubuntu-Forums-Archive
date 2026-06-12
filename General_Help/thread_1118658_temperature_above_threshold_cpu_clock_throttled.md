---
title: "temperature above threshold cpu clock throttled"
date: 2009-04-07
forum: General Help
---

### Post by anjanesh on 2009-04-07
My office PC has shut down twice.
Now, whenever I switch on my PC, I get this msg briefly (after grub loader)
```
temperature above threshold cpu clock throttled
```

I switched computers too - just moved the hard-disk and wireless network card to the new one.
Could this be because of the power supply ?

Ubuntu 8.10 x86_64 | Intel Pentium D

Thanks

---

### Post by 3Miro on 2009-04-07
Boot and go into the BIOS. There should be a PC Health section that lets you see the temperature of the CPU. Overheating is a hardware not Ubuntu problem.

Check to see if all the fans are working properly. Have you removed the CPU, perhaps it wasn't installed properly.

---

### Post by recallfx on 2009-12-12
Hello. Just recently I had some experience with this message. Indeed the problem was clogged CPU fan with excess of dust. Unfortunately, for normal user there was only symptoms:

dd process taking most of the CPU cycles and fast decrease of free space on root partition, until no free space left and system freeze.

I see two problems concerning Ubuntu OS:
 First: message about CPU clock throttling was generated several hundred times a second so syslogd was very busy picking it up.

Second and most important: there was no notification for simple user about CPU temperature above threshold.

Should I report it as a bug?

---

### Post by waggingtail on 2010-04-02
> Hello. Just recently I had some experience with this message. Indeed the problem was clogged CPU fan with excess of dust. Same here.

> Unfortunately, for normal user there was only symptoms:
dd process taking most of the CPU cycles and fast decrease of free space on root partition, until no free space left and system freeze. In my case, computer became slower and slower over time and I thought it was because Ubuntu added more complexity via GNOME over time - or that I was probably not quite sharp in observing timing etc. etc. To think that dust on the CPU fan heatsink would slow down the computer noticeably is actually quite a long shot, IMO.

>  I see two problems concerning Ubuntu OS:
First: message about CPU clock throttling was generated several hundred times a second so syslogd was very busy picking it up. Several times per second in my case.

>  Second and most important: there was no notification for simple user about CPU temperature above threshold. Except while booting ... which cannot be associated with dust on the CPU fan heatsink if you are not knowledgeable

Obviously there should be a notification. Google is great, but computer-speed-to-heatsink-dust is not an obvious link to end users. 

> Should I report it as a bug? Ideally we should, but I doubt they would accept it as a "bug".  "It is a hardware problem", after all. 

We could probably ask very politely for a feature request and then they **might** consider it.

---

