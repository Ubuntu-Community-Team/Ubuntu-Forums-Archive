---
title: "Extra buttons in Breezy"
date: 2005-10-19
forum: Desktop Environments
---

### Post by ad noiseam on 2005-10-19
Hello,

First, I have read the wiki ([one](https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons?highlight=%28mouse%29) and [two](https://wiki.ubuntu.com/ManyButtonsMouseHowto?highlight=%28mouse%29), read all the post in this forum, as well as documentations [here](http://forums.gentoo.org/viewtopic.php?t=98028), [there](http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons) and [there](http://www.student.oulu.fi/~savaisan/stuff/mx700.txt), but I still can't figure it out. I would be really thankful if somebody could help me.

**The situation**
-I have a [Microsoft Trackball Optical](http://images.amazon.com/images/P/B00005853X.01.LZZZZZZZ.jpg), with two normal buttons, two side buttons, a scroll whell on which one can press (7 buttons total).
-what I want to do is use the scroll wheel to scroll, and the side buttons to copy and paste. I don't care about the middle click.
-this worked perfectly in Hoary, but I can not get it back for the life of me on a clean install of Breezy.

**The code**

-In /etc/X11/Xorg.conf:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
        Option 		"Protocol"		"ExplorerPS/2"
        Option 		"Buttons"		"7"
	Option 		"ZAxisMapping"		"6 7"
  EndSection

```

-in /etc/X11/imwheel/imwheelrc:
```

 ".*"
None, Up, Control_L|C
None, Down, Control_L|V

```

-in /etc/X11/imwheel/startup.conf:
```

IMWHEEL_START=1
IMWHEEL_PARAMS="-b -p "67""

```

in /etc/X11/Xsession.d/57xmodmap:
```

  #/bin/bash
  xmodmap -e "pointer = 1 2 3 4 5 6 7"

```

**3. The results.**

1. the copy / paste works well in every window once Imwheel is started.

2. Imwheel doesn't start at boot. I have to go to a terminal and enter "imwheel".

3. The scroll wheel does not do anything at all in Firefox or Epiphany.

3. in any other window (Nautilus, for example), the scroll wheel scrolls horizontaly, unless I put my mouse on the vertical scroll bar (in this case, it scrolls vertically, as it always should.

**4. Questions**

1. How can I get Imwheel to start at boot?

2. How can I get the scroll wheel to scroll in Firefox? All the tutorials I saw explained how to do so, but with the side button assigned as "back" and "forward", which I do not want.

3. How do I get the scroll wheel to scroll vertically in the other apps?

Thank you.

---

### Post by ad noiseam on 2005-10-20
Actually, I tried this again with a clean install of Hoary, and I am having the exact same problems. This is annoying, as I am sure that there is a way to do it (it was the case on my Hoary install before I wiped it up with Breezy). :(

I solved the problem of Imwheel not starting by itself, by adding two "startup programs" in System -> Preference -> Sessions:

Order / Command
57 / exec xmodmap -e "pointer = 1 2 3 6 7 4 5" 
60 / imwheel 

Anyway, I still have the two following issues:
-no screel wheel at all in Firefox or Epiphany
-horizontal scrolling (instead of vertical) in any other app, unless I put the pointer on the vertical scroll bar.

Any idea?

---

