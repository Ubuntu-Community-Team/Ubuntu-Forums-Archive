---
title: "Sudden &quot;Operating System not found&quot; message"
date: 2010-05-20
forum: Desktop Environments
---

### Post by bhagwad on 2010-05-20
I've been using Lucid 10.04 for quite a while now including during the beta testing phase. Everything has been just fine.

Yesterday the system suddenly hanged. Pressing Ctrl+Alt+F1 to take me to the terminal, I wasn't even able to log in and got the error read I/O error something. So I rebooted.

On reboot, I got this message: **"Operating system not found"**. No Grub nothing. Repeated reboots kept giving me the same error. I didn't have a Live CD with me either so I was stuck.

Then I found out something strange. If I *shut down* the system (not restart), and then power it on again, Grub loads up fine!

It happened once again - hanging and "Operating System not found" on reboot. This time I immediately shut down and powered on instead of restarting, and it worked!

Surely someone knowledgeable can tell me what this means?

Thanks in advance for any help you can give me...

---

### Post by seagullplayer77 on 2010-05-20
I just started having the exact same problem with 8.04 Ubuntu Studio. It's never happened before, but yesterday, X froze up and when I went to a virtual terminal, I too was unable to log in. Lots of error messages, and the magic restart combo (Ctrl+Alt+PrtScr+REISUB) didn't work either. I held the power button and turned my laptop back on, and I get nailed with that message. I took the battery out, let it sit for a while, and powered back on without a hitch.

Today, the same thing happened. X froze, and I couldn't restart, so I powered the machine off manually and turned it back on. No luck. "Operating System Not Found." I figured that it would just need a clean restart, so I popped in a live disk and restarted. Still no dice. Perhaps I'll have to try powering off from the live disk, then restarting . . . 

In any case, it seems strange that this problem popped up suddenly with two different versions of Ubuntu. Perhaps it was due to a recent update?

---

### Post by seagullplayer77 on 2010-05-20
Well, after doing some tests, I'm starting to think that the "Operating System Not Found" isn't Linux related at all, but rather an HD issue.

My hard drive doesn't show up in the BIOS configuration tools. It didn't show up in the live CD at all. And I just popped in a copy of the UBCD, and none of the HD diagnostic tools were able to even find a drive. I opened up the laptop and reseated the drive, and still no dice.

When this happened last night, the possibility of the HD being on the fritz crossed my mind and I thought about backing up all my data, but I just wrote the error off as a fluke. It looks like I should've trusted my gut, because methinks the HD is toast :(.

---

### Post by maedox on 2010-05-20
bhagwad:
I would say it could be a number of things. 
1. Your power supply unit is getting old and cannot keep a steady voltage over time and/or when hot. Some components in the PSU may fail soon.
2. Your motherboard may have failing components (disk controller, capacitors, voltage controllers, overheated mosfets etc.). Check the temperature of the small black squares and cylinders (capacitors) around your CPU socket on the motherboard.
3. Your disk may fail soon.

What to do: Check all connections. Refit all cables; power cables as well as data cables. Test out your drive in another computer. Boot with a live-CD and do some drive diagnostics. Try another disk controller plug and data cable.


seagullplayer77:
Depends on the drive of course, but a drive failing like that, without even a little noise, may not be dead. (If you put your head close to the chassis, can you hear the drive? Does it make very rhythmic noises when you start the computer?) 
It may well be the controller or motherboard. Put it in one of those external hubs, or get it to a repair shop to check it out. If you have warranty on your computer, it's better to use that first of course.

---

### Post by bhagwad on 2010-05-20
> **maedox said:**
> bhagwad:
I would say it could be a number of things. 
1. Your power supply unit is getting old and cannot keep a steady voltage over time and/or when hot. Some components in the PSU may fail soon.
2. Your motherboard may have failing components (disk controller, capacitors, voltage controllers, overheated mosfets etc.). Check the temperature of the small black squares and cylinders (capacitors) around your CPU socket on the motherboard.
3. Your disk may fail soon.

What to do: Check all connections. Refit all cables; power cables as well as data cables. Test out your drive in another computer. Boot with a live-CD and do some drive diagnostics. Try another disk controller plug and data cable.


seagullplayer77:
Depends on the drive of course, but a drive failing like that, without even a little noise, may not be dead. (If you put your head close to the chassis, can you hear the drive? Does it make very rhythmic noises when you start the computer?) 
It may well be the controller or motherboard. Put it in one of those external hubs, or get it to a repair shop to check it out. If you have warranty on your computer, it's better to use that first of course.
 
Thanks for the advice, but I'm using a laptop! Sony VAIO VGN-NR498E and I use it like a desktop - I never move it around. You're sure it's a hardware problem?

---

### Post by maedox on 2010-05-20
I see. Well, my comments still apply, but I guess the troubleshooting is a bit more difficult on a laptop. Do you still have warranty?

One can never be 100 % sure, but I would say I am pretty sure it is a hardware issue. It can be as simple as a bad connection between the harddrive and the rest, or it can be some of the other things I mentioned.
What you can try is a BIOS reset and an upgrade too if you're up for it. Make sure you have enough power on the battery, because you're in even more trouble if the BIOS upgrade fails.
By the way, does the computer get very hot? Or in other words; Do you think it gets warmer now than when it was new? Your issue can be related to overheating components as I mentioned earlier. Have you checked the cooler entries and exits for dust?

---

### Post by bhagwad on 2010-05-20
I'll see what the bios upgrade can do. As for the heating, it's not gotten much hotter now than what it was two years ago.

Thanks for the advice. I'll get back if anything new happens.

---

