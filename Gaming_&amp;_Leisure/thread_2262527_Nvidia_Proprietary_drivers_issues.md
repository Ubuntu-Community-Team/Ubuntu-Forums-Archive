---
title: "Nvidia Proprietary drivers issues"
date: 2015-01-25
forum: Gaming &amp; Leisure
---

### Post by greg69 on 2015-01-25
[COLOR=#000000]Kit:[/COLOR]
[COLOR=#000000]Gigabyte GA-78-LMT-S2P[/COLOR]
[COLOR=#000000]AMD FX 6100 6 core processor[/COLOR]
[COLOR=#000000]EVGA GTX 760[/COLOR]
[COLOR=#000000]G.Skill Ripjaws 8GB RAM

I'm trying to get my Proprietary drivers to work. I had them installed for a few months (A friend installed them for me) until one day they stopped working. Apparently "OpenGL is not using direct rendering".
Note: The Additional drivers work perfectly fine. But they're many versions behind and slower in modern games. I'd like the latest ones.
I read that a reinstall would fix it and I followed all the instructions exactly.
Although, Every time I've tried it, It's stuck me at the Login screen and I can't input with mouse or keyboard. I can't even Ctrl alt F1.
Here's the commands that I did.
Ctrl alt F1
Login
sudo stop lightdm
cd Downloads/
[/COLOR]chmod +x NVIDIA(Vers number)
sudo apt-get remove xserver-xorg-video-nouveau (I tried variations like --purge)
sudo ./NVIDIA(Vers number)

And I ran the installer.
Is there anything I did wrong? I've tried it with the additional drivers selected from the Ubuntu menu. The same result.
EDIT: Forgot to mention, Disabling ACPI lets me type and enter my password but I get stuck in a limbo between the Login screen and the Desktop. I can't do anything in this time.

---

### Post by ajgreeny on 2015-01-25
You need ```
sudo service lightdm stop
``` not the command you used.

See if that helps you to do what you want and if it is not successful come back again.

I can't comment much on your nvidia driver installation method as I have never had an nvidia card, but I do know that normally it is best to use the version from additional drivers, not those direct from nvidia.

---

### Post by jorge8 on 2015-01-25
You might also want to purge your existing (old) Nvidia proprietary drivers before installing the latest ones.  Sometimes you get adverse effects when you have multiple Nvidia proprietary drivers installed.

I'd install them using the Xorg-edgers PPA:

Step 1: Find the driver version that supports your graphics card here: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Step 2: Add the Xorg edgers PPA to apt-get:
```
$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo apt-get update
```
Step 3: Search for the actual driver name in the Xorg-edgers PPA using "sudo apt-cache search nvidia"
Step 4: Install the driver using apt-get (using the driver number and name from step 3 in the *apt-get install* command):
```
$ sudo service lightdm stop
$ sudo apt-get autoremove --purge nvidia-*
$ sudo apt-get install nvidia-[driver number goes here] nvidia-settings
$ sudo service lightdm start
```

Optionally, to avoid accidentally upgrading the proprietary driver in the future, you can remove the Xorg-edgers repository using:
```
sudo apt-get install ppa-purge && sudo ppa-purge ppa:xorg-edgers/ppa
```

Also, you can find some ideas on how to do some advanced configurations for your proprietary Nvidia drivers here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by oldrocker99 on 2015-01-26
Don't forget to do this before installing the drivers:
```
sudo apt-get install dkms
```

This will link the driver to any new kernel update (and they do happen). You'll be glad you did.

---

### Post by greg69 on 2015-01-26
Thanks. Jorge8 Solved the problem. I also took the advice of oldrocker99 and added dkms. Thanks. I'll keep this thread bookmarked for the future.

---

### Post by jorge8 on 2015-01-26
Great! Glad I could help.  I just went through this myself last month as I've installed a new Nvidia graphics card into my HTPC/gaming rig. :)

Oldrocker99, good call on dkms, I need to add that myself! :D

---

