---
title: "Gray screens and lag?"
date: 2009-01-07
forum: General Help
---

### Post by fiel on 2009-01-07
I'm not sure why this happens (especially in FireFox), but when I'm using FireFox or programming in Eclipse I start to experience considerable lag.  At times things will lag heavily and the screen will go gray.

Does anyone know a way to resolve this?  

I have 1GB of RAM, but can having a swap space of 2GB be bad?

---

### Post by Yashiro on 2009-01-07
Uninstall any and all Flash plugins and see how that goes.

---

### Post by fiel on 2009-01-08
> **Yashiro said:**
> Uninstall any and all Flash plugins and see how that goes.

Already did, but still no luck.

---

### Post by Yashiro on 2009-01-09
Have you removed nspluginwrapper also?

---

### Post by mssever on 2009-01-09
> **fiel said:**
> I have 1GB of RAM, but can having a swap space of 2GB be bad?
Check your memory usage to find out if RAM or swap is your problem. I like htop for this purpose. In general, the more swap (within reason), the merrier. If you're slowing down due to excessive swapping, you'll see a lot of telltale disk activity.

I think it's more likely that some program is misbehaving and/or consuming all available CPU. Several Firefox plugins and extensions can cause those kinds of problems (I have a whole lot more trouble with the acroread plugin than the Flash plugin), and it sounds like something's going on with Eclipse, too. However, I don't use Eclipse, so I can't help you there.

---

### Post by fiel on 2009-01-09
Well the only thing I have enabled in FireFox is Shockwave Flash.  But in either case, I noticed the swap space isn't in great demand, but my CPU usage spikes up to 100%.

---

### Post by Yashiro on 2009-01-09
When it bugs out check 'System Monitor'.
Which process is using your cpu time.

[COLOR="Silver"]I'm guessing npviewer.bin[/COLOR]

---

### Post by allisonp166 on 2010-08-25
I am seeing a similar behavior.

System is a P4/2gb ram and nominally never shows swap usage.  Ran fine under 9.x
version and after upgrade to 10.4 It does this once ever 4-6 days, it varies..

Symptom graying of firefox, erratic slow  mouse, cannot open terminal or monitor without waiting several minutes.   While this is going on the system will be accessing the disk.
If I'm lucky to get a terminal open and run top from root I see the system consuming 
100% cpu and eventually 100% of available swap 1092380K!  Ram usage typically runs
719584K.  there is so specific task showing 100% or near that cpu utilization.

Once the swap burning is done the system becomes responsive again but noticeably slower until I shutdown and reboot.  Nominally the system is never shutdown save for maintenance or to reboot past this swap strangeness. 

Thoughts, info needed?

Allison

---

