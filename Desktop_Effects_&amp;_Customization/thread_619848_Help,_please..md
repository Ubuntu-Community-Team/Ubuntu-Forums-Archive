---
title: "Help, please."
date: 2007-11-21
forum: Desktop Effects &amp; Customization
---

### Post by Rowdy73 on 2007-11-21
First off, i am very grateful to have found a nice free alternative to windows. Having said that, i can get into what i really want to do with it. I simply want a sick beryl 3d desktop like i had back in June '07 when MaximumPC magazine showed me how to do it.

I've since formatted since then and ever since i've not been able to get **ANY** of the Nvidia glx settings to work in feisty 7.04, please tell me how to configure this so i can have that sick *** 3d desktop again, (i've done ALL of the latest updates). Been using my laptop in windows, surfing these forums for hours now, seeking help on how to get my desktop looking amazing again.

This is my system:

AMD 4800+ dual core processor (water cooled)
Asus premium motherboard
4 gb of Corsair ram
EN7900GTX video card (Nvidia)
DVD burner by Samsung
Creative X-fi  soundcard
Dell 2407 widescreen monitor
Hitachi 42" plasma (for gaming)

Thanks for any/all input, i've tried a lot of things but will try anything you guys suggest for the results that i'm after. (And will share them with others, later).

---

### Post by FuturePilot on 2007-11-21
What exactly is the problem? Could you please post your xorg.conf? This command will dump the contents of your xorg.conf right in the terminal, then you can just copy and paste them.
```
cat /etc/X11/xorg.conf
```

---

### Post by Rowdy73 on 2007-11-21
> **FuturePilot said:**
> What exactly is the problem? Could you please post your xorg.conf? This command will dump the contents of your xorg.conf right in the terminal, then you can just copy and paste them.
```
cat /etc/X11/xorg.conf
```

My computer simply dumps to a black screen.
I'll try to get more info, (reinstalling Feisty now).

---

### Post by Rowdy73 on 2007-11-21
> **FuturePilot said:**
> What exactly is the problem? 

I can't seem to get the 3d acceleration working for the Nvidia video card.
-Therefore, Beryl can't be installed on my feisty ubuntu. (7.04)

---

### Post by Rowdy73 on 2007-11-21
Ok, i have it reinstalled with all of the 140+ updates installed, now how can i get this going?
(Sucks having to reinstall Ubuntu after every failed attempt at 3d video acceleration).

-Any help will be appreciated, it simply fails and crashes to a black screen after attempting any kind of Nvidia glx sudo entry..

---

### Post by Rowdy73 on 2007-11-22
> **FuturePilot said:**
> What exactly is the problem? Could you please post your xorg.conf? This command will dump the contents of your xorg.conf right in the terminal, then you can just copy and paste them.
```
cat /etc/X11/xorg.conf
```


No such file or directory

-(That's what it told me when i typed what you wrote, in the Terminal).

---

### Post by jack_teagarden on 2007-11-22
If you want 3D proprietary support you would probably have a lot more success in Gutsy... heaven knows I did..
Another thing to try would be Envy, which will install the Nvidia drivers for you.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
is the link for envy.

Good luck!

---

### Post by Rowdy73 on 2007-11-22
> **jack_teagarden said:**
> If you want 3D proprietary support you would probably have a lot more success in Gutsy... heaven knows I did..
Another thing to try would be Envy, which will install the Nvidia drivers for you.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
is the link for envy.

Good luck!

I'll try that now, thanks for the suggestion.

Just got done loading all of the newest stuff from Gutsy Gibbons and same thing, as soon as i enabled 3D support - Bam! screen goes black after the reboot.  I'll go ahead and load it all up again and give Envy a shot.

---

### Post by Rowdy73 on 2007-11-22
Been reading these forums for about 12 hours now, it seems that nobody else that uses Ubuntu has the same Nvidia powered video card that i do. EN7900GTX by Asus.

Getting pretty fed up of installing Ubuntu, enabling 3d acceleration, crashing..
I have the most current driver for my video card installed and my computer runs perfect in Windows, and its really fast as well. Feisty, Gutsy i've tried all of these, are there any other suggestions out there??

All i wanted Ubuntu for was the eye candy when i surf the internet, i know gaming is still an achilles heel but that's ok, i can go back to windows for that.

---

### Post by Rowdy73 on 2007-11-22
Ok, i'm making a little progress.

Was getting a black screen after rebooting but did a little research and tried something a little different, i used the 8800 video cards driver to work with my 7900 card.
Reinstalled Feisty, getting updates now-
Going to reinstall Gutsy, then install the video driver that works with my video card, the one in this thread:

[http://ubuntuforums.org/showthread.php?t=616718](http://ubuntuforums.org/showthread.php?t=616718)

Then i'm hoping to have Gutsy all dialed in, then ultimately install Beryl.

---

### Post by Rowdy73 on 2007-11-25
All fixed, (just had to reinstall).

---

