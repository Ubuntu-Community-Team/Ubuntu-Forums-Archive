---
title: "Strange Keybinding Behavior, Please Help"
date: 2009-05-30
forum: General Help
---

### Post by e64462 on 2009-05-30
Hello, I'm having trouble configuring (atleast) one of the keys on my Lenovo X61 Tablet after upgrading to Jaunty. Specifically, the key dedicated to rotating the screen, located on the lower left corner of the laptop's LCD.

I've been working on this for hours it seems, so I dont remember the order of the steps I took, but I can tell you everything I've tried.

This key had a keycode assigned to it out of the box, but no keysym (I think this is what the English-like names are called). So first i tried the following to assign a keycode.

```

echo 'keycode 199 = XF86RotateWindows' > ~/.Xmodmap && xmodmap ~/.Xmodmap

```

Then I believe I started with the ccsm, because i recalled from Intrepid that this was the easiest way (in addition to gconf-editor) to assign keysyms to commands. So i used the "grab key combination" option and assigned my rotate script to the respective command option. I also Remembered to check that the keysym, XF86RotateWindows, was assigned to the appropriate key using xev.

But pressing the key at this point had no effect. My thought at this point was that it might either be a problem with my rotate program, or with the binding itself. I eliminated the former by typing "rotate" (the name of my program) in the shell, which created no problems. When I replaced "rotate" in the ccsm command option with "touch /home/nick/Desktop/lawls" and pressed the key, nothing happened.

I tried restarting the window manager, restarting X, restarting the laptop... i tried applying these changes in gconf-editor, and I just recently tried using the System->Preferences->Keyboard Shortcuts gui (which i realized during my searches is now capable of custom keybindings). 

I'd really rather not resort to xbindkeys or anything like that... especially since everything suggests that the key is working.

I'm really at a loss here, any output you need to help me diagnose this problem I'd be happy to provide. Thanks in advance!

EDIT:
I also eliminated the possibility that perhaps ccsm wasn't binding keys correctly by binding another unconventional key to the rotate script, which worked without error. This key didn't require assigning a keycode to a keysym though, so perhaps the problem lies somewhere in this step?

--
Nick

---

### Post by Favux on 2009-05-30
Hi e64462,

If xev is showing a keycode you should be able to bind it provided it isn't already bound to something.  You may have to remove your changes to Xmodmap.  I also think CCSM is the easiest way to go.  For a little more info. on keybinding see:  [http://ubuntuforums.org/showthread.php?t=996830&page=16](http://ubuntuforums.org/showthread.php?t=996830&page=16)

---

### Post by e64462 on 2009-05-30
Hey Favux, thanks for the reply

Unfortunately I don't think i follow you. I think what you're saying is that I dont need to bind the keycode to a keysym with xmodmap, that just the keycode is necessary in Jaunty. I read your first post on that thread, it just more or less outlines (slightly more eloquently) exactly what I did.

As for the key being previously bound, this is a fresh install, only a few days old, and I certainly haven't bound it to anything... I noticed no strange behavior when I pressed the key before messing with it (also it had no keysym, so I don't see how it could have done anything).

I feel like I've already tried everything, any other ideas would be great.

EDIT:
This seems to be a problem with the buttons on the tablet's screen, I did the following, in accordance with [http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Fixing_the_Tablet_Toolbox_Button](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Fixing_the_Tablet_Toolbox_Button)

```

sudo setkeycodes 68 241
echo 'keycode 249 = XF86Launch3' >> ~/.Xmodmap && xmodmap ~/.Xmodmap

```

(i realize that 241 != 249 ... xev reported the keycode as 249 after issuing the first command)

then I assigned this keycode to my rotate script using ccsm with no effect. Any ideas as to why the x61 tablet's screen buttons don't work properly?

---

### Post by Favux on 2009-05-30
Hi e64462,

I guess partly I wanted to show you others were doing the same thing and having success.

If xev is reporting a keycode for the key then it seems to me the key is working.  When you bound to the other unconventional key that did work with the rotate script was that a single key?

The other part of the reason I linked you there was the stuff about HAL breaking single key key binding.  No one else in Jaunty has reported that so I thought it was fixed.  But it sounded like that may be what's going on with you.  Unless of course the other unconventional key you used was a single key.

---

