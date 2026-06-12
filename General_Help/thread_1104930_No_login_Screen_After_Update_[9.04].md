---
title: "No login Screen After Update [9.04]"
date: 2009-03-24
forum: General Help
---

### Post by homemadejam on 2009-03-24
I've been using 9.04 for a while now, and the only problems I have really had is that my display will dissapear every now and then. A simple restart sorted this problem out.

I updated my installation last night, it asked me to restart. When I booted back up, it got to the stage where the login screen should be, but instead the screen went black, and I had a few mulitcolored lines at one side of the screen.

I have booted up in the recovery mode, and chose to Repair X Display (or something like that) but no luck. I have also tried dpkg-reconfigure xserver-xorg ... but no luck. I tried startx, and it would just give me the black screen again. Once at the login screen stage, I have tried Ctrl Alt + F1 - F10.. but none of them will load.

I am runnung Ubuntu 9.04 on a MSI Wind U90x

Thankyou in advice,
Jam

---

### Post by homemadejam on 2009-03-24
Bump?

---

### Post by gyrovirus on 2009-04-14
Hello,
I've got the same problem.
Did you manage to solve it?

---

### Post by gyrovirus on 2009-04-14
bump?

---

### Post by homemadejam on 2009-04-18
Hey,
No I didn't manage to solve it...
I guessed that it was a problem with my xorg.conf file, but I tried everything I could think of, and I didn't get any closer at all.

In the end I ended up just re-installing 8.10 back on :(


Jam

---

### Post by elargus on 2009-04-24
I just did an update from 8.10 to 9.04 and I have the same problem. Anyone with a solution to this?
I have a via P4M890 UniChrome Pro integrated graphic.

---

### Post by ubu-for on 2009-04-24
> **homemadejam said:**
> I am runnung Ubuntu 9.04 on a MSI Wind U90x

With NVIDIA or ATI GPU?

---

### Post by dstein on 2009-04-24
I am having the same problem with an ATI GPU.

---

### Post by jamessnell on 2009-04-24
I haven't really read all of your guy's posts here nor have I really thought about it, but I had some weirdness (not quite the same stuff) happen with my ATI card after upgrading, I installed the 9.4 ATI Driver and that resolved my video issues for me, have you guys given that a whirl yet?

---

### Post by dstein on 2009-04-24
What command would install the 9.4 driver from the terminal? I am able to get to a root terminal from GRUB. This morning I tried ```
$dpkg-reconfigure xserver-xorg
```
but I still had the problem.

Please let me know how to upgrade the driver from the root terminal. I will try it later when I get home.

Thanks.

---

### Post by jamessnell on 2009-04-24
Go to the [ATI website]("http://support.amd.com/us/gpudownload/Pages/index.aspx") and download the latest driver for your setup.

You can download it at the command line by running:
```
wget <url>
```

Then you'll need to make the installer you downloaded executable:
```
chmod +x <filename>
```

Finally, run the installer:
```
sudo ./<filename>
```

---

### Post by jmchardy on 2009-04-24
Hi,
People, please tell us what HW you are using, when we have display problems, tell us what Graphics System you are using.  Don't know? try
```
lspci -nn | grep VGA
``` at the command line, that way, we can relate to your problem and perhaps provide an answer, or share the complaint.  
For me, this shows:
```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591]
```
I was originally using 8.10 and the Proprietary ATI fglrx drivers (enabled by selecting "System->Administration->Hardware Drivers" letting it figure it out and then accepting the change).
I updated to 9.04 this morning and when it rebooted I had a Blank   Screen, and CTRL-ALT-F1, 2, 3... don't work either.
So, what did I do to fix it. This is more likely to work for people with ATI graphics cards, but there should be something similar for people with different cards, you essentially want to go back to the non-proprietary drivers (or perhaps you need to goto proprietary drivers). Follow this tutorial: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver"), but don't just blindly follow it, perhaps just try the "Removing the proprietary fglrx driver" section and when you have finished updating the mesa drivers, run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and check that /etc/X11/xorg.conf doesn't contain flgrx.
That worked for me, I now have my full screen resolution and no corruption, but... I don't have any accelerated graphics and the refresh is pretty slow, but it is working and I can get on with what I need to untill the ATI driver is updated (or I figure something else out).
By the way, I have since then tried letting Hardware Drivers update to the Proprietary Driver and I had the same problem, had to reboot and remove it manually. Perhaps one day Linux Distros will come up with a more sensible solution to Graphics drivers by providing a fallback and complete reconfigure, during a full install I have never had a problem, but once I have installed and I change the driver, I can never normally get it back, why can't I ask it to do what it did during installation? who knows...
Cheers
J

---

### Post by jamessnell on 2009-04-25
> **dstein said:**
> What command would install the 9.4 driver from the terminal? I am able to get to a root terminal from GRUB. This morning I tried ```
$dpkg-reconfigure xserver-xorg
```
but I still had the problem.

Please let me know how to upgrade the driver from the root terminal. I will try it later when I get home.

Thanks.

Sure, you need to download the third party installer from the [ATI website]("http://http://support.amd.com/us/gpudownload/Pages/index.aspx").

Once you've got the installer, you need to make the files executable:
```
chmod +x <filename>
```

Then run the installer:
```
sudo ./<filename>
```

Once you've got it installed, reboot, and perhaps that'll cut it :)

