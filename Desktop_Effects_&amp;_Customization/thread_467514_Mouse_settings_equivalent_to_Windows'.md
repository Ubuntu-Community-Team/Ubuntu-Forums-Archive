---
title: "Mouse settings equivalent to Windows'"
date: 2007-06-07
forum: Desktop Effects &amp; Customization
---

### Post by unimatrix on 2007-06-07
Did anyone else get a strange feeling when booting from Windows to Linux (KDE) by grabbing the mouse and noticing it moved differently?
Well.. I was wondering if it were possible to set the advanced cursor movement settings so moving the mouse would feel exactly like in Windows. 
As for me, I've kind of gotten used to the Linux way. Though, it's still very annoying when I try to make small, precise movements with the cursor, it just sort of jumps around for a few pixles (I have a Logitech MX1000).

So if I wanted to replicate the Windows XP settings, how would I set the following 4 parameters:
[LIST]
[*]Pointer acceleration
[*]Pointer threshold
[*]Drag start time
[*]Drag start distance
[/LIST]

If anyone has some ideas or at least feels the same about this, please reply. Thanks!

---

### Post by madmetal on 2007-06-07
in gnome you can find mouse settings at system >> preferences >> mouse..
i think in KDE there must be something similar..  at KDE control center / peripherals?

---

### Post by unimatrix on 2007-06-08
Yes I know, it's in Kcontrol under Peripherals > Mouse > Advanced
The problem is I've been playing around with settings to get them to be more like in Windows, but no luck. The entire movement configuration system is obviously different.
In Windows there's just: _Pointer speed_ (default: 50%) and _Enhance pointer precision_ (default: true).
But in KDE there's _Pointer acceleration_, _Pointer threshold_, _Drag start time_, _Drag start distance_.
I don't even know what most of these linux controls even do, but i really want to set them so the mouse would behave the same as in Windows by default.

---

### Post by unimatrix on 2007-06-11
So noone knows this? Wow I must be the first person in the world to think of this! :)

---

### Post by Bandit09 on 2007-06-14
No, you're not. I just got a logitech notebook mouse for my kubuntu laptop and the pointer is very jumpy. It's hard to click on the maximize, minimize, etc buttons because the mouse is waaay to fast it jumps around too much.  If anyone can help, we'd appreciate it.

---

### Post by CrazyGuy123 on 2007-06-14
probably no way to set those settings to make them the same as windows - there's probably some highly complex formula behind the windows one.  The "drag" ones shouldn't affect normal mouse use - only when dragging and dropping files.

I do remember seeing some discussions of someone working on the issue to make the mouse movement in linux easier to use, but I don't think it's progressing yet.

---

### Post by kpolice on 2007-06-14
If you don't understand what is the purpose of each setting just click on the **Help** button, the description is there.

---

### Post by satx on 2007-06-14
So what kind of mouse is it- optical or roller ball?

---

### Post by kpolice on 2007-06-14
The MX1000 is a laser mouse, I have it too.

---

### Post by Bandit09 on 2007-06-15
I'm using a logitech optical mouse, and I can't seem to get it to stop being so jumpy. I just need to slow ti down a bit.

---

### Post by Sergiu on 2007-06-19
i have the same problem.

anyone found an solution to this?

---

### Post by unimatrix on 2007-06-20
A partial solution I found was to _decrease the "Pointer acceleration" to 1.0x_ (thus obviously disabling it)
Still doesn't quite feel like Windows, but it's much better.

Anyway there might be something about the MX1000 using 400dpi instead of 800dpi.
#*sudo logitech_applet*    returns this:
> 
002/003     046D/C50E   M-RAG97         MX1000 Laser Mouse
   Channel 1    Battery: 7    Single channel   **No 800cpi support**   No Horiz Roller   No Vert Roller   2 butt.


While my xorg.conf mouse setting looks like this:
> Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "mouse"
        Option          "Name" "Logitech USB Receiver"
        Option          "Buttons"               "12"
        Option          "HWHEELRelativeAxisButtons" "7 6"
        Option          "Resolution" "800"
EndSection


---

### Post by jdarias on 2008-04-04
Hello. Got  a logitech LX5 mouse, but i'm all new to this stuff about mouse resolution. I even don't know how to set it up in windows.
This mouse has a resolution of 1000 dpi, so i added the "option resolution" (not exactly that) to xorg. But how can i tell something has changed and is now working at full res?

---

### Post by unimatrix on 2008-04-05
_ATTENTION!_

Ubuntu Linux is set to poll the mouse position every 100 milliseconds.
That is UGLY SLOW and will cause jumpy behavior on accurate mice.

The **SOLUTION** to this problem is very simple and can be found here:
[http://ubuntuforums.org/showthread.php?t=392494](http://ubuntuforums.org/showthread.php?t=392494)
I have just tried it and it makes a HUGE difference. Now my desktop feels like I'm actually in control of my mouse.

Credits go to [Cappy]("http://ubuntuforums.org/member.php?u=233080"). Thank you for your post!


PS: More details about mouse polling here: [http://gentoo-wiki.com/TIP_Change_mouse_hz](http://gentoo-wiki.com/TIP_Change_mouse_hz)
PPS: If you want this problem solved by default, go VOTE here: [http://brainstorm.ubuntu.com/idea/6390/](http://brainstorm.ubuntu.com/idea/6390/)

---

### Post by jbaerbock on 2008-06-17
I have been wondering about this for a loooong time too. Changing mouse speed to 1.5 did best for me but also plan to try that /etc/modules solution later today.

---

