---
title: "Performance Issues 2"
date: 2009-05-24
forum: General Help
---

### Post by Vors on 2009-05-24
Hello everybody!
The problem is that after a little uptime (about 3-10 hours), memory used as cache reaches 70-80% of all memory. With 20-30% used by programs it is 100% and this situation slow down the PC. Every operation is delayed.
Or for example i run linuxdc++ and start hashing folder. The memory used as cache grows extrimely fast and problem appear even earlier.


The second problem is that it seems the linux does not allow motherboard to overclock CPU. i've got celeron dual-core E1200@1600Mhz. It works stable on 3200. But after i boot linux it become 1600mhz again. Linux does not allow to use overclocked hardware?

Help please!

---

### Post by XCan on 2009-05-24
From your screenshot it appears like you're not using that much memory at all. In fact it looks like you're using 378 MB of memory (look at the row -/+ buffers/cache), so I don't think memory is an issue considering you have 2 GB of memory.

Your second question I'm not sure what you mean. How did you check the clock frequency in Ubuntu? As a matter of fact, most tools only look at the file /proc/cpuinfo, which does not reflect the true frequency of your CPU, it only reflects the factory standard set frequency. For example, my CPU is overclocked to 2.53 GHz but according to cpuinfo it's running at 2.13 GHz.

---

### Post by lovinglinux on 2009-05-24
> **Vors said:**
> Hello everybody!
The problem is that after a little uptime (about 3-10 hours), memory used as cache reaches 70-80% of all memory. With 20-30% used by programs it is 100% and this situation slow down the PC. Every operation is delayed.
Or for example i run linuxdc++ and start hashing folder. The memory used as cache grows extrimely fast and problem appear even earlier.

I have the same problem posted [here](http://ubuntuforums.org/showthread.php?t=1166437) (includes a dirty workaround), but no one answered yet. I don't think there is a solution or maybe nobody fully understands this, because the answers are always the same. In most of the threads I have searched about this issue, people will argue that unused memory is wasted memory and that Linux memory management is excellent. While I do agree that memory should be used, I prefer to waste memory and have a more responsive system. I think this is a real issue and I really would like to know a solution. For example, would it be possible to limit the memory used by cache?

---

### Post by Vors on 2009-05-24
Thx for answers.
The second problem seems not to be :) It seems that i forgot to overclock the CPU :)))
About the first: since i've post the first message, there is no slow down even when the usage of memory (with cache) reaches almost 100%. So.. i don't know what to think :)

---

### Post by Vors on 2009-05-25
[XCan]("http://ubuntuforums.org/member.php?u=358759") i found how to check cpu clock. use default gmome panel applet "cpu clock change monitor". it shows real value.

---

### Post by Greenwidth on 2009-05-25
> **Vors said:**
> About the first: since i've post the first message, there is no slow down even when the usage of memory (with cache) reaches almost 100%. So.. i don't know what to think :)


Unlike windows, Linux does not wipe the RAM when you stop a process, so it is available quickly if the process is restarted as it is loading from RAM rather than the HDD. 

If the memory is needed for a different process, the cached RAM is reallocated accordingly.

---

### Post by moster on 2009-05-25
For graphic presentation of CPU, GPU, etc clock install from synaptic Sysinfo, and for quick info from terminal just type > sudo dmidecode --type processor

Sorry, for that cache problem, I do not know WTF is that :)

---

### Post by XCan on 2009-05-25
> **Vors said:**
> [XCan]("http://ubuntuforums.org/member.php?u=358759") i found how to check cpu clock. use default gmome panel applet "cpu clock change monitor". it shows real value.

Kewl. But I can't find "cpu clock change monitor" in mine (not in synaptics either). The only thing I found was an applet called "CPU frequency scaling monitor", and that guy still only shows my factory standards. :(

---

### Post by lovinglinux on 2009-05-25
> **Greenwidth said:**
> Unlike windows, Linux does not wipe the RAM when you stop a process, so it is available quickly if the process is restarted as it is loading from RAM rather than the HDD. 

If the memory is needed for a different process, the cached RAM is reallocated accordingly.

That's my problem. I don't know the reason, but maybe this reallocation is slow. When there is enough free memory my system runs normally, but when memory is mostly used by the cache, I loose performance.

---

### Post by Greenwidth on 2009-05-25
I have not tried this:

HOWTO: Clear filesystem memory cache
[http://ubuntuforums.org/showthread.php?p=3882342](http://ubuntuforums.org/showthread.php?p=3882342)

---

### Post by lovinglinux on 2009-05-25
> **Greenwidth said:**
> I have not tried this:

HOWTO: Clear filesystem memory cache
[http://ubuntuforums.org/showthread.php?p=3882342](http://ubuntuforums.org/showthread.php?p=3882342)

Thank you. Here is the command:

```
sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

I tried so many commands, but this is the only one that really works. Thanks again.

---

### Post by Vors on 2009-05-26
Oh, great! if the problem appears again I will know what to do.
XCan, sorry i've got russian localisation, i translate it as i can, and as i guess pretty exactly.
u can see the icon of the applet in attachment. maybe it can help.

---

### Post by XCan on 2009-05-26
> **Vors said:**
> Oh, great! if the problem appears again I will know what to do.
XCan, sorry i've got russian localisation, i translate it as i can, and as i guess pretty exactly.
u can see the icon of the applet in attachment. maybe it can help.

Thanks for the attachment! We are indeed running the same app. Perhaps I misunderstood your first question. Are you referring to the function of AMD's CPUs Cool n' Quiet or do you mean overclock as in increasing its speed above factory settings?

---

### Post by Vors on 2009-05-26
I mean overclock as overclock :) 
increasing above factory settings

---