That's all I had to do.

---

### Post by homemadejam on 2009-04-25
The MSI Wind uses this:

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
```


I made a spare partition on my Hard drive, and upgraded that to 9.04, and it works fine. But on my normal installation, I have upgraded to 9.04 and I still get the same problems...


thanks,
Jam

---

### Post by dstein on 2009-04-25
To fix the problem, I first tried installing the 9.4 drivers that can be downloaded from ATI's website, as this worked for some. However, I was still getting the black screen. I proceeded to follow the 'removing fglrx driver' on the link provided by jmchardy. This worked for me. Afterwards, I tried installing the 9.4 drivers from ATI's website, and they installed successfully, with no black screen. However, conky is not working as it did, and my widget layer starts very slowly.

---

### Post by homemadejam on 2009-04-26
I have just installed Ubuntu 9.04 from scratch onto my laptop, and it works fine. After installing all of the old appications that I had before (using dpkg --get-selections), I restarted, and I had the same problem again. So I guessed that it was something to do with one of the things that I had just installed.

After a bit of thinking, and looking around, I found out that it was down to the **fglrx-kernel-source** & **xorg-driver-fglrx** packages.

After these were removed, everything was back to how it should have been.


My problem is now solved, I am unsure of if this will work for the rest of the people having similar problems... (I know very little when it comes to graphics cards & drivers!)


Thanks for all of your help,

Jam

---

### Post by dstein on 2009-04-26
Could someone who has solved this problem please post their xorg.conf setting. For some reason, the problem is only solved for me when relying upon the proprietary driver from ATI's website. Upon uninstalling, and setting xorg.conf to use 'ati' or 'radeon' drivers, I have the same problem, even with all fglrx packages uninstalled. I know that dpkg-reconfigure can be used to change xorg.conf back to its defaults. Is there any way to configure xorg.conf to how it would have been set up on a fresh Ubuntu install? Thanks. I would keep the ATI driver as is, but things are working slow. Thanks.

---

### Post by homemadejam on 2009-04-27
> **dstein said:**
> Could someone who has solved this problem please post their xorg.conf setting. For some reason, the problem is only solved for me when relying upon the proprietary driver from ATI's website. Upon uninstalling, and setting xorg.conf to use 'ati' or 'radeon' drivers, I have the same problem, even with all fglrx packages uninstalled. I know that dpkg-reconfigure can be used to change xorg.conf back to its defaults. Is there any way to configure xorg.conf to how it would have been set up on a fresh Ubuntu install? Thanks. I would keep the ATI driver as is, but things are working slow. Thanks.

Do any of the backup xorg.conf files work?
They should be located within the same DIR as the xorg.conf file you are using at the moment...

Jam

---

### Post by dstein on 2009-04-27
I don't believe so. I am unsure how xorg.conf even works anymore. It seems that there used to be much more control allowed with this file, and more configuration options with $dpkg-reconfigure xserver-xorg. I ended up reinstalling using Intel integrated graphics, thinking that a fully open-source solution would work. Unfortunately, my screen flickers. I searched for this problem, and it seems it is still unresolved. I am debating whether I want to try a fresh install of 9.04 with my ATI card or just going back to 8.10, which I know works (with problems however - I have to turn off Compiz for Google Earth to work properly).

---

### Post by pire1024 on 2009-04-28
I had the same issue. 
I followed the instructions given by one of you folks to uninstall the fglrx drivers.
I had to connect to the machine through ssh. I then typed this:

```
sudo apt-get remove --purge xorg-driver-fglrx

sudo dpkg-reconfigure -phigh xserver-xorg
```

Then reboot, and it worked.
Thanks for this. I hope it works for the others.
Best regards

---

