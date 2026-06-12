---
title: "Need help with my Hp pavilion dv5 and sound"
date: 2009-04-30
forum: General Help
---

### Post by eyeshield23 on 2009-04-30
Hello, I'm a total noob with Ubuntu and just upgraded two hours ago. I need help as I get now sound from anything. This includes youtube videos and downloaded youtube videos I play with vlc. How do I get sound working on my dv5-1000? I'm also a complete noob to linux so I wont understand anything unless you guys dumb it down for me. Thanks in advance.

---

### Post by DeMus on 2009-04-30
> **eyeshield23 said:**
> Hello, I'm a total noob with Ubuntu and just upgraded two hours ago. I need help as I get now sound from anything. This includes youtube videos and downloaded youtube videos I play with vlc. How do I get sound working on my dv5-1000? I'm also a complete noob to linux so I wont understand anything unless you guys dumb it down for me. Thanks in advance.

Okay, let's start with the most obvious:
are your speakers connected and switched on?
When you have booted into Gnome and you see your desktop, on top you see what is called a panel. On the right side you see a loudspeaker. Click it and then select Volume control.
You should see the mixer now. Are there any volume control buttons all the way down or marked with a red cross at the bottom? If so, slide them up with your mouse or click on the speaker symbol at the bottom (the ones with a red cross) to make the cross disappear.

Do you have sound now?
If not we'll continue:
On the top panel click on System and select Preferences to open up a menu. In this drop down menu click on Sound.
In the window you see now do you have similar items selected as I have (see attached pictures)
When pushing the test button on the right, do you hear sound now?

Let's start with this. In the mean time if somebody else knows anything about sound (s)he can also join and help you.

---

### Post by eyeshield23 on 2009-04-30
> **DeMus said:**
> Okay, let's start with the most obvious:
are your speakers connected and switched on?
When you have booted into Gnome and you see your desktop, on top you see what is called a panel. On the right side you see a loudspeaker. Click it and then select Volume control.
You should see the mixer now. Are there any volume control buttons all the way down or marked with a red cross at the bottom? If so, slide them up with your mouse or click on the speaker symbol at the bottom (the ones with a red cross) to make the cross disappear.

Do you have sound now?
If not we'll continue:
On the top panel click on System and select Preferences to open up a menu. In this drop down menu click on Sound.
In the window you see now do you have similar items selected as I have (see attached pictures)
When pushing the test button on the right, do you hear sound now?

Let's start with this. In the mean time if somebody else knows anything about sound (s)he can also join and help you.yep I tried and it still wont work I don't even hear anything when pressing test and its all not muted.

---

### Post by DeMus on 2009-04-30
> **eyeshield23 said:**
> yep I tried and it still wont work I don't even hear anything when pressing test and its all not muted.

Okay, we go on:

Click Applications (in top panel) - Accessories - terminal
to open up a terminal. Drag the corners to get a monitor wide size.
In here type 
```
lspci
```

Select the output of the lspci code and use Shift-Ctrl-C to copy the text.
Paste it in your answer.

lspci is showing a list of your hardware. This is all it does.

---

### Post by Brandon Williams on 2009-04-30
Elsewhere, I see some information suggesting that you may be able to fix this by specifying your computer model when you load the sound driver.

Add the following line to /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=hp-dv5
```

You will have to open the config file using your favorite editor and sudo:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```

I don't have a dv5 myself, so I'm only relaying the suggestion. Please let us know if it works for you.

---

### Post by eyeshield23 on 2009-04-30
> **DeMus said:**
> Okay, we go on:

Click Applications (in top panel) - Accessories - terminal
to open up a terminal. Drag the corners to get a monitor wide size.
In here type 
```
lspci
```Select the output of the lspci code and use Shift-Ctrl-C 

lspci is showing a list of your hardware. This is all it does.alright heres what I got 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by eyeshield23 on 2009-04-30
> **Brandon Williams said:**
> Elsewhere, I see some information suggesting that you may be able to fix this by specifying your computer model when you load the sound driver.

