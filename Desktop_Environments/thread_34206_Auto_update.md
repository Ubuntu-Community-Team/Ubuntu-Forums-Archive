---
title: "Auto update"
date: 2005-05-13
forum: Desktop Environments
---

### Post by arunsub on 2005-05-13
1.I installed KDE through Ubuntu. I get an icon in the status bar in Ubuntu GNOME if there's any update available. I would like to know how to enable that in KDE. 

2. How do I enable my Logitech keys (like media player keys, volume, mail etc) in KDE? I can do it easily in GNOME through System - preference - keyboard.

---

### Post by dhanish on 2005-05-13
Yea, I wonder if the update applet from Ubuntu can be installed in Kubuntu and if so what's the package name?

As far as configuring your keyboard go to Control Center -> Region and Accessibility -> Keyboard Layout then select your model of the keyboard.

---

### Post by arunsub on 2005-05-13
[QUOTE=dhanish]Yea, I wonder if the update applet from Ubuntu can be installed in Kubuntu and if so what's the package name?

As far as configuring your keyboard go to Control Center -> Region and Accessibility -> Keyboard Layout then select your model of the keyboard.[/QUOTE]
If i select the model of my keyboard, do Logitech special keys (like volume control, mail etc) work?

---

### Post by arunsub on 2005-05-13
[QUOTE=dhanish]Yea, I wonder if the update applet from Ubuntu can be installed in Kubuntu and if so what's the package name?

As far as configuring your keyboard go to Control Center -> Region and Accessibility -> Keyboard Layout then select your model of the keyboard.[/QUOTE]

I tried as you said. the media player keys work fine, but other keys like Mail. My home etc doesn't work. How do I enable those?

---

### Post by dhanish on 2005-05-13
Yes it should unless the specific model is not there.

After you select the model and save the settings you should be able to use those keys as shortcuts/hotkeys however you will have to configure them manually they won't be preconfigured.

EDIT: Seems like you posted a reply before I got around to posting the reply to the original.

Anyhow if the other keys are not working not exactly sure. I have some other no name brand keyboard which I had to go through the hassle of configuring manually(xkb configuration files.) As I was reading into how to do that I ran into web pages which discussed what you were experiencing  but can't remember the resolution (if any.)

Sorry I wish I can help you further but you might start from here as I did:
[http://www.ubuntulinux.org/wiki/MultimediaKeys](http://www.ubuntulinux.org/wiki/MultimediaKeys) 
[http://www.ubuntuforums.org/showthread.php?t=12159](http://www.ubuntuforums.org/showthread.php?t=12159)

---

### Post by johnprgr on 2005-05-15
I have a logitech lx300 cordless desktop duo.  I had to modify the "logicdp" section of the /etc/X11/xkb/symbols/inet file to get most of my keys to work.  If you have this same keyboard.  I did this long ago when I used Mandrake so I don't even know what I changed I just copy this file over to every new distro I try, anyway it looks like this:

xkb_symbols "logicdp" {
    name[Group1]= "Logitech Cordless Desktop Pro";

    key <I5F>	{	[ XF86Standby		]	};

    key <I20>	{	[ XF86AudioMute		]	};
    key <I2E>	{	[ XF86AudioLowerVolume	]	};
    key <I30>	{	[ XF86AudioRaiseVolume	]	};
    key <I22>	{	[ XF86AudioPlay, XF86AudioPause ] };
    key <I24>	{	[ XF86AudioStop		]	};
    key <I10>	{	[ XF86AudioPrev		]	};
    key <I19>	{	[ XF86AudioNext		]	};
    key <XFER>   {       [ XF86AudioMedia        ]       };

    key <I02>	{	[ XF86HomePage		]	};
    key <I6C>	{	[ XF86Mail		]	};
    key <FK17>	{	[ XF86Search		]	};
    key <I66>	{	[ XF86Go		]	};

    key <I6A>	{	[ XF86Back		]	};
    key <I69>	{	[ XF86Forward		]	};
};

As for the Volume/pause/play etc... buttons I have to use khotkeys and attach them via dcop to kmix.  Its pretty self explanitory how to do it, press "New Action"  button change "Action type" from Generic to "Keyboard Shortcut -> DCOP Call (simple).  Select the Keyboard Shortcut tab press the button that says "None" and them press the button you want to use.  On the DCOP Call Settings tab, press the "Run KDCOP" button and you'll get a list of all the apps you can send messages to along with a list of messages you can send.  Just fill in the blanks with the information from KDCOP.

The KDE keyboard layout part of kcontrol does not work for my keyboard.

This is how I do it, maybe it would work for you also.  Good luck and I hope this helps.

---

### Post by arunsub on 2005-05-16
> **johnprgr]I have a logitech lx300 cordless desktop duo.  I had to modify the "logicdp" section of the /etc/X11/xkb/symbols/inet file to get most of my keys to work.  If you have this same keyboard.  I did this long ago when I used Mandrake so I don't even know what I changed I just copy this file over to every new distro I try, anyway it looks like this:

xkb_symbols "logicdp" {
    name[Group1]= "Logitech Cordless Desktop Pro" said:**
> 	};

    key <I20>	{	[ XF86AudioMute		]	};
    key <I2E>	{	[ XF86AudioLowerVolume	]	};
    key <I30>	{	[ XF86AudioRaiseVolume	]	};
    key <I22>	{	[ XF86AudioPlay, XF86AudioPause ] };
    key <I24>	{	[ XF86AudioStop		]	};
    key <I10>	{	[ XF86AudioPrev		]	};
    key <I19>	{	[ XF86AudioNext		]	};
    key <XFER>   {       [ XF86AudioMedia        ]       };

    key <I02>	{	[ XF86HomePage		]	};
    key <I6C>	{	[ XF86Mail		]	};
    key <FK17>	{	[ XF86Search		]	};
    key <I66>	{	[ XF86Go		]	};

    key <I6A>	{	[ XF86Back		]	};
    key <I69>	{	[ XF86Forward		]	};
};

