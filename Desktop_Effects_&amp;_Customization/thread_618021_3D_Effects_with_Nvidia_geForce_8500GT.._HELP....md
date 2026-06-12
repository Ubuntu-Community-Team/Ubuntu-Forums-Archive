---
title: "3D Effects with Nvidia geForce 8500GT.. HELP..."
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by mumushi on 2007-11-19
I had trouble lately installing the proprietary driver for my Nvidia GeForce 8500GT and luckily solved it today. I now have the correct resolution and would have the max of 1280x800. My problem right now is when i started installing compiz fusion it asked me to enable the driver for it so i could run 2d and 3d. After doing so my screen resolution went back to 640x480 and no other resolution to choose from. Is there a way i could have a high resolution and 3d effects as well? Your help is greatly appreciated. Thanks in advance.

---

### Post by angryfirelord on 2007-11-20
Run this handy Debian tool:
```
sudo dpkg-reconfigure xserver-xorg
```
Select nvidia as your driver and the resolutions you want. Then, go back into your xorg.conf and add the necessary Composite and AIGLX stuff.

---

### Post by mumushi on 2007-11-20
> **angryfirelord said:**
> Run this handy Debian tool:
```
sudo dpkg-reconfigure xserver-xorg
```
Select nvidia as your driver and the resolutions you want. Then, go back into your xorg.conf and add the necessary Composite and AIGLX stuff.

Thank you for the help. I don't know if i'll do it with the restricted driver for nvidia turned on or off so i did it first with the restricted driver turned off. after doing so i tried to run my desktop effects but no effects at all. then i decided to turn on the restricted driver and do what you told me to do. After doing it my screen resolution which became 640x460 after turning on the restricted driver did not change. So i tried changing my detected monitor because it says its a Plug and Play monitor. Mine is Samsung SyncMaster 151. I chose that and set what resolution i want and after doing so it asked me to log off for the changes to take effect. After logging off my screen went black :(.. 

What should i do now? I can't even log on.. i can't see something on my screen... :(

---

### Post by psyopper on 2007-11-21
What I think you were seeing was the "Bullet Proof X" feature of GUtsy; where if you try to do something that your video system/ driver can't do it sends you into a default desktop. Somehow you managed to subvert it.

Does anyone know what version the Gutsy Nvidia driver is based on? As I recall there were some identification issues with some of the Nvidia 8x series of cards in some of the 100.x.x drivers. The solution may be to use the latest driver from Nvidia.

In the mean time you should be able to run with the "nv" driver instead. Can you at least get to a shell? Assuming you're new to Linux (please don't be offended if you are not), this looks a lot like the old Windows "DOS" prompt? If X is crashing when you boot ( a Blue screen with red and white text) just keep exiting when it gives you the options. then:

```
sudo nano /etc/X11/xorg.conf
```

look for the part that says 
```
Section "Device"
    Identifier     "Nvidia Video Card"
    Driver         "nvidia"

```

Your "Identifier" may be different. Change the Driver from "nvidia" to "nv"

Press Ctrl+O to write out (save) the file, then Ctrl+X to exit.

Reboot the machine by typing:
```
sudo restart now
```

If the "nv" driver fails to load you can try using "vesa" instead.

---

### Post by mumushi on 2007-11-21
> **psyopper said:**
> What I think you were seeing was the "Bullet Proof X" feature of GUtsy; where if you try to do something that your video system/ driver can't do it sends you into a default desktop. Somehow you managed to subvert it.

Does anyone know what version the Gutsy Nvidia driver is based on? As I recall there were some identification issues with some of the Nvidia 8x series of cards in some of the 100.x.x drivers. The solution may be to use the latest driver from Nvidia.

In the mean time you should be able to run with the "nv" driver instead. Can you at least get to a shell? Assuming you're new to Linux (please don't be offended if you are not), this looks a lot like the old Windows "DOS" prompt? If X is crashing when you boot ( a Blue screen with red and white text) just keep exiting when it gives you the options. then:

```
sudo nano /etc/X11/xorg.conf
```

look for the part that says 
```
Section "Device"
    Identifier     "Nvidia Video Card"
    Driver         "nvidia"

```

Your "Identifier" may be different. Change the Driver from "nvidia" to "nv"

Press Ctrl+O to write out (save) the file, then Ctrl+X to exit.

Reboot the machine by typing:
```
sudo restart now
```

If the "nv" driver fails to load you can try using "vesa" instead.


Thanks a lot for the help. I will be doing that later when i get home. I'll be updating later.

---

### Post by mumushi on 2007-11-21
Thank you so much.... it solved my problems but i also did what angryfirelord suggested tocorrect my monitor settings... now ill be working on my desktop effects.. Hope things will run smooth. Once again thank you so much.. :):guitar:

---

