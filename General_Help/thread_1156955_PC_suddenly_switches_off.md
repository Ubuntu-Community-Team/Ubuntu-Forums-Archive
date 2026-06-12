---
title: "PC suddenly switches off"
date: 2009-05-12
forum: General Help
---

### Post by dhruv_parekh on 2009-05-12
Hello Ubuntu users,

From last 5 days I'm facing weird problem in Ubuntu 8.10.
I had read a review of new Desktop Environment called Enlightenment, and wanted to install it in Ubuntu 8.10. 
I've downloaded all source files into my home folder.
Then I tried to run script called "autogen.sh" and after half minute my PC suddenly switched off. I thought that there may be some RAM or over heating problem. So, I cleaned up my CPU thoroughly and again tried to run that script. Got same problem, it switched off again after half minute. Then I restart my PC and switched to Win XP Pro. I waited for 1 and half hour. Meanwhile I was doing really heavy work in XP (1026 lines of Java code compiling, watched piece of movie in VLC player and surfing). I did these things all together. And nothing happened in XP. 

My Machine Config. is as below :
  1) M/B : ASUS P5GVC-MX VIA P4M800 Chipset
  2) RAM : 512 MB Trancend 553 Ghz DDR2
  3) HDD : Samsung 180 GB SATA
  4) OS  : Ubuntu 8.10 (GNOME) & Windows XP Pro (Dual partition)
  5) CPU : Intel Dual Core 2.06 GHz
  6) Others : Sound Card, Graphics Card and LAN Card built-in with ASUSU M/B

Please tell me What's wrong with my PC/Ubuntu? :confused:

---

### Post by dhruv_parekh on 2009-05-12
I forgot to add one more point. I tried to check memory status using Boot loader's "Memtest86" option. It again switched off after one minute. But XP works fine.

---

### Post by cdenley on 2009-05-12
> **dhruv_parekh said:**
> I forgot to add one more point. I tried to check memory status using Boot loader's "Memtest86" option. It again switched off after one minute. But XP works fine.

If it happens with ubuntu and memtest86, then it's definitely a hardware problem. Not sure why it hasn't happened in XP yet. Are you sure all your fans are working (CPU, power supply)?

---

### Post by dhruv_parekh on 2009-05-12
yeah, everythings are working fine. Ther are three fans on my CPU.
First installed on Chip (Intel), Second in PSU and third one is in cabinate.
If it is H/W problem then why my PC doesn't switch off during heavy process in XP?

---

### Post by cdenley on 2009-05-12
> **dhruv_parekh said:**
> If it is H/W problem then why my PC doesn't switch off during heavy process in XP?

I said I don't know, but memtest86 and ubuntu have no software in common, so it can't be a software problem.

---

### Post by dhruv_parekh on 2009-05-12
Okay, 

But when I do nothing on Ubuntu, it remains for long time (untill i manually switch it off or shut it down).

---

### Post by El Zoido on 2009-05-12
Hm, I guess if it is e.g. a memory problem then "doing nothing" in Ubuntu is not demanding enough memory to cause the problem that shuts down your pc.

I'd say do a memtest, but you already tried that ;)

---

### Post by dhruv_parekh on 2009-05-12
> **El Zoido said:**
> Hm, I guess if it is e.g. a memory problem then "doing nothing" in Ubuntu is not demanding enough memory to cause the problem that shuts down your pc.


Yeah,
exactly what I'm assuming. Just tell me one thing, how much memory requires for GNOME desktop? 512 MB is enough for it? B'cause when I develope some jsp pages on Netbeans 6.5 in Ubuntu it usually consume lots of memory (some times i have to wait for atleast 1 minute to view my changes in Netbeans). So, my point is does GNOME eats lots of memeory compare to any other Desktop Env. ?

---

### Post by cdenley on 2009-05-12
Just to make sure, you said that while running memtest86, your computer shut off for no reason, correct? It certainly sounds strange. I would say it was an overheating problem, except XP worked fine under heavy load. Typically, a memory or hard drive problem would cause an error or make the system hang, but not shutdown the computer. Also, memory problems are almost always random, and don't happen one minute after a certain action. If your computer shuts off, it is because the motherboard is turning it off for some reason (power switch, overheating failsafe, software ACPI), or the motherboard is not getting enough power from the power supply. Do you have a speaker connected to your motherboard? Does it make any sounds when it shuts down?

I think gnome requires more memory than kde or xfce. However, I'm pretty sure having insufficient memory would not cause your system to shutdown, especially while running memtest86.

---

### Post by dhruv_parekh on 2009-05-12
> **cdenley said:**
> Do you have a speaker connected to your motherboard? Does it make any sounds when it shuts down? 


Yeah, I've pair of speakers connected with CPU and it doesn't make any sound when PC shuts down. 

> **cdenley said:**
> 
I think gnome requires more memory than kde or xfce. However, I'm pretty sure having insufficient memory would not cause your system to shutdown, especially while running memtest86.

Hmm, you are right. 
OK, Then I'll re-check all H/W components, and get back to this forum.

Thanx a lot guys, for showing interest in my problem. :)

---

### Post by El Zoido on 2009-05-12
> **dhruv_parekh said:**
> Yeah,
exactly what I'm assuming. Just tell me one thing, how much memory requires for GNOME desktop? 512 MB is enough for it? B'cause when I develope some jsp pages on Netbeans 6.5 in Ubuntu it usually consume lots of memory (some times i have to wait for atleast 1 minute to view my changes in Netbeans). So, my point is does GNOME eats lots of memeory compare to any other Desktop Env. ?

512 MB should be the reccomended minimum erquirement for Ubuntu 9.04.
However, if you have more than that the OS will make use of it of course. On systems with less memory swap-usage will be higher as the OS has to use the hard-drive to buffer memory.
I don't know about the memry usage of gnome compared to kde or other environments.

---

