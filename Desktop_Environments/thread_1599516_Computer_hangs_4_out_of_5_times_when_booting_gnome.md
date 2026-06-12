---
title: "Computer hangs 4 out of 5 times when booting gnome"
date: 2010-10-17
forum: Desktop Environments
---

### Post by LinuxNurse on 2010-10-17
Hi all.

I'm running Maverick on an Acer AO521 netbook. I've got a k125 processor and an ATI Mobility Radeon HD 4200 series video card.

Since upgrading to 10.10 with the new version of gnome my computer has started getting stuck on blank screen when booting the GUI. Not every time, but most times i boot.

If I boot to command line through GRUB there's no problem. When I try to run gnome from the command line i get the same problem.

Any ideas? I'm a seasoned newbie and i'm stumped.:confused:

thanks all. peace.

---

### Post by 3Miro on 2010-10-17
We need to identify the problem first. Right after a crash, use grub to get to a command line and check the Xorg log file

```
 less /var/log/Xorg.0.log 
```

(you can exit the less viewer with escape (Esc).

Look for any errors "(EE)" or if you can, post the content.

Copy the file to your home folder:

```
 cp /var/log/Xorg.0.log ~/ 
```

then you can post it to us from a good boot (you will have Xorg.0.log file in your Places -> Home folder).

---

### Post by LinuxNurse on 2010-10-18
yeah sorry about that. right after i posted i realized that i should have posted a log of what went down. in true computer form, i cannot seem to replicate the crash now that i want to, which is weird cause it's never worked this well since upgrade to 10.10.

---

### Post by LinuxNurse on 2010-10-18
I caught one...thanks for the help

---

### Post by 3Miro on 2010-10-18
You get a bunch of (WW) warnings about the fglrx driver, which is the proprietary ATI driver. It seems like it has not been configured correctly. There are only two things that I can say (others may know more).

1. You can try to reinstall the driver. Remove it form the Hardware Center, the reboot, install, reboot. It is an ugly windows like thing, but this may fix the Xorg configuration. I am sure there is another way, it is just that I don't know it.

2. From my limited experience with the ATI cards, I found that sometimes I am able to get better performance with the default free river (i.e. don't install the proprietary driver). You may want to give that a try (however, I have also heard people complain about the free driver making the GPU run too hot, so try to watch out for that).

---

### Post by LinuxNurse on 2010-10-19
Tried uninstalling the ATI driver and using the free driver. Now it will only boot with an external monitor. As in, the external monitor is the primary display but i can still use the LCD as a display after booting. Not sure how i adjust this because i haven't really used the ubuntu driver.

---

### Post by 3Miro on 2010-10-19
Does is work if you reboot without the primary monitor plugged?

Go to System -> Preferences -> Monitor and see if you can activate your other monitor from there.

---

### Post by LinuxNurse on 2010-10-20
Both monitors work. The problem is that the external monitor seems to be set as default. I tried changing this in the settings but no dice. When i boot without the external monitor i just get the orange and black login background on the LCD. I can even login blindly even though the login window is in on the non-existent external monitor.

Aside from this, the free driver seems to be working a lot better than its unfree counterpart. But this is a fairly major problem.

---

### Post by jbluzb86 on 2010-10-25
my problem is maverick will not install at all due to problem during boot-up

same computer specs

---