### Post by e64462 on 2009-05-31
Yes, the other key I tried was the Thinkvantage button (if you're familiar at all with the X61, its the big blue one) ... again, this key already had a keysym assigned to it, XF86Launch1 I believe. It appears to only be the keys on the screen itself that fail to work... I just tested the arrow keys located on the screen (which worked out of the box in Intrepid) ... and they don't have a keysym, keycode, or scancode .... so they appear to be 100% inoperable in Jaunty... Is there anything I can do with HAL to make this work?

Thanks

---

### Post by Favux on 2009-05-31
Hi e64462,

I'm assuming you've been looking at the Think wiki, since they usually have the best info.

You could "lshal>my_lshal.txt" and then comb through it.  Gedit would help with searching.  But it is an enormous pain.  Maybe you could install the gui for it, gnome-device-manager, in Synaptics.  Be sure to select properties in View.  Look for "Unknown Button" or something similar.  See if it has anything useful.

---

### Post by e64462 on 2009-05-31
EDIT: Yes, I have been on the wiki, specifically the 9.04 Jaunty Install guide... which doesn't report any trouble at all with this key... 

There does exist an unknown button ... but I have to admit that I'm pretty far afield at this point... I'm not sure (read: uncertain) I know how to use this information....

Under Computer->Unknown button->Properties->input.keymap.data

there is a line that reads 0x01:screenlock, 0x02:battery, 0x03:sleep, 0x04:radio, 0x06:switchvideomode, 0x07:f22, 0x08:f24, 0x0b:suspend, 0x0f:brightnessup, 0x10:brightnessdown, 0x11:kbdillumtoggle, 0x13:zoom, 0x14:volumeup, 0x15:volumedown, 0x16:mute, 0x17:prog1

---

### Post by Favux on 2009-05-31
Hi e64462,

Ah hah.  I just remembered a useful site.  I was helping someone with suspend using a thinkpad example.  He added the video quirk to his laptops .fdi and got it working.  See if this site is of any use:  [http://people.freedesktop.org/~hughsient/quirk/index.html](http://people.freedesktop.org/~hughsient/quirk/index.html)

Again, someone at the Thinkpad wiki may have figured this all out already.

---

### Post by e64462 on 2009-05-31
wow... I've been trying to figure out a few of the pages for a while now... this HAL thing has me so lost... where do I start?

---

### Post by Favux on 2009-05-31
Hi e64462,

I know what you mean.  The couple of HAL issues I've dealt with I've teamed up with someone and we hammered away at it until we came up with something.  So don't expect instant success.  Figuring out how to get touch on our usb tablet pc's through a .fdi took us about two weeks of off and on effort.  Let it percolate while you look it over.

In a completely different direction Irfy tried to help me with my hotkeys and he wrote a pretty good wiki.  I don't know if it applies but you can give it a glance between HAL.  The thread:  [http://ubuntuforums.org/showthread.php?t=1103674&highlight=tablet](http://ubuntuforums.org/showthread.php?t=1103674&highlight=tablet)  And his wiki:  [https://help.ubuntu.com/community/LaptopSpecialKeys](https://help.ubuntu.com/community/LaptopSpecialKeys)

---

### Post by Favux on 2009-05-31
Hi

Doing a search on the hal-info page here:  [http://cgit.freedesktop.org/hal-info/](http://cgit.freedesktop.org/hal-info/)  using X61 got me to this page:  [http://cgit.freedesktop.org/hal-info/log/?qt=grep&q=x61](http://cgit.freedesktop.org/hal-info/log/?qt=grep&q=x61)  With a 10/07 keymap?  Using X61t got me:  [http://cgit.freedesktop.org/hal-info/log/?qt=grep&q=x61t](http://cgit.freedesktop.org/hal-info/log/?qt=grep&q=x61t)  with a 1/08 suspend quirk.

---

### Post by e64462 on 2009-05-31
I'm confused though, suspending isn't the problem... or did i miss something essential

EDIT: This link seems useful... I dont know what to do with it though
[http://cgit.freedesktop.org/hal-info/commit/?id=1b40bdf002a95d8cc4b1641776146e62f86c726b](http://cgit.freedesktop.org/hal-info/commit/?id=1b40bdf002a95d8cc4b1641776146e62f86c726b)

---

### Post by Favux on 2009-05-31
Hi e64462,

That may be it or you may want to try and find a more recent one.  I've found the laptop specific .fdi's before.  I don't have the exact address but they're somewhere around in "/usr/share/hal/fdi/".

---

