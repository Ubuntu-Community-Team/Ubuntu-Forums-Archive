---
title: "XFCE Memory Hog - RAM Release"
date: 2006-08-12
forum: Desktop Environments
---

### Post by saphil on 2006-08-12
I bet you never thought you would see this title.

XFCE is using over 800Mb ot virtual memory and 178Mb of physical ram with only a terminal emulator, gnome system monitor and this firefox window open.  

What would be the command to make xfce release all this ram 
```
xfdesktop -reload 
```
has no apparent effect.

Logout and log back in solves the issue, but that seems pretty lame, especially since I am specifically using xfce because it is supposed to be a light GUI

---

### Post by tseliot on 2006-08-12
moved to a more appropriate section

---

### Post by Nuwanda on 2006-10-31
I am having a similar problem.
When using XFCE, the "Xorg" process takes up more and more memory, until the system becomes unusable.

Any ideas?

---

### Post by dannyboy79 on 2006-10-31
> **Nuwanda said:**
> I am having a similar problem.
When using XFCE, the "Xorg" process takes up more and more memory, until the system becomes unusable.

Any ideas?
i run xubuntu dapper on my old hitachi laptop, it's a 266mhz Pentium MMX w/ 128mb ram. I can tell you that the first thing I did to see my system run faster was NOT use Firefox, it's a ram hog! I use Opera and it serves me just fine. I have a gogle search bar, bookmarks, and opera even has these things called widgets which add additional functionality. The latest Flash even works but since my laptop has such limited resources it doesn't run very well. I have my laptop sitting out in my family room and I just use it mainly for email, surfing, and sometimes, remote desktoping into my ubuntu machine to play some of my music as I have rca cables running all the way from my ubuntnu box to my receiver in the family room. It's a sweet setup. I even have the rca's split and a pair go downstairs to that recevier as well. Anyway, I don't have this issue with xorg taking resources until unusable, I have had my laptop of for over 3 weeks once before I shut her off to give her a break. Hope you figure this out as I can see how this would suck! Oh, maybe it has something to do with your graphics card? I am running a 
0000:00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01) (prog-if 00 [VGA])
        Flags: bus master, medium devsel, latency 128, IRQ 9
        Memory at fd000000 (32-bit, prefetchable) [size=16M]
        Memory at fea00000 (32-bit, non-prefetchable) [size=2M]
        Memory at fed00000 (32-bit, non-prefetchable) [size=1M]

and I am just using the 

Section "Device"
        Identifier      "NeoMagic Corporation NM2160 [MagicGraph 128XD]"
        Driver          "neomagic"
        BusID           "PCI:0:2:0"
        Option "XaaNoScanlineImageWriteRect"
        Option "XaaNoScanlineCPUToScreenColorExpandFill"
 
driver, and I can only seem to get 800x600 but I wish I could figure out how to get 1024x768 but I haven't been able to figure it out and I just gave up.

---

### Post by kerry_s on 2006-10-31
Have you tried not loading gnome services?(settings>sessions&startup>advanced tab). I'm running edgy-server-install+xfce4 and don't have any problems with memory.

---

### Post by CaveRat on 2006-10-31
That's odd indeed. I have Xubuntu installed with Gnome desktop running, xmms streaming, and now typeing this in Firefox. I've been getting super performance so far.

top - 22:48:51 up  1:44,  2 users,  load average: 0.34, 0.30, 0.36
Tasks:  82 total,   1 running,  81 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5% us,  0.9% sy,  0.0% ni, 97.6% id,  0.0% wa,  0.0% hi,  0.9% si
Mem:    774812k total,   381844k used,   392968k free,    14824k buffers
Swap:  1044184k total,        0k used,  1044184k free,   200056k cached

---

### Post by Aoplayo on 2006-11-01
Caverat how did you get that information?

---

### Post by Vadatajs on 2006-11-01
> **Aoplayo said:**
> Caverat how did you get that information?

That's just the upper portion of the 'top' command.

Applications->Accessories->Terminal, and type 'top'. When in top, press 'h' to show a list of commands that sort by various aspects (memory usage, cpu time, etc).

---

### Post by saphil on 2006-11-01
Gnome did not show the same mem usage as XFCE.  THe good news is that testing on edgy, XFCE-Desktop and its components were not creeping up.

---

### Post by dannyboy79 on 2006-11-01
i have a question for anyone who can answer it, i know this is off topic but I figured instead of starting a new thread for somthing this easy I would just ask it here. Does anyone know how to see the very far right of terminal screen when I type in top but since I am on a laptop and I can only get 800x600, I can't see the complete commands all the way on the right. Is there anyway that I can have top or for that matter anything in the terminal do a "wrap" when the line is too long?? This so annoying! I really wish I could get 1024x768 but I can't seem to get it even after I did was someone told me. Thanks if anyone can answer it, if it's really an issue I will take this and post a new thread.

---

### Post by CaveRat on 2006-11-01
> **dannyboy79 said:**
> i have a question for anyone who can answer it, i know this is off topic but I figured instead of starting a new thread for somthing this easy I would just ask it here. Does anyone know how to see the very far right of terminal screen when I type in top but since I am on a laptop and I can only get 800x600, I can't see the complete commands all the way on the right. Is there anyway that I can have top or for that matter anything in the terminal do a "wrap" when the line is too long?? This so annoying! I really wish I could get 1024x768 but I can't seem to get it even after I did was someone told me. Thanks if anyone can answer it, if it's really an issue I will take this and post a new thread.

Show us your /etc/X11/xorg.conf, but only the screen resolution section.

---

### Post by rameshms on 2008-01-18
> **saphil said:**
> I bet you never thought you would see this title.

XFCE is using over 800Mb ot virtual memory and 178Mb of physical ram with only a terminal emulator, gnome system monitor and this firefox window open.  

What would be the command to make xfce release all this ram 
```
xfdesktop -reload 
```
has no apparent effect.

Logout and log back in solves the issue, but that seems pretty lame, especially since I am specifically using xfce because it is supposed to be a light GUI

I still see this problem. It seems to be a slow memory leak. Instead of logging out / in to reclaim the memory, I do this.

Menu -> Settings -> Desktop Settings
Disable "Allow Xfce to manage the desktop", wait for couple of seconds  and turn it back on.
Voila!! the xfdesktop process is stopped & started again. This time the memory footprint is much smaller than earlier. Remember to do this every couple of weeks :-( until the memory leak bug is fixed.

---

### Post by vambo on 2008-01-18
Never experienced this myself. However the following may be of interest.
[http://www.xfce.org/documentation/changelogs/4.4.2]("http://www.xfce.org/documentation/changelogs/4.4.2")
This bug fix might have something to do with it (just a guess on my part).

> Fix missing xfce_rc_close() causing memleak and too many open file descriptors (Bug #3065).

Mind you, if you're already running XFCE 4.4.2 it's another issue!!

---

