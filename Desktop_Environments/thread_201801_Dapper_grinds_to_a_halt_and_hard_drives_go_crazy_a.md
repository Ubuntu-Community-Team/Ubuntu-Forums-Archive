---
title: "Dapper grinds to a halt and hard drives go crazy and around 10pm..."
date: 2006-06-22
forum: Desktop Environments
---

### Post by blue_nowhere_junkie on 2006-06-22
Hey,
I recently got Xgl and Compiz working on my home machine running Ubuntu Dapper 6.06.
It seems to run fine with a few minor glitches in plugins now and again.
But my new problem is, two nights in a row now, at around 10pm, i would be working away in OpenOffice, and the hard drives would start working away on something that i hadn't initiated, thus all my aMSN conversations would slow and Xgl would be a total dog, until such time as it ground to a complete halt. I don't know if Xgl or Compiz are directly related, as i've had them both for a while and they only started this two nights ago.
I had the sense to check crontab and the like, but i didn't find anything in there, and /var/log hasn't revealed anything to me as to what the program is that causes this.

The first time i got this in /var/log/messages

Jun 21 22:18:47 localhost kernel: [17231571.944000] oom-killer: gfp_mask=0x201d2, order=0
Jun 21 22:18:49 localhost kernel: [17231571.944000] Mem-info:
Jun 21 22:18:54 localhost kernel: [17231571.944000] DMA per-cpu:
Jun 21 22:19:01 localhost kernel: [17231571.944000] cpu 0 hot: low 0, high 0, batch 1 used:0
Jun 21 22:19:44 localhost kernel: [17231571.944000] cpu 0 cold: low 0, high 0, batch 1 used:0
Jun 21 22:19:50 localhost kernel: [17231571.944000] DMA32 per-cpu: empty
Jun 21 22:19:58 localhost kernel: [17231571.944000] Normal per-cpu:
Jun 21 22:20:03 localhost kernel: [17231571.944000] cpu 0 hot: low 0, high 186, batch 31 used:173
Jun 21 22:20:10 localhost kernel: [17231571.944000] cpu 0 cold: low 0, high 62, batch 15 used:1
Jun 21 22:21:22 localhost syslogd 1.4.1#17ubuntu7: restart.
Jun 21 22:21:22 localhost kernel: Inspecting /boot/System.map-2.6.15-25-386
(the rest is just bootup from here)

and on the second night, i got this from the same file:

Jun 22 21:45:36 localhost kernel: [17228902.384000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Jun 22 21:46:07 localhost kernel: [17228932.740000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Jun 22 21:46:07 localhost kernel: [17228932.740000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Jun 22 21:46:42 localhost kernel: [17228967.224000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jun 22 21:46:42 localhost kernel: [17228967.224000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jun 22 21:49:57 localhost syslogd 1.4.1#17ubuntu7: restart.
Jun 22 21:49:57 localhost kernel: Inspecting /boot/System.map-2.6.15-25-386
Jun 22 21:49:57 localhost kernel: Loaded 23020 symbols from /boot/System.map-2.6.15-25-386.

I'm running an Athlon 2500+ with Ubuntu 6.06 and 768mb of ram, an ATI Radeon 9550 graphics card, all on kernel version 2.6.15-25-386

I hope i haven't done something stupid and forgotten about it, but any help would sure be appreciated, because i can't tell whether this is eating my hard drives or simply cataloguing something...
Thanks in advance!

blue_nowhere_junkie

---

### Post by x64Jimbo on 2006-06-22
Right when it gets slow, I'd recommend doing this command in a terminal:
top
it will list all your running processes in descending order of CPU usage. It sounds like some process is chewing up all your CPU. Once you've determined what program it is, post its name here.

---

### Post by blue_nowhere_junkie on 2006-06-22
I tried doing that the first time, but i couldn't get it to start up before it got too heavy on me.
Now i guess i have to just wait til next time.
Thanks!
blue_nowhere_junkie

---

### Post by blue_nowhere_junkie on 2006-07-02
Hello again,
Thanks for the reply,
it seems to have fixed itself, not sure what happened...
Thanks again!
blue_nowhere_junkie

---

