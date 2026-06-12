---
title: "hibernate like windows on laptop"
date: 2005-09-30
forum: Desktop Environments
---

### Post by digits on 2005-09-30
hello,

when i hibernate my computer, the screen goes black, and after a while the hd-led turns off. so, it looks like the computer has shut down, but the power-led is still green. also, i can't restart my laptop. i have to cut the power cable before i can restart my latop. when i restart my laptop, it boots up , but there is no sign from hibernation.

is there any solution to solve this ? i would like to have a hibernate function like in windows xp.

thank you!
greetings,
digits

---

### Post by netsyd on 2005-09-30
[QUOTE=digits]hello,
when i hibernate my computer, the screen goes black, and after a while the hd-led turns off. so, it looks like the computer has shut down, but the power-led is still green. also, i can't restart my laptop. i have to cut the power cable before i can restart my latop. when i restart my laptop, it boots up , but there is no sign from hibernation.
is there any solution to solve this ? i would like to have a hibernate function like in windows xp.
thank you!
greetings,
digits[/QUOTE]

What kind of laptop? 

You have a couple of options here, depending on the type of machine... here's in general your options if hibernate doesn't work "out of the box".

Option 1: Disable ACPI and switch to APM. This assumes your system supports APM. I chose this option and no have no problems with suspend. I haven't tried hibernate since I just finished everything up last night, but it worked last time I used Ubuntu w/ APM so I don't see why it wouldn't this time around. You will need to apt-get the kernel source (I think...) for whatever kernel you are running, then follow these instructions: [https://wiki.ubuntu.com//SuspendHowto](https://wiki.ubuntu.com//SuspendHowto)

Option 2: Only do this if APM doesn't work for you. You will need to compile a custom kernel with Suspend2 built in. There's a kernel recompile how to in the "how-to" section that should help you a lot, or feel free to send me a pm and I'll try to help you through it. Again, if oyu can avoid it, I would try not to do this, because things tend to get broken (wifi, sound, etc) the first few times you do it. 

:rolleyes:  Yay Linux! LOL

Anyway, good luck.

---

### Post by digits on 2005-09-30
thank you very much for that link!

my laptop is an acer travelmate 4500, and this thing did do the trick:

[https://wiki.ubuntu.com/HoaryPM](https://wiki.ubuntu.com/HoaryPM)

thank you !

---

### Post by netsyd on 2005-09-30
:D Glad you got it working. 

I forgot they didn't have resume=xxxx in grub, I'm so used to ACPI being a waste of time on my laptop!

---

