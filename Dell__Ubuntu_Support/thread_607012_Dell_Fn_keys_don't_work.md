---
title: "Dell Fn keys don't work"
date: 2007-11-08
forum: Dell  Ubuntu Support
---

### Post by Gyatak on 2007-11-08
I've just done a fresh install of Gutsy on my Dell Inspiron 9400. It took a day of following one set of advice after another, but I finally got my ATI Radeon X1400 card to work and am happily running Compiz.

But now, none of the Fn keys on my machine work. I know I got trapped in an Xorg reconfigure at some point, where it made me manually select my keyboard. Does anyone know if there is a way to get it to auto-recognize my keyboard again?

Or is this a deeper problem with Gutsy/Compiz and Dell?

Thanks!

---

### Post by Dellfan on 2007-11-08
Away from my notebook so cannot provide the exact listing but Gutsy recognized and uses all my Fn keys, including the Standby, Hibernate, wireless etc secondary functions, on my 1505. Many/most Dell's use a pc-105 keyboard.

You could just rerun the xorg config via:

sudo dpkg-reconfigure -phigh xserver-xorg

Off the top of my head I would suggest backing up up xorg.conf and trying (assuming you want a US layout):

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

---

### Post by Gyatak on 2007-11-08
Thanks, DellFan.

Unfortunately, that didn't help.

I'm wondering if  there a way to install a driver specific to the Dell Inspiron keyboard instead of using "Generic Keyboard". Or should I try another key setting in xorg?

---

### Post by Dellfan on 2007-11-09
Please post your current xorg.conf

---

### Post by Gyatak on 2007-11-09
Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	30.0	-	70.0
	Vertrefresh	50.0	-	160.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"ATI RADEON X1400"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option		"XaaNoOffscreenPixmaps"
	Busid		"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X1400"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "Extensions"
	Option		"Composite"	"0"
	Option		"Composite"	"0"
EndSection

---

### Post by Dellfan on 2007-11-09
Unfortunately your xorg.conf looks perfectly sane. Could you describe in more detail exactly what is not working with your keyboard. ie. all the function keys, just the Fn->Function_Key values, etc.

It certainly should just work, without messing around. Do you get the same behaviour with another keyboard?

---

### Post by Gyatak on 2007-11-09
> **Dellfan said:**
> Unfortunately your xorg.conf looks perfectly sane. Could you describe in more detail exactly what is not working with your keyboard. ie. all the function keys, just the Fn->Function_Key values, etc.

1- The super (windows) key is simply not recognized by the system--at least not by Compiz, where it's crucial.

2- The Fn monitor brightness keys (up/down arrow) never work

3- Other Fn keys work sporadically. Sometimes Fn-Page Up/Down works correctly to adjust the volume and sometimes not. If I log out and log back in (not reboot), the Fn keys seem to get enabled most of the time. But, if I try to use an Fn key when it's not working, it can disable the entire keyboard (but not the mouse). Its as if on booting from scratch. It's as if Compiz is trying to load too early. Sometimes items in the system tray appear to load late. Consequently, they load into the application bar instead of the system tray.

> It certainly should just work, without messing around. Do you get the same behaviour with another keyboard?

I've just tried it with a 104-key Compaz keyboard. It doesn't have a Fn key, but the super key didn't work on it, either.

BTW, thanks for helping me work this out.

---

### Post by Linicks on 2007-11-09
I see the 9400 is similar to my 6400.

One thing I do note about your xorg.conf is the Serverlayout section.

Mine comes at the very end, and also you have no DRI section.

So comment out the top:

```
# Section "ServerLayout"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
#Identifier "Default Layout"
#screen "Default Screen" 0 0
#Inputdevice "Generic Keyboard"
#Inputdevice "Configured Mouse"
#Inputdevice "Synaptics Touchpad"
#EndSection
```

and add this to the end and restart X:


```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

I doubt it will help - but you never know...

Nick

---

### Post by Gyatak on 2007-11-09
> **Linicks said:**
> 
...and add this to the end and restart X:


```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Thanks, Nick. It didn't like having the ServerLayout at the end, but the boot up seems to be better now. I'll have to watch it over time, since there seem to be inconsistencies in how Kubuntu loads. Perhaps the DRI section helped.

However, the super key and Fn up/down keys still don't work. :-(

Cheers,
Bill

---

