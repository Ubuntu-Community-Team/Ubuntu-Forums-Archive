---
title: "System freezing, kernel panicking"
date: 2012-08-11
forum: Desktop Environments
---

### Post by Ratatwisker on 2012-08-11
Hi,

since the last 3 days (including today) I'm experiencing crashes on my Ubuntu 12.04. Before that day I didn't have any problems of this kind.

The pattern was always similar to this:

When turning my computer on, I can use it fine for a few minutes, maybe around five. Then, the system freezes - I can't use any input device and the screen does not show any changes. Pressing Ctrl + Alt + F1 to switch to console doesn't work either. When I do a reboot then, I get a Kernel Panic at the log in screen (indicated by blinking caps lock and scroll lock LEDs). Unfortunately, I didn't try displaying the console at this point yet. However, after a second reboot, the system was running fine the rest of the day.

Today this behaviour got a little worse. Right before the first freeze I noticed that firefox was not responding any more, though I could still use the mouse and switch to other applications. Then: reboot, kernel panic, reboot, log in normally. After a short time, maybe 10 seconds or so, ubuntu rebootet itself without any error message or something. I can't remember exactly if I had another freeze or kernel panic after this reboot, but now the system is running fine again.

I've already taken a look into syslog without noticing any entry indicating the cause of the crash before it happens. Also none of the kernel panics was logged, though I don't know if it usually is logged at all and I'm by no means en expert interpretating syslog.

I also tried different kernel versions - grub2 (I think) offers me 3.2.0-26, -27 and (since yesterday) -29. Does not seem to change anything, but since this behaviour occurs once a day I couldn't test that much. Currently I'm running -29, yesterday it was -26.

As a side note (don't know if it's connected to the problem), I'm experiencing a strange behaviour when I'm shutting ubuntu down ever since I installed 12.04. The duration the last screen that is shown before shut off (the "unbuntu" text with the dots changing from grey to red or something) sometimes is just a few seconds, but most of the times the computer seems to idle at this screen for several tens of seconds, up to a minute or so. Eventually I discovered that if I press any key a few times, the computer almost immediately turns off. When at first pressing ESC to show the console when the idleing happens, it says something about halting all processes or something if I recall correctly (sorry about being unprecise, didn't take the time to write it down yet). Upon pressing any key then a few other messages are shown, but the computer is then shuttong down so quickly I have had no time of reading these messages yet.

However, I can live with this, my main concern is the freezing and kernel panicking. I'd really appreciate any help tracking down the cause of this.

Regards

---

