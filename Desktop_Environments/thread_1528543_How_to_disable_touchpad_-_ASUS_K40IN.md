---
title: "How to disable touchpad - ASUS K40IN"
date: 2010-07-10
forum: Desktop Environments
---

### Post by nxhoaf on 2010-07-10
Hi, how can i disable touchpad while running ubuntu 10.04. Asus support only create the driver for Window, i cannot find the equivalent driver for Linux
Help me please, I always have a big problem when typing...

---

### Post by bobcollard on 2010-07-11
> **nxhoaf said:**
> Hi, how can i disable touchpad while running ubuntu 10.04. Asus support only create the driver for Window, i cannot find the equivalent driver for Linux
Help me please, I always have a big problem when typing...
In Synaptic Package Manager or Terminal install gpointing-device-settings.  You can run it in Startup Applications, via Terminal, or with Alt F2 (Run Program)

---

### Post by Synoc on 2011-05-16
I installed the gpointing program. I am having some issues. The "disable touch pad while another other device is present" setting won't save. and the "enable palm detection" isn't helping either. any idea what the problem is?

I am running an ASUS G72GX laptop and Ubuntu 10.10.
not the same system, but I should think close enough?

---

### Post by wildmanne39 on 2011-05-16
> **Synoc said:**
> I installed the gpointing program. I am having some issues. The "disable touch pad while another other device is present" setting won't save. and the "enable palm detection" isn't helping either. any idea what the problem is?

I am running an ASUS G72GX laptop and Ubuntu 10.10.
not the same system, but I should think close enough?
Hi, I found this information for your problem, I hope it helps.

LAPTOP TOUCHPAD

Using a laptop? If your cursor shoots off all over the place when you type and seemingly clicks on things without your consent, have no fear, you can disable it's click function while you're typing by opening your terminal and (carefully) doing the following:

gksudo gedit /etc/X11/xorg.conf

Next, find the section concerning your touchpad and copy the bold text below into your Xorg configuration file, so it looks similar to the example below:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "SHMConfig" "true"
EndSection

Make sure it all looks okay and that the "EndSection" text is in the right place, then close and save.

Ubuntu/Xubuntu Users: Navigate to "System > Preferences > Sessions" ("Applications > Settings > Autostart Applications" in Xubuntu) and click on "Add". Name it something like "Touchpad Syndaemon", the description can be "Disables touchpad while typing", and the all important command you need is "syndaemon -i 1 -d -t -K". For it to take effect, either logout or reboot.

Kubuntu: Create a text document in your home directory called "syndaemon", then open it with a text editor and add the following lines to it:

#!/bin/sh
syndaemon -i 1 -d -t -K

Close and save the file, then move it to the autostart folder with:

mv syndaemon ~/.kde/Autostart

Finally, make the file an executable script with the following command:

chmod u+x ~/.kde/Autostart/syndaemon
:D

---

### Post by Copper Bezel on 2011-05-16
I was about to suggest the synclient command to shut off the trackpad, checked mine, and found that my trackpad was supposedly already deactivated. = P I don't think I trust that, now, but then, I'm using an Elantech, so your chances might be better:

```
synclient TouchpadOff=1
```

None of this happens at the driver level like the original poster was suggesting, and Synaptics trackpads are, for the most part, Synaptics trackpads, so the model and make shouldn't matter. It's generally the less obvious details that get in the way. = P

Most machines also have a hardware switch or a function key for switching the trackpad on and off. Yours is Fn+F3. Try it out. (This works on my Asus in 10.10.)

---

