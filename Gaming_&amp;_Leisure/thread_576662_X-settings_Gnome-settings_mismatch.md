---
title: "X-settings Gnome-settings mismatch"
date: 2007-10-15
forum: Gaming &amp; Leisure
---

### Post by drfox on 2007-10-15
When I log into Ubuntu, I get the error:

The X system keyboard settings differ from your current GNOME keyboard settings.
Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc105", layout "us" and no options.
Which set would you like to use?
*Use X settings*   *Keep Gnome settings*

I've tried running: 
gnome-settings-daemon

And get the following output:

** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)

TIA

Larry

---

### Post by nik_nah on 2007-10-21
I have this problem too, both my xorg.conf and in the gnome settings is for pc-104 keyboard.  But it complains about me having setup pc-101 somewhere and pc-104 elsewhere, it's not clear in the message which one is in the gnome config and which one is xorg config.

How do I get rid of this message?

That gnome-settings-daemon error looks like you're not running it as the same user as the one you used to first login.

---

### Post by CheeseEatingBulldog on 2007-10-24
I am getting the same problem:

```
The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc105", layout "us" and no options.

Which set would you like to use
```

And this is after I commented out 
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"gb"
# 	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

```

To see if it would reset itself. But no. I also tried looking for the two files with no idea where what is defined. Resetting via the systems menu does nothing either. 

I think it started after I did a dkpg-reconfigure xserver-xorg.

does anyone know why modules are no longer defined in the xorg?

---

### Post by Ant_Merlin on 2007-10-25
Hi, this sometimes happens when you change sessions (eg: gnome to xscript) to fix this go to system>accesories and select keyboard, check the settings in there and make sure correct keyboard layout it selected. 

To stop in the future you will need to log in to the other session types and choose the same keyboard layout.

---

### Post by asphixmx on 2007-10-27
I had the same problem. This is the way I solved it.
From synaptics Package Manager, install:
xkeyboard-config
then, from the MAIN MENU, choose OTHER/KEYBOARD LAYOUT

In my case, I had different keyboard layout here that from my preferences. I just matched both, and solved my prob.
Hope it helps you
By the way..this is my first post trying to help someone in ubuntu...I am a newbie in Linux :)

---

### Post by noamh on 2007-10-29
xkeyboard-config is said to be obsolete.

I am having the same problem.
After a game messed up my screen resolution, I restarted and this message came up.

I do not know how to remove it.

Any help will be appreciated!

---

### Post by noamh on 2007-10-30
I solved the problem by commenting some lines in the keyboard section:

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    # Option         "XkbLayout" "us,il"
    # Option         "XkbVariant" ","
    # Option         "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection

```


I am not sure what put those lines there in the first place, but it may have been
the nvidia-settings utility I played with a couple of days ago.

From now on, I am adding xorg.conf to my svn repository on a daily basis!

---

### Post by noamh on 2007-10-31
One additional comment:

After making those changes, the error disappeared but the keybaord was reverted to Us only with no options.

To fix that, just go the preferences->keyboard and redo the changes 
you want (add language, options, etc.).

---

