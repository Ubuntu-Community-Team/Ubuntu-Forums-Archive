---
title: "Can't enable Visual Effects"
date: 2011-05-30
forum: Desktop Environments
---

### Post by AngelAir on 2011-05-30
I'm running Ubuntu 10.10 64bit on my system. Upgraded the NVidia driver to the latest one on the NVidia website: 270.41.19 to see if it corrected a problem of when VEs were enable (even Normal not Extra), I got a white or blank screen.  I could tell the system was still working because I got the text info bubbles when I moved the mouse; but when I open an app or a window, the screen was blank.

After updating the driver; I can see a sharper and faster rendering image but when I enable the VEs I still get the blank screen.

---

### Post by wildmanne39 on 2011-05-30
> **AngelAir said:**
> I'm running Ubuntu 10.10 64bit on my system. Upgraded the NVidia driver to the latest one on the NVidia website: 270.41.19 to see if it corrected a problem of when VEs were enable (even Normal not Extra), I got a white or blank screen.  I could tell the system was still working because I got the text info bubbles when I moved the mouse; but when I open an app or a window, the screen was blank.

After updating the driver; I can see a sharper and faster rendering image but when I enable the VEs I still get the blank screen.Hi, have you went to synaptic and installed ccsm and all plugins including fusion?

---

### Post by AngelAir on 2011-05-31
Thank you for your responce.

If you mean Compiz; yes is installed.  I ran Perfecbuntu 6 from Category5.  One of the things it installed among others was Compiz. It also istalled Emerald Theme Manager.

I am sorry but I still traying to learn more about Linux / Ubuntu.  I know that I don't know exactly where or what to do, yet!!

Let me know if there is other information that can help you help me with this issue.

Thank you!!!

---

### Post by wildmanne39 on 2011-05-31
> **AngelAir said:**
> Thank you for your responce.

If you mean Compiz; yes is installed.  I ran Perfecbuntu 6 from Category5.  One of the things it installed among others was Compiz. It also istalled Emerald Theme Manager.

I am sorry but I still traying to learn more about Linux / Ubuntu.  I know that I don't know exactly where or what to do, yet!!

Let me know if there is other information that can help you help me with this issue.

Thank you!!!Hi, you need to install ccsm, type that into the search window in synaptic and it bring it up that is how you configure compiz when it comes up install it and there will be plug ins and install them including infusion, I tried emerald a long time ago then uninstalled it, I do not remember how to set it up but do not use it and ccsm with out getting instructions because I do not remember if they can be active at the same time but I pretty sure they cant because they are both window managers so it would cause a conflict.

---

### Post by AngelAir on 2011-05-31
The CompizConfig Settings Manager was installed by the Perfecbuntu 6.

---

### Post by wildmanne39 on 2011-05-31
> **AngelAir said:**
> The CompizConfig Settings Manager was installed by the Perfecbuntu 6.
Hi , what about the extra plugins? Sorry I was wrong about one thing in synaptic type in compiz and then it shows the plugins. Here are some screen shots.

---

### Post by wildmanne39 on 2011-05-31
> **AngelAir said:**
> The CompizConfig Settings Manager was installed by the Perfecbuntu 6.Hi, the last 2 did not get on the other post like it was suppose too.

---

### Post by AngelAir on 2011-05-31
As far as I can tell the plugins are installed.  The 1st SS is wat is installed.  The 2nd is after enabling Normal VEs.  The 3rd is after disabling VEs.

---

### Post by wildmanne39 on 2011-05-31
> **AngelAir said:**
> As far as I can tell the plugins are installed.  The 1st SS is wat is installed.  The 2nd is after enabling Normal VEs.  The 3rd is after disabling VEs.Hi, what nvidia card do you have and what is your system specs? I have to use the old driver for my card the new one is stilling having issues. With the old one I got white windows when they were maximized, but if I shrank them far enough they would show up properly, are you logged in to ubuntu classic?

---

### Post by AngelAir on 2011-06-01
Hello and again thank you for your help.

My system is an eMachines W3115 with an NVIDIA GeForce 6100 GPU. The OS is Ubuntu 10.10 64bit, GNOME 2.32.0.  ?? Logge into Ubuntu Classic? ??

---

### Post by wildmanne39 on 2011-06-01
> **AngelAir said:**
> Hello and again thank you for your help.

