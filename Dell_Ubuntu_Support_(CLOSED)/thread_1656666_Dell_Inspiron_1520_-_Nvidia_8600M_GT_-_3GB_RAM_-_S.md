---
title: "Dell Inspiron 1520 - Nvidia 8600M GT - 3GB RAM - Slow performance"
date: 2010-12-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sherbieny on 2010-12-31
Hello,

Please find Attached for my system info:

I'm using an 80GB partition of 320GB HDD for Ubuntu10.10

after I installed Compiz and generic-headers-24 performance is low

even if I disable effects still things are slow

when I open application menu the Icons appear after the words 

when I open any explorer it takes time

Any video keeps lagging and glitching on MoviePlayer or VLC

Notes:
** I noticed I have two compiz managers 
1) CompizConfig settings manager
2) Simple CompizConfig settings manager
if this is wrong how can I remove Simple CompizConfig

** I activated the nvidia driver from additional drivers and then installed Compiz, I DIDNOT download external driver from nvidia.com because last time I did this ubuntu went to tty1 then Windows 7 went black then the whole HDD died and I got every thing from scratch again with a new 320HDD and I installed XP and Ubuntu again :D


Is my laptop weak for ubuntu and compiz?
or where is the problem?

---

### Post by mikewhatever on 2011-01-02
Question: Why did you have to install the 'generic-headers-24' and compiz packages? Both should have been installed by default, unless you have a custom installation.
Another possible cause may be your root partition. Contrary to what you've said, Ubuntu is not on an 80GB partition. According to the screenshot you posted, root and home are separate, and the root partition is 71% full. Do you, by any chance, notice excessive of disk activity?

---

### Post by sherbieny on 2011-01-07
generic-headers-24 was installed automatically 
and I installed compiz to enable custom effects 

I dedicated 10gb to the root as I was told to do that on this forum so that when I want to upgrade or re-install I won't lose the data 

should I make the root and home are the same

---

