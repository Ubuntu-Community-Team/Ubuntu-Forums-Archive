---
title: "Gnome on Windows"
date: 2010-01-17
forum: Desktop Environments
---

### Post by ferdinanddemara on 2010-01-17
I've been using Ubuntu for over a year now and because of it I can once again have pride in being a PC owner. However, I recently got a new laptop and while ubuntu works perfectly, I'm afraid that it will cause unnecessary wear and tear on the hardware itself. For example, there a constant high pitched noise is produced whenever I use ubuntu (but my laptop is whisper silent using windows 7). Also, the cpu temperature using ubuntu is twice that of the temperature using Windows. 

So to protect my investment, I'm forced to downgrade to windows. However, I would very much like to keep the user interface (eg Gnome, AWN) which I had with Ubuntu. Is there any way to do this? I've heard about xming and cygwin, but which do you think is faster/more stable. 

Much appreciated!

---

### Post by blackened on 2010-01-17
Your problem lies in Ubuntu not properly recognizing the ACPI capabilities of your machine. This is pretty common with laptops.

What is the brand/model of your laptop? We may be able to make some progress with a little more information.

---

### Post by chaanakya_chiraag on 2010-01-17
I don't think it's possible to run a Desktop Environment in cygwin because for one, it would need to completely replace Windows Explorer, which is NOT happening.  So, pretty much, Gnome probably won't work.  AWN, however, might.  However, you would have to install Xorg and run AWN on top of that, which would probably wreak havoc on Windows 7.  I'd say try to figure out what's going on :)  I'm pretty sure this is a fan problem (the fan isn't turning on automagically) which should be relatively easy to fix if the make/model of the laptop is known.
- Chiraag

---

### Post by efflandt on 2010-01-17
You might mention what computer mfr and model, because without knowing what hardware you have, anyone who answers may be totally guessing about unrelated possibilities.  In fact, you have not even mentioned which Ubuntu version you are using, since it may be something that was corrected in a more recent version.  For example I have seen posts of people complaining about laptop battery life and heat with Ubuntu, but that was earlier versions.

I had seen Windows 7 users complaining about heat around the mousepad of certain Dell models from Best Buy, but one I ordered directly from Dell for someone was a only mildly warm and 64-bit Ubuntu 9.10 ran fine throttling the cpu with minimal heat, only turning the laptop fan on when necessary (busy).

PS: When running Linux years ago with a new unsupported video card, the fan on the card ran full speed all the time in Linux instead of as needed.  But that may happen if you are on the bleeding edge of new hardware, unless willing to participate and learn how to troubleshoot or program new drivers.

---

### Post by ferdinanddemara on 2010-01-17
To be honest I've had given up: I've been spooked about claims of Ubuntu causing unnecessary wear and tear on machines.

My laptop is a Lenovo t500 , with  Intel Core 2 Duo processor P8700 (2.53GHz 1066MHz 3MBL2) and I am running ubuntu 9.10. 
I read up on similar problems that other lenovo users were having ([http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises#Solutions_for_CPU-triggered_noise](http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises#Solutions_for_CPU-triggered_noise)), but couldn't figure out their instructions... For example, it says to "Pass the processor.max_cstate=3 kernel argument" Does that mean that i create a new file in /etc/modprobe.d/ with only  "options processor max_cstate=3"?

The second thing I've noticed is the cpu temperature... with Ubuntu it is usually about 40, but in Windows 20 is the usual temp. A CPU monitor tells me that CPU scaling isn't enabled on my laptop...could this be the reason?

What other diagnostics can I run to compare the physical effect of windows and ubuntu on my hardware? Haha, I have great hopes now that I'll be able to keeping using ubuntu.

---

### Post by gradinaruvasile on 2010-01-17
Attach a cpu frequency scaling monitor to the taskbar (right click on taskbar, add). If its working you should set the ondemand governor to keep the frequency at minimum when idle.

---

### Post by ferdinanddemara on 2010-01-17
thank you, i tried cpu scaling, but it has a negligible effect. Does ubuntu still cause hard drive problems: eg) [http://istunner.com/?p=91](http://istunner.com/?p=91) ? or has that been fixed?

---

### Post by sliketymo on 2010-01-17
You do realize that that is just that particular individuals experience ?

---

### Post by ferdinanddemara on 2010-01-17
hey, there's a lot of other articles on the same thing, that was one example: another one: [http://www.theinquirer.net/inquirer/news/1038568/ubuntu-eats-lappy-hard-drive](http://www.theinquirer.net/inquirer/news/1038568/ubuntu-eats-lappy-hard-drive)

are the specs i posted enough, or is more info needed?

---

### Post by mick222 on 2010-01-17
Hi their is a project to port kde to windows, just google it, but not gnome as far as i know.

---

### Post by prosigna on 2010-01-17
You have said which laptop but not which Ubuntu (9.04, 9.10, ... ) or which kernel.  I have a brand new T500 but it has a T9400 cpu and I have not experienced any of the problems you described regarding heat or fan noise running 9.10.

---

### Post by ferdinanddemara on 2010-01-18
sorry, i didn't realize: i'm using 9.10

---

