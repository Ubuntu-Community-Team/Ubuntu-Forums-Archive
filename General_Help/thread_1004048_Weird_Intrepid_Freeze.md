---
title: "Weird Intrepid Freeze"
date: 2008-12-06
forum: General Help
---

### Post by Mathja on 2008-12-06
Somethig wierd, happens on my Dell XPS M1210 with Dual Boot Windows
XP and Ubuntu 8.10. My system suddenlly freezes even the clock stops,
but I can move my cursor in very very slow and not-smooth way. Keyboard
does not respond. Ctrl+Alt+del or backspace doesn't work. But during all
this process my 'thinking' LED (I dont know how to call it) is on. It's
like if suddenlly an applications starts using 100% of CPU capability
and everything slows down and freezes. Just like in windows 95...

This has happened to me about 5 times this week. And everytime I have
been using different applications so I dont know if there is anything in
common (besides the symptoms). I am not sure but I think that in this 5
times, I had a pdf viewer running (could have been evince or acroread, I
use both) + other standard stuff like firefox, thunderbird,etc . By the way in each of this five times I had to force reboot by using the power button.

Any ideas?

---

### Post by bayvista on 2009-04-27
I have exactly the same problem on a HP Pavillion 9500 laptop. Just started happening after 2 months of clean running on Intrepid. I suspect it's a recent update that has screwed something. Don't know how to track it. Maybe I'll log a Bug Report

---

### Post by kurtfb on 2009-04-28
This is happening to me as well. I just upgraded from Hardy to Jaunty, and  my system periodically freezes for a minute or so. Sometimes it will do it once and then run fine all day, and sometimes it will do it every couple of minutes until I reboot. Every now and then when it has a particularly nasty spate of freezes it wipes out GRUB and I have to reinstall it. 

I leave system monitor running to try to see what application is causing the freeze, but there are no indications there - it usually freezes with the rest of the system and when/if it comes back the history does not show any unusually high system load.

Does anyone have any thoughts what might be causing this? It reminds me of Windows 3.1

---

### Post by kurtfb on 2009-04-28
a bit more followup on this problem -

I had been running the system monitor to see if any processes were spiking up and hogging the cpu. It didn't seem like there was. And I was also running the little system monitor graphic in the panel, and it was also showing that the CPU was not overly burdened. But I discovered that there is a barely noticeable color change in that system monitor graphic and it seems the system is maxxed out in a state of "IOWait" when it is locked up. When it locks I can move the cursor, but that is about all and sometimes I can't even do that, and sometimes even system monitor freezes and doesn't update. Anyone have any ideas what might be causing this?  I am running a new install, and made sure that Wine, compiz, etc.  are not running. Pretty much just using firefox when this happens.

---

