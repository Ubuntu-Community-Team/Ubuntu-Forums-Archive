---
title: "amd turion heat"
date: 2009-04-21
forum: General Help
---

### Post by nordmar on 2009-04-21
Hi,

There is the question:

I have AMD Turion X2 64bit and run Ubuntu 8.10 x64 and the proc goes really hot. The lm-sensors show about 70 degrees Celsium and the fans go on maximum speed.

Earlier when I had WinXP it was running on 56-60 degrees when I was not using the comp and the fans were quiet. The temperature went high only when I played a game.

Any solution?

Thank you

---

### Post by MartyBuntu on 2009-04-21
Do you have CPU frequency scaling installed and configured?
I think there's a tutorial on that, I can't remember where I saw it.

---

### Post by nordmar on 2009-04-21
I don't.

Thanks for the tip though

---

### Post by 3rdalbum on 2009-04-21
CPU frequency scaling should be automatic and out-of-the-box unless it has been turned off in your BIOS.

I would check to see that there aren't any programs running away with your CPU. I advise putting the "System Monitor" applet onto your Gnome panel, assuming you're running Gnome, and this will give you a visual indication of how hard your CPU is working.

If it's working hard all the time, you can find the offending program by using the "top" command in the terminal, and then kill it.

Another good idea is to install Powertop - it gives an indication of the most power-hungry programs that are running and can give suggestions for decreasing power use. This is unlikely to be a solution to your problem, but it's something I recommend for battery-powered computers anyway.

---

### Post by nordmar on 2009-04-27
I know I'm resurrecting a 5 days dead thread, but.

I found and enabled scaling. I allowed Power Save in BIOS and added everything needed to /etc/modules.

After a reboot my comp went up to 90 degrees Celsium and I had to switch it off very quickly. Then I decided to disable the scaling again for some time.

How come when I was running windozz I had minimum 800 mHz and silent cooling fans and when I run Kubuntu on 800 mHz I have the fans on one speed with lots of noise? I don't have fans speed module/program regulation? Or else?

---