### Post by Dellfan on 2007-11-09
I originally thought the same about the placement of the "ServerLayout" section but according to the xorg.conf docs all sections in the file are position independent. Unfortunately this should not have anything to do with your issue.

DRI is only needed for 3D acceleration on some ATI cards. Should have absolutely nothing to do with keyboard issues. Some higher end cards don't want/won't work with DRI.

---

### Post by Linicks on 2007-11-09
**Dellfan**: Yes, it was a wild shot anyway.

Another thought.

**Bill:** Have these keys ever worked in a previous installation, or is it a new machine you installed 7.10 on?  Could the keyboard be duff?

>>> > 3- Other Fn keys work sporadically. Sometimes Fn-Page Up/Down works correctly to adjust the volume and sometimes not.

That is strange - either they work or don't.

Can you run the dell diagnostics on it?

Nick

---

### Post by Rinzwind on 2007-11-09
In my 9300 I can change some stuff regarding the Fn keys (I can turn Fn-F2 (wireless on/off)) in the BIOS. Might not be much advice but you never know...

Did you fiddle with gconf-editor?

Some hints:

do a 
```
xmodmap -pke > .Xmodmap

```and a 
```
$ more .Xmodmap | grep Super
```
I get this: 
keycode 115 = Super_L
keycode 116 = Super_R
keycode 127 = NoSymbol Super_L

(says 115 for Super).

My Fn'keys work and I have a 9300 so it might be the same.
I saw something called```
 xev
``` 
> 
XEV(1)                                                                  XEV(1)

NAME
       xev - print contents of X events

SYNOPSIS
       xev  [-display displayname] [-geometry geom] [-bw pixels] [-bs {NotUse&#8208;
       ful,WhenMapped,Always}] [-id windowid] [-s] [-name string] [-rv]

DESCRIPTION
       Xev creates a window and then asks the X server to send it events when&#8208;
       ever  anything  happens to the window (such as it being moved, resized,
       typed in, clicked in, etc.).  You can also attach  it  to  an  existing
       window.   It  is  useful  for seeing what causes events to occur and to
       display the information that they contain; it is essentially  a  debug&#8208;
       ging and development tool, and should not be needed in normal usage.
```
KeyPress event, serial 30, synthetic NO, window 0x2a00001,
    root 0x52, subw 0x0, time 645656815, (96,77), root:(101,128),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2a00001,
    root 0x52, subw 0x0, time 645656818, (96,77), root:(101,128),
    state 0x40, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
It shows 115 (same as xmodmap)

---

### Post by Dellfan on 2007-11-09
What do you get when you run the monitor, via "lshal -m", and then press Fn-F10 and Fn-uparrow and Fn-downarrow?

You should get a status message which ends in  ButtonPressed = eject-cd,etc. If you don't then perhaps your "Fn" key is flaky.

Further to Nick's question, by "sometimes" do you mean in different sessions or sometimes in the same session it will work and then stop working? Have you tried removing and reseating the keyboard connector? Need to resolve if you are having a driver/software issue or a hardware issue.

---

### Post by Gyatak on 2007-11-09
> **Linicks said:**
> **Dellfan**: Yes, it was a wild shot anyway.

Another thought.

**Bill:** Have these keys ever worked in a previous installation, or is it a new machine you installed 7.10 on?  Could the keyboard be duff?

>>> 


The machine's less than a year old, and I had Feisty working decently well on it. I tried running Beryl on it, but it was too buggy, so I never really worked a lot with the super key. The machine came preloaded with Vista, and all keys worked well.

Something tells me this isn't a hardware issue, but I'll try running diagnostics just to be sure.

---

### Post by Gyatak on 2007-11-09
> **Rinzwind said:**
> 

Did you fiddle with gconf-editor?



I think we might be onto something. In gconf-editor->compiz->general->allscreens->options, ```
window_menu_key
``` is set to ```
<Alt>space
```. I'm running KDE and <Alt>space currently launches Katapult.

Should I unset the Compiz <Alt>space mapping or should I set it to a new value, like <Super> (is that a valid entry?)?

> 
I get this: 
keycode 115 = Super_L
keycode 116 = Super_R
keycode 127 = NoSymbol Super_L

(says 115 for Super).

I got the same result. So i don't think it's a hardware issue.

> 
My Fn'keys work and I have a 9300 so it might be the same.
I saw something called```
 xev
