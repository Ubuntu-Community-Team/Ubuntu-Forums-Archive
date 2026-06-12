---
title: "[SOLVED] Intel P4 - CPU Throttling"
date: 2006-11-28
forum: Desktop Environments
---

### Post by wieman01 on 2006-11-28
Does anybody know a reliable CPU throttling program/applet for a **Intel Pentium 4** (3.0 GHz)? Support for **dynamic switching** would be perfect... The reason is that I am using my PC as a media center but most of the time it just sits there doing nothing. So a program controlling the CPU frequency would certainly help reduce power consupmtion.

Thanks!

---

### Post by wieman01 on 2006-11-29
Bump

---

### Post by tedrogers on 2006-11-30
Doesn't Ubuntu have a CPU speed control applet built in?

I think you can just add it to the panel. I don't know if it will switch dynamically though.

On my P4 3.06 Northwood, throttling/scaling is not possible - at least this is what the applet reports.

This is about all I know!

---

### Post by wieman01 on 2006-11-30
Alright... This is the answer I was looking for & expecting... Throttling is not possible on a Pentium 4. Interestingly that's is possible in Windows using a little tool called CPU Cool or others. Anyway, thanks for your help.

---

### Post by tedrogers on 2006-11-30
Correction...it's a 3.6 GHz Northwood...but still no scaling.

It can be switched to half speed (safe mode due to overheating) through the BIOS....but no software control as far as I know in Linux. Didn't know about CPU Cool in wind-blows. Maybe wine or alien?

---

### Post by wieman01 on 2006-11-30
Thought about the BIOS option, but then 3D will be severely impacted. So I guess that's not an option.

I would not want to use "wine" for critical (and low-level) applications such CPU Cool. So I'll do some more research & post the results IF I find anything usefule.

---

### Post by tedrogers on 2006-12-01
I understand, if you windows application layer were to crash (as it is still in development...and even then nothing is every really that stable!) then your CPU goes pop! :)

I would be interested if you find anything out about this.

---

### Post by wieman01 on 2006-12-08
I eventually found something here: [http://www.seismo.ethz.ch/linux/debian_software_installation.html]("http://www.seismo.ethz.ch/linux/debian_software_installation.html")

---

### Post by tedrogers on 2006-12-09
Yes....that would seem to be just the ticket....as long as you're not running VMWARE. From what I read on the link there is a problem with this when the cpu stayed in it's low-power state at 300mhz and didn't throttle up to 3ghz.

Glad you found something to help though.

---

### Post by wieman01 on 2006-12-09
I don't seem to have the problem with the low-power state. But apparently my CPU only support 3 states:
> 2250000 2625000 3000000
I reckon this is a hardware restriction... My P4 (3.0 GHz) does not seem to support other any state below 2.25 GHz.

---

### Post by tedrogers on 2006-12-10
Just a thought...but my ASUS mainboard has some throttling software that can adjust many speed factors including RAM and CPU. Perhaps there is a debian version of similar software for your mainboard? Try the manufacturer website maybe.

---

