---
title: "won't boot to the desktop"
date: 2010-05-15
forum: Desktop Environments
---

### Post by bywhatnow on 2010-05-15
Please help......I installed Ubutu 10.4, did several suggested updates,then all of a sudden it won't boot to the desktop. I attempted to reload the OS,and it would not let me,so I opted to do a low level format on the drive,(using Troubleshooter) and all I was able to get was a bunch of errors. I assumed that my hard drive failed. So, I put in a brand new, fresh out of the package 500GB drive. Loaded my Wins\dows XP Pro,and then loaded Ubuntu (this is the 10.4 just released version). All went well, did several updates as recommended by the OS. Then I tried to change my background. The OS told me I needed to update my video driver to do this and would I like to do so now. I said yes. The OS downloaded the (one that Ubuntu said was the right one),went to restart my machine,as instructed,and now all I get are the lights on my keyboard flash, the boot up sound sounds like a broken record, and the machine is locked up.control/alt/delete do nothing have to manually shut the machine off. The two OS's were loaded in a side by side config,the video card is an Nvidia Gforce 6800GT 256 MB AGP card and works flawlessly in Win XP.I'm sure the driver is what has this messed up......BUT.......what can I do? If I format(not sure if it will let me on this drive) then I loose my working Windows as well. If I could boot into Ubuntu I may be able to figure out how to uninstall the ofending driver. Again please help.
My system is not the newest or the fastest,but should be plenty for this OS, AMD 3200+ athlon 64, 2 GB ram,10/100/1000 nic,GT6800 256 Video card.....I am very much trying to learn this OS, I have been with Windows now since 3.1 and I think I'm ready to move on.......Thank you for taking the time to read this, and hopfully you may be able to offer the advise that I need to get this running again

---

### Post by realzippy on 2010-05-16
Ok.strange issue.
If I understand the problem:

You installed XP on a brandnew HD,everything fine,then installed
Ubuntu 10.04 (Wubi?) along,made all updates,then installed the
NVIDIA driver (because of backroundimage?),what needs a reboot,then
mainboard issues?
Sounds like a weak mainboard or PSU.Did you overclock?
Can you boot in recovery mode

