---
title: "Mouse and Keyboard not being recognized"
date: 2009-04-14
forum: General Help
---

### Post by Lancen833 on 2009-04-14
Hey guys,

I've been using Ubuntu on my computer for a couple of days, and I had just about configured it exactly how I wanted it. With one exception:

I am using a Logitech g15 keyboard and a g5 mouse. On my Windows box, I had set the extra-buttons on the mouse to do handy things like open new tabs and go back and forward. I really started to miss this functionality, so I checked out a few fixes on Google and came up with this site: [http://www.hidpoint.com/home.html](http://www.hidpoint.com/home.html)

I installed the right file for my OS, (8.10) and I followed all of the instructions to the letter. The application did not find my peripherals. "That's ok," I said, as the tutorial said that this might happen. It told me to unplug my keyboard and mouse and plug them back in. When I did this, they no longer functioned on my Linux partition. 

I tried rebooting in recovery mode and replugging things in at various stages in the boot-up stage. As soon as Ubuntu loads they turn right off. They work just fine for Windows. 

Is there anything I can do?

---

### Post by Lancen833 on 2009-04-15
Bump.

I'd really like some help with this.

---

### Post by Lancen833 on 2009-04-15
Is my only option to reformat my drive? I really don't want to...

---

### Post by codeseer on 2009-04-15
Hi. Welcome to Ubuntu. Getting adjusted will take some time and patience; I've been working with Ubuntu for about a month now and am still trying to figure things out. However, I've learned a great deal already.

I have the G15 and G5 as well. I have to admit that I haven't played around with them much so far.

With the G5, I was able to use the 'evdev' settings in my X11 configuration and it has my G5 back button working in Firefox, as well as the side scrolling and such. I have yet to figure out a way to automatically adjust the dpi (resolution) of the G5. Everytime I boot, I have to hit the up arrow to make it go to 2000 dpi.

To access the X11 configuration type this in the terminal:

```

gksudo gedit /etc/X11/xorg.conf

```

This is the relevant parts and how I changed the xorg.conf:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    **InputDevice    "Logitech G5" "CorePointer"**
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

[b]Section "InputDevice"
    Identifier     "Logitech G5"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Device" "/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse"
    Option         "ZAxisMapping" "invert"
    Option         "Emulate3Buttons" "false"
    Option         "Buttons" "9"
    Option	   "Resolution" "2000"
EndSection[/b]

```

The areas in bold are where I changed it. I replaced the ServerLayout and matched the name with the "Identifier" in the "InputDevice" area. As far as the "Device" option, that may be different on your system; just use the terminal and the 'cd' or 'ls -al' commands to search it out. This is basically a compilation of what I've read here and there; I do know that the "Resolution" option doesn't work, as I previously mentioned I'm still trying to solve that one. You basically need to restart for the configuration to take effect.

With the G15, I was able to get a clock and some other minor things to display on the LCD screen by loading the G15 stuff from the repository. I think you can configure macros for the keys with that also; I will explore it a bit and let you know what I get. I do remember that after installing that G15 stuff from the package manager, I was able to select the G15 keyboard from the System->Preferences->Keyboard, Layout tab. To get the stuff from the repository, go to System->Administration->Synaptic Package Manager, click the 'Search' button, type in G15 and hit Enter. I have everything listed there installed, except for the stuff with 'dev' at the end; that's for programming the keyboard directly.

---

### Post by codeseer on 2009-04-15
Through further exploration on the keyboard issue, I'm basically in the same boat as you. I can run 'sudo g15macro &' and get the lights to come on and the button lights to respond when I press them, at least for the M1-M3 and MR buttons. I have tried several things and just can't get the keys to work. The only thing working is the volume knob and the mute button, besides the LCD buttons. From the looks of it, the G14 key on M1 mode is supposed to launch a calculator when pressed; all it does is type ')'.

I'll keep researching it. Maybe someone will come along that knows how to progress.

---

### Post by Lancen833 on 2009-04-15
That seems like a good idea, and I will probably try it when I get my stuff working again, but I still need help actually making my computer recognize my keyboard and mouse. As far as Linux is concerned, they don't exist. Button presses have no result and the backlighting isn't even on. (They work just fine in windows still)

Should I try using a different keyboard to fix my problem?

---

### Post by codeseer on 2009-04-15
> **Lancen833 said:**
> That seems like a good idea, and I will probably try it when I get my stuff working again, but I still need help actually making my computer recognize my keyboard and mouse. As far as Linux is concerned, they don't exist. Button presses have no result and the backlighting isn't even on. (They work just fine in windows still)

Should I try using a different keyboard to fix my problem?

I'm pretty sure my backlighting worked fine before I tried anything. I'm using it on a USB port; you don't have it in a PS/2 port, do you?

My standard 10X, 116?, keys worked fine as well with the defaults.

Do you have any settings about the keyboard in the BIOS? I seem to remember that some BIOS won't let keyboards operate under certain ports or certain operating conditions without flipping a setting in the BIOS. Have you also tried another port?

---

### Post by wolfen69 on 2009-04-15
you might want to check your BIOS settings. there is usually a setting for legacy usb support. enable it if you need to.

---

### Post by codeseer on 2009-04-15
> **wolfen69 said:**
> you might want to check your BIOS settings. there is usually a setting for legacy usb support. enable it if you need to.

That's it. 'Legacy USB'. That's what I was trying to say in my edit.

---

### Post by Lancen833 on 2009-04-15
They are both USB, and they are plugged in correctly. 

I had it working for several days before I tried to make it so that the extra buttons worked as well. The instructions on the site had me unplug my keyboard, but when I pulgged it back in linux wouldn't recognize it anymore.

My bios recognizes the keyboard, but as soon as the Ubuntu start-up screen loads the keyboard dies. I have been using this keyboard with the same computer for over 3 years, so I doubt it is a compatibility issue

When I get home, I'll try the legacy settings, but I don't think that is the problem. 

Thanks for your help so far guys!

---

### Post by codeseer on 2009-04-15
> **Lancen833 said:**
> They are both USB, and they are plugged in correctly. 

I had it working for several days before I tried to make it so that the extra buttons worked as well. The instructions on the site had me unplug my keyboard, but when I pulgged it back in linux wouldn't recognize it anymore.

My bios recognizes the keyboard, but as soon as the Ubuntu start-up screen loads the keyboard dies. 

When I get home, I'll try the legacy settings, but I don't think that is the problem. 

Thanks for your help so far guys!

Well there's an uninstall for that software, try:

```

sudo uninstall_hidpoint

sudo rm -rf /root/.hidpoint/
sudo rm -rf $HOME/.hidpoint/

```

Then restart. It may have also modified /etc/X11/xorg.conf, because their website says that it needs root permissions to configure stuff.

---

### Post by Lancen833 on 2009-04-15
> **codeseer said:**
> Well there's an uninstall for that software, try:

```

sudo uninstall_hidpoint

sudo rm -rf /root/.hidpoint/
sudo rm -rf $HOME/.hidpoint/

```

Then restart.

Well, I *would*do that if I could log in or use my keyboard. :D


----

If I attached an older style Dell keyboard, do you think I would be able to use it?

---

### Post by codeseer on 2009-04-15
You could try using another keyboard. If that doesn't work, you could try to delete those files from a Live CD and check the xorg.conf.

I think they should call their software pre-alpha, if it strips the ability to use the basic keys and mouse functions.

---

### Post by Lancen833 on 2009-04-15
Well, as far as I know, I was the first person that this has happened to. From the looks of it, this software has been around since before 2006.

:(

---

### Post by Lancen833 on 2009-04-15
Ok, I'm home now. I found the Legacy USB setting in my BIOS. It was already enabled.

No dice there.

---

### Post by Lancen833 on 2009-04-15
Alright. I'm tired of dicking with it. Gonna do a fresh install.

---

### Post by codeseer on 2009-04-15
> **Lancen833 said:**
> Alright. I'm tired of dicking with it. Gonna do a fresh install.

Yeah, that's the good thing about Ubuntu. You can reinstall in 20 minutes and have everything back going, with proper backups, in under an hour total.

---

### Post by Lancen833 on 2009-04-15
Yup!

Around an hour from when I started to mess with it, I am back and better than ever. Got my custom Interface and fonts all installed with a sweet new background to top it off. :D

I'm going to try configuring my mouse your way.

---

### Post by Lancen833 on 2009-04-15
> **codeseer said:**
> Hi. Welcome to Ubuntu. Getting adjusted will take some time and patience; I've been working with Ubuntu for about a month now and am still trying to figure things out. However, I've learned a great deal already.

I have the G15 and G5 as well. I have to admit that I haven't played around with them much so far.

With the G5, I was able to use the 'evdev' settings in my X11 configuration and it has my G5 back button working in Firefox, as well as the side scrolling and such. I have yet to figure out a way to automatically adjust the dpi (resolution) of the G5. Everytime I boot, I have to hit the up arrow to make it go to 2000 dpi.

To access the X11 configuration type this in the terminal:

```

gksudo gedit /etc/X11/xorg.conf

```

This is the relevant parts and how I changed the xorg.conf:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    **InputDevice    "Logitech G5" "CorePointer"**
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

[b]Section "InputDevice"
    Identifier     "Logitech G5"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Device" "/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse"
    Option         "ZAxisMapping" "invert"
    Option         "Emulate3Buttons" "false"
    Option         "Buttons" "9"
    Option	   "Resolution" "2000"
EndSection[/b]

```

The areas in bold are where I changed it. I replaced the ServerLayout and matched the name with the "Identifier" in the "InputDevice" area. As far as the "Device" option, that may be different on your system; just use the terminal and the 'cd' or 'ls -al' commands to search it out. This is basically a compilation of what I've read here and there; I do know that the "Resolution" option doesn't work, as I previously mentioned I'm still trying to solve that one. You basically need to restart for the configuration to take effect.

With the G15, I was able to get a clock and some other minor things to display on the LCD screen by loading the G15 stuff from the repository. I think you can configure macros for the keys with that also; I will explore it a bit and let you know what I get. I do remember that after installing that G15 stuff from the package manager, I was able to select the G15 keyboard from the System->Preferences->Keyboard, Layout tab. To get the stuff from the repository, go to System->Administration->Synaptic Package Manager, click the 'Search' button, type in G15 and hit Enter. I have everything listed there installed, except for the stuff with 'dev' at the end; that's for programming the keyboard directly.

Hmm... I don't have half of that stuff! This is what I see:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by codeseer on 2009-04-15
You'll need to get all your upgrades and restart before it gets the new base. X11 was updated.

---

### Post by Lancen833 on 2009-04-15
Hmmm... My system says that it is fully updated.

Do I need to use synaptic to get it?

---

### Post by codeseer on 2009-04-15
> **Lancen833 said:**
> Hmmm... My system says that it is fully updated.

Do I need to use synaptic to get it?

I'd open synaptic and hit the 'reload', then make sure nothing needed updating. You restarted after the updates?

---

### Post by Lancen833 on 2009-04-15
Perhaps I am trying to update the wrong file. This is x.org, right?

---

### Post by codeseer on 2009-04-15
It should have just been part of your normal updates. I don't know if you being on Xubuntu would make any difference or not.

---

### Post by Lancen833 on 2009-04-15
My thing says Xubuntu?

Oops!

Nah, I'm on Ubuntu 8.10. I have 0 updates that my compy says I need and I have restarted since updating.

:(

---

### Post by codeseer on 2009-04-15
Well, that's very strange. Your side-scroll and back button on the mouse doesn't work?

---

### Post by Lancen833 on 2009-04-16
Oddly enough, my back button does work, but what do the sidescroll buttons do?

Can I remap them?

---

### Post by Lancen833 on 2009-04-16
I do feel exceptionally stupid for not noticing that.

---

### Post by codeseer on 2009-04-16
> **Lancen833 said:**
> Oddly enough, my back button does work, but what do the sidescroll buttons do?

Can I remap them?

Sidescroll works when you push on one or the other side of the scroll wheel. Try it out in a text editor or something that has a long line, bigger than the window.

---

### Post by Lancen833 on 2009-04-16
Can I change the functionality of the buttons? Like make my back button Ctr + T and my sidescrolls Alt + Left or right respectively?

---

### Post by codeseer on 2009-04-16
I'm still trying to figure that one out myself. Everything I've tried (I've tried a lot) has failed thus far.

---

### Post by Lancen833 on 2009-04-16
Well, that's a bummer. At least my original problem of not being able to use my keyboard has been solved.

Thanks so much for your help codeseer! :)

---

### Post by codeseer on 2009-04-16
No problem. I'll let you know if I figure out a real way to map those keys on the keyboard or the mouse either one.

---

### Post by Lancen833 on 2009-04-16
Thanks man, have a good night.

---

