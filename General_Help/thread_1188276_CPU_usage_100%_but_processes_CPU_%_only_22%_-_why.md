---
title: "CPU usage 100% but processes CPU % only 22% - why?"
date: 2009-06-15
forum: General Help
---

### Post by DylanH on 2009-06-15
Thank you to the Ubuntu community for your ongoing help! I've used your advice on a number of occasions and I greatly appreciate the time and energy you put into helping others.

I had a strange problem on my last boot - it seems to be fine after I rebooted. Here were the stats before:

Via system monitor:

PROCESSES
(in sorted order of CPU %)
firefox-bin 19
gnome-system-monitor 11
gnome-panel 1
metacity 0

RESOURCES
Cpu History:
98-100% constant

So my questions are: What could possibly be using up my CPU? How do I fix this in the future?

---

### Post by munky99999 on 2009-06-15
Does it have 100% from the restart or do you need to start doing something to cause 100%?

Next question: Do you have something like Boinc Manager? As I do. I will have 100% cpu all the time. Relative to the processes list Boinc isnt there.

---

### Post by DylanH on 2009-06-15
Not sure if I did anything to trigger it. Was running Firefox, but unsure whether that caused it. The problem persisted after I closed Firefox and wasn't resolved until I restarted. Also had 90% memory usage and 50% swap file usage.

Stats after reboot:

Resources -> CPU History: 20%-70% (fluctuating)
Resources -> Memory: 24% Swap 0%

Using Jaunty - should have said that before. Not using anything like Boinc Manager.

Not a pressing matter since it seems to have been resolved. Just curious what could have caused it so I can take appropriate action in the future (new to Linux - still trying to understand how it works.)

---

### Post by izizzle on 2009-06-15
Are you using the beta version of Firefox (3.5)? Maybe firefox just didn't close right...

---

### Post by DylanH on 2009-06-15
izizzle: Completely correct. 3.5b4 - perhaps this was the culprit.

---

### Post by izizzle on 2009-06-16
Nice. :wink:

---

