---
title: "Slow effects on an Nvidia 8400m GS"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by theophane on 2007-10-28
Hi folks.

My desktop effects are slow on my brand new computer.

It is an Acer Aspire 7720G with a 2.0Ghz intel core 2 duo processor, 2Gb of ram and an Nvidia 8400m gs, which is supposed to be a fast graphic card.

The effects are slow and are getting a little better once they have been practised for awhile. This is pretty frustrating since this graphic card is part of the reason I've spent 1000€ to purchase this computer. 

I've searched the whole internet, and a lot of 8400m gs users are facing the same problem.

I've found no solution yet.

Some help would be appreciated 

Cheers :)

---

### Post by theophane on 2007-12-10
Has anyone solved this problem ?

---

### Post by rsambuca on 2007-12-10
Have you tried the new beta driver?

---

### Post by theophane on 2007-12-10
I have, and I still get lame performances :mad:

---

### Post by theophane on 2007-12-16
I found a hack on the official Nvidia boards, here it is :

[QUOTE=Sayonara]try this:

in terminal run:
# while true; do nvidia-settings -q all > /dev/null; sleep 25; done

this seems to stick PowerMizer at maximal performance level
I have no time to track this down yet.

card: Quadro 1600M
driver: x86_64-169.04

watch out do not burning your gpu :)[/QUOTE]


Worked out for me, I hope this will also work for anyone else out there.

---

### Post by dumplinknet on 2007-12-26
> **theophane said:**
> I found a hack on the official Nvidia boards, here it is :




Worked out for me, I hope this will also work for anyone else out there.

what exactly does that code do? does it heat up and blow up the Nvidia 8400M GS?

---

### Post by theophane on 2007-12-26
> **dumplinknet said:**
> what exactly does that code do? does it heat up and blow up the Nvidia 8400M GS?

I think it allows the GPU to run at full speed all the time.
However, I read the new nvidia drivers have solved this issue.

---

### Post by s0ury on 2008-01-04
It's no problem, powermizer is SUPPOSED to be there.
The only solution is a check-box which we can click to disable the damned thing.
Are you guys sure though, there isn't an option to disable powermizer?
I'm sry for being a bit aggressive i've been googling about the matter the last 5 days.

---

### Post by dumplinknet on 2008-01-05
i have still not come across anything that will fix the issue with our nvidia 8400M GS video card. i dont know why the 8400M GS slows down and is very inconsitent...
if anyone finds a fix this would be great!
im still searching by the way.

---

### Post by manuelb on 2008-01-13
I can confirm this behavior is related to PowerMizer: if you try to insist with SuperL+E, you'll see it get really faster and flicker-free when powerMizer report 400mhz instead of 100.. in fact it's correct, when you start to play games the tool "see" the usage, but i think compiz-like effects are too short and powermizer actually doesn't get it..

---

### Post by mongo on 2008-01-24
Try this fellas. Open a terminal and type in
sudo gedit /usr/bin/powermizer-off
then paste this in
```

#!/bin/bash
while true; do
        nvidia-settings -q all > /dev/null;
        sleep 20;
done

```
save and exit
chmod 755 /usr/bin/powermizer-off
run it with "powermizer-off &" or just put it in your sessions config.
Works fine for me. It's not a perfect solution though. All that the script does is make a silent query (to the graphic card and then sleep for 20 seconds. Kill the task if you wish to prolong battery life as the clocks stay at 400/600 at all time.

---

### Post by jobeirne on 2008-01-26
> **mongo said:**
> Try this fellas. Open a terminal and type in
sudo gedit /usr/bin/powermizer-off
then paste this in
```

#!/bin/bash
while true; do
        nvidia-settings -q all > /dev/null;
        sleep 20;
done

```
save and exit
chmod 755 /usr/bin/powermizer-off
run it with "powermizer-off &" or just put it in your sessions config.
Works fine for me. It's not a perfect solution though. All that the script does is make a silent query (to the graphic card and then sleep for 20 seconds. Kill the task if you wish to prolong battery life as the clocks stay at 400/600 at all time.

You, sir... Well, I owe you a pint.

---

