---
title: "Ubuntu stalls while booting and shutdown"
date: 2009-01-11
forum: General Help
---

### Post by bigbadbrad on 2009-01-11
I've had this issue since I installed ubuntu. When ever I boot up or even shutdown ubuntu hangs. I normally press and hold the space bar and it continues just fine. I would really like to fix this. Also I don't think I can suspend or hibernate.

---

### Post by Ahadiel on 2009-01-11
Do you have an HP or Compaq laptop? Because the hanging on boot can be solved by adding "acpi=noirq" to the end of the appropriate *kernel* line in /boot/grub/menu.lst.

---

### Post by whoop on 2009-01-11
Do you get any (error) messages?
You can try booting in recovery mode; then you can see where it hangs. If it runs fine in recovery mode you can try and edit menu.lst and remove the splash screen so you get more info on what your system is doing and where it hangs:

```

gksudo gedit /boot/grub/menu.lst

```

And remove "quiet splash" from the first kernel line, and reboot.

---

### Post by bigbadbrad on 2009-01-11
> **Ahadiel said:**
> Do you have an HP or Compaq laptop? Because the hanging on boot can be solved by adding "acpi=noirq" to the end of the appropriate *kernel* line in /boot/grub/menu.lst.



Hp DV6747cl to be exact. So open terminal and type in "/boot/grub/menu.lst?

NVM: Which line do I add it too?

NVM: Thanks I think I got it.

---

### Post by avtolle on 2009-01-11
> **Ahadiel said:**
> Do you have an HP or Compaq laptop? Because the hanging on boot can be solved by adding "acpi=noirq" to the end of the appropriate *kernel* line in /boot/grub/menu.lst.
Thank you. Works like a champ.

---

### Post by Ahadiel on 2009-01-11
> **avtolle said:**
> Thank you. Works like a champ.
Awesome. :D

---

### Post by avtolle on 2009-01-11
> **bigbadbrad said:**
> Hp DV6747cl to be exact. So open terminal and type in "/boot/grub/menu.lst?
No. First, hit esc while grub is loading to get into the menu; select the kernel to work with (usually the one you are currently using). Then, press the e key to edit the kernel line(the second line in my list); it will be rather lengthy. Press the e key to edit that line, go to the end of that line, press the space bar to enter a space, and type in acpi=noirq then press the Enter key when done. Press the b key to boot the machine. This will show you if it works.

If it does work, you will want to make it a permanet change by editing the grub menu.lst file. To do this, open a terminal to make a backup of your file```
 sudo cp /boot/grub/menu.lst /boot/gurb/menu.lst.original
```then while still in terminal, type```
sudo nano /boot/grub/menu.lst
```which opens the file for editing. Scroll down to the kernel line for the kernel you are using, again add a space at the end and type in the parameter given above, and press Ctrl and o (lower case letter o) at the same time, verify the file name is correct (i.e. /boot/grub/menu.lst, edit to that if it is not), press Enter to save the file, then press Ctrl and x to exit the editor. Then,ile sstill in the terminal type```
sudo update-grub
```. Exit the terminal, and check your work by restarting the system. Good luck.

EDIT: Under 8.10, the last command I gave above seems not to be needed.

---

### Post by Blue Snapper on 2009-01-22
> **Ahadiel said:**
> Do you have an HP or Compaq laptop? Because the hanging on boot can be solved by adding "acpi=noirq" to the end of the appropriate *kernel* line in /boot/grub/menu.lst.

Thanks Ahadiel, the "acpi=noirq" addition fixed the startup stalling problem on my HP Pavilion dv6736nr.

---

### Post by 67GTA on 2009-04-30
Adding acpi=noirq is not a good fix. This may disable needed services. This bug is caused by a broken DSDT file in newer HP laptop BIOS's. I can fix them. Follow my how to here to the point of getting your dsdt.dsl file and email it to me. This will fix the boot, temp, and suspend/hibernate problems. [http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt)

---

### Post by ftabor on 2009-04-30
Is this needed for 9.04?  My HP dv6917d boots fine now, on A/C without the problems from 8.10.

---

### Post by Monotoko on 2009-04-30
If it boots and shutsdown fine, its not needed, why fix something that aint broken? ;)

---

### Post by ftabor on 2009-04-30
The reason I was asking is that while it boots ok on A/C, on battery it exhibits the same problems booting that 8.10 does all the time.  I also am having problems coming out of suspend.  I have to press the power button several times to get it to wake.

---

### Post by Monotoko on 2009-04-30
I had the same problem, adding that line into my boot fixed it for me :)

---

### Post by 67GTA on 2009-04-30
The fix issued by the devs only works around the problem. Your DSDT is still broken. It is up to you weather you fix it or not. The problem is that the DSDT was compiled with Microsoft's home brewed compiler instead of the open standards Intel compiler. This lets Windows work around the errors, but Linux will choke on them. Adding acpi=noirq disables acpi irq routing, and can cause trouble on newer PC's. This is only making the kernel ignore hardware specs/capabilities. Is your PC running warm? Is the fan loud? Post the output of these commands:

