---
title: "customizing a 5 button mouse / trackball"
date: 2005-08-10
forum: Desktop Environments
---

### Post by ad noiseam on 2005-08-10
Hello,

I am new to Linux, like it so far, but here is another question:

I've got a Microsoft Trackball Explorer. It looks [like this](http://www.nmit.se/images/ms_trackball-opt.jpg), with two main buttons (left / right), a wheel, and two side buttons (far left / far right).

I have read the HOWTOs and the Wiki about configuring a special mouse, installed imwheel and read its doc.

All I can do, it seems, is to have the side buttons go back or forward in Firefox, and the wheel goes up and down. No matter what I put in the imwheelrc file, the behavior of my mouse doesn't change.

What I would like to do is:
-copy with the far left button (that's "Control_C", right)?
-paste with the far right button ("Control_V", I guess)?

In my "Xorg.conf", I have

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "100"
  EndSection
[code]

(note that, if the ZAxisMapping was "6 7", I would go back / forward with the wheel, and up / down with the side button, which makes little sense)

and my /etc/X11/imwheel/imwheelrc file is:
[code]
 ".*"
Control_C,Control_C,None
Control_C,Control_V,None

```

What kind I do to make this work? it seems to me that the imwheel file is not read at all.

Thank you.

---

### Post by ad noiseam on 2005-08-10
Solved. The way to do this is to have this in Imwheel:

```

".*"
None,Up,Control_L|C
None,Down,Control_L|V

```

the "L" after control doesn't stand for the key being hit, that's what I was doing wrong. :)

---

