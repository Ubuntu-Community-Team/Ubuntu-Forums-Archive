---
title: "CPU fan speed, temperatures,etc..."
date: 2009-05-01
forum: General Help
---

### Post by klemzy on 2009-05-01
Hi!

I have recently installed Ubuntu 9.04, before that I was on Windows, so I'm quite new on this scene. Generaly I made everything working for now, however I ran into some problems with CPU load, temperatures and fan speed. First problem is that cpu fan runs all the time, and when CPU get hotter fan goes louder, which is logical, however when CPU temps cools down, fan is still loud, it is not flexible to temperatures. On windows fan switched on cooled CPU then after some time switched off (not for long but it did), I tried everything , lm-sensors (tried tutorial), but half of sensors didn't work, only cpu temps. Then kgrull, coretemp, installed acpi, tried to update bios (which was already up to date), now I ran out of ideas. Another problem that occurs is CPU load, when I play videos on youtube, CPU load goes to 70% and temps go 50-51 celsius. Is this normal?  I'll be very glad if someone could give me some advice, because this is becoming very frustrating.

Thanks in advance!

---

### Post by wpshooter on 2009-05-01
Is this a laptop or a desktop ?

Is there any of those fancy parameters in the BIOS regarding how fan speed, etc. are handled ?  If there are, my recommendation would be that you turn them off/disable and then see if you still have fan speed problems.

Also, are you running Ubuntu or Kubuntu ?  Do you have Xsensor program installed and working ?

---

### Post by klemzy on 2009-05-02
Hi!


I have a dell laptop, the only thing in bios is speedstep, bu this one handles processor doesn't it? I'm using ubuntu.
I tried Xsensors like you suggester, but it says "Sensors coretemp not supported by xsensors.".
Is there a possibility that i have overidden some config files for fan?. I have also question what  is the difference between coretemp and lm-sensors?

---

### Post by danwood76 on 2009-05-02
Have you tried updating the BIOS for your motherboard?
Sometimes this can help alot with regards to BIOS ACPI support.

Most BIOS ACPI (the thing that controls power, fans, etc) are geared for windows and linux has implemented the API as much as possible but some BIOS are still slightly incompatible, updating can usually solve some issues.

Have you got any boot options enabled like acpi = off?

---

### Post by klemzy on 2009-05-02
Well I tried to update my bios already, but it says that it doesn't need to be updated, even though I have version A03 , the latest version is A06, I used dell-firmware-tools and the instructions provided by dell to update bios. I also looked in menu.lst and there are no options acpi=off, so it is on right? I also boot with options acpi=on and no difference.

---

### Post by wpshooter on 2009-05-02
Go back and re-read the instructions for updating the BIOS.

Are you trying to update BIOS from within an O/S like windows ?

If so, my suggestion would be that you NOT do that and instead update the BIOS from a bootable sources.

---

### Post by klemzy on 2009-05-02
Problem solved!

Here is what i've found:
1. When playing videos on youtube, CPU load went 60%, I just removed swfdec and installed adobe-flash player and voila almost 0% CPU load when playing videos.
2. My fan was running all the time because of the GPU drivers, I was running radeon drivers, then switched to fglrx and now fan is working as it should be.

Thank you for your help anyway...hope this will help someone to.

---

