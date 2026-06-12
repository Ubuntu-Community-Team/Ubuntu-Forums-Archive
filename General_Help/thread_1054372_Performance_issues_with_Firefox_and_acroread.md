---
title: "Performance issues with Firefox and acroread"
date: 2009-01-29
forum: General Help
---

### Post by sharp11 on 2009-01-29
I'm running gutsy on a 900MHz system with 1G of RAM. It works basically okay, but Firefox is easily overwhelmed by heavy javascript. My biggest issue is that gmail runs slowly, esp. if I'm looking at a long thread. I recently used gmail on a friend's Mac and was astonished at how responsive it was -- it felt like a desktop app, not like what I'm used to (click and wait).

A similar issue with reading PDFs with acrobat. Small PDFs are okay, but larger ones are like little time machines that transport me back to the early days of desktop computing.

I am not convinced that more RAM will help. Thoughts?

---

### Post by clueless on 2009-01-29
I have 2 GB of RAM and have the same problems as you. Flash can consume all my RAM when viewing multiple tabs and acrobat is little responsive. I hope Adobe will start fixing those problems at some time, we've been waiting for years!

---

### Post by khedron on 2009-01-29
Regarding acroread, you could try a different pdf reader to see if it performs better.
Try installing kpdf or pdf-viewer.

---

### Post by sharp11 on 2009-02-07
Thanks for these suggestions. I have started to use evince for PDFs. It lacks some acrobat features that I like, but is much much faster.

---

### Post by Arjunanda on 2009-02-15
I'm using evince as well, but using gmail, facebook or youtube is a killer. These web apps cause firefox, galeon or epiphany to eat up all CPU, and even closing them is not much of help, as the Xorg will continue to eat up all the available resources for several minutes. For this reason, I cannot play any music on this computer, and should I want to answer a skype call, I have to close all my web browsers first. Othervise I'll be experiencing popping and clicking sounds, and dropped skype connections.

Should I re-install my system? I really hate doing that, as I have so much stuff and tweaks installed on my system. And yes, that may be contributing to the problem aswell.

Any ideas where to go?

---

### Post by binbash on 2009-02-15
You may want to switch to firefox 3.1b which is a lot faster than firefox 3.0.x . I had same problems with a speedy machine but after  the switch it was a lot faster

---

### Post by Arjunanda on 2009-02-15
I did a re-install of firefox, epiphany, galeon and Xorg. That made totally no difference. I have another laptop (#2), on which the same version of firefox runs nicely gmail, facebook and youtube, but that is a fresh install of 8.10. This #1 is upgraded from 6.10 through all versions to the latest.

I will give a try to the new version of firefox, as you suggested. But the strange thing here is: it does not matter which browser I'm using, all of them have the same problem.

Edit: I have installed 1.3b2 and testing it now.

---

### Post by Arjunanda on 2009-02-15
Ok, that seems to have solved the issues related to Firefox. This helps me to see that my problem is not only firefox, it is Xorg eating up 70% of CPU. It varies between Xorg taking 43-86% CPU, and then at times going down to 6%, while most of the time taking some 46-66%. Any ideas for this one? I will look for another thread..

---

### Post by binbash on 2009-02-15
Hmm if you are using compiz and have an ati card, you should look to this thread :

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by Arjunanda on 2009-02-15
Yes, I have ATI Radeon, and Compiz has been enabled, though at the moment it is disabled. Checking your link. Thanks :)

BTW, now my system looks more normal again - the 3.1b2 install did a big difference!

```
top - 14:26:09 up  3:49,  3 users,  load average: 0.40, 0.30, 0.43
Tasks: 127 total,   1 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us,  1.7%sy,  0.0%ni, 88.7%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:   1284088k total,  1245928k used,    38160k free,    22520k buffers
Swap:  1590424k total,     5004k used,  1585420k free,   376596k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                     
14195 user      20   0  393m 168m  31m S  7.0 13.4   6:08.24 firefox-bin                 
 5070 root      20   0  436m 171m  13m S  5.7 13.7  43:50.70 Xorg                        
 6830 user      20   0 88196  22m  12m S  1.3  1.8   0:31.54 gnome-terminal              
 5472 user      20   0 44872  11m 7776 S  0.7  0.9   0:11.04 scim-panel-gtk              
 5903 user      20   0  134m  57m  21m S  0.7  4.6  14:39.80 exaile                      
14920 user      20   0  2416 1156  876 R  0.7  0.1   0:09.44 top                         
 4797 chipcard  20   0  4660 1572 1156 S  0.3  0.1   2:06.85 chipcardd4                  
 5509 user      20   0 13960 4792 3608 S  0.3  0.4   3:09.64 at-spi-registry             
 5516 user      20   0 23996  14m 9684 S  0.3  1.2   0:47.77 metacity                    
 5677 user      20   0 98952  62m  12m S  0.3  5.0   3:40.72 skype                       
12169 user      20   0  353m 189m  81m S  0.3 15.1   2:37.12 soffice.bin                 
    1 root      20   0  1740  592  512 S  0.0  0.0   0:01.50 init                        
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                    
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                 
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.74 ksoftirqd/0                 
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.02 watchdog/0                  
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.46 events/0   
```

---

### Post by sharp11 on 2009-02-15
So it sounds like I need to finally upgrade from gutsy to hardy (otherwise I'm stuck with firefox 2.0.x.). I've been avoiding this, just afraid of getting bogged down in complications.

---

### Post by Arjunanda on 2009-02-15
> **sharp11 said:**
> So it sounds like I need to finally upgrade from gutsy to hardy (otherwise I'm stuck with firefox 2.0.x.). I've been avoiding this, just afraid of getting bogged down in complications.

Better you stay with hardy, if you don't have performance issues. For me that upgrade was a real bummer. And my performance issues are still not solved, 3.1b2 did not solve them. As soon as I start wrting reply to email, Firefox CPU load jumps to 70% and system remains unresponsive for about 5 minutes at a time. Really frustrating!

Do I really have to re-install the whole thing? This start to sound like a windows world! (Btw, ten years of active linux use behind..)

---

### Post by Arjunanda on 2009-02-15
> **binbash said:**
> Hmm if you are using compiz and have an ati card, you should look to this thread :

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Thanks for the link binbash, I checked it out. The instructions seemed so long, that I decided to uninstall entire compiz for now, as I want to solve this issue. And un-installing it did not help, the problem remains.

---

### Post by sharp11 on 2009-02-15
> **Arjunanda said:**
> Better you stay with hardy, if you don't have performance issues. For me that upgrade was a real bummer. 

Did you mean "gutsy"? Anyway, I do have performance issues, that was the point of this thread. 

I just completed the upgrade from gutsy to hardy (8.04), it seems to have gone quite smoothly. (Thank you, ubuntu team!!) (Fortunately I read about the [kernel version issue]("https://help.ubuntu.com/community/HardyUpgrades") before upgrading, so booted into 2.6.22-14 before upgrading, and had no issue with locales.)

Based on first impressions, firefox performance (3.0.6) is **much** better. Gmail is responsive and I was able to load one of those long NYTimes blog pages w/o a problem. 

There is hope! Cheers to all ...

---

