---
title: "nvidia-settings command line"
date: 2008-09-03
forum: Desktop Environments
---

### Post by palomar on 2008-09-03
Hi,
I'm looking for a console command to control my 2nd monitor using nvidia-settings. I want to turn it on or off in 'user space' (not editting xorg.conf). When turned on it has to use twinview (wide desktop).

I.e. **nvidia-settings -screen1 enable twinview** or something like that. Already read the manual (man nvidia-settings), but I can't find the right command to do this.

Does anyone know how to do this?

---

### Post by Firerat on 2008-09-03
Not tried this, but I guess you could make two configs with the gui and then load them
```
nvidia-setings -l --config=~/.nvidia-settings-rc1
nvidia-setings -l --config=~/.nvidia-settings-rc2
```

However, I don't think that this will help you

The TODO section in the below file surgests that TwinView can't yet be configured via nvidia-settings
[ftp://download.nvidia.com/XFree86/Linux-x86/nvidia-settings-user-guide.txt](ftp://download.nvidia.com/XFree86/Linux-x86/nvidia-settings-user-guide.txt)

---

### Post by redmoskito on 2008-09-10
No dice, Firerat.  Looks like the rc file doesn't have any configuration info regarding which outputs are enabled.

---

### Post by wd5gnr on 2008-09-10
The answer is to set a metamode with 2 monitors and another with only one monitor in xorg.conf. Then you can use the usual GNOME/KDE/whatever utility for changing screen resolution. 

Here's what I have in my Screen section:

   Option          "metamodes" "CRT: 1280x1024 +1280+0, DFP: 1280x1024; DFP:1280x1024,CRT: NULL"

So the first mode is CRT at 1280x1024 offset by 1280,0 and the DFP at 1280x1024 (no offset). That means my CRT is to the right of the DFP. Then the second mode is just the DFP and no CRT.

---

### Post by jacksenechal on 2009-03-08
I was seeking a solution to quickly reconfigure my X display to swap between monitors. Actually, I wanted it to default to dual-screen twinview mode, and I wanted to be able to unplug the laptop and quickly reconfigure for single-display mode on the fly. Originally I'd thought to try nvidia-settings command line interface, but as it's revealed on this thread and others, nvidia-settings doesn't work for that.

After lots of searching and trying things I stumbled upon the program "disper". I installed the Ubuntu package and the program does exactly what I wanted. [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

I used nvidia-settings to save my dual-screen setup to xorg.conf so that it will default to that on boot-up. Then I used CompizConfig to bind a shortcut key to execute the command 

```
disper -d auto -e
```

This auto-detects the display configuration and sets up the dual-monitor configuration if both are available. If the monitor isn't plugged in, it correctly configures just the laptop monitor. If you wanted to configure just the external monitor, you could run something like 

```
disper -d CRT-0 -s
```

Use "disper -l" to find out the names of your attached displays.

Now, for the win, someone tell me how to configure this to automatically happen as soon as the monitor is unplugged! Ultimately, I think Ubuntu ought to act just like OS X with respect to on-the-fly display configuration. With disper and a hotplug type solution, we're getting close.

---

### Post by warp99 on 2009-03-08
You can do if you have a basic xorg.conf file located in your /etc/X11 directory. Just press alt-F2 and run:

```
gksudo nvidia-settings
```

You'll have the nvidia-settings GUI pop-up as root. Go to "X Server Display Configuration" then click the "Configure" button. You'll be given an option to enable twinview. Once you have made all of the changes you need click on "Save to X Configuration File". Nvidia-settings will back up your old xorg.conf then apply the settings. After that press crtl-alt-backspace to reload X server. 

If you run into problems just restore the backup file in the /etc/X11 directory. :D

Edit:

Twinview will only be enabled if the second monitor is connected to the actual port. So all you have to do is plug the monitor in then crtl-alt-backspace to reload X-server.

---

### Post by Valentini on 2009-12-31
> **jacksenechal said:**
> I was seeking a solution to quickly reconfigure my X display to swap between monitors. Actually, I wanted it to default to dual-screen twinview mode, and I wanted to be able to unplug the laptop and quickly reconfigure for single-display mode on the fly. Originally I'd thought to try nvidia-settings command line interface, but as it's revealed on this thread and others, nvidia-settings doesn't work for that.

After lots of searching and trying things I stumbled upon the program "disper". I installed the Ubuntu package and the program does exactly what I wanted. [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

I used nvidia-settings to save my dual-screen setup to xorg.conf so that it will default to that on boot-up. Then I used CompizConfig to bind a shortcut key to execute the command 

```
disper -d auto -e
```

This auto-detects the display configuration and sets up the dual-monitor configuration if both are available. If the monitor isn't plugged in, it correctly configures just the laptop monitor. If you wanted to configure just the external monitor, you could run something like 

```
disper -d CRT-0 -s
```

Use "disper -l" to find out the names of your attached displays.

Now, for the win, someone tell me how to configure this to automatically happen as soon as the monitor is unplugged! Ultimately, I think Ubuntu ought to act just like OS X with respect to on-the-fly display configuration. With disper and a hotplug type solution, we're getting close.
Thanks a lot :) this was exactly what i was looking for.
I have simply binded disper -s and disper -S to two different keys. Now i can easily shift between my laptop monitor and my external monitor at home.

---

### Post by Valentini on 2009-12-31
> **jacksenechal said:**
> I was seeking a solution to quickly reconfigure my X display to swap between monitors. Actually, I wanted it to default to dual-screen twinview mode, and I wanted to be able to unplug the laptop and quickly reconfigure for single-display mode on the fly. Originally I'd thought to try nvidia-settings command line interface, but as it's revealed on this thread and others, nvidia-settings doesn't work for that.

After lots of searching and trying things I stumbled upon the program "disper". I installed the Ubuntu package and the program does exactly what I wanted. [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

I used nvidia-settings to save my dual-screen setup to xorg.conf so that it will default to that on boot-up. Then I used CompizConfig to bind a shortcut key to execute the command 

```
disper -d auto -e
```

This auto-detects the display configuration and sets up the dual-monitor configuration if both are available. If the monitor isn't plugged in, it correctly configures just the laptop monitor. If you wanted to configure just the external monitor, you could run something like 

```
disper -d CRT-0 -s
```

Use "disper -l" to find out the names of your attached displays.

Now, for the win, someone tell me how to configure this to automatically happen as soon as the monitor is unplugged! Ultimately, I think Ubuntu ought to act just like OS X with respect to on-the-fly display configuration. With disper and a hotplug type solution, we're getting close.
Thanks a lot :) this was exactly what i was looking for.
I have simply bound ```
disper -s
``` and ```
disper -S
``` to two different keys. Now i can easily shift between my laptop monitor and my external monitor at home.

---

### Post by BoobaSkaya on 2010-10-13
Disper just do the trick for me.
Thanks for the info.

I have just wrote a little script toggle.bash to have only 1 shortkey :
(assuming disper is installed locally in *~/Documents/scripts/python/disper/src* )


This will display a zenity list choice.

```

#!/bin/bash

#Show a selection list for DISPLAY settings
RESPONSE=$(zenity  --list  --text "Choose display" 			\
--radiolist  --column "Pick" --column "config" 				\
TRUE  LAPTOP 			\
FALSE TV 			\
FALSE DUAL			\
);

#Disper configuration
DISPER_PATH=~/Documents/scripts/python/disper/src
DISPER_BIN=cli.py

#Going to DISPER folder
cd $DISPER_PATH

case $RESPONSE in 
	LAPTOP )
		echo "Configuring display to laptop only"
		./$DISPER_BIN -s
	;;
	TV )
		echo "Configuring display to TV only"
		./$DISPER_BIN -S
	;;
	DUAL )
		echo "Configuring extended desktop to TV"
		./$DISPER_BIN -e
	;;
esac

```

---

### Post by thomi_ch on 2012-08-22
hey hey.. :popcorn:

exact this is also what i'm searching for.. easy toggle single/dual monitor ;) GREAT.. thanks to the dev of disper...

> **jacksenechal said:**
> I was seeking a solution to quickly reconfigure my X display to swap between monitors. Actually, I wanted it to default to dual-screen twinview mode, and I wanted to be able to unplug the laptop and quickly reconfigure for single-display mode on the fly. Originally I'd thought to try nvidia-settings command line interface, but as it's revealed on this thread and others, nvidia-settings doesn't work for that.

After lots of searching and trying things I stumbled upon the program "disper". I installed the Ubuntu package and the program does exactly what I wanted. [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

I used nvidia-settings to save my dual-screen setup to xorg.conf so that it will default to that on boot-up. Then I used CompizConfig to bind a shortcut key to execute the command 

```
disper -d auto -e
```

This auto-detects the display configuration and sets up the dual-monitor configuration if both are available. If the monitor isn't plugged in, it correctly configures just the laptop monitor. If you wanted to configure just the external monitor, you could run something like 

```
disper -d CRT-0 -s
```

Use "disper -l" to find out the names of your attached displays.

Now, for the win, someone tell me how to configure this to automatically happen as soon as the monitor is unplugged! Ultimately, I think Ubuntu ought to act just like OS X with respect to on-the-fly display configuration. With disper and a hotplug type solution, we're getting close.

regards
thomi

---

