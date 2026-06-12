---
title: "Help! Accidently uninstalled gdm and xubuntu desktop!! URGENT :("
date: 2009-03-20
forum: General Help
---

### Post by Final Fantasy on 2009-03-20
Ok so I accidently removed gdm along with xubuntu-dekstop.

Now when I reboot, it shows up with black screen/terminal.

I login and type: sudo apt-get install gdm xubuntu-desktop

Goes through it all asking Y/n ? I say Y and then enter, but then it can't fetch it/can't connect.  My WiFi is switched on, how can I configure in this CLI to connect to my home network along with configuring ip addresses/mask/gateway/DNS??

If it helps, I'm on Dell Vostro, Xubuntu 8.10

I need to connect to my network SSID: homepc
I need to configure my IP to: 192.168.2.2
I need to configure my Subnet Mask to: 255.255.255.0
I need to configure my Gateway to: 192.169.2.1
I need to set my DNS to the following: 194.168.4.100, 194.168.8.100

Once i've configured the following, I will have internet access and then I can try out the apt-get install command to reinstall gdm and xubuntu-desktop.

Anyone help? This is my only laptop, If you're wondering how I came on here, I'm currently booting from a Live CD of Xubuntu 8.10

Edit: I need step-by-step on what commands to enter, I will write these down and reboot and carry it out.

Many thanks!

---

### Post by taurus on 2009-03-20
Did you install Ubuntu first and then added xubuntu-desktop to your computer?  Even if you removed gdm, Gnome should still be on your machine if you installed Ubuntu.  Log in and at the prompt, type

```
startx
```

---

### Post by Final Fantasy on 2009-03-20
> **taurus said:**
> Did you install Ubuntu first and then added xubuntu-desktop to your computer?  Even if you removed gdm, Gnome should still be on your machine if you installed Ubuntu.  Log in and at the prompt, type

```
startx
```

Hi thanks for quick reply, basically, I installed Xubuntu 8.10 couple of months ago, all went fine until today I did something stupid and uninstalled/reinstalled ALSA files to get sound working, I missed the warning that gdm and xubuntu-desktop would be uninstalled along with it and that I would need to reinstall it.  Well I missed that part and rebooted, and now I'm always facing a prompt.

I don't have Ubuntu, only Xubuntu, I'm currently on the Live CD Xubuntu 8.10 - it's the only way I could think of to get on the internet here and ask for help.

EDIT: If I try the command: sudo apt-get install gdm xubuntu-desktop

It won't work, infact anything that requires internet access will not work, I can't even ping my own router (i'm not connected to anything, wifi is simply switched on).

---

### Post by taurus on 2009-03-20
Removing xubuntu-desktop would not remove XFce4 from your machine.  Xubuntu-desktop is only a metapackage.  So reboot without the LiveCD and after you have logged in, run that command again to see if XFce4 would start.

```
startx
```

---

### Post by Final Fantasy on 2009-03-20
> **taurus said:**
> Removing xubuntu-desktop would not remove XFce4 from your machine.  Xubuntu-desktop is only a metapackage.  So reboot without the LiveCD and after you have logged in, run that command again to see if XFce4 would start.

```
startx
```

Ok, thanks I will try this :)

---

### Post by Final Fantasy on 2009-03-20
> **taurus said:**
> Removing xubuntu-desktop would not remove XFce4 from your machine.  Xubuntu-desktop is only a metapackage.  So reboot without the LiveCD and after you have logged in, run that command again to see if XFce4 would start.

```
startx
```

It worked, you are a bloody genius, mate! :D

Now...all this still hasn't fixed my damn sound.  Why the hell did I have to go and install Realtek HD drivers, when mine is freaking Intel HD Audio ><

---

### Post by taurus on 2009-03-20
How did you install that Realtek HD drivers for the "wrong" sound card?  I guess you are all good with reinstalling gdm now.

---

### Post by Final Fantasy on 2009-03-20
> **taurus said:**
> How did you install that Realtek HD drivers for the "wrong" sound card?  I guess you are all good with reinstalling gdm now.

I went on the Realtek website, searched for the latest driver for linux, downloaded and installed it.  Rebooted, no sound.  Went on to try guides/help and learned about ALSA and pulseaudio, probably made it worse now.

I've made a thread here: [http://ubuntuforums.org/showthread.php?t=1101660](http://ubuntuforums.org/showthread.php?t=1101660)

EDIT: Yes reinstalled gdm too thanks :)

---

### Post by taurus on 2009-03-20
Did you download the file in filename.deb, filename.bin, or filename.tar.gz?

If you installed a wrong driver for your sound card, it's best to remove it first before you go any further.

---