``` 

```
KeyPress event, serial 30, synthetic NO, window 0x2a00001,
    root 0x52, subw 0x0, time 645656815, (96,77), root:(101,128),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2a00001,
    root 0x52, subw 0x0, time 645656818, (96,77), root:(101,128),
    state 0x40, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
It shows 115 (same as xmodmap)
[/QUOTE]

Again I got the same result as you. So the question is why isn't Compiz recognizing super key input. Does it work on your machine? If so, what are your settings in gconf-editor?

Interestingly, I got no response with the Fn key on its own using XEV. I then tried using Fn-PgUp to up the volume, and it worked. Perhaps Fn on its own doesn't count as an input signal...?

---

### Post by Gyatak on 2007-11-09
> **Dellfan said:**
> What do you get when you run the monitor, via "lshal -m", and then press Fn-F10 and Fn-uparrow and Fn-downarrow?

Interestingly, I got this:

```
Start monitoring devicelist:
-------------------------------------------------
18:05:07.642: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = eject-cd
18:05:12.086: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = brightness-up
18:05:12.168: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = brightness-up
18:05:15.042: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = brightness-down
18:05:15.057: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = brightness-down

```

> Further to Nick's question, by "sometimes" do you mean in different sessions or sometimes in the same session it will work and then stop working? Have you tried removing and reseating the keyboard connector? Need to resolve if you are having a driver/software issue or a hardware issue.

By "sometimes" I mean in different sessions. Once they work, they seem to work. I haven't tried removing/reseating the connector, and--not to discount your suggestion--but my intuition tells me this is probably a Compiz issue.

If the gconf-editor exploration doesn't pan out, I'll try figuring out how to reseat the connector in my laptop.

---

### Post by Dellfan on 2007-11-09
The "Fn" key acts as a modifier, similar to "Shift"... so you don't get an event just for pushing it. Sounds like you have a config issue. Note sure what to suggest at this point as I have not messed with Compiz config files (mine just works :-) 