```
cat /proc/acpi/thermal_zone/THRM/state
```

```
cat /proc/acpi/thermal_zone/THRM/trip_points
```

---

### Post by ftabor on 2009-04-30
```
cat: /proc/acpi/thermal_zone/THRM/state: No such file or directory
```

```
cat: /proc/acpi/thermal_zone/THRM/trip_points: No such file or directory.
```

---

### Post by 67GTA on 2009-04-30
Your thermal capabilities aren't being recognized. Ubuntu is just guessing at the correct temp. That is a big reason to fix it IMHO. One more thing:

```
sudo apt-get install acpi
```

```
acpi -V
```

---

### Post by 67GTA on 2009-04-30
You can also check by running ```
dmesg | grep MFST
``` If this returns anything with MFST in it, then you know for sure that your BIOS DSDT was compiled with Microsoft's aml compiler and will not completely work right with Linux unless you correct the errors made by Microsoft's lazy compiler.

---

### Post by 67GTA on 2009-04-30
This has happened recently with Foxconn, but they were forced to fix it. If you remember the Microsoft antitrust lawsuit, this was one of the arguments. Read here: [http://hehe2.net/thedarkside/even-more-incriminating-evidence-in-the-foxconn-debacle/](http://hehe2.net/thedarkside/even-more-incriminating-evidence-in-the-foxconn-debacle/) The end of Bill's email talks about patenting something. Their own aml compiler was the answer. BIOS venders get kickbacks from Microsoft to use their compiler instead of industry standards.

---

### Post by ftabor on 2009-04-30
> **67GTA said:**
> You can also check by running ```
dmesg | grep MFST
``` If this returns anything with MFST in it, then you know for sure that your BIOS DSDT was compiled with Microsoft's aml compiler and will not completely work right with Linux unless you correct the errors made by Microsoft's lazy compiler.

This one returns nothing.  I just go back to $.

Still working on installing apci.  root, (in it's own partition) got filled by simple backup.

---

### Post by ftabor on 2009-04-30
> **67GTA said:**
> The fix issued by the devs only works around the problem. Your DSDT is still broken. It is up to you weather you fix it or not. The problem is that the DSDT was compiled with Microsoft's home brewed compiler instead of the open standards Intel compiler. This lets Windows work around the errors, but Linux will choke on them. Adding acpi=noirq disables acpi irq routing, and can cause trouble on newer PC's. This is only making the kernel ignore hardware specs/capabilities. Is your PC running warm? Is the fan loud? Post the output of these commands:

```
cat /proc/acpi/thermal_zone/THRM/state
```

```
cat /proc/acpi/thermal_zone/THRM/trip_points
```

I installed acpi.  /proc/acpi/thermal_zone/ is empty.

The output of ~$ acpi -V
     Battery 0: Full, 100%, rate information unavailable
     Battery 0: design capacity 6000 mAh, last full capacity 4288 mAh = 71%
  AC Adapter 0: on-line
     Cooling 0: LCD 0 of 10
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10


And as noted previously, ```
dmesg | grep MFST
``` returned nothing

---

### Post by 67GTA on 2009-04-30
I'm an idiot. I misspelled it.

```
dmesg | grep MSFT
```

---

### Post by ftabor on 2009-04-30
> **67GTA said:**
> I'm an idiot. I misspelled it.

```
dmesg | grep MSFT
```

```
~$ dmesg | grep MSFT
[    0.000000] ACPI: DSDT BBF5C0F8, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
```


It looks as if the NVIDIA drivers are the only thing being controlled.  I think I'll just leave things alone.  The suspend issue isn't worth the trouble to try to correct.  And there's no guarantee that it will fix the suspend issue.

But thanks for information and assistance.

---

### Post by 67GTA on 2009-04-30
That is your motherboard chipset, not your graphics driver. It is ultimately your decision, but is not much trouble, and is very painless:) You might want to read all of the bug reports here before shrugging it off. Microsoft is basically controlling your PC. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247?comments=all)

Be sure to expand the messages. There are 300+

---

### Post by ftabor on 2009-04-30
I probably should, but your procedure is a little daunting.  While I can change points and plugs, I can't work on fuel injection or automatic transmissions.  :)

---

### Post by 67GTA on 2009-05-01
Thanks for pointing out the typo. I edited the how to. Just send me your dsdt.dsl if you ever change your mind.

---

### Post by ftabor on 2009-05-01
I got one error fixed, but there are 6 warnings, and while it worked, it still doesn't populate /fan or /thermal_zone.  Should I attach to a post here, or send it via private message?  I guess I would like to get it operating properly.

---

### Post by 67GTA on 2009-05-01
You can just email me the dsdt.dsl file, and I can email it back to you when I get it fixed.

---

