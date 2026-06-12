---
title: "Extra mouse buttons in Dapper (broken and insane)"
date: 2006-06-18
forum: Desktop Environments
---

### Post by niviche on 2006-06-18
Hello,

I have a Microsoft Trackball Optical, with two normal buttons (left + right), a scroll wheel and two extra buttons. I found out how to make these two bonus ones work fine in Hoary and in Breezy, and [helped people to set up their mouse](http://ubuntuforums.org/showthread.php?t=132384)

However, I can't get this to work in Dapper for the life of me. No idea why, but the two extra buttons just do not do anything at all anymore.

Here's the deal:

_xorg.conf:_
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

```

_output of xev:_
when pressing extra button 1:
```

ButtonRelease event, serial 29, synthetic NO, window 0x3400001,
    root 0x4c, subw 0x0, time 3874431361, (9,88), root:(607,111),
    state 0x10, button 8, same_screen YES

```
when pressing extra button 2:
```

ButtonRelease event, serial 28, synthetic NO, window 0x1c00001,
    root 0x4c, subw 0x0, time 3874462780, (0,159), root:(598,182),
    state 0x10, button 9, same_screen YES

```

[COLOR="red"]Note that I have 7 buttons according to Xorg.conf, but xev gives me some buttons numbered 8 and 9, and no 6 and 7.[/COLOR]

Then, I have xbindkeys starting when I beg[COLOR="black"][/COLOR]in a session, and running. xvkbd is also installed

_content of my .xbindkeysrc file:_
```

#copy
 "/usr/X11R6/bin/xvkbd -xsendevent -text "\[c]""
    m:0x0 + b:8.

#paste
 "/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[v]""
    m:0x0 + b:9.

```

And this just doesn't do anything. I've tried:
1. changing the actions in xbindkeys: didn't do anything, I don't think the problem is there.
2. changing xorg.conf from 7 to 9 buttons
3. changing the mapping in xbindkeys to 6 and 7.

And still, it doesn't work. 

I guess that some people, just like me, had their extra buttons working in Breezy. What with Dapper? Did they experience breakage as well?

Any help would be very welcome, this thing is turning me crazy.

---

### Post by BeeRockxs on 2006-06-18
I have it working, with this X configuration:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

In addition to that, I run xmodmap, with this configuration in 
/etc/X11/Xsession.d/63xmodmap

xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 10 11"

---

### Post by niviche on 2006-06-18
[QUOTE=BeeRockxs]I have it working, with this X configuration:[/quote]

same as mine

[QUOTE=BeeRockxs]xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 10 11"[/QUOTE]

If I do this without xbindkeys, my two extra buttons work like an horizontal scroll wheel (weird). And if I run xbkindkeys after this, they don't do anything at all anymore.

I have tried to play with the xmodmap configuration, but all I manage to do is to assign the scrolling to other buttons, nothing seem ever to be sent to xbkindkeys.

What's the content of your xbindkeysrc file?

---

### Post by BeeRockxs on 2006-06-18
[QUOTE=niviche]
What's the content of your xbindkeysrc file?[/QUOTE]


I don't use xbindkeys at all, so I don't have one.

---

### Post by niviche on 2006-06-18
In this case, how do you tell Ubuntu what to do with the two extra buttons?

---

### Post by BeeRockxs on 2006-06-18
[QUOTE=niviche]In this case, how do you tell Ubuntu what to do with the two extra buttons?[/QUOTE]

I use imwheel, with this .imwheelrc:
```

".*"
None, Up, Alt_L|Left
 None, Down, Alt_L|Right
  
 "(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

```

and the startup parameter of "-b 89", set in /etc/X11/imwheel/startup.conf

---

### Post by niviche on 2006-06-18
Done that, restarted K, and still nothing. The two extra buttons do not do anything at all. :(

---

### Post by BeeRockxs on 2006-06-18
[QUOTE=niviche]Done that, restarted K, and still nothing. The two extra buttons do not do anything at all. :([/QUOTE]

I just noticed that I don't use the ZAxisMapping option in xorg.
Also, did you change the IMWHEEL_START=0 line in /etc/X11/imwheel/startup.conf to IMWHEEL_START=1?

---