My system is an eMachines W3115 with an NVIDIA GeForce 6100 GPU. The OS is Ubuntu 10.10 64bit, GNOME 2.32.0.  ?? Logge into Ubuntu Classic? ??Hi, my nvivdia card is the 6150, I think you should activate the 173 or if you have the 185 and it worked at one time try that one,because the new driver has been causing problems,make sure you have only one active by going into synaptic and put nividia in the search box.:)

---

### Post by fetbec on 2011-06-01
> **wildmanne39 said:**
> Hi, have you went to synaptic and installed ccsm and all plugins including fusion?
hello,
i'm new in linux os also computer, i have Thinkpad T420 with Win7, recently i install Ubuntu 10.04 LTS 64Bits, and i cannot connect to internet, i get on network manager applet: "no network devices available", also Ubunto cannot detect any hardware, just i have sound.
so please can u teach me how to do, please !!!!!!!!!!!!!!!!!

---

### Post by wildmanne39 on 2011-06-01
> **fetbec said:**
> hello,
i'm new in linux os also computer, i have Thinkpad T420 with Win7, recently i install Ubuntu 10.04 LTS 64Bits, and i cannot connect to internet, i get on network manager applet: "no network devices available", also Ubunto cannot detect any hardware, just i have sound.
so please can u teach me how to do, please !!!!!!!!!!!!!!!!!Hi, you will be able to get more help if you start your own thread by clicking networking and wireless and post there by clicking new thread.That is back a the forums main page.

---

### Post by wildmanne39 on 2011-06-01
> **AngelAir said:**
> Hello and again thank you for your help.

My system is an eMachines W3115 with an NVIDIA GeForce 6100 GPU. The OS is Ubuntu 10.10 64bit, GNOME 2.32.0.  ?? Logge into Ubuntu Classic? ??
Hi, I installed the new 270 driver again a few minutes ago because I was told it was fixed but it is not when I stalled it I got the same white or blank windows that you have so go to synaptic and uninstall 270 and reinstall the 173 then restart.):P

---

### Post by AngelAir on 2011-06-01
Sorry that it took so long to answer; but, ran into problems.

I went to SPM to look for the Nvidia drivers: 173 and 185.  Tried first the 185 (Screenshot-4).  I tried enabling everything that said 185.  Rebooted the system then tried to enable VEs to Normal.  Got a message that stated that the VEs could not be enabled.  Checked in the Additional Drivers.  The nvidia_current drivers were activated but not in use.  The NVIDIA X Server Settings showed that the 270.41.19 was still being used.

Un-installed all the nvidia drivers from SPM and rebooted the system.  The system only booted to tty. I was lost.  Redid the steps to install the 270.
Was able to log back into system to wright and tell you what happen.

---

### Post by wildmanne39 on 2011-06-02
> **AngelAir said:**
> Sorry that it took so long to answer; but, ran into problems.

I went to SPM to look for the Nvidia drivers: 173 and 185.  Tried first the 185 (Screenshot-4).  I tried enabling everything that said 185.  Rebooted the system then tried to enable VEs to Normal.  Got a message that stated that the VEs could not be enabled.  Checked in the Additional Drivers.  The nvidia_current drivers were activated but not in use.  The NVIDIA X Server Settings showed that the 270.41.19 was still being used.

Un-installed all the nvidia drivers from SPM and rebooted the system.  The system only booted to tty. I was lost.  Redid the steps to install the 270.
Was able to log back into system to wright and tell you what happen.
Hi, the part that says it is not in use is just a bug if you activated it, it is in  use, also when I installed the 270 from synaptic today it did not remove the 173 so I had 2 active at the same time and it caused problems. Make sure you only have one installed through synaptic, I would think since your card is a 6000 series like mine it would run best with the 173, just not 2 at the same time. Your card is a 6000 series but it is a little older then mine you might not be able to run the cube,but I think that older driver should get rid of your blank windows.

---

### Post by AngelAir on 2011-06-03
I am not able to uninstall the 190 driver and go back to 185 or 173.  When I remove all drivers from SPM and reboot the system it reboots to tty mode and I have to reinstall the 190 (270.41.19) driver to log onto the GNome gui.  I I choose a driver from SPM and reboot the system, the NVIDIA X Server Settings shows that the 190 is still in use.

---

