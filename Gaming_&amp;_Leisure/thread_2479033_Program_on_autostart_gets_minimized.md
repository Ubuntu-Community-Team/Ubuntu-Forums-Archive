---
title: "Program on autostart gets minimized"
date: 2022-09-12
forum: Gaming &amp; Leisure
---

### Post by groddjur42 on 2022-09-12
Hi,

I have installed RetroPie and want it to autostart (because then I would not need keyboard, only controller). It does autostart but gets send to the taskbar on the left side after a only a few seconds.

Is there any way to prevent this?

Thanks for advice
Martin

---

### Post by ActionParsnip on 2022-09-14
What is the output of
```

lsb_release -a; uname -a

```
Thanks

---

### Post by mIk3_08 on 2022-09-15
> **groddjur42 said:**
> Hi,
I have installed RetroPie and want it to autostart (because then I would not need keyboard, only controller). It does autostart but gets send to the taskbar on the left side after a only a few seconds.
Is there any way to prevent this?
Thanks for advice
Martin
ActionParsnip is asking you your system info. so he can escalate your system regarding the issue. Regards and cheers
```
hostnamectl status
```

---

### Post by groddjur42 on 2022-09-23
Sorry for not being able to reply sooner.

Here is what you asked for:

```
lsb_release -a

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
```

```
uname -a

Linux NES 5.15.0-48-generic #54-Ubuntu SMP Fri Aug 26 13:26:29 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

```
hostnamectl status

 Static hostname: NES
       Icon name: computer-desktop
         Chassis: desktop
      Machine ID: ec2f07ec8f364721bdaeb2c45d6be39f
         Boot ID: 821a86f1ef604f1ba1f2b67d95691cb8
Operating System: Ubuntu 22.04.1 LTS
          Kernel: Linux 5.15.0-48-generic
    Architecture: x86-64
 Hardware Vendor: To Be Filled By O.E.M.
  Hardware Model: To Be Filled By O.E.M.

```

---

### Post by ajgreeny on 2022-09-23
I had to look to find what retropie is and it seems that the application is for **gaming** and **Respberry-Pi** hardware so have moved this thread accordingly as I doubt it has anything to do with your DE.

Moved to Gaming.

---

### Post by skorpien on 2022-10-16
> **ajgreeny said:**
> I had to look to find what retropie is and it seems that the application is for **gaming** and **Respberry-Pi** hardware so have moved this thread accordingly as I doubt it has anything to do with your DE.

Moved to Gaming.

Hi ajgreeny. Actually, RetroPie can be installed on a Debian/Ubuntu system using the terminal, [as is outlined here]("https://retropie.org.uk/docs/Debian/").

I am experiencing the same issue as the OP, where running RetroPie on startup is minimizing it automatically. This happens whether I use gnome-terminal to launch emulationstation (the script that is added by RetroPie setup), or if I launch emulationstation directly.

This issue doesn't happen when running the commands manually through the terminal, only on startup using Startup Applications.

---

### Post by mIk3_08 on 2022-10-17
> **skorpien said:**
> 
I am experiencing the same issue as the OP, where running RetroPie on startup is minimizing it automatically. This happens whether I use gnome-terminal to launch emulationstation (the script that is added by RetroPie setup), or if I launch emulationstation directly.
 This kinda tricky.  Maybe you should create a script with maximize command then run the script in your start application. Actually, I'm not so expert on this but maybe it will work. Regards and cheers.

---

### Post by skorpien on 2022-10-19
> **mIk3_08 said:**
> This kinda tricky.  Maybe you should create a script with maximize command then run the script in your start application. Actually, I'm not so expert on this but maybe it will work. Regards and cheers.
Thank you for the reply :) I've tried using the --maximize argument but that unfortunately did nothing.

After extensive troubleshooting and coming up with nothing, I decided to try a different Linux distro. I installed Ubuntu Mate 22.04 LTS and that seems to have solved the issue.

I'm still uncertain what was causing it, but my guess would be some other program being run and shifting focus from emulationstation, thus minimizing it? This is purely conjecture though.

The problem hasn't presented itself thus far with Mate, and I'm hoping it won't in the future.

---

### Post by skorpien on 2022-10-19
So it seems I spoke too soon. The behaviour started again with Ubuntu Mate, but thankfully it was accompanied by an error message.

After research, it seems the **retropie** autostart script was causing the program **lightdm** to crash due to a race condition.

Adding the following to **/etc/lightdm/lightdm.conf** has once again fixed things... fingers crossed...
```

[LightDM]
logind-check-graphical=true
```
[S]I believe this solution would also work for plain Ubuntu as I think **lightdm** was crashing silently but still causing **emulationstation** to minimize.[/S]

Ubuntu doesn't have **lightdm** installed, so this solution doesn't work.

---

### Post by mIk3_08 on 2022-10-20
> **skorpien said:**
> but my guess would be some other program being run and shifting focus from emulationstation, thus minimizing it?. Maybe, I doubt the same. Other application program that triggered to automatically minimize your emulationstation application program or also it maybe on jammy because jammy uses almost all latest application features when it was release. Or it maybe in your emulationstation settings. Regards and cheers

---

