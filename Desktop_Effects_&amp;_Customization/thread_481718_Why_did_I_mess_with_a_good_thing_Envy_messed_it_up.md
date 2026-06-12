---
title: "Why did I mess with a good thing? Envy messed it up for me..."
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by bravo_zulu on 2007-06-22
Hi, 

I had my dual monitors (ViewSonic something or other and Toshiba Tecra laptop with NVIDIA Quadro NVS 110M) working with dualview. 

I thought I'd try out Envy, so I downloaded it and installed it.

On the restart, I got a blue screen saying:

*Failed to start X-server. It is likely that it is not set up correctly. Would you like to view the X-server output to diagnose the problems? *

If I say OK to this, I can't make sense of what is on the next screen. From there, I go to another screen telling me that the X-server has been disabled, and to restart GDM when it's configured correctly. Then I go to a command prompt. 

Can anyone help me with uninstalling Envy or otherwise returning my system to the way it was before I tried Envy? 

Thanks.

---

### Post by bikeboy on 2007-06-22
Have a look in your /etc/X11/ folder, Envy will have made a backup xorg.conf file. Try copying that backup to overwrite /etc/X11/xorg.conf

```
sudo cp /etc/X11/xorg.conf.#### /etc/X11/xorg.conf
```

---

### Post by CheShA on 2007-06-22
Yup - I had the same problem, restoring the back up xorg.conf should do it. The secret is to say "NO!!!!" when envy asks you last thing if you would like it to attempt to configure your xorg.

---

### Post by bravo_zulu on 2007-06-22
Hmmmm, it's not working for me. 

Here is what I did (I'm new to this so I'm including all the steps):

cd /etc/X11
ls
-- There were a couple of backup and other files in here from different things that I did. I tried a couple of different ones including:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

and

sudo cp /etc/X11/xorg.conf_backup_200706221654 (this was from around when I was messing with envy)

Then I did this...

sudo shutdown -r now

and when it started up again I still had the blue screen saying my x-server wasn't configured properly...

Any more ideas??

---

### Post by bravo_zulu on 2007-06-22
I just notice I typed in the copy command wrong in my post (for the second one). When I did it I had:

sudo cp /etc/X11/xorg.conf_backup_200706221654 /etc/X11/xorg.conf

---

### Post by bikeboy on 2007-06-23
Alright, you could try posting your current xorg.conf for us to look at, if you can.

Otherwise, another option is to reconfigure the x-server in a semi-manual way.
```
sudo dpkg-reconfigure xserver-xorg
```

This will take you into a sort of wizard, accept the defaults for anything you're not sure about, but when you get to select the driver, choose nv. If that fails, you could try choosing vesa as the driver just to get you a desktop to troubleshoot from.

---

### Post by Plaaa on 2007-06-23
Hello 

I just _had_ the same problem with Envy. I don't really know what Envy do everything in my setup but I think the problem is not only in the xorg.conf file but with the driver itself, which has been installed from envy.

So following what I did and how I get the perfect (nvidia) driver for my graca:

To load the GUI again after the blue-screen, simply edit your xorg.conf file in section Driver with the standard Driver. In my case with nvidia driver i had to change nvidia into nv:

```

...
Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Standardgrafikkarte"
	Driver		"nvidia" // <- "nv"
	BusID		"PCI:1:0:0"
EndSection


```

After this I was able to start without bluescreen. So this show me that when you just over-copy your backup xorg.conf, it does not solve the problem, because it depends on the installed driver.

Next to get the perfect driver, I've done like this:

First i uninstall "all" drivers with the synaptic-package manager **(menu->system->administration)**
Secondly I run Envy and choose Uninstall Nvidia drivers again.
Finally I choose install manually (yes with Envy :)
Here now i had 3 options (I can't remember the exactly driver-names. Too much beer last night :D 
So I choose the second driver (I was lucky yesterday) and the install run again.
I choose "YES"when I was asked to let Envy do the configuration for my xorg.conf.
Also you will have to answer some questions in the (blue-screen) terminal. 

So that was it. After a reboot I have very good performance with display-effects and everything.
I can't tell you which driver you should choose,maybe google for the correct one or do like I did and just try it out :D

---

### Post by Seraed on 2007-07-17
In response to the OP: I actually get that problem alot when using Envy. When it fails to launch the GDM and dumps you on the login prompt, just log in as normal (though you will be at a CLI now) and run Envy in text mode (otherwise it will slap you and tell you to run in text mode).

For some reason the text mode for Envy fixes whatever problem it causes in the first place.

---

