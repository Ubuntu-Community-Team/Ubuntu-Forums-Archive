---
title: "Synaptics Touchpad gone crazy."
date: 2010-11-17
forum: Desktop Environments
---

### Post by credomane on 2010-11-17
Ever since upgrading to 10.10 my laptops synaptics touchpad has gone haywire. From what I've learned it has to do with the new, what I deem terrible, defaults of using "corner" buttons. It is driving me absolutely insane. I mean it when I say terrible. There is apparently no easy way to turn them off. My laptops touchpad is fairly small and, I assume, this causes the corner buttons to take up a gigantic portion of the touchpad.

I have firefox and Nautilus contantly opening links in new tabs and in the current window. They also random close a tab instead of switching to it when I click an unfocused tab.

I'm always having issues with copying things. Almost everything I selected either gets copied then pasted immediately or just copied.

Trying to drag anything has become a fruitless struggle. I've literally had to resort to using a usb mouse to workaround this problem for now. Being a person that likes to figure things out on his own I've search around found several other complaining about the same issues but haven't managed to get their solutions to work. So here I am in dire need of some guidance.

All I'm wanting it my touchpad to work like it always has before the terrible deed 10.10 has done to it. I want just a flat boring old touchpad with nothing special except for a small sliver on the right side that acts like a scroll wheel. I don't need corner buttons as I have keyboard shortcuts for everything that have always been there.

Anyone out there that can help me out here?

---

### Post by credomane on 2010-11-18
Just ran into [http://ubuntuforums.org/showthread.php?t=1607973](http://ubuntuforums.org/showthread.php?t=1607973) . Which is the same problem as me. I never used middle-click before outside of games. hehe.

Tried some middle-clicking here at work. Middle click does all the same issues I'm having at home. Now I need to look into it when I get home.
the synaptic touchpad option "EmulateMidButtonTime" looks like it might fix it...Certainly hope it does.

Just a link to all the options of the synaptic driver with descriptions that others might find useful, I certainly did.
[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html)

Seems adding the above options to /usr/share/X11/xorg.conf.d/xx-synaptics.conf will do the trick to make them permanent. Which is way different from the other suggestions I've been running into. Other solutions have been telling me to do stuff in HAL (which is gone in Ubuntu I believe) and udev. Found this info here: [http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html](http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html) also the page where I found link to the synaptic options.

---

### Post by credomane on 2010-11-19
Looks like I fixed it. Had to do a few other options to the driver. Now the touchpad is working great!

The Option lines MUST be place right after the driver line, so that it looks something like mine below. Otherwise the Xorg server WILL NOT START!! Wasted all day yesterday on that. Then upon reading the the guide I got my info from a little more closely points this out. hehe, oops.
```

Section "InputClass"
        Identifier	"touchpad catchall"
        Driver		"synaptics"

	Option		"TapButton2"		"1"
	Option		"TapButton3"		"1"
	Option		"ClickFinger3"		"1"

        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"

EndSection


```
It would seem the touchpad was actually thinking my figure was two fingers and that meant middle click to the driver. This forces a left click on two and three finger taps. Don't think my touchpad supports multi-touch; not that I care if it does. Hope this helps some one else.

Marking the thread as solved. :D

[edit]
Does an admin have to mark the thread solved? I went to edit my original post to do that and all I can do it edit the title but not set it to solved. Just gonna change the title to solved I guess or is that the way it is done. >_>

[edit2]
....Someone mark this thread as solved, please. I'm unable to figure it out apparently.

---

