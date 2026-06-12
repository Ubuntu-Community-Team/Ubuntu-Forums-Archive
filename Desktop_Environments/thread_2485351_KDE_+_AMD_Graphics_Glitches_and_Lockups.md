---
title: "KDE + AMD Graphics Glitches and Lockups"
date: 2023-03-28
forum: Desktop Environments
---

### Post by SadaraX on 2023-03-28
**TLDR The Problem**: I'm having serious KDE graphical issues.


**Symptoms Details**: On a fresh bootup/restart, the system works fine, until I put it to sleep. After waking up, there will be gradually increasing graphical glitches, until the entire graphic system freezes and becomes completely unresponsive. Examples: 

* Menus will appear completely BLACK
* Save-File windows, pop-up windows, new Dolphin or Gwenview windows will be completely black.

The system will still be partially usable for a while, as these errors increase in frequency. I have tried toggling on/off the KDE Compositor, which will *clear* the BLACK window problem, but only temporarily for some applications.

Toggling on/off the Compositor will not delay or stop the total graphic session lockup. Without fail, eventually the graphical session will **completely lock-up** and **block any keyboard input**. (Unless I reboot before the lockup.)

Initially:
[IMG]https://i.stack.imgur.com/0NVh7.png[/IMG]

Then eventually:
[IMG]https://i.stack.imgur.com/eZw9w.png[/IMG]

And finally total graphics system lockup.


NOTE on Input: In KDE you can assign a shortcut hotkey sequence to do an no-prompts automatic KDE logout and reboot.When the whole graphics session freezes, even this key sequence will not work.

But this appears to be limited only to the graphical session: But the underlying system is still working. I can press CTRL+ALT+SHIFT+F2 for example, which will take me to an emergency console and I can run all my normal commands from there.


**System Info**:

I'm using Kubuntu 22.10, with backports enabled for the upcoming release of 23.04.


```

Operating System: Kubuntu 22.10
KDE Plasma Version: 5.27.3
KDE Frameworks Version: 5.104.0
Qt Version: 5.15.6
Kernel Version: 5.19.0-38-generic (64-bit)
Graphics Platform: X11
Processors: 24 × AMD Ryzen 9 5900X 12-Core Processor
Memory: 62.7 GiB of RAM
Graphics Processor: AMD Radeon RX 580 Series
Manufacturer: Gigabyte Technology Co., Ltd.
Product Name: X570 AORUS ELITE WIFI
System Version: -CF
```


I have tried turning on 'TearFree' but it does not seem to help.

My /etc/X11/xorg.conf.d/20-amdgpu.conf file:

```

# /etc/X11/xorg.conf.d/20-amdgpu.conf
Section "Device"
    Identifier           "AMD"
    Driver               "amdgpu"
    Option "DRI"         "3"
    Option "TearFree"    "true"
EndSection
```

This has persisted with my Kubuntu system since at least 22.04 and it is driving me crazy. I would appreciate ANY help, including possibly moving distros to something else!

(I would even be happy to know how to safely shutdown KDE from commandline! But I've never found anything that worked for modern KDE-5.)

  [1]: [https://i.stack.imgur.com/0NVh7.png](https://i.stack.imgur.com/0NVh7.png)
  [2]: [https://i.stack.imgur.com/eZw9w.png](https://i.stack.imgur.com/eZw9w.png)

---

### Post by kinddolphin8827 on 2023-04-13
It would very advantages to everyone on these forums.

1. A Log dump of your x windows logs
2. a more through explanation of the issue(s) that your running up against.

---

### Post by SeijiSensei on 2023-04-13
If you leave it in the text-mode display for a long period of time, do you experience similar symptoms? Trying to rule out Linux here and make sure everything works fine on the hardware side. 

Can you boot into Windows and see if it happens there? I'm wondering about possible heat issues as the graphics card is used more and more.

"sudo shutdown now" usually works. You'll have to turn off the system manually after it goes back to single-user mode. I've had issues with turning my system off from KDE as well. "sudo reboot" is another option.

I've used Kubuntu since 8.04. I've never seen this problem. However I only ever use NVIDIA graphics hardware, so if this is an AMD-specific problem I won't have seen it.

---

### Post by ActionParsnip on 2023-04-14
Have you tried a different theme (If you are able)?

---

### Post by blackbird34 on 2023-04-21
bumping the thread - I have this issue too and have no idea how to deal with it apart from rebooting.

EDIT: pressing Alt+ Shift + F12 twice disables and re-enables the KDE compositor and the problem seems to go away.

---

