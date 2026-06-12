---
title: "Enabling extra keys on Sun type 6 keyboard in 7.10"
date: 2007-11-18
forum: Desktop Environments
---

### Post by edh on 2007-11-18
I've recently upgraded to 7.10 on my Sun AMD box.  I have a Sun type-6 keyboard and it appears that I should be able to assign the additional function keys to do things like minimize windows using the keyboard shortcuts.  However, if I enter a key sequence for one of the additional keys (OPEN for instance) it has no effect despite the fact that the key code appears in the keyboard shortcuts window. 

Does anyone have the magic formula for making these additional keys do something?

---

### Post by xuande on 2008-03-19
> **edh said:**
> I've recently upgraded to 7.10 on my Sun AMD box.  I have a Sun type-6 keyboard and it appears that I should be able to assign the additional function keys to do things like minimize windows using the keyboard shortcuts.  However, if I enter a key sequence for one of the additional keys (OPEN for instance) it has no effect despite the fact that the key code appears in the keyboard shortcuts window. 

Does anyone have the magic formula for making these additional keys do something?

I've been able to keep the spare Sun keys working by mapping them with xmodmap.  If you want the keys to work more or less the way they were intended to, for example the help key calling up help windows, you can use an .Xmodmap like so:

! Sun Type 6 USB PC keyboard special keys
keycode 117 = SunCompose
keycode 134 = SunProps
keycode 140 = SunFront
keycode 248 = SunCopy
keycode 191 = SunOpen
keycode 192 = SunPaste
keycode 188 = SunCut
keycode 222 = SunPowerSwitch SunPowerSwitchShift
keycode 135 = SunUndo
keycode 133 = SunAgain
keycode 122 = SunFind
keycode 232 = SunStop
keycode 113 = SunAltGraph
keycode 174 = SunAudioLowerVolume SunVideoLowerBrightness
keycode 176 = SunAudioRaiseVolume SunVideoRaiseBrightness
keycode 160 = SunAudioMute SunVideoDegauss
keycode 245 = Help

Read the file with "xmodmap ~/.Xmodmap", which you can put in your .xsession or .xinitrc or whatever you use to initialize your desktop.  Ubuntu's default Gnome desktop will detect a .Xmodmap and ask you if you want to read it in when you next log in.

If you want to use the keys to do other things than the default, you can replace, say, Help with F13, Stop with F14, and so on, and then tell your programs to use those function keys as hotkeys.

Note that the keycodes given there are from my type 6 usb keyboard with PC layout (Caps Lock left of A).  They might be different from a keyboard with the UNIX layout (Control left of A).  I got them by running xev, pressing each key, and recording the keycode xev reported was pressed.

One nagging problem I've had with this solution is that although the compose key works, the compose LED doesn't light up.  I'm not sure how to get that to work right.

The "right" way to do this, btw, is probably through xkb, and it looks like Ubuntu 7.10 has some xkb files for type 6 usb keyboards in /usr/share/X11/xkb/, but I'm not having any luck getting them to work.

Hope this helps some!

---

### Post by xuande on 2008-03-19
I should add that, by default, there are no alternative graphics assigned to the keys, so AltGr isn't very useful at first.  To get use out of AltGr, you'll need to assign them yourself.  I've been doing this using xmodmap.

The format of an xmodmap keycode line is something like

keycode <num> = [keysym1] [keysym2] [keysym3] [keysym4] ...

which assigns keysym1 to the key with keycode num when pressed by itself, keysym2 when pressed with Shift, keysym3 when pressed with AltGr, and keysym4 when pressed with Shift and AltGr.  For keysyms you can use, check the file /usr/include/X11/keysymdef.h (you'll need to install x11-dev first, if you haven't already).  Remove the XK_ from the beginning of each macro name to get the name of the keysym.

Let's say I want to map AltGr-minus to endash '–' and Shift-AltGr-minus to emdash '—'.  First, I find they keycode for the minus sign using xev.  On my keyboard, it's 20.  Next, so I don't clobber '-' and '_', I run 'xmodmap -pke | grep 20' and look for the line that's for keycode 20 (instead of 120, say):

keycode  20 = minus underscore

In other words, when key 20 (minus) is pressed unshifted, produce a minus.  If it's pressed shifted, produce an underscore.  Add to your .Xmodmap the line

keycode 20 = minus underscore endash emdash

And 'xmodmap ~/.Xmodmap' to read it in.  Test it in something that will actually display an emdash, like OpenOffice, since in an xterm an emdash won't look much longer than a minus sign.

---

