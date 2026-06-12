---
title: "Replaced monitor. Now during boot - screen blanks (Revivable with cable re-connect)"
date: 2023-08-19
forum: Desktop Environments
---

### Post by david4100 on 2023-08-19
I have been using my Ubuntu 22.04.2 machine for a fairly long time without issues.  
All this time I had a very old monitor that has 1080p resolution at 60Hz.  
That old monitor was connected to Intel CPU's (11th gen) integrated GPU via DisplayPort.  
  

Recently I changed to a new monitor which is capable of 4K at 144Hz.  
I had set its resolution to 1440p and 120Hz.  

But whenever I power on the PC then I am able to see Ubuntu OS/Kernel loading, but then the screen blanks (all I can see is a black screen) and I get a monitor's message about a lost signal.  
(Note that I passed the phase of GRUB.)  

So I disconnect the DisplayPort cable and then I connect it again - which makes the screen to appear without issues.  
Conclusion: The issue isn't with the Graphic Driver (I don't need to update this).
  
I also noticed that by clicking *twice* (power off and then power on) on the Power button of the monitor, then after the 2nd click the monitor displayed Ubuntu properly.

I had read several resources online (URLs referred below), but I don't think that these are necessarily related to me issue, except maybe for the GRUB entry options which replaces "quiet splash" with "nomodeset".  
Also I don't want to change anything "just to try if it works" because it might break something.  

I prefer to understand what is the issue in my case - for example by reading an error in the logs - and only later after verifying the issue - then I will apply its solution.  

My GPU driver is - according to "lspci -vv":
"Kernel driver in use: i915"


Is there something I could check to understand the root cause of this issue?


Related Resources:

[https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

[https://www.yosoygames.com.ar/wp/2022/11/my-ubuntu-linux-boots-into-a-black-screen-guide/](https://www.yosoygames.com.ar/wp/2022/11/my-ubuntu-linux-boots-into-a-black-screen-guide/)

[https://askubuntu.com/questions/47506/how-do-i-install-additional-drivers](https://askubuntu.com/questions/47506/how-do-i-install-additional-drivers)

[https://linuxconfig.org/ubuntu-black-screen-solution](https://linuxconfig.org/ubuntu-black-screen-solution)

[http://ubuntuguide.net/no-input-signal-and-boots-into-blank-screen-after-ubuntu-installation](http://ubuntuguide.net/no-input-signal-and-boots-into-blank-screen-after-ubuntu-installation)

[https://www.stephenwagner.com/2019/05/05/ubuntu-linux-black-screen-frozen-system-after-upgrade-install/](https://www.stephenwagner.com/2019/05/05/ubuntu-linux-black-screen-frozen-system-after-upgrade-install/)

---

### Post by Autodave on 2023-08-19
What GPU are you using?  What driver for the GPU and where did you get the driver from?  Are you using any adapters on the display port line between the PC and the monitor?

---

### Post by david4100 on 2023-08-26
> **Autodave said:**
> What GPU are you using?
Using the internal GPU of an Intel 11th gen CPU.
(The DisplayPort cable is connected to the motherboard.)


> **Autodave said:**
> What driver for the  GPU and where did you get the driver from?
My GPU driver is - according to "lspci -vv":
"Kernel driver in use: i915"

It was automatically installed during Ubuntu installation.

> **Autodave said:**
> Are you using any adapters  on the display port line between the PC and the monitor?
No.
There is only a single DisplayPort cable which is directly connected between the motherboard DP connector and the monitor's DP connector.

---

