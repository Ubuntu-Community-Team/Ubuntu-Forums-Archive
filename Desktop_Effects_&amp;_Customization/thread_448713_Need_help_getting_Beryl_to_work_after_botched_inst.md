---
title: "Need help getting Beryl to work after botched install."
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by jerrykobes on 2007-05-19
#I tried installing Beryl on my Ubuntu Feisty system by using the following steps from :
[http://wiki.beryl-project.org/wiki/I...ty_with_nVidia](http://wiki.beryl-project.org/wiki/I...ty_with_nVidia)

> 1. Open a terminal. Execute:
>
> sudo echo "Beryl & nVidia installation script for ubuntu Ubuntu Feisty"
>
> (this one line requires your password so that, the next text paste is uninterrupted.)
>
> 2. Copy and paste all the text into the Terminal in one action. [Select all the text. Then middle button click in terminal]
>
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script
> sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup.beryl-script
> echo "deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
> deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main" | sudo tee -a /etc/apt/sources.list
> wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
> sudo apt-get update
> sudo apt-get -y install beryl beryl-manager emerald-themes
> sudo nvidia-xconfig --add-argb-glx-visuals
> sudo cp /usr/share/applications/beryl-manager.desktop /etc/xdg/autostart/beryl-manager.desktop
> cp /usr/share/applications/beryl-manager.desktop ~/Desktop/beryl-manager.desktop
> echo -e "Logout now and then press \e[0;31mCTRL+ALT+BACKSPACE\e[0m to restart xorg"
> echo "Installation completed !"
>
> 3. Now Logout and then press [CTRL+ALT+BACKSPACE] to restart xorg

#After hitting CTL+ALT+BACKSPACE I was brought back to login prompt. From there I logged in and Ubuntu loaded my account normally but as soon as I saw the panel the screen turned white and all I could see is my cursor. Now everything time I restart and login I am brought to a blank white screen.

#I also want to mention that I own a Dimension Dell 8300 with a 128mb DDR Nvidia Geforce FX 5200 graphics card inside of it. This is a pretty fresh install of Ubuntu so I haven't installed any new drivers yet. Please don't tell me to reinstall to OS I want to fix the problem not wipe it out of existence. What went wrong and how do I fix it? Is there still any hope of me getting Beryl to work?

#Then I tried these commands that I got on another forum:

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config-enable

#Then when I rebooted rather than going to the login screen it gave me the following text-based prompt:

> Failed to start X server (your graphical interface). It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem? YES/NO

#I selected YES and got this info:

> X Window System Version 7.2.0
> Release Date: 22 January 2007
> X Protocol Version 0, Release 7.2
> Build Operating System : Linux Ubuntu
> Current Operating System: jerry-desktop 2.6.20-15-generic #2 SMP
> Sun Apr 15 07:36:31 UTC 2007 i686
> Build Date: 04 April 2007
> 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
>	to make sure that you have the latest version.
> Module Loader present
> Markers: (--) probed, (**) from config file, (--) default setting,
> 	(++) from command line, (!!) notice, (II) informational,
> 	(WW) warning, (EE) error, (NI) not implemented, (??) unknown
> (==) Log file: "var/log/Xorg.0.log", Time: Sat May 19 11:10:14 2007
> (==) Using config file: "/etc/X11/xorg.conf"
> (WW) NVIDIA: No matching Device section for instance (Bus ID PCI:1:0:0)
> found
> (EE) No devices detected
>
> Fatal server error:
> no screens found

#Any ideas on what I can do next to get Beryl running? Please tell me that there is still hope.

---

### Post by jerrykobes on 2007-05-19
# WOOHOO! I entered the following command and configured "x server" for nv (nvidia)

sudo dpkg-reconfigure xserver-xorg

# And now the desktop loads fine now at a better resolution along with Beryl. Unfortunately, I don't get any of the effects. When I try to change to window manger in the settings to Beryl it automatically jumps back to metacity. However, when I switch it to compitz it sticks, but I still don't get any effects. 

Am I failing to see something here?

---

### Post by jerrykobes on 2007-05-19
NEVERMIND......... :)

ran "sudo dpkg-reconfigure xserver-xorg" again and changed the settings to nvidia instead of nv. now it works!!!!

---

