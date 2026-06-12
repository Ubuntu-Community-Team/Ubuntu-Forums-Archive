---
title: "[Lubuntu] How to swap Up and Right_Shift keys?"
date: 2014-04-09
forum: Desktop Environments
---

### Post by Kai_Konnen on 2014-04-09
How can I swap the the UP and the right shift key in Lubuntu? Xev tells me the <UP> button has the keycode 111, and the <RTHS> (Shift_R)-key has the keycode 62. This is as far as I get. Can anybody give me an hint? 

The two keys are in awkward positions on my  EeePC 1000H. Every time I want to hit right shift I press UP instead. On Windows XP, I swapped the keys using an Autohotkey script. 


Thank you for your help
Kai

---

### Post by egeezer on 2014-04-10
The way I've used  to mess around with keycodes in LXDE is to write a short script in Leafpad.  I've had more success with just removing the function of a key than swapping it, so I tend to use a script like:

                        !
! Set Caps_Lock to no symbol 
!
remove Lock = Caps_Lock
keysym Caps_Lock = 0x0000

Substitute your <UP> name, then save the file as a run file (using intitial dot) like .upkiller.

Then if you want to autostart it, go to
```
/etc/xdg/lxsession/LXDE
```
and open the autostart text.  At the bottom, add the line:
@.upkiller enable
Then log out and log in again.

---

### Post by Kai_Konnen on 2014-04-10
Thank you for your answer. Unfortunately I need both UP and Right Shift- key. Disabling the UP-key is no option.

---

### Post by egeezer on 2014-04-10
I haven't done this sort of thing myself, but I would guess that you could modify the former script:

!
!Swap UP and Shift_R
!
remove UP = 0x0111
remove Shift_R = 0x0062
keysym UP = 0x0062
keysym Shift_R = 0x0111

NO GUARANTEES, you understand - this would just be the way I would do it, and hope for the best.  If I could cite a reliable reference, I would, but I don't know a good place to look!

---

### Post by Kai_Konnen on 2014-04-11
I tried that, but it didn't work, the keyboard was unchanged. 

Maybe I misunderstood your posting. What I did was:
1. I pasted the following code in a text document and save it as .swapkeys in my home directory:
```
[COLOR=#000000]![/COLOR]
[COLOR=#000000]!Swap UP and Shift_R[/COLOR]
[COLOR=#000000]![/COLOR]
[COLOR=#000000]remove UP = 0x0111[/COLOR]
[COLOR=#000000]remove Shift_R = 0x0062[/COLOR]
[COLOR=#000000]keysym UP = 0x0062[/COLOR]
[COLOR=#000000]keysym Shift_R = 0x01[/COLOR]
```

2. I pasted the line ```
@.swapkeys enable
``` into the document autostart.txt (that document was empty) in the directories* [COLOR=#000000][FONT=Ubuntu Mono]/etc/xdg/lxsession/Lubuntu [/FONT][/COLOR]* and  [COLOR=#000000][FONT=Ubuntu Mono]/etc/xdg/lxsession/Lubuntu-Netbook [/FONT][/COLOR]. A directory * [COLOR=#000000][FONT=Ubuntu Mono]/etc/xdg/lxsession/LXDE  [/FONT][/COLOR]*doesn't exist on my system.

Any ideas?

---

### Post by egeezer on 2014-04-12
In your first code block the last line should be keysym Shift_R = 0x0111 (not 0x01) - bu that might be a copy error.

As to a missing /etc/xdg/lxsession/LXDE, I'm as baffled as you are.  Did you try running .swapkeys as an ordinary command?  That would be a good first test of whether it's doing what it should.

---

### Post by Kai_Konnen on 2014-04-13
I finally found a script that swaps the two keys (here: [http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys):](http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys):)
```

 #!/bin/bash
 xmodmap -e "keycode 62 = Up" # Shift => Up xmodmap -e "keycode 111 = Shift_R" # Up => Shift
 xmodmap -e "add shift = Shift_R" # Make the new Shift key actually do shifting
 xmodmap -e "remove shift = Up" # Prevent the old Shift key from shifting
 xset r 62 # Make the new Up key autorepeat
 xset -r 111 # Prevent the new Shift key from autorepeating

```

I saved the script as swapkeys.sh and moved it to /home/USERNAME/bin. [COLOR=#000000]The scripts path is [/COLOR][COLOR=#000000][FONT=courier new]/home/USERNAME/bin/swapkeys.sh[/FONT][/COLOR][COLOR=#000000]. I made the script executable. 
Then I opened [/COLOR]**Preferences - Default applications for LXSession - Autostart **and added the line [COLOR=#000000][COLOR=#000000][FONT=courier new]/home/USERNAME/bin/swapkeys.sh[/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000] as a "Manual autostart application". After a new login, everything works. 

[/COLOR][/COLOR]

---