[http://linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html](http://linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html)

to uninstall/disable the nvidiadriver?Deleting xorg.conf should prevent
this driver from loading;lucid does not need a xorg.conf file.In recovery mode drop to root shell and type:

```

rm /etc/X11/xorg.conf
```

```
exit
```

reboot.

---

### Post by bywhatnow on 2010-05-17
> **realzippy said:**
> Ok.strange issue.
If I understand the problem:

You installed XP on a brandnew HD,everything fine,then installed
Ubuntu 10.04 (Wubi?) along,made all updates,then installed the
NVIDIA driver (because of backroundimage?),what needs a reboot,then
mainboard issues?
Sounds like a weak mainboard or PSU.Did you overclock?
Can you boot in recovery mode

[http://linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html](http://linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html)

to uninstall/disable the nvidiadriver?Deleting xorg.conf should prevent
this driver from loading;lucid does not need a xorg.conf file.In recovery mode drop to root shell and type:

```

rm /etc/X11/xorg.conf
```

```
exit
```

reboot.
No, no overclock, everything as came from the factory in that area. What told me to reboot was the OS, Ubuntu 10.4 after the updated driver was installed.....all I did was say/clicked OK and the machine went to reboot.....then just a hang/lockup....not exactly what I was expecting either. I was expecting the driver to install and just keep on keeping on........BUT.....as a Windows user....I am used to having to reboot after a driver install so......no questions I did what (I thought) the OS told me to do.......The machine is about 5 years old....but seems to be solid...I test all my hardware with the TroubleShooter and I get a clean bill of health.....do you thing I need to re format and just start over, or is there a way to remove that driver without being able to get to to Ubuntu desktop? Thank you for your time and response to my question.....would love to know if anyone else is having simalar problems with the Nvidia AGP (older higher end) video cards

---

### Post by bywhatnow on 2010-05-17
> **bywhatnow said:**
> No, no overclock, everything as came from the factory in that area. What told me to reboot was the OS, Ubuntu 10.4 after the updated driver was installed.....all I did was say/clicked OK and the machine went to reboot.....then just a hang/lockup....not exactly what I was expecting either. I was expecting the driver to install and just keep on keeping on........BUT.....as a Windows user....I am used to having to reboot after a driver install so......no questions I did what (I thought) the OS told me to do.......The machine is about 5 years old....but seems to be solid...I test all my hardware with the TroubleShooter and I get a clean bill of health.....do you thing I need to re format and just start over, or is there a way to remove that driver without being able to get to to Ubuntu desktop? Thank you for your time and response to my question.....would love to know if anyone else is having simalar problems with the Nvidia AGP (older higher end) video cards
Yes it boots to a command line in recovery mode.....BUT.....I don't know the Linux/Ubuntu commands to do anything from there

---

### Post by bywhatnow on 2010-05-18
> **bywhatnow said:**
> No, no overclock, everything as came from the factory in that area. What told me to reboot was the OS, Ubuntu 10.4 after the updated driver was installed.....all I did was say/clicked OK and the machine went to reboot.....then just a hang/lockup....not exactly what I was expecting either. I was expecting the driver to install and just keep on keeping on........BUT.....as a Windows user....I am used to having to reboot after a driver install so......no questions I did what (I thought) the OS told me to do.......The machine is about 5 years old....but seems to be solid...I test all my hardware with the TroubleShooter and I get a clean bill of health.....do you thing I need to re format and just start over, or is there a way to remove that driver without being able to get to to Ubuntu desktop? Thank you for your time and response to my question.....would love to know if anyone else is having simalar problems with the Nvidia AGP (older higher end) video cards
OK, will try this code and will let you know if it works................Thanks

---

### Post by realzippy on 2010-05-18
*.I don't know the Linux/Ubuntu commands to do anything from there*

run the above given command to delete the xorg.conf file which
"starts" the nvidia driver....(mind that capital "X")...


*.....would love to know if anyone else is having simalar problems with the Nvidia AGP (older higher end) video cards*

..used to run Athlon64 Venice with NVIDIA AGP 6600 GT on a nforce3 mainboard years ago...everything ran great.

---

### Post by bywhatnow on 2010-05-18
> **realzippy said:**
> *.I don't know the Linux/Ubuntu commands to do anything from there*

run the above given command to delete the xorg.conf file which
"starts" the nvidia driver....(mind that capital "X")...


*.....would love to know if anyone else is having simalar problems with the Nvidia AGP (older higher end) video cards*

..used to run Athlon64 Venice with NVIDIA AGP 6600 GT on a nforce3 mainboard years ago...everything ran great.
Ran the command.....was told I don't have permission to delete/uninstall xorg.....Hummmmm, I signed on as root,so should have had rights to do this.......Note to realzippy....it was running good until I tried to change my desktop back ground......bet I won't do that again........I'm thinking a format and reload may be my only answer......if you can think of anything else, please let me know.....wanting to get away from Windows, and having troubles........

---

### Post by realzippy on 2010-05-18
No idea.Fastest:
Install ubuntu again,update it;reboot,then activate the NVIDIA driver directly in *Hardware Drivers*.
Which driver are offered?

---

### Post by bywhatnow on 2010-05-19
> **realzippy said:**
> No idea.Fastest:
Install ubuntu again,update it;reboot,then activate the NVIDIA driver directly in *Hardware Drivers*.
Which driver are offered?
mark this thread as solved......not sure how to do that......I reinstalled from the CD...went to boot to Ubuntu....same thing......booted into my XP and installed from there....nicer boot menu....still no luck.....going to re format full drive and start fresh.....thanks very much for you help......this next time I won't just let the OS update my Video drivers....LOL....(LAL......live and learn)

---

### Post by Despotic on 2010-06-03
I think I'm having a similar problem.
I've got a fairly weak nVidia AGP card (6800 I think) which worked fine in 8.04.
Just installed 10.04 from scratch because the upgrade failed miserably.
Upon completion of the install, the system booted fine and I opted to install the "current" nVidia driver from the list of 3 possible from "restricted drivers"
When the driver update was complete, I restarted and X will not start.
I'm getting a terminal login screen. I can login fine, and when I do I run "startx" (that's still current right?)
errors observed:
NVIDIA(0) failed to initialize the NVIDIA graphics device PCI:2:0:0
Please check your system's kernel log for additional error messages and refer to chapter 8: Common Problems in the README for additional Info.
Failed to initialize the NVIDIA graphics device! Screen(s) found, but none have a usable configuration.
Fatal server error:
no screens found.

My Samsung 205BW is connected via DVI and worked previously.

I'm thinking I need to update xorg.conf but I've read that it is obsolete now and the kernel handles that?
I'm just a lowly private with limited configuration skillz.

Any help out there in the forums?

Thanks for your assistance.

---

### Post by Despotic on 2010-06-03
Just to clarify, I removed the xorg.conf file and restarted as recommended in this thread, with no improvement.

---

