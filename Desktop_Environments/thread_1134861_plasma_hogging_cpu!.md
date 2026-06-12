---
title: "plasma hogging cpu!"
date: 2009-04-24
forum: Desktop Environments
---

### Post by rkakkar on 2009-04-24
I just got the Jaunty RC installed and noticed that plasma is consuming 50% of my cpu usage! Its causing my lappy to run quite hot. Is this normal?

---

### Post by Monsieur Gonzalez on 2009-04-24
Well, I think there are some problems with certain graphic cards, so, which one are you using? Restricted drivers?

---

### Post by inobe on 2009-04-24
Monsieur is correct, if you have an nvidia card pending on the model' most issues were fixed with driver nvidia 180.44.

---

### Post by rkakkar on 2009-04-24
Yup I think its restricted drivers. I'm using integrated graphics - Mobile Intel Graphics Media Accelerator X3100. My lappy is: [http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-89315-3442832.html]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-89315-3442832.html")

---

### Post by Monsieur Gonzalez on 2009-04-24
You might have been hit with [this]("https://wiki.kubuntu.org/JauntyJackalope/ReleaseNotes/#Performance%20regressions%20on%20Intel%20graphics%20cards"). 

There are some advices as to how to solve it. Or if you'd rather wait, try to disable "desktop effects" while they upgrade the intel package.

Good luck.

---

### Post by rkakkar on 2009-04-25
> **Monsieur Gonzalez said:**
> You might have been hit with [this]("https://wiki.kubuntu.org/JauntyJackalope/ReleaseNotes/#Performance%20regressions%20on%20Intel%20graphics%20cards"). 

There are some advices as to how to solve it. Or if you'd rather wait, try to disable "desktop effects" while they upgrade the intel package.

Good luck.

:(

Well how do I know if the way my current system is running is safe? I mean if its not damaging  it then i'll let it run as it is otherwise I'll disable desktop effects. Is there any way we can confirm this?

---

### Post by Monsieur Gonzalez on 2009-04-25
Well, if I were you I'd try reverting the driver to a previous version, as per directions [here]("https://wiki.kubuntu.org/ReinhardTartler/X/RevertingIntelDriverTo2.4") and check for CPU usage improvement. Just keep the directions at hand (maybe even print them). 

As for damaging the system, well, I don't think so, but you're using CPU cycles for something that should come for "free", as the graphic card should do the heavy lifting.

---

### Post by rkakkar on 2009-04-29
this can't be good right?

```
$ acpi -V
  AC Adapter 0: on-line
     Thermal 0: ok, 73.0 degrees C
     Thermal 1: ok, 72.0 degrees C
     Thermal 2: ok, 80.0 degrees C
     Thermal 3: ok, 20.0 degrees C
     Thermal 4: ok, 54.0 degrees C
     Cooling 0: LCD 0 of 10
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10
     Cooling 3: Fan 1 of 1
     Cooling 4: Fan 1 of 1
     Cooling 5: Fan 1 of 1
     Cooling 6: Fan 1 of 1
     Cooling 7: Fan 0 of 1

```

---

### Post by Monsieur Gonzalez on 2009-04-29
I'm on a desktop here, so I couldn't tell if those numbers are right, but I think notebooks are designed to stand higher temperatures. 

Have you installed lm-sensors? If you have, run 'sensors' from the command line to make sure your fans are working ok. If you haven't, you can do with 'sudo apt-get install lm-sensors'; then 'sudo sensors-detect', agree to everything and reboot.

---

### Post by tlue on 2009-04-29
> **Monsieur Gonzalez said:**
> You might have been hit with [this]("https://wiki.kubuntu.org/JauntyJackalope/ReleaseNotes/#Performance%20regressions%20on%20Intel%20graphics%20cards"). 

There are some advices as to how to solve it. Or if you'd rather wait, try to disable "desktop effects" while they upgrade the intel package.

Good luck.


In my case it was the calendar plasmoid I had on my desktop. see
[this]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/352673").
I just removed it an plasma came down from 100% CPU to 2-3%.

---

### Post by rkakkar on 2009-04-30
> **tlue said:**
> In my case it was the calendar plasmoid I had on my desktop. see
[this]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/352673").
I just removed it an plasma came down from 100% CPU to 2-3%.

oh wow! it was the calendar plasmoid!! thanks man.

---

### Post by fornix on 2009-05-02
I can confirm this.
The calendar applet is buggy.
Eats 100% CPU

---

### Post by funkster on 2009-05-04
Same here. Calendar Plasmoid uses an entire core of my dual-core amd (7750BE, ATI HD3300 OnBoard GFX).
Hilarious. 

Have a nice day people, 

Raphael ;)

---

### Post by mwolfgang on 2009-05-13
I'm having the same problem.  It's using 50% of my CPU cycles, and the touchpad on my laptop is too hot to touch.  I have to use my left hand that has callouses from playing guitar.
sensors:
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +72.0°C
Core0 Temp:  +71.0°C
Core1 Temp:  +68.0°C
Core1 Temp:  +65.0°C

I know these aren't critical levels, but I don't have this problem with the touchpad when I boot to Windows.  If I leave the lid closed overnight, it freezes up and the entire lower half is uncomfortably hot to the touch.

---

### Post by mwolfgang on 2009-05-13
BTW...Disabling Twitter and LCD Weather seems to have helped.

Sensors Since:
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +54.0°C
Core0 Temp:  +48.0°C
Core1 Temp:  +46.0°C
Core1 Temp:  +42.0°C

---

### Post by pro003 on 2009-06-01
> **fornix said:**
> I can confirm this.
The calendar applet is buggy.
Eats 100% CPU

Positive! 

Calendar applet eats 100% of my CPU, too :(

---

### Post by czarama on 2009-06-04
tlue

thanks for tip, I remove the calendar widget and my plasma is using 1% instead of 50%

:p

---

