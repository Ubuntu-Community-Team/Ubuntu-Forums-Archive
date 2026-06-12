---
title: "NVIDIA 9600GT detection issues"
date: 2008-08-24
forum: Desktop Environments
---

### Post by _cdp_ on 2008-08-24
Hi,

Please help. I'm stuck!

I just bought a Nvidia 9600GT, am running a fresh install of ubuntu 8.04. The display is working correctly (it seems). However the card is not listed in the Hardware (restricted) drivers.

lspci | grep -i nvidia  shows:

02:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)

so the card is working and detected. Can anyone tell me how to force it to use the restricted driver? I want to try and so some gaming and I will need the 3d acceleration.

Thanks!

Chris.

---

### Post by nikgare on 2008-08-24
You need to install **nvidia-glx-new** and then enable the driver via the restricted drivers dialogue.

It is probably worth installing **nvidia-settings** at the same time - tjis will give you much more control when the driver is installed.

---

### Post by _cdp_ on 2008-08-24
Hi,

I did install both those packages, rebooted.

which brings me to the problem. The drivers are not listed in the restricted drivers dialog. :(

Chris.

---

### Post by habtool on 2008-08-24
I may be wrong, but as far as i recall (cant check just now as I am in debian lenny), but the nvidia-glx-new version in hardy does not support the 9600 card.

You will need to use the envy one.
(search for envy in synaptic)

you can also install the latest one from nvidia site, but that is more work and you need to run it each time you have a kernel upgrade.
(this is not really that painful, but if you are new here then it will appear to be a pain, esp if you install a new kernel and then the xserver fails on boot and you end up at a CLI session.

Double check this advise, but as far as i know it should be correct.

---

### Post by d0b33 on 2008-08-24
habtool is correct you need to download the nvidia driver and install envy glx.

I got my 9600GT working by doing this...

Download the latest driver from NVidia:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Place it in your home folder(you should be able to navigate there in terminal later)

The latest driver is 173.14.12 so refresh your repos, use synaptic manager to find glx packages that have the corresponding driver version numbers(173.14.12) and install them, but be sure you have the "build-essential" and "NVIDIA-settings" packages installed as you'll need this later.

Now go CTRL+alt+f1 on your keyboard and login


Type:

```
sudo /etc/init.d/gdm stop
```

Wait for the drop out of X11.


Go to the directory where you downloaded the newest Nvidia driver.

```
cd /home/(your name)
```

Then type:
```

sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run
```

(NVIDIA-Linux-x86-173.14.12-pkg1.run = name of the file you downloaded. If it's different, then make corrections)

Follow directions on the screen, Reboot(ctrl+alt+del)

Open settings manager using terminal

```
sudo nvidia-settings
```

Adjust you settings and reboot if necessary
Good Luck

Optional...
If you having display problems you could try to reconfigure X
```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```

ctrl-alt-del

---

### Post by nbayiha on 2008-08-24
Follow this thread and you should have your problem fixed .

[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver)

---

