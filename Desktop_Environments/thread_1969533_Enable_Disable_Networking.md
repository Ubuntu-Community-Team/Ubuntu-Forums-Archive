---
title: "Enable /Disable Networking"
date: 2012-04-30
forum: Desktop Environments
---

### Post by amit112amit on 2012-04-30
Hi all.
I am using Gnome 3.4.1 with Ubuntu 12.04(64-bit).
In Gnome classic, if we right-click the system tray icon for network connections we would get options like
1. Enable networking
2. Enable Wireless
etc.
But in Gnome 3.4.1, I don't get these options.
What is the way to enable/disable networking in Gnome 3.4.1?

Regards,
amit112amit

---

### Post by RichardCain on 2012-04-30
Please open a terminal, enter
```
sudo rfkill list
```
and post the results.

---

### Post by amit112amit on 2012-04-30
Hi Richard.
Please find the results below:

```
sudo rfkill list
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

I just wanted to know what command is executed when I select "Enable Networking" from context-menu of network icon in system tray in Unity / Gnome classic. And how to do that in Gnome.

Thanks for help, in advance.

Regards,
amit112amit

---

### Post by RichardCain on 2012-04-30
Sorry, crossed wires there.

If you go to the gnome control centre and select "Network, there is a switch on the wireless tab.  Alternatively:
```
$ gnome-control-center network
```

Not sure of the actual command to switch the switch though.

---

### Post by RichardCain on 2012-04-30
I did a bit of digging and it seems that *nmcli* is the command you're looking for:
```
$ nmcli nm wifi on
```will turn wifi on, while:
```
$ nmcli nm wifi off
```will turn wifi off.

Full details & syntax can be found in:
```
$ man nmcli
```

---

### Post by amit112amit on 2012-05-03
Thanks a lot for your help Richard.

The exact command I was looking for is
```

nmcli nm enable false
nmcli nm enable true
```I could find it only by through your suggestion.
The reason I needed it is that sometimes if I plug in my network cable immediately after restarting into Gnome 3.4, the "Network Cable Unplugged" status does not change. In Gnome Classic I would enable/disable networking once and it would detect my cable. But in the latest gnome I had to log off, log in into Gnome classic and do enable/disable networking.

Thanks once more.
Regards,
amit112amit

---

### Post by bina7777 on 2012-05-31
@ubuntu:~$ sudo rfkill list
0: sony-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
6: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


________________________________

@ubuntu:~$ nmcli nm enable true

** (process:15487): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

** (process:15487): WARNING **: Error enabling/disabling networking: The name org.freedesktop.NetworkManager was not provided by any .service files
_____________________________

Please help what should i do next

---

### Post by richardh9936 on 2012-05-31
Many thanks to Richard Cain for the nmcli command.  I don't know why my 12.04 system decided against wifi, but this command rectified it.

---

### Post by kushdilip on 2012-07-05
> **richardh9936 said:**
> Many thanks to Richard Cain for the nmcli command.  I don't know why my 12.04 system decided against wifi, but this command rectified it.
Why need command line when there is an option available as 'Enable Networking' while clicking on network manager indicator on top panel. Both nmcli command line and clicking that option doest same thing.  
*nmcli  *has been added as extra functionality for *nm-applet.*

---

### Post by TheCalm101 on 2012-07-11
Hi, 

I just updated my software (automatically) on my laptop. I'm using Ubuntu 12.04 LTS and now I can't go onto the internet. It says that the "cable unplugged". There's a "switch" for on/off network "plug"- it won't go on. 

Seriously frustrated 

PLEASE HELP

---

