---
title: "nvidia-settings: ERROR: Failed to add X screens to X config."
date: 2007-05-30
forum: Desktop Effects &amp; Customization
---

### Post by nickless on 2007-05-30
Hi,
Im currently trying to get Dual Screens to work (without beryl or other neat customizations...). I have a Dell Inspiron 9400 Laptop with an  GeForce Go 7900 GS and an BenQ FP93G X Flatscreen Monitor. Working with nvidia-settings (in root) I get an error, when I try to save the X Settings:
```

ERROR: Unable to determine valid vertical refresh ranges for display device 'LPL' (GPU: GeForce Go 7900 GS)!


ERROR: Failed to add display device 'LPL' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!

```

The LPL-screen is my Laptop-Screen. What can I do? Find new drivers/nvidia-settings?

---

### Post by virtualj on 2007-06-02
Hi,

I am having the same problem with my dell latitude D820 laptop and a CRT monitor.
When I run nvidi-settings as root (gksudo nvidia-settings), I can make all the changes. But when I try to save the X configuration file I get the same error.
```

ERROR: Unable to determine valid vertical refresh ranges for display device
       'LPL' (GPU: Quadro NVS 110M)!


ERROR: Failed to add display device 'LPL' to screen 1!


ERROR: Failed to add X screen 1 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!

```

---

### Post by Avvatar on 2007-06-04
I am also having this problem on my Dell laptop:
```
ERROR: Unable to determine valid vertical refresh ranges for display device
       'Seiko' (GPU: Quadro NVS 110M)!


ERROR: Failed to add display device 'Seiko' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!
```
And the settings do not save.

I don't know if its meaningful, but I also encounter an error when I start nvidia-settings:
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

Any help would be much appreciated.

---

### Post by virtualj on 2007-06-09
Anyone else with the same problem or better yet, a solution?

In 2 weeks I have to give a presentation for my exams and I need to be able to easilly attach the projector to my laptop. It would be stupid if I have to install windows on my laptop just for that presentation.

It looks like it's a Dell laptop problem.

---

### Post by freindler on 2007-07-07
Dear all,

just do this:

rm -fr /root/.nvidia-settings-rc
and maybe
rm -fr /home/YOURUSERNAME/.nvidia-settings-rc

and everything works again ;)

mfg 
freindler

---

### Post by garcher@mac.com on 2007-08-10
Well, removing the .nvidia-settings.rc files did NOT work.  I have a Dell D620 with the WUXGA screen 1440x900:  I now get the following error:
archer@USITARCHEGL1C:~$ sudo nvidia-settings

ERROR: Unable to determine valid vertical refresh ranges for display device
       'Seiko' (GPU: Quadro NVS 110M)!


ERROR: Failed to add display device 'Seiko' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!


ERROR: Unable to determine valid vertical refresh ranges for display device
       'Seiko' (GPU: Quadro NVS 110M)!


ERROR: Failed to add display device 'Seiko' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!

---