Add the following line to /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=hp-dv5
```You will have to open the config file using your favorite editor and sudo:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```I don't have a dv5 myself, so I'm only relaying the suggestion. Please let us know if it works for you.can you dumb it down as I don't quite understand

---

### Post by Brandon Williams on 2009-04-30
I think I just put the two instruction steps in the wrong order.

1. open the alsa-base module config file with nano
```
sudo nano /etc/modprobe.d/alsa-base.conf
```

2. use the editor to add this line at the bottom of the file
```
options snd-hda-intel model=hp-dv5
```

3. save the file, close the editor, and reboot to see if this suggestion solves the sound problem

If it doesn't solve the problem, then repeat step 1 to open the file in the editor and remove the line you added in step 2.

---

### Post by eyeshield23 on 2009-04-30
> **Brandon Williams said:**
> I think I just put the two instruction steps in the wrong order.

1. open the alsa-base module config file with nano
```
sudo nano /etc/modprobe.d/alsa-base.conf
```2. use the editor to add this line at the bottom of the file
```
options snd-hda-intel model=hp-dv5
```3. save the file, close the editor, and reboot to see if this suggestion solves the sound problem

If it doesn't solve the problem, then repeat step 1 to open the file in the editor and remove the line you added in step 2.worked great the only thing that doesnt work now is the volume thing on my labtop. When I move it volume isnt lowered.

---

### Post by Brandon Williams on 2009-04-30
Glad that worked for the sound.

I've got a dv7, so I expect the volume thing on my laptop is quite similar to yours. Here's what I did ...

Configure a custom keyboard shortcut that runs this command 'aumix -v -10'. When asked to set the shortcut key, press the '-' button on the left of the volume slider. Configure another custom shortcut for 'aumix -v +10' and assign the '+' button on the right of the volume slider.

After this, the volume slider works as expected on my laptop.

---

### Post by eyeshield23 on 2009-04-30
> **Brandon Williams said:**
> Glad that worked for the sound.

I've got a dv7, so I expect the volume thing on my laptop is quite similar to yours. Here's what I did ...

Configure a custom keyboard shortcut that runs this command 'aumix -v -10'. When asked to set the shortcut key, press the '-' button on the left of the volume slider. Configure another custom shortcut for 'aumix -v +10' and assign the '+' button on the right of the volume slider.

After this, the volume slider works as expected on my laptop.how do you create the shortcut and also can you help me get sound onflash videos because I'm not getting any.

---

### Post by eyeshield23 on 2009-05-01
can anyone help me out?

---

### Post by Brandon Williams on 2009-05-01
Go to System->Preferences->Keyboard Shortcuts to find the dialog for creating a shortcut.

When I first got sound working on my dv7, there were multiple sound channels that I had to turn up in order to finally hear something, including the volume control on the flash video I was watching. Also, flash sometimes seems to be greedy with the sound, steeling it from other apps. If you've got another app running that is also greedy with the sound, then the flash won't be able to do anything.

If the flash problem persists, you will want to search the forum for other threads related to flash, or start a new thread if you don't find any relevant existing ones. People with the answers might not look at this thread, since it's not about flash.

---

### Post by eyeshield23 on 2009-05-01
> **Brandon Williams said:**
> Go to System->Preferences->Keyboard Shortcuts to find the dialog for creating a shortcut.

When I first got sound working on my dv7, there were multiple sound channels that I had to turn up in order to finally hear something, including the volume control on the flash video I was watching. Also, flash sometimes seems to be greedy with the sound, steeling it from other apps. If you've got another app running that is also greedy with the sound, then the flash won't be able to do anything.

If the flash problem persists, you will want to search the forum for other threads related to flash, or start a new thread if you don't find any relevant existing ones. People with the answers might not look at this thread, since it's not about flash.it says its lowering the volume but its not o.o

---

