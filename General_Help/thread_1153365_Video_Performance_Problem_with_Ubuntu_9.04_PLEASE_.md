---
title: "Video Performance Problem with Ubuntu 9.04 PLEASE HELP"
date: 2009-05-08
forum: General Help
---

### Post by pjmed on 2009-05-08
Hello Everyone.

I am having some problems with the performace of my laptop running Ubuntu 9.04. Please not that I am new to Linux (and Ubuntu) since I have been using Windows all my life. I always wanted to try Linux and have been considering Ubuntu for a while now. I finally decided to jump in and give it a go. My knowledge of Linux ranges from very limited to non existant. Having said that I will start by explaining what hardware I have. I am currently writing this post from my laptop running Ubuntu 9.04. I have a Sony VAIO VGN-S260. For those unfamiliar with the hardware it has a Pentium M 1.7mhz, 1 gig of RAM and a ATI Mobility Radeon 9200. This laptop runs XP Pro smoothly. I also installed recently the Windows 7 RC which also ran smoothly (without AERO) so I am assuming it will run Ubuntu well, correct??? Here is the information about the graphic card and chipset straight from the terminal.

$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] [1002:5c61] (rev 01)


My problem.
I actually have several problems but the biggest one is the performance. Everything seems to be detected and working but performance with Visual Effects turned on is somewhat jumpy and slow with window tearing. Performance with VE turned off is better but still not smooth with some tearing and jumpiness (is that even a word? jumpiness) Also the laptop seems to be running very warm compared to when it is running windows. I have tried reading and doing some research but still cannot find the solution. Here is what I have noticed so far which I hope helps. Please keep in minde that I know nothing about linux or Ubuntu. I installed the CPU Frequency monitor on the upper taskbar or panel. I also added the system monitor to the upper panel so I have 3 small windows showing me the CPU usage percentage, memory and network. Monitoring these Ihave noticed certain things which might help you experts to diagnose my problem. I have noticed that CPU usage goes way up (80 to 100%) when all I have up is Firefox and I scroll up a down a page quickly. This also happens if I grab a window and move it quickly around the screen. Not only does the CPU usage goes up to 100% but the CPU Frequency monitor increases the speed of the CPU to maximun. Like I said I don't know anything about linux but this would suggest to me that the CPU is rendering everything thru software instead of using the ATI card. This would explain the poor performance and the very warm laptop surface. Also the CPU usage is many times at around 30% when Firefox is open and just sitting there (which again would explain the temperature since the CPU seems to be working too much all the time) I don't know where should I look to see what drivers I have installed but I guess it is under SYSTEM/ADMINISTRATION/HARDWARE DRIVERS (if this is the incorrect place let me know) but when I open this aplication it just says "Looking for drivers" and then it states that no propietary drivers are being used in this system. Anyway I would like to know what the experts think and would really appreciate any help I can get. I will be online for a while so I can aswer any questions or give you any extra information I might have missed and you deem necesary. Thanks in advance.

---

### Post by spiderbatdad on 2009-05-08
I have seen a bug report that suggests loading the module sony_acpi with modprobe to fix certain issues...presumably:```
sudo modprobe sony_acpi
```Beyond that, there may be boot parameters that make ubuntu run better on your hardware. If you read through dmesg, you might see suggestions like: "try using acpi=off" Or "try using lapic." Output dmesg to your desktop ```
dmesg > ~/Desktop/dmesg.txt
```

---

### Post by pjmed on 2009-05-08
Thank you very much for responding. I do appreciate your time and effort. Please keep in mind that I know nothing about Ubuntu or linux. If this was windows I probably would have solved the problem on my own. So having said that I am not sure I understand what you are writing. I understand what the sudo command does and I assume you want me to write this on the terminal window:
sudo modprobe sony_acpi I don't know what this does or what it is but if I do try it, is there a way to revert it in case it causes the performance to worsen. Is there any place that I can read about it so I can start to learn. Also, based on what I wrote in my original post, am I missing a video driver or something similar? Thanks.

---

### Post by Tipped OuT on 2009-05-08
What you want to learn? Command lines? Or just Linux in general..nothing much to it really. :P

And that thing shouldn't cause any performance issues, but if you want to remove it, I believe the command is "sudo remove modprobe sony_acpi". Don't quote me on it.

---