As for the Volume/pause/play etc... buttons I have to use khotkeys and attach them via dcop to kmix.  Its pretty self explanitory how to do it, press "New Action"  button change "Action type" from Generic to "Keyboard Shortcut -> DCOP Call (simple).  Select the Keyboard Shortcut tab press the button that says "None" and them press the button you want to use.  On the DCOP Call Settings tab, press the "Run KDCOP" button and you'll get a list of all the apps you can send messages to along with a list of messages you can send.  Just fill in the blanks with the information from KDCOP.

The KDE keyboard layout part of kcontrol does not work for my keyboard.

This is how I do it, maybe it would work for you also.  Good luck and I hope this helps.

I'll give this a try. How do I find the keys numbers like  key <I5F>?

---

### Post by Terracotta on 2005-05-17
Since we're talking about keyboard layout, is there something similar for the logitech x300 mouse? to use the forward and bakward buttons? and the switch programs button?

---

### Post by johnprgr on 2005-05-17
The keycodes like "<I5F>" are found in the file /etc/X11/xkb/keycodes/xfree86.  I don't mess with this file, but I believe the process goes like this.  Run the program "xev" from konsole.  A window will pop up, make sure the window has focus and press the key you want to know about.  You will get output like the following:

KeyPress event, serial 27, synthetic NO, window 0x3800001,
    root 0xd6, subw 0x0, time 1405480, (144,852), root:(148,924),
    state 0x10, keycode 122 (keysym 0x1008ff1b, XF86Search), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

Note the " keycode 122 (keysym 0x1008ff1b, XF86Search)"  you use the 122 in the /etc/X11/xkb/keycodes/xfree86 file to assign a symbol to the key like this example from said file "    <FK17> =  122; ", then you use the /etc/X11/xkb/symbols/inet file to mape the <FK17> to the message "XF86Search".

That is the gist of it, I have tried messing with the keycodes and symbol files in the past with no luck so I can't say much more about it.

Hope this helps you a little more.

---

### Post by johnprgr on 2005-05-17
[QUOTE=Terracotta]Since we're talking about keyboard layout, is there something similar for the logitech x300 mouse? to use the forward and bakward buttons? and the switch programs button?[/QUOTE]
 The x300 mouse does not have all those buttons, it just has two plus the scroll wheel.  All the special mouse buttons are still a mystery to me.

---

### Post by Terracotta on 2005-05-17
[QUOTE=johnprgr]The x300 mouse does not have all those buttons, it just has two plus the scroll wheel.  All the special mouse buttons are still a mystery to me.[/QUOTE]

Euhm, ok my mistake, it was the mx310, and this one definitaly has forward backward and one button to switch between programs (like alt-tab). In windows it used to work perfectly.

---

### Post by arunsub on 2005-06-23
Any idea on how to enable auto update in Kubuntu?

---

