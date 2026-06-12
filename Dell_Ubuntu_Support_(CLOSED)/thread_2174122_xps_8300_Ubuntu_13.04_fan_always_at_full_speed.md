---
title: "xps 8300 Ubuntu 13.04 fan always at full speed"
date: 2013-09-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MonsterPipe on 2013-09-12
Hi,

I'm using a DELL XPS 8300 with a i7.

OS is Ubuntu 13.04.

My fan is always running at full speed no matter what I do.
lm-sensors and pwmconfig detect no fan.

Is there another way to control the fan?

Thank you

---

### Post by mikewhatever on 2013-09-15
Here you go: 
[http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/](http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/)
[http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed)

---

### Post by MonsterPipe on 2013-09-16
Ok, a big thank! I'll those and get back to you :)

Thank you

---

### Post by MonsterPipe on 2013-09-30
I tried those thing and it does not seems to work. Installation was fine. Execution looks fine but it does not recognize any fan.

I'll try to find more about the subject, maybe there is another way.

Thanks again, :)

---

### Post by Coloban on 2013-10-02
Hello,

did you look into the graphics drivers? I am trying that right now for an ATI Card, because I tried LM-Sensors / Fanspeed Tweaks and nothing worked on my DELL INSPIRON 1545. If the gfx alway runs on high performance, the fan will run full speed too.

Right now I am on Ubuntu 13.04 and use the Open Radeon Driver, that came with it. Card is ATI Mobility Radeon RV710/M9 HD 4330 / 4350 / 4550.

Look here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I did not realize that the new GRUB Option was only coming up with 13.10, so I had to use the recovery console to undo it.
-----------------------------------------

I also tried a Thinpad solution via ACPI, that did not help.

Now I found this tool [http://manpages.ubuntu.com/manpages/hardy/man1/acpitool.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/acpitool.1.html)

Maybe that could solve the issue. But before lowering fan speed by hand, one should check temperatures, I guess...

EDIT: acpitool reports no fan found, so that one is out too
-----------------------------------------

Looking into i8kmon right now.

[URL="http://ubuntuforums.org/showthread.php?t=842775"]http://ubuntuforums.org/showthread.php?t=842775

[/URL]That thread is from 2008, I think some things have changed like the modprobe options file etc. . Also the force option should not be neccessary for all DELL models.

Readme from Ubuntu:

[http://manpages.ubuntu.com/manpages/raring/man1/i8kmon.1.html](http://manpages.ubuntu.com/manpages/raring/man1/i8kmon.1.html)

and the Readme from the package:

[http://www.shrib.com/i8kmon](http://www.shrib.com/i8kmon)

Those Manuals are not written for the average user, so it seems, I cannot extract any information from them on how to get it running correctly.

I've installed it, no problem, enabled it via the ik8man configfile in etc/default/ and rebooted.

If I open it via the console, there is an old gnome window, showing two numbers, and I can change some options. I don't know where to go from here.
Maybe someone could get more out of the links I provided above.

Also the Gnome Applet Swallower is not available anymore to get i8kmon inside the applet bar.

---

