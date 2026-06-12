---
title: "A program is still running... unknown"
date: 2009-02-07
forum: General Help
---

### Post by BuntuFirstTimer on 2009-02-07
I tried to shut down my Ubuntu 8.10 and I sometimes encounter a window box that says **A program is still running** while saying there is a program so-called **unknown** and says **not responding**.

Is there a problem with my Ubuntu installation by any chance?

---

### Post by jrusso2 on 2009-02-07
It could be a bug in the program.  More information is needed.

---

### Post by travmon69 on 2009-02-07
I get that too sometimes.  I just logout anyway unless it's a package manager running. you never want to interupt a package manager!!

---

### Post by tom56 on 2009-02-20
I just started getting this problem a week or so ago

---

### Post by joshaman on 2009-03-10
Isn't there a way to figure which process it is?

---

### Post by kryptikos on 2009-03-10
sounds as if a process or program is horking and dieing off leaving a zombie child process. Hard to tell. Are you running any particular programs when you get this error appearing during logoff/shutdown? Can you list out 'ps aux' (from a console) and see if there are any process that are listed with a "Z"? Have you checked /var/log/messages to see if there are any errors being posted there?

---

### Post by joshaman on 2009-03-10
I was only running Transmission and this happened when I tried to reboot.  I then closed Transmission and got the same thing again.  Then I checked System Monitor for processes which were labeled not responding but there were none.  I didn't check ps aux - what's the F mean (for future reference)?  

Here's what my log says - it looks as though Compiz was the issue - I'm using the default "extra" setting without compiz config installed:

```

Mar 10 06:57:18 josh-desktop kernel: [21506.490324] Inbound IN=eth0 OUT= MAC=00:1d:7d:d5:ff:5b:00:1d:5a:1c:67:e9:08:00 SRC=83.212.128.162 DST=192.168.1.74 LEN=56 TOS=0x00 PREC=0x00 TTL=235 ID=23962 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.1.74 DST=83.212.135.158 LEN=44 TOS=0x00 PREC=0x00 TTL=0 ID=17711 DF PROTO=TCP INCOMPLETE [8 bytes] ] 
Mar 10 06:57:30 josh-desktop kernel: [21518.493739] Inbound IN=eth0 OUT= MAC=00:1d:7d:d5:ff:5b:00:1d:5a:1c:67:e9:08:00 SRC=83.212.128.162 DST=192.168.1.74 LEN=56 TOS=0x00 PREC=0x00 TTL=235 ID=23998 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.1.74 DST=83.212.135.158 LEN=44 TOS=0x00 PREC=0x00 TTL=0 ID=59545 DF PROTO=TCP INCOMPLETE [8 bytes] ] 
Mar 10 06:57:33 josh-desktop kernel: [21521.492822] Inbound IN=eth0 OUT= MAC=00:1d:7d:d5:ff:5b:00:1d:5a:1c:67:e9:08:00 SRC=83.212.128.162 DST=192.168.1.74 LEN=56 TOS=0x00 PREC=0x00 TTL=235 ID=24008 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.1.74 DST=83.212.135.158 LEN=44 TOS=0x00 PREC=0x00 TTL=0 ID=59546 DF PROTO=TCP INCOMPLETE [8 bytes] ] 
Mar 10 07:19:08 josh-desktop -- MARK --
Mar 10 07:39:08 josh-desktop -- MARK --
Mar 10 07:59:08 josh-desktop -- MARK --
Mar 10 07:59:41 josh-desktop kernel: [25249.410571] compiz.real[6382]: segfault at 120 ip 000000000041024e sp 00007fff3ef9b8b0 error 4 in compiz.real[400000+3b000]
Mar 10 07:59:46 josh-desktop exiting on signal 15
```

are those ICMP IN blocks before the compiz error?

---

### Post by richardh9936 on 2009-03-17
Don't panic.  These people think it's a remnant from Firefox.  See 
 [http://ubuntuforums.org/showpost.php?p=6629969&postcount=9]("http://ubuntuforums.org/showpost.php?p=6629969&postcount=9")

---

### Post by Rhemat on 2009-03-27
I just started getting this yesterday, I think.  I also couldn't find any processes in System Monitor that were using any CPU % except System Monitor (of course) and Firefox (but Firefox was open when I checked it).  I also not that whenjust letting my computer idle (with System Monitor and Firefox open), the CPU % usage goes from 18 to 26 percent.  My computer stats are:

AMD Athlon 64 3200+ (2GHz)
2GB DDR1 RAM
MSI RX2400 Pro (ATi HD2400 chipset) (Eye Candy is not enabled)
Ensoniq Audio PCI card
OnBoard Ethernet Adaptor
Ubuntu 8.10 32bit

I wish I had made note of my CPU usage before that event.

---

### Post by aiadruide on 2009-05-11
Hello
I have the same problem, and I think gnome's buggy :
[http://bugzilla.gnome.org/show_bug.cgi?id=546755](http://bugzilla.gnome.org/show_bug.cgi?id=546755)
Hope they will solve it soon, cause I think only Win* would crash when halting ...

---

### Post by gmoctav on 2009-06-28
i've got the same problem, and still no solution yet...

---

### Post by junglist313 on 2009-07-11
Same problem here. It only happens when my wife logs out. Doesn't happen to me. I am going to try turning off compiz and see if that helps.

---

### Post by maverick340 on 2010-01-14
Yeah it looks like compiz is the culprit here. I am running Ubuntu 9.10 updated (today). I have Docky (not Gnome-do) installed and compiz turned on. I have a Nvidia 8800Gt gfx card so nvidia 180 restricted drivers installed. Docky needs compiz turned on so i had it turned on. Few things i noticed 
1. The Ubuntu-one applet does not load anymore
2. When i try to shut down/restart/log off a window pops up saying unknown program is not responding.

I turned of compiz now, docky complains, and the bottom border of windows is missing but 
1. The Ubuntu-one applet is back
2. The Unknown program error is gone

Hope the extra info helps and the problem is figured out fast.

---

### Post by Docaltmed on 2010-02-09
Happens to me on every shutdown. Thing is, I don't run compiz. 

Reading through the forums, I've now seen this problem attributed to Firefox, compiz, and a couple of other programs. 

Obviously, it is none of the above.

I'd report this bug, except I haven't got a clue where to report it.

---

### Post by verdomde on 2010-07-18
Hey, the simplest solution is to kill processes in system monitor, trying to shut down after each one, you can then identify which one was the problem- for me it was tangerine. Uninstalling that solved my problem.

---

### Post by kidknapp on 2010-08-13
> **verdomde said:**
> Hey, the simplest solution is to kill processes in system monitor, trying to shut down after each one, you can then identify which one was the problem- for me it was tangerine. Uninstalling that solved my problem.
More specifically Open >System>Administration>System Monitor. Look at the the CPU(do this while it shows "unknown program not responding" when you go to restart- find a program (besides system monitor) and see if that CPU is running at all- that could be your program....For me it was Tangerine...:)

---

