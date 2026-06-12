---
title: "Ubuntu Mate 15.10, Nvidia &amp; Steam"
date: 2016-02-10
forum: Gaming &amp; Leisure
---

### Post by ecrosby on 2016-02-10
[FONT=Helvetica]So, I am having an issue with Steam not successfully running a game. I have a fresh install of 15.10 and this is the first time I have attempt to play games on Steam in Linux. I have an Nvidia GeForce GTX 970 in my machine. Here is what I have done so far:
Installed the Nvidia ppa (sudo add-apt-repository ppa:graphics-drivers/ppa) based upon a thread I found out there on the webs and then installed Nvidia 358 (sudo apt-get install nvidia-358 nvidia-settings). I then downloaded the Steam .dep package from the Steam site and installed, the install ran smooth. Launched the Steam client and then downloaded Insurgency and started the game. The game started and I was able to join a server, but the actual game never started after the map was downloaded, I believe it froze. I then minimized the game window and happened to notice an OpenGL error.
I researched all over and tried many steps. At some point during my troubleshooting I broke something because now Steam doesn't launch at all. I've tried everything from removing Steam and the Nvidia driver and reinstalling everything and even upgraded the driver to 361. The error I am getting when I attempt to launch Steam from the terminal is the following:

[/FONT]
[FONT=Helvetica][I]Running Steam on ubuntu 15.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1454620878)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

[/I][/FONT]
[FONT=Helvetica]I have found this error online on multiple occasions and have attempted some of the troubleshooting steps but have not found a solution yet. I believe this to be a driver issue and I'm not sure how to fix it.
Any assistance would be greatly appreciated.[/FONT]

---

### Post by Vladlenin5000 on 2016-02-10
Hi and welcome.

Uninstall Steam.
Open the file manager (Files AKA Nautilus), press CTRL+H to see the hidden folders, find and delete .Steam (notice the dot before Steam which means it's an hidden folder).
Install Steam from the official repositories:
Either find it and install using the Ubuntu Software Centre like any other software or ```
sudo apt-get install steam
```

In the first run it'll update whatever is required.

---

### Post by ecrosby on 2016-02-11
> **Vladlenin5000 said:**
> Hi and welcome.

Uninstall Steam.
Open the file manager (Files AKA Nautilus), press CTRL+H to see the hidden folders, find and delete .Steam (notice the dot before Steam which means it's an hidden folder).
Install Steam from the official repositories:
Either find it and install using the Ubuntu Software Centre like any other software or ```
sudo apt-get install steam
```

In the first run it'll update whatever is required.


Thank you for your response.
I had already tried that before but I tried it again per your recommendation and it's still an issue, I have the same output.
One thing I noticed is that it looks as if I have the official Steam repo:

*[ ed@edmate15: ~ ]$ sudo cat /etc/apt/sources.list.d/steam.list *
*[sudo] password for ed: *
*deb [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam*
*deb-src [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam*

Is there an alternate repo that is supposed to be better, that will work?
Using Ubuntu Mate 15.10, I do not believe the Ubuntu Software Center is installed by default. I prefer to use the terminal anyway to install software, I never use GUI for installing software.

---

### Post by MikeCyber on 2016-02-11
for the opengl error I would update with the latest nvidia. download directly from nvidia and update in a virtual terminal
soemthing alike:
ctrl+alt+f2
sudo /etc/init.d/lightdm stop
chmod +x nviidia*
sudo ./nvidia*
sudo reboot

I remember having some different gl problems with some ppa years back. Since I do the initial Nvidia install from Ubuntu but updates 
from Nvidia.

---

### Post by abobier on 2016-02-11
Same problem as here I think:

[https://bugs.archlinux.org/task/48123]("https://bugs.archlinux.org/task/48123")

---

### Post by ecrosby on 2016-02-12
> **MikeCyber said:**
> for the opengl error I would update with the latest nvidia. download directly from nvidia and update in a virtual terminal
soemthing alike:
ctrl+alt+f2
sudo /etc/init.d/lightdm stop
chmod +x nviidia*
sudo ./nvidia*
sudo reboot

I remember having some different gl problems with some ppa years back. Since I do the initial Nvidia install from Ubuntu but updates 
from Nvidia.


I tried this but it looks as if it had difficulties because of Nouveau. I'll be troubleshooting this more over the weekend, removing Nouveau and installing the Nvidia driver from Nvidia's site.
By the way, the best way to install the Nvidia driver from command line is to boot to multi-user mode (terminal). The install didn't like Ctrl+Alt+F2.

---

### Post by oldrocker99 on 2016-02-13
There is a problem with Steam and nVidia 3.58 (or so it's said); the latest version is 361.28. I'd advise installing that.

---