### Post by Synoc on 2011-05-17
ok fn F9 (mine) doesn't work, the hardward switch doesn't work, and I had to remove gpointing-device... because it disabled my touchpad as soon as Gnome loaded into the GDE from the sign on screen. (to clarify, I used the touch pad to select my account and sign in, then it stopped working soon after.

---

### Post by Copper Bezel on 2011-05-17
Ick. Yeah, gpointing-device-settings (thankfully) doesn't run as root, so it affects only your account, not the login screen.

Sorry about the Fn+F3 thing. It's really hard to see the little buttons in the Amazon photos. = ) Since my Google-fu has failed me, would you mind installing gnome-device-manager and finding the entry for your touchpad? (Probably relatively low in the list.) That way, we can at least identify whether it's Synaptics, Elantech, etc. Just running gpointing-device-settings certainly shouldn't be disabling your trackpad.

---

### Post by Synoc on 2011-05-17
> **Copper Bezel said:**
> Ick. Yeah, gpointing-device-settings (thankfully) doesn't run as root, so it affects only your account, not the login screen.

Sorry about the Fn+F3 thing. It's really hard to see the little buttons in the Amazon photos. = ) Since my Google-fu has failed me, would you mind installing gnome-device-manager and finding the entry for your touchpad? (Probably relatively low in the list.) That way, we can at least identify whether it's Synaptics, Elantech, etc. Just running gpointing-device-settings certainly shouldn't be disabling your trackpad.

SynPS/2 Synaptics TouchPad
Device file: /dev/input/event8

BTW not only does it disable it, I can't even open the pointing devices application some times. it tries to open it, then returns nothing. I tried from terminal as well. I probably should haive redirected sterr but, I wasn't thinking about it before I uninstalled it.

---

### Post by Copper Bezel on 2011-05-17
Moving into the realm of the freaky, then. Synaptics touchpad, and everything's enabled in 10.10 by default. 

Did you try that Synclient command? If so, did you try any other Synclient tweaks to see if they would apply? The setting won't stick (some Synclient settings disappear after suspend and none persist on reboot) but we can keep narrowing down what's broken.

---

### Post by Synoc on 2011-05-18
> **Copper Bezel said:**
> Moving into the realm of the freaky, then. Synaptics touchpad, and everything's enabled in 10.10 by default. 

Did you try that Synclient command? If so, did you try any other Synclient tweaks to see if they would apply? The setting won't stick (some Synclient settings disappear after suspend and none persist on reboot) but we can keep narrowing down what's broken.

Synclient works like a dream. I may have to add a laucher to the panel to enable and disable it. since it doesn't persist through reboots I won't have to fear not having a mouse on hand : )

---

### Post by Copper Bezel on 2011-05-18
Sweet. = ) 

Do you one better on the launcher - put this into an executable text file named .trackpadtoggle.sh in your home folder,

```
#!/bin/bash
trackpadstate=`cat ~/.trackpadtoggle.txt`
	if [ "$trackpadstate" = "off" ];
	then
	synclient TouchpadOff=0;
	trackpadstate=on
	else
	synclient TouchpadOff=1;
	trackpadstate=off
	fi
echo $trackpadstate > ~/.trackpadtoggle.txt
```

then create a blank .trackpadtoggle.txt to save its setting in. Set ~/.trackpadtoggle.sh to a Compiz Command keybinding - say, Super+F9 - and the keystroke will toggle the trackpad on and off, meaning that you have a semblance of normal functionality. = )

---

### Post by Synoc on 2011-05-18
The glory of the shell script. dont' know why I didn't think of it...
I take that back, I have a 15 page pseudo-code to translate... and I'm tired of looking at kate : ) thank for the code. : )

Question: I set it to ~/.trackpadtoggle.sh. Yes it is executable. and it give me an err when I map it to mod4 (super) F9 or the fn+F9, either way. I tried to an err redirect to a text file to see what the actual error was. but it won't show up. 

If I type the same code in terminal it works fine. ideas?

Also the launcher I set up I put on a separate panel that autohides. now the panel won't come out and I can't even delete it and make a new one. it worked last night

---

### Post by Synoc on 2011-05-20
found the answer... it doesn't like the path ~/.trackpadtoggle.sh.

had to use absolute path /home/name/trackpadtoggle.sh

no idea why. but the laptop now fuctions as designed. Also found out who my autohide panel couldn't be accessed: Doesn't like my rotate cube desktop. had to switch to desktop wall again... but now I don't need it, so... back to cube. thank you very much.

---

### Post by Copper Bezel on 2011-05-20
Hey, no problem - sorry I didn't get back to you. I'm also sorry that the path didn't work, but I'm glad you got it figured out! = )

As for the Gnome Panel, if you have a Compiz edge binding on the same screen edge, Compiz will catch the hover and the Panel won't get it. However, you can give the panel a slightly larger edge of its own in gconf-editor, so that it'll still be triggered regardless: go to apps > panel > global and change panel_minimized_size to greater than one. Just in case you need it in the future. = )

---

### Post by Synoc on 2011-05-21
> **Copper Bezel said:**
> Hey, no problem - sorry I didn't get back to you. I'm also sorry that the path didn't work, but I'm glad you got it figured out! = )

As for the Gnome Panel, if you have a Compiz edge binding on the same screen edge, Compiz will catch the hover and the Panel won't get it. However, you can give the panel a slightly larger edge of its own in gconf-editor, so that it'll still be triggered regardless: go to apps > panel > global and change panel_minimized_size to greater than one. Just in case you need it in the future. = )

it's no big deal. in fact, thank you. if you had just told me, I wouldn't have learned anything. : )

---

### Post by Copper Bezel on 2011-05-21
Fair enough. = D Oh, mark the thread as Solved, if you would, Thread Tools in the upper right.

---

### Post by wb8nbs on 2011-09-05
The given shell script worked for me.. 10.04 on an Asus eee 901 netbook.  I mapped the script to the rightmost user key with the system > preferences > keyboard mapping tool.

---

