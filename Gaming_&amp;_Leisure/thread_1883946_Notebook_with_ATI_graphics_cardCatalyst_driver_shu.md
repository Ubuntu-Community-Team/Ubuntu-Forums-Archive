---
title: "Notebook with ATI graphics card/Catalyst driver shuts itself down when gaming."
date: 2011-11-20
forum: Gaming &amp; Leisure
---

### Post by H3R3T1K on 2011-11-20
My notebook sports an ATI graphics card that should handle the 3d games I  occasionally play with ease. Now I know about the issues with ATI  graphics cards and the Catalyst driver. I'm using the older one, since I  can't install the 'post release updates' one somehow. Everything's  working fine except for the fact that my notebook is louder running  Ubuntu than it was running Windows. The problem is that the notebook  shuts itself down without warning a couple of minutes after starting a  game like ET. I'm not sure about uninstalling the proprietary driver  since the open source one, Radeon it's called I think, gave me trouble  displaying the Unity desktop properly. What do you guys suggest me to do?

---

### Post by landeel on 2011-11-20
I suppose your system may be overheating.
Can you give your specs?
Can you monitor the temperatures while playing?

---

### Post by H3R3T1K on 2011-11-20
Intel Core i5 450M
2 Gigs RAM
ATI Mobility Radeon HD 540v 512 MB

I don't know how to display CPU/GPU temperatures. System monitor doesn't show any values.

edit: I got Psensor but I don't know if it's working properly since it just names 2 out of 9 sensors: Core 0 and Core 2. I don't know which of the other 'temp's is my GPU and what the other sensors are picking up. The temperatures measured vary between 47 and 83 degrees Celsius. The fans are blowing kinda loud.

---

### Post by landeel on 2011-11-20
Hm, I have a netbook with the E-350 APU, and the APU temperature simply shows up in "sensors".

try this:
> aticonfig --od-gettemperature

---

### Post by H3R3T1K on 2011-11-21
Does APU mean that your GPU is integrated in your CPU?

I'll try the command. Still, if my machine is getting too hot it must be because of the drivers not doing their job properly, mustn't it?

---

### Post by oldrocker99 on 2011-11-21
You may be running Compiz, which is a resource hog. Try this:

sudo apt-get install fusion-icon

Then run fusion-icon and see which window manager is running. If it's compiz, change it to metacity, and your graphics should speed up.

And good luck!

---

### Post by kaldor on 2011-11-21
Like the above poster said, Compiz can be a hog when gaming. Using Unity 2d might be able to help. Log out, and select the 2d session in the gear's drop-down menu. Log back in and see if it improves anything.

Proprietary drivers seem to be very badly affected when Compiz is running.

---

### Post by H3R3T1K on 2011-11-22
OK I installed fusion icon and also dconf-editor in order to put fusion icon on the unity panel because it wouldn't stay there. I did what's suggested in this vid [http://www.youtube.com/watch?v=456oHCTFPn0](http://www.youtube.com/watch?v=456oHCTFPn0) but I can't make fusion icon stay in the panel :-(

OK, did a reboot, started fusion icon. It shows Metacity as the window manager being used. And I got the top panel and side menu. Will try if I can play.

edit: The fans turn up noticeably after starting ET. All of a sudden neither ET nor True Combat: Elite list any any servers :-( I googled the problem and the solution seems to be to add 'default masters'. Now I don't know what that means. Can't test the new settings if I can't play :-( Will try another game.

---

### Post by H3R3T1K on 2011-11-23
I'm starting to believe that my systems heat issues aren't just compiz's fault. Right now i just got Firefox, Nautilus and Psensor running and most of the temperatures measured are in the 60s with one value as high as 79 degrees celsius. There seems to be quite some people that have overheating issues with HP notebooks. I played some more games and had the system shut down on me once more. This is really frustrating.

In this (old)

[http://ubuntuforums.org/showthread.php?t=951838](http://ubuntuforums.org/showthread.php?t=951838)

thread it was recommended to add this

battery
ac
processor
thermal
acpi-cpufreq
cpufreq-userspace

to the config file in /etc/modules, install kpowersave, enable it at startup and set dynamic processor usage.

I don't know if this helps me with my GPU too but what the hell. Would you guys recommend me to try this?

---

