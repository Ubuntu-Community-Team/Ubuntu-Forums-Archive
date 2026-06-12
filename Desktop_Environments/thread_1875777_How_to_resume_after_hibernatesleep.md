---
title: "How to resume after hibernate/sleep"
date: 2011-11-05
forum: Desktop Environments
---

### Post by test006 on 2011-11-05
Hi,
I am running kubuntu as my desktop OS. I would like to know how to resume the session up after i have used hibernate/sleep option. Under leave option i have Suspend and hibernate, when i use this option the computer does go into hibernate/sleep but how do i resume the session. I know in windows 7 once the computer is in sleep mode you can press and key on the keyboard and it will resume the session. Currently when i put computer into hibernate/sleep i have press the power button to bring it back up but this pretty much reboots the PC. 

Any help will be appreciated....

Thanks

---

### Post by 2F4U on 2011-11-05
You need to distinguish between suspend (suspend to RAM) and hibernate (suspend to disk). For suspend to RAM you should be able to wake the PC with a key press, while for suspend to disk you need to press the power button.
Suspend to disk takes longer by design because it first writes an image of your RAM to disk and on startup reads that image. Since the hard disk is involved, this naturally takes much longer.

---

### Post by test006 on 2011-11-05
> **2F4U said:**
> You need to distinguish between suspend (suspend to RAM) and hibernate (suspend to disk). For suspend to RAM you should be able to wake the PC with a key press, while for suspend to disk you need to press the power button.
Suspend to disk takes longer by design because it first writes an image of your RAM to disk and on startup reads that image. Since the hard disk is involved, this naturally takes much longer.

Hi thanks for response.
OK i would like to use the sleep function and than press any key to wake up the computer.
I have tried this, i.e. i go to leave and than select Sleep (suspend to RAM). Now i can see my computer basically stop, i.e. go into sleep state. Now when i press any key on the keyboard or mouse button nothing happens. I pretty much have press the power button and have to go through the reboot cycle again.

Any help with this...as i am doing anything wrong or do i need to configure anything to make this work. I have a asus H67 chipset MB with i5 processor and it has 16GB of RAM. I have this as dual boot with Windows 7 and the sleep function works fine in Windows 7.
I am using dell 24" monitor.

---

### Post by inobe on 2011-11-05
i press the power button to resume my desktop.

all applications are running as expected upon resume, my profile is set for performance.

i do see the system bios prompt during this time, a mere 5 seconds till i reach a functional desk.

---

### Post by Copper Bezel on 2011-11-06
If the system is going through any part of the boot process on resume from suspend, then your suspend and resume feature is broken. You should see at most a splash of console text while the GPU wakes up, and the resume process should take no more than a few seconds, bringing you back to your desktop or screenlock (not the login window, but a password prompt to access your desktop.) All your running applications should be where you left them.

Pressing any key should initiate the resume process.

While the machine is asleep, is the power light flashing or otherwise indicating the state? If the machine seems to be shut off completely, it probably *is*. If that's the case, there's probably a problem specific to your hardware (that can probably be solved with some Googling.) What's the make and model of your PC?

---

### Post by test006 on 2011-11-06
> **Copper Bezel said:**
> If the system is going through any part of the boot process on resume from suspend, then your suspend and resume feature is broken. You should see at most a splash of console text while the GPU wakes up, and the resume process should take no more than a few seconds, bringing you back to your desktop or screenlock (not the login window, but a password prompt to access your desktop.) All your running applications should be where you left them.

Pressing any key should initiate the resume process.

While the machine is asleep, is the power light flashing or otherwise indicating the state? If the machine seems to be shut off completely, it probably *is*. If that's the case, there's probably a problem specific to your hardware (that can probably be solved with some Googling.) What's the make and model of your PC?
Hi,
When i do sleep in linux the power light is not blinking but on the PC if i do sleep in windows 7 i can see power light blinking.
PC is home built using Asus P8H67-M H67 Chipset motherboard with i5 processor. Dell 24" monitor. 16GB of memory, 4x 4GB.

Thanks

---

### Post by Copper Bezel on 2011-11-06
Oh - that's a Sandy Bridge board. See the bug [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760842"). There are a couple of suggestions in there that might help, but depending on the chip, if might not be possible to get suspend in Linux working on your CPU.

---

### Post by xc8 on 2011-12-13
*SAME* problem with an Asrock H67 (not ONLY under Ubuntu...I tried  OpenSUSE and CentOS ... same results) ... I sent a lot of emails to the (assholes) Asrock, their reply was something like "we have no problems under windows XP/7" .... I read somewhere that Intel fixed it on their m/boards...

---

