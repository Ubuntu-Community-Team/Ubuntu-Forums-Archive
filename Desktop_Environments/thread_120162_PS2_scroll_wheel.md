---
title: "PS/2 scroll wheel"
date: 2006-01-20
forum: Desktop Environments
---

### Post by ubuntu irv on 2006-01-20
I finally go it to recognize the PS/2 mouse and it also see's the synaptic pad.  Now the problem is it does not see the scroll wheel on the mouse. Whenever I try to roll it up or down it jumps to the top of the page. Can you tell me what to do or direct me in the right location? 
Its a compaq presario laptop.
What else do you need to know?
Irv

---

### Post by Urmas on 2006-01-21
Read this thread:

[http://ubuntuforums.org/showthread.php?t=78483&highlight=scroll+wheel](http://ubuntuforums.org/showthread.php?t=78483&highlight=scroll+wheel)

Hope it helps you some.

---

### Post by ubuntu irv on 2006-01-21
Thanks Again,
The way I got it to recognize the PS/2 mouse was by going into: 
sudo gedit /etc/modules
and adding proto=bare

lp
mousedev
psmouse proto=bare  

That the only configuration that I would find that would make it work, and spent the whole day yesterday getting that far.    I tried everything that I could find.  This is what I found works right now, but whenever you roll the wheel back or forward the mouse jumps to the top of the page.

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "Auto"
Option "Buttons"  "5"
Option "ZAxisMapping"  "4 5"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

What I would like to do is delete the Synaptic TouchPad completely, as I do not want it at all.  Is that a possiblity?

I would appreciate any help from the Guru's as I am new to Ubuntu and Linux.
Irv

PS I forgot the: 
"ServerLayout"
Identifier     "Default Layout"
Screen         "Default Screen"
InputDevice    "Generic Keyboard"
InputDevice    "Configured Mouse"
InputDevice    "Synaptics Touchpad"
EndSection

---

### Post by slashem on 2006-01-21
Sure, delete the Synaptic section. Also delete the line InputDevice "Synaptics Touchpad". Restart X.

Use xev and scroll back and forth, and see what events you get. Here is what I get, you should get button 4 and 5:

ButtonRelease event, serial 25, synthetic NO, window 0x2400001,
    root 0x40, subw 0x0, time 32396910, (55,133), root:(60,205),
    state 0x1000, [COLOR="Blue"]button 5[/COLOR], same_screen YES

ButtonPress event, serial 25, synthetic NO, window 0x2400001,
    root 0x40, subw 0x0, time 32398475, (55,133), root:(60,205),
    state 0x0, [COLOR="Blue"]button 4[/COLOR], same_screen YES

---

### Post by ubuntu irv on 2006-01-21
I would love to follow your instructions, but the way its written is to deep for me.  Could you please explain in clearer terms?
Sorry

---

### Post by slashem on 2006-01-21
Well, delete this from xorg.conf:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

and this line:

InputDevice "Synaptics Touchpad"

under "ServerLayout"


Type "xev" in a terminal. You'll get a little window.  Move the mouse inside it. You'll notice output in the terminal. Now, while the mousepointer is in that window, scroll back and forth. Note the output. It should be similar to what I have posted above.

---

### Post by ubuntu irv on 2006-01-21
Thanks so much..that's perfect.  I tried it and followed your instructions.  After reboot the touch pad still works...:(
Have'nt gotten to the other part yet...doing it now..

---

### Post by ubuntu irv on 2006-01-21
See both Posts 8 and 9
Left Button:
ButtonPress event, serial 30, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 1023010, (171,174), root:(182,223),
    state 0x0, button 1, same_screen YES
ButtonRelease event, serial 30, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 1023284, (171,174), root:(182,223),
    state 0x100, button 1, same_screen YES
Right Button:
ButtonPress event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 1164677, (174,172), root:(184,244),
    state 0x0, button 3, same_screen YES
ButtonRelease event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 1164895, (174,172), root:(184,244),
    state 0x400, button 3, same_screen YES
Center Button:
EnterNotify event, serial 27, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 1233381, (37,48), root:(622,157),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 512
KeymapNotify event, serial 27, synthetic NO, window 0x0,
    keys:  64  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
ButtonRelease event, serial 27, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 1235445, (37,48), root:(622,157),
    state 0x200, button 2, same_screen YES

Irv

---

### Post by ubuntu irv on 2006-01-21
Here are the reading that I get:  I have no idea about the smiley's  where not showing when I copy and pasted.
ScrollWheel Forward:
LeaveNotify event, serial 27, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 684528, (184,174), root:(194,246),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus NO, state 0
Scroll Wheel Back:
LeaveNotify event, serial 27, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 776010, (180,175), root:(191,224),
    mode NotifyNormal, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

---

### Post by slashem on 2006-01-21
Well thats just weird. Did you say it was cordless? Is it connected to the PS/2 port? Can you try it in a USB port?

---

### Post by slashem on 2006-01-21
Googled a little around, and found this:

[http://www.linuxquestions.org/questions/showthread.php?t=332155](http://www.linuxquestions.org/questions/showthread.php?t=332155)

Note that:
> 
If your mouse protocol is set to

Option "Protocol" "PS/2"
or
[COLOR="Blue"]Option "Protocol" "auto"[/COLOR]

You may have to change it to:

Option "Protocol" "IMPS/2"
or
Option "Protocol" "ExplorerPS/2"

which applies to you. Hope this helps.

---

### Post by ubuntu irv on 2006-01-21
No its not cordless...its a wired mouse.

Also I tried both of those options and no good.

Remember that although we remove the Touchpad its still working!!

---