### Post by pjmed on 2009-05-08
I am searching and reading about the modprob sony_acpi and granted I haven't read much yet it seems to be more about making the fn keys work and stuff like that. Posts seem to be from around 2006, does this still apply with 9.04. Should I still try it? I must add that when I installed 9.04 and turned on the laptop for the first time everything seemed to be working, sound, FN keys, correct display resolution. I haven't installed anything I think, other than Flash for Firefox. Still would like some thoughts about the video performance or performance issue. Thanks again.

---

### Post by Don1500 on 2009-05-08
```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M9+ 5C61 
[Radeon Mobility 9200 (AGP)] [1002:5c61] (rev 01)
```

That card is not supported by the new ATI driver (9.4) required for 9.04

---

### Post by pjmed on 2009-05-08
Tried the command and this is what I got.

sudo modprobe sony_acpi
FATAL: Module sony_acpi not found.

---

### Post by spiderbatdad on 2009-05-08
[http://ubuntuforums.org/showthread.php?t=309533&page=1](http://ubuntuforums.org/showthread.php?t=309533&page=1)
Apparently not a default kernel module, there is a package available here.

---

### Post by mysoogal on 2009-05-08
there is a work around, its pretty simple you know, go back to ubuntu 8.10 ! it just works

ubuntu 8.10 = windows xp - things run very smooth
ubuntu 9.04 = windows vista - lots of drivers not seem to work.

you get my drift.........

---

### Post by Tipped OuT on 2009-05-08
> **mysoogal said:**
> there is a work around, its pretty simple you know, go back to ubuntu 8.10 ! it just works

ubuntu 8.10 = windows xp - things run very smooth
ubuntu 9.04 = windows vista - lots of drivers not seem to work.

you get my drift.........

-_-

---

### Post by pjmed on 2009-05-08
Tried the command and this is what I got.

sudo modprobe sony_acpi
FATAL: Module sony_acpi not found.

---

### Post by pjmed on 2009-05-08
> **mysoogal said:**
> there is a work around, its pretty simple you know, go back to ubuntu 8.10 ! it just works

ubuntu 8.10 = windows xp - things run very smooth
ubuntu 9.04 = windows vista - lots of drivers not seem to work.

you get my drift.........

Interesting.
I didn't know about this. I have seen Ubuntu 8 and it seemed the same as 9 at least on the outside. What are the differences between the 2?
Still, I am hoping I can get some help from someone knowledgeable so I don't have to go back to Win XP. Thanks for the help.

---

### Post by mysoogal on 2009-05-28
> **pjmed said:**
> Interesting.
I didn't know about this. I have seen Ubuntu 8 and it seemed the same as 9 at least on the outside. What are the differences between the 2?
Still, I am hoping I can get some help from someone knowledgeable so I don't have to go back to Win XP. Thanks for the help.

dont worry dude, use wubi ubuntu installer !

you can have dual boot with xp and ubuntu

can you try the new version, but i will bet your drivers will be black listed and few other things will not work right ;)

ubuntu 8.10 is more stable for me, when i run ub 9.04 everything seems weird ! when i run on 8.10 things are normal.

---

### Post by deadlockedgamer on 2009-05-28
9.04 has new stuff and is faster and has more wireless support and fixed my vid problems. Also has package clean up and lot of under the hood tuning for curtain things. However this is assuming everything works right. I think the vid isues have to due with new drivers and the new x.org video server now in use. Ubuntu devs cut it close in geting the new x.org witch was not in statable release while 9.04 was in beta as far as i can find!

---

### Post by shae on 2009-05-28
The problem with poor performance with compositing is due to an unfortunate situate created by ATI.  Although the Radeon 9200 is getting old, it is still an acceptable piece of hardware, but ATI decided that it would no longer support that card in the newer versions of their driver (anything newer than 8.28.8 (Which is going on 3 years old at this point).  Unfortunately, drivers must be built against the kernel and newer versions of the kernel will sometimes break the older drivers like ATI's fglrx.  It is very difficult if not impossible to build 8.28.8 against Ubuntu 9.04's kernel (or for that matter most modern versions of Ubuntu or any other Linux distribution).

Fortunately, that card is supported reasonably well by the open source drivers, but they do not preform as well or run compiz as well as the closed source drivers now.  The open source drivers have some configuration options though that you should pursue because I believe some of them will improve the performance and reduce the CPU load when redrawing windows, but I am not too familiar with them.  Perhaps someone else is?

---

