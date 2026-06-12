---
title: "Interface in Ubuntu"
date: 2005-07-20
forum: Desktop Environments
---

### Post by ahv on 2005-07-20
Hello out there,

I decided to try Linux for the first time yesterday, so please be patient :), and got the Ubuntu install CD to day :)
I followed the instructions on the screen and everythings was fine.
I started up the new installed system and got through the initializing process, it ask for my username and password, when I type my username and password i got log in. But what now? I was expecting some sort of interface comming up like in windows?
What about this Gnome? How do I come to this interface, this sort of "command promt" really give no sence to me.

Thanks for your help,
Alexander Viborg

---

### Post by kiddo on 2005-07-20
from what I understand, you are logging in on a black text-only (command line interface) screen? Then that means your graphical interface, the Xorg server is not functionning properly. Does it work with the Live CD?

---

### Post by codejunkie on 2005-07-20
[QUOTE=ahv]Hello out there,

I decided to try Linux for the first time yesterday, so please be patient :), and got the Ubuntu install CD to day :)
I followed the instructions on the screen and everythings was fine.
I started up the new installed system and got through the initializing process, it ask for my username and password, when I type my username and password i got log in. But what now? I was expecting some sort of interface comming up like in windows?
What about this Gnome? How do I come to this interface, this sort of "command promt" really give no sence to me.

Thanks for your help,
Alexander Viborg[/QUOTE]
if you can only get to a terminal/text only command line your not in gnome, login and type startx and post what it says here. Note if you did a server install it doesn't include a gui by default you have to install it with this ```
sudo apt-get update
``` then ```
sudo apt-get install ubuntu-desktop
```

---

### Post by ahv on 2005-07-20
It's right now install "something". I was typing in was you had write to me codejunkie. Anything special to do when its finish?
If there are comming up more troubles I'll post them here.

Codejunkie, maybe you got ICQ or MSN if its ok I contact you there?

Thanks!

---

### Post by codejunkie on 2005-07-20
[QUOTE=ahv]It's right now install "something". I was typing in was you had write to me codejunkie. Anything special to do when its finish?
If there are comming up more troubles I'll post them here.

Codejunkie, maybe you got ICQ or MSN if its ok I contact you there?

Thanks![/QUOTE]
it should install everything ok now after it finishes you need to reboot your pc. if everything went ok you will be greated with the gnome login screen. it would be ok to contact me by IM if you need to but i only have a yahoo messenger account  i'll try and help you the best i can if you have anymore trouble just let me know.

---

### Post by ahv on 2005-07-20
It was all going on fine, the interface login screen was coming up, my mouse dos'nt work, but I could log in.
when I had typed in the username and password, it was coming with a error screen "I could not start the X server...........".
When I restart the system now, it says someting about remounting?

Codejunkie I tried to add you to min contact list.

Anybody who knows what to do with this remounting problem, and after that how do I get this interface to work?

My friend said to me "This is linux made so newbies can handle it", from this point I would have drop it out if I have'nt found this forum. I really want this to work and start using Linux.

Thanks.

---

### Post by ahv on 2005-07-20
I fixed the mount problem, and got through to the logon screen again, but it came up with the same error screen again.

Any ideas?

---

### Post by codejunkie on 2005-07-20
[QUOTE=ahv]I fixed the mount problem, and got through to the logon screen again, but it came up with the same error screen again.

Any ideas?[/QUOTE]
is it freezing at login screen or is it trying to start X and then just dies. also could you do me a favor and post the specs of your computer here like
manufacture 
video card 
processor
amount of ram etc.

---

### Post by ahv on 2005-07-20
It is saying;

"I could not start the X server (your graphical environment) due to some internal error. Please check your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart gdm when the problem is corrected.
<ok>"

I only know that it has 350 mhz and about 156 mb of ram

---

### Post by codejunkie on 2005-07-20
[QUOTE=ahv]It is saying;

"I could not start the X server (your graphical environment) due to some internal error. Please check your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart gdm when the problem is corrected.
<ok>"

I only know that it has 350 mhz and about 156 mb of ram[/QUOTE]
is there anyway you could post the output of this command here ```
lspci
``` or at least look through it for something like this  VGA compatible controller or video this will list the name and type of your video card i really need to know this. for example mine says something like this 
```
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev a4)

```

---

### Post by ahv on 2005-07-20
After the message I post before it say this, a lot of times after each other;

"EXT3-fs error (device hdb1) in start_transaction: Readonly filesystem"

---

### Post by ahv on 2005-07-20
When i type lspci it says;

0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter (rev a2)

---

### Post by codejunkie on 2005-07-20
[QUOTE=ahv]After the message I post before it say this, a lot of times after each other;

"EXT3-fs error (device hdb1) in start_transaction: Readonly filesystem"[/QUOTE]
i hate to tell you to go through the install again but where you are having all these errors that might not be a bad idea reinstalling again, and just choosing a default install, just press enter when the cd boots up, and do not use any special boot methods like server or expert it seems like you might have some broken packages namely the x server with all these errors your getting that's the best thing to do. also if you have or can get a copy of the ubuntu live cd try that if it works you shouldn't have any trouble doing a default install.

---

### Post by codejunkie on 2005-07-20
> **ahv]When i type lspci it says said:**
>  530/620 PCI/AGP VGA Display Adapter (rev a2)
try this at the terminal ```
sudo nano /etc/X11/xorg.conf
``` scroll down till you see something like this in the blue
```

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	[COLOR=Blue]Driver		"nvidia"[/COLOR]
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"

```
this is your device driver where mine says "nvidia" i want you to cange yours to "vesa" so it will look like this ```
Driver		"vesa"
```save the file by pressing ctrl+x and choose yes to change the file. reboot and see if it works now.

---

### Post by ahv on 2005-07-20
That did'nt change anything.
Should I try a default install?

---

### Post by codejunkie on 2005-07-20
[QUOTE=ahv]That did'nt change anything.
Should I try a default install?[/QUOTE]
yes if changing the driver didn't work  it would be best to do a clean default install it seems like you have alot of broken packages.

---