If you need help reseting the keyboard (which I don't think is your problem) send me a message and I can walk you through it... it is really easy. The keyboard typically requires removing one trim piece and 4-6 screws.

I just checked the the GConf settings and mine look the same for the windows-menu-key so I don't think that is it. 

I would be very interested to see what lshal -m reports when your Fn key stops working.

---

### Post by Gyatak on 2007-11-11
Hey everyone,

I found the answer! The Windows/Super key just wasn't activated correctly. If anyone else has this problem, check out this link:

[https://help.ubuntu.com/community/MappingWindowsKey](https://help.ubuntu.com/community/MappingWindowsKey)

I haven't figured out the Fn-Up/Down lighting keys yet, but I think I'm onto something.

Thanks for all your help!

---

### Post by piousp on 2007-11-14
I have the same problem. Some of the Fn keys work like they should (e.i sound, battery, wireless) but some others just appear to be doing nothing. So far i know my Fn + F10 (Eject cd) and Fn Up/Down combinations are not working at all. I have Dell Inspirion 6400 with Kubuntu Gutsy! The Fn worked really well in Feisty by the way.

---

### Post by Dellfan on 2007-11-14
Piousp, open a terminal and type the command "lshal -m", and then try out the Fn-Fwhatever key combinations. It should report out what they are bound to.

You may have something happening in xorg.conf and have mis-defined the keyboard or have somehow changed the keybindings (or for whatever reason they are not defined in KDE, can't comment on that since I have only been running Gnome on Ubuntu).  They work out of the box on a 1505 (which is the same as a 6400) with both 7.04 and 7.10 under Gnome.

---

### Post by Linicks on 2007-11-15
Out of interest, in a console run:

```
gnome-keybinding-properties
```

a box will pop up with gnome key bindings.   Don't change anything, just close it.  Now try your fn keys.

I have to do this in Fluxbox to get the fn keys to work.

Nick

---

### Post by geeree on 2007-11-15
I have an Inspiron 640m that I got last January. The first Linux I installed on it was Ubuntu 6.10 and most Fn keys never worked. I did not bother to troubleshoot the issue and then in April upgraded to 7.04. All Fn keys started working after that! 

Girish.

---

### Post by piousp on 2007-11-15
> **Dellfan said:**
> Piousp, open a terminal and type the command "lshal -m", and then try out the Fn-Fwhatever key combinations. It should report out what they are bound to.

You may have something happening in xorg.conf and have mis-defined the keyboard or have somehow changed the keybindings (or for whatever reason they are not defined in KDE, can't comment on that since I have only been running Gnome on Ubuntu).  They work out of the box on a 1505 (which is the same as a 6400) with both 7.04 and 7.10 under Gnome.

Ok, here is the result of the lshal -m:

Fn + UP:
10:40:34.269: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = brightness-up
10:40:34.413: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = brightness-up

Fn + Down:
10:40:36.495: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = brightness-down
10:40:36.572: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = brightness-down

FN + F10 (eject CD):
10:40:39.304: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = eject-cd

As i said, those functions are not working at all.

Here is my xorg.conf just in case:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
EndSection
...
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

Thanks for helping me out :)

---

### Post by Dellfan on 2007-11-15
It seems to be a confirmed bug in Gutsy.... see:

[https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/111943]("https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/111943")

I would suggest reading the thread, but the basic idea seems to be:

If you have other input actions (kcontrol -> Regional & Accessibility -> Input Actions), you should add it yourself.

You can do this by going there (you'll need to open kcontrol through the run command) and making a new action of type "Keyboard Shotcut -> Command/URL (simple)", using your Eject key for the shortcut, and 'kdeeject cdrom' as the command.

I would suggest adding khotkeysrc back to kubuntu-default-settings with this key included. (This bug is really a kubuntu-default-settings bug in that case).

---

### Post by piousp on 2007-11-15
Dellfan,

Thanks a lot. I'm gonna try that out as soon as i get home. I'll tell you how it went ;)

---

### Post by secretspicy15 on 2007-11-16
I am running Edgy on a Dell Inspiron E1705.

Most of my Fn keys work, however I have a similar problem with Fn-up Fn-down, which should control monitor brightness... When I press Fn-up, it restarts X. Fn-down does nothing. I have tried running lshal - m, but it yields nothing at all for Fn-down, and X restarts when I press Fn-up, even when lshal -m is running.

I cannot find a way to control the brightness at all... i don't think it would be too much of a challenge to assign a shortcut key to a command, if I could find a command that did what I want... as it is, I cannot change brightness...

Please advise...

Thank you!

---

### Post by piousp on 2007-11-19
Gyatak,

the eject cd room command is now working, but i found something really weird:

I tried to make the same process for the brighten-up/down and ESPECIALLY the F8 (CRT/LCD) which i'm gonna NEED in a week. When i tried to assing those keys for the action, they weren't even recognize so i couldnt assing them to the action.

---

### Post by piousp on 2007-11-25
:( I switched to Ubuntu. So i'm starting to get use to gnome. It does feels weird for now. But i'm glad that ubuntu recognize all fn keys, EXCEPT that the media buttons of my I6400 are not working. Maybe they are linked to an specific app, or they are just not working. At least, those aren't as important as the Fn keys :popcorn:

---

### Post by fragos on 2007-11-25
I recently purchased a Dell 1420n with 7.04 installed.  The function and media keys work as you'd expect.  There may be some deb packages on dell.com that can help you.  Dell states an intension to release 7.10 as an upgrade for Dell pre-installed devices.  Apparently they are still working some issues relating to complete 7.10 support on Dell boxes.

---

### Post by kuja on 2007-11-26
> **fragos said:**
> I recently purchased a Dell 1420n with 7.04 installed.  The function and media keys work as you'd expect.  There may be some deb packages on dell.com that can help you.  Dell states an intension to release 7.10 as an upgrade for Dell pre-installed devices.  Apparently they are still working some issues relating to complete 7.10 support on Dell boxes.

With any luck they might even get the FN keys on the 1420Ns in gutsy working again :|

---

### Post by huck416 on 2007-11-29
I've got the Dell 1521 (AMD) and most of the function keys work fine. Fn F3 for batter status and such. But the Fn up arrow / down arrow for brightness control do not work. They did (I'm sure) when I still had Feisty on it but now with Gutsy they don't. Also, when I press the mute key on the front it displays "mute on" but sound will still play, and yet, the volume up/down keys on the front do control the volume just fine although in 10% increments.

I'm sure someone will figure it out.

Huck416

---

### Post by Linicks on 2007-11-29
OK, I noticed after I suspend, my battery status (fn+F3) and CD eject (fn+F10) stopped working - these work perfectly after a fresh boot.

So, investigating, I found this.

File: ** /usr/share/hotkey-setup/dell.hk**
```

# Dell Laptops
                                        # Fn+Esc        Standby (ACPI)
setkeycodes     e00a    $KEY_SUSPEND    # Fn+F1         Hibernate (e00a)
#setkeycodes    e008    $KEY_           # Fn+F2         Wireless (e008)
setkeycodes     e007    $KEY_BATTERY    # Fn+F3         Battery (e007)
setkeycodes     e00b    $KEY_VIDEOOUT   # Fn+F8         CRT/LCD (e00b)
setkeycodes     e009    $KEY_EJECTCD    # Fn+F10        EjectCD (e009)
setkeycodes     e005    $KEY_BRIGHTNESSDOWN # Fn+Down   Brightness Down (e005)
setkeycodes     e006    $KEY_BRIGHTNESSUP # Fn+Up       Brightness Up (e006)
setkeycodes     e012    $KEY_MEDIA      # MediaDirect   Load Media Player (e012)

# inspiron multimedia keys
setkeycodes     e001    $KEY_PLAYPAUSE  # Dell E Key    Play/Pause (e001)
setkeycodes     e002    $KEY_STOP       # Dell i Key    Stop (e002)
setkeycodes     e003    $KEY_PREVIOUSSONG # Dell 1 Key  Previous Song (e003)
setkeycodes     e004    $KEY_NEXTSONG   # Dell 2 Key    Next Song (e004)
setkeycodes     e022    $KEY_PLAYPAUSE  # front         Play/Pause (e022)
setkeycodes     e010    $KEY_PREVIOUSSONG # panel       Previous Song (e010)
setkeycodes     e019    $KEY_NEXTSONG   # media         Next Song (e019)
setkeycodes     e024    $KEY_STOPCD     # buttons       Stop (e024)
setkeycodes     e06d    $KEY_MEDIA      # (Inspiron)    Media (e06d)
```

This gets called from:  **/etc/rc2.d/S20hotkey-setup**

I have attached this file (remember to remove the .txt extension, only added for upload in here).

I found that if I run **/etc/rc2.d/S20hotkey-setup restart** after suspend, my fn keys work again.

Hope this helps a little more.

Nick

---

### Post by huck416 on 2007-12-08
Linicks,

Two questions really:
1. I understand you have suspend (and hibernate) working with a Dell 1521 and Gutsy?

2. The restart (/etc/rc2.d/S20hotkey-setup restart) had no effect on my Fn UP / DOWN keys and the brightness control. They still don't work. Is there something else I need to configure so it knows to grab the Dell sequence from the file you uploaded? I think it's really a keymap issue and I don't understand why some of the Fn key combinations work and others don't. I obviously knows there's a Fn key on the keyboard. Thanks.

huck416

---

### Post by fragos on 2007-12-08
> **Linicks said:**
> OK, I noticed after I suspend, my battery status (fn+F3) and CD eject (fn+F10) stopped working - these work perfectly after a fresh boot.

So, investigating, I found this.

File: ** /usr/share/hotkey-setup/dell.hk**
```

# Dell Laptops
                                        # Fn+Esc        Standby (ACPI)
setkeycodes     e00a    $KEY_SUSPEND    # Fn+F1         Hibernate (e00a)
#setkeycodes    e008    $KEY_           # Fn+F2         Wireless (e008)
setkeycodes     e007    $KEY_BATTERY    # Fn+F3         Battery (e007)
setkeycodes     e00b    $KEY_VIDEOOUT   # Fn+F8         CRT/LCD (e00b)
setkeycodes     e009    $KEY_EJECTCD    # Fn+F10        EjectCD (e009)
setkeycodes     e005    $KEY_BRIGHTNESSDOWN # Fn+Down   Brightness Down (e005)
setkeycodes     e006    $KEY_BRIGHTNESSUP # Fn+Up       Brightness Up (e006)
setkeycodes     e012    $KEY_MEDIA      # MediaDirect   Load Media Player (e012)

# inspiron multimedia keys
setkeycodes     e001    $KEY_PLAYPAUSE  # Dell E Key    Play/Pause (e001)
setkeycodes     e002    $KEY_STOP       # Dell i Key    Stop (e002)
setkeycodes     e003    $KEY_PREVIOUSSONG # Dell 1 Key  Previous Song (e003)
setkeycodes     e004    $KEY_NEXTSONG   # Dell 2 Key    Next Song (e004)
setkeycodes     e022    $KEY_PLAYPAUSE  # front         Play/Pause (e022)
setkeycodes     e010    $KEY_PREVIOUSSONG # panel       Previous Song (e010)
setkeycodes     e019    $KEY_NEXTSONG   # media         Next Song (e019)
setkeycodes     e024    $KEY_STOPCD     # buttons       Stop (e024)
setkeycodes     e06d    $KEY_MEDIA      # (Inspiron)    Media (e06d)
```

This gets called from:  **/etc/rc2.d/S20hotkey-setup**

I have attached this file (remember to remove the .txt extension, only added for upload in here).

I found that if I run **/etc/rc2.d/S20hotkey-setup restart** after suspend, my fn keys work again.

Hope this helps a little more.

Nick

These files are part of the standard Ubuntu 7.10 distribution I'm running on my desktop.  They appear to accommodate a number of laptop brands.  I purchase an Inspiron 1420n a few weeks ago that came with 7.04 pre-installed.  My function keys all seem to work.  I decided to wait for Dell to announce they were ready for the 7.10 upgrade.  I ran Shared Folders on both systems and installed whatever version of Unison was in the respective distributions.  I created a work in progress folder on both desktops and Unison with NFS keeps them in sync.

---

### Post by tobleron on 2007-12-09
Has anyone sorted that problem out yet? I have the same problem with my dell inspiron 1420n after installing gutsy. Some of the fn keys work, others don't. The arrow keys for brightness control belong to the ones that don't work, which is particularly annoying. The problem is not connected to suspend/hibernate in my case and the dell hotkey-setup file looks just like the one posted. Everything was fine under feisty.

---

### Post by fragos on 2007-12-09
It would appear that Dell may have done some engineering work with 7.04 to achieve complete operability with with their hardware like the 1420n.  We may need to wait for Dell to release those changes for 7.10.  I for one, would love to know exactly what they have done.  My 1420n came from Dell with an Ubunru CD with some additional stickers on it.  The 1420n also shiped with some special partitions which appear to be used for problem diagnosis and creating the preinstalled 7.04.  When I first turned on my 1420n it went through what looked like a regular Ubuntu install but without the live CD.  It may be a simple matter to go back to 7.04 pre-install to get everything working until Dell makes 7.10 available.

---

### Post by kuja on 2007-12-09
> **tobleron said:**
> Has anyone sorted that problem out yet? I have the same problem with my dell inspiron 1420n after installing gutsy. Some of the fn keys work, others don't. The arrow keys for brightness control belong to the ones that don't work, which is particularly annoying. The problem is not connected to suspend/hibernate in my case and the dell hotkey-setup file looks just like the one posted. Everything was fine under feisty.

Believe it or not, it's actually a **kernel** issue ... I hope the bug gets sorted out too.

---

### Post by battlesound on 2007-12-20
Well, I searched for anything "dell" on my Inspiron E1505, running Ubuntu Studio 7.10 with the low latency/realtime kernel 2.6.22-14-rt (upgraded from Fiesty 7.04), and found the same file (/usr/share/hotkey-setup/dell.hk):

```

# Dell Laptops
					# Fn+Esc	Standby (ACPI)
setkeycodes	e00a	$KEY_SUSPEND	# Fn+F1		Hibernate (e00a)
#setkeycodes	e008	$KEY_		# Fn+F2		Wireless (e008)
setkeycodes	e007	$KEY_BATTERY	# Fn+F3		Battery (e007)
setkeycodes	e00b	$KEY_VIDEOOUT	# Fn+F8		CRT/LCD (e00b)
setkeycodes	e009	$KEY_EJECTCD	# Fn+F10	EjectCD (e009)
setkeycodes	e005	$KEY_BRIGHTNESSDOWN # Fn+Down	Brightness Down (e005)
setkeycodes	e006	$KEY_BRIGHTNESSUP # Fn+Up	Brightness Up (e006)
setkeycodes	e012	$KEY_MEDIA	# MediaDirect	Load Media Player (e012)

# inspiron multimedia keys
setkeycodes	e001	$KEY_PLAYPAUSE	# Dell E Key	Play/Pause (e001)
setkeycodes	e002	$KEY_STOP	# Dell i Key	Stop (e002)
setkeycodes	e003	$KEY_PREVIOUSSONG # Dell 1 Key	Previous Song (e003)
setkeycodes	e004	$KEY_NEXTSONG	# Dell 2 Key	Next Song (e004)
setkeycodes     e022    $KEY_PLAYPAUSE	# front		Play/Pause (e022)
setkeycodes     e010    $KEY_PREVIOUSSONG # panel	Previous Song (e010)
setkeycodes     e019    $KEY_NEXTSONG	# media		Next Song (e019)
setkeycodes     e024    $KEY_STOPCD	# buttons	Stop (e024)
setkeycodes	e06d	$KEY_MEDIA	# (Inspiron)	Media (e06d)


```

I had everything working in Fiesty -- all multimedia buttons, all Fn commands.

I needed to download the linux header file for the lowlatecy kernel and then I noticed that I had some problems with some buttons and commands.  

After upgrading to Gutsy 7.10, I still had the problems, but the brightness up/down command (Fn + up arrow/down arrow) was buggy.  Those commands worked, but the change in brightness took forever... there were too many divisions of brightness for each key stroke.  This was fixed sometime recently... probably in an update and now works as it should (about 5 key strokes to go from full brigtness to dimmest).  yay, but...

Here's the issue, and I'm wondering if this is what anyone else sees.  All the Fn buttons and multimedia buttons work except for:
[INDENT]Volume mute
Volume down
Volume up

Both with the multimedia buttons and Fn commands for them!![/INDENT]

In the file:
/usr/share/hotkey-setup/dell.hk (above)
**we don't see anything for the volume!  So can these be added here to correspond to the volume Applet (2.20.0)??**  I'm going to investigate more.  Also, I checked the keys using ```
xev
``` and I got very little help:
(Fn mute, volume down, and up, multimedia button mute, vol down, and up)

```
FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
```

The keys return pretty much the same information as the ones that work!  Sometimes, though, I get  4294967223 instead of 2 after "keys:" on ones that work.  hmm?

---

### Post by fragos on 2007-12-20
I have a 1420n that came with Feisty and all keys worked.  I downloaded the Dell 7.10 DVD image and did a factory install which included I believe the extra partitions Dell uses.  All the keys work.  I also run 7.10 on my DIY Desktop.  I've noticed some small differences between the two 7.10's.  For one, the mouse preferences from Dell include a tab for touchpad.  A small detail, being about to disable touchpad taps, but one that some users wanted.  To me, it's an indicator that Dell has gotten into even the mundane details specific to what their users had issue with.  Granted, disabling touchpad taps was always available but the user had to know to install "gsynaptics" to get it.  I would think that the Dell changes will work themselves into Ubuntu but they will appear first on the Dell provided distributions.

---

### Post by Monkey_Tales on 2007-12-21
Fn-keys/fan and cpu control:

Go to Synaptic Package Manager and search for i8kutils:

    utilities for Dell Inspiron and Latitude laptops
    This is a collection of utilities to control Dell Inspiron and Latitude
    laptops. It includes programs to turn the fan on and off, to read fan
    status, CPU temperature, BIOS version and to handle the volume buttons
    and Fn-keys.

    The package includes also a small Tk applet, designed to be swallowed in the
    gnome panel, which monitors the CPU temperature and controls automatically
    the fans accordingly to user defined thresholds.

    The programs require the kernel module i8k.o which can be compiled from
    the package sources or found in Linux kernel 2.4.14 and later versions.
    The kernel module has been tested only on Inspiron 8000 laptops but it
    should work on any Inspiron and Latitude laptops.

---

### Post by stevoo on 2007-12-21
> 
```
FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
```

The keys return pretty much the same information as the ones that work!  Sometimes, though, I get  4294967223 instead of 2 after "keys:" on ones that work.  hmm?


Are you sure they work ? 
Cause if i do it on my working button 
they will display more infos and on the not working one like the display one i will have 0 0 0 0 
```
FocusOut event, serial 30, synthetic NO, window 0x3a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 30, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 30, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 30, synthetic NO, window 0x3a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 30, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 30, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyPress event, serial 30, synthetic NO, window 0x3a00001,
    root 0x5d, subw 0x0, time 4274148513, (159,169), root:(163,244),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3a00001,
    root 0x5d, subw 0x0, time 4274148513, (159,169), root:(163,244),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x3a00001,
    root 0x5d, subw 0x0, time 4274148543, (159,169), root:(163,244),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3a00001,
    root 0x5d, subw 0x0, time 4274148543, (159,169), root:(163,244),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
the infos were on working buttons and the 0z on the not working

---

