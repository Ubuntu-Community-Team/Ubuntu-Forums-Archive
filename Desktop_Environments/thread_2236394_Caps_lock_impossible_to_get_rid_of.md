---
title: "Caps lock impossible to get rid of"
date: 2014-07-26
forum: Desktop Environments
---

### Post by tad2 on 2014-07-26
Hello

I am trying to get rid of caps lock, to make it do nothing. I have followed the instructions for remapping keys in [http://wiki.linuxquestions.org/wiki/Configuring_keyboards#The_Xmodmap.2FSetxkbmap_Method](http://wiki.linuxquestions.org/wiki/Configuring_keyboards#The_Xmodmap.2FSetxkbmap_Method) and also read the advice and followed the instructions exactly as described in at [http://ubuntuforums.org/showthread.php?t=1218221&p=7675138#post7675138](http://ubuntuforums.org/showthread.php?t=1218221&p=7675138#post7675138) (with appropriate modifications for the different keys).

But to no avail. If I let my finger wander over here I CAN SHOUT AT EVERYONE ALL DAY LONG. Apart from ripping the damn thing off, has anyone found a more reliable way of giving it such a lamping that it can never get up again?

Thanks

Tadeusz, oop north, England
Lubuntu 14.04 / LXDE

---

### Post by buzzingrobot on 2014-07-26
Here's the way I do it in Unity.  Don't use Lubuntu, though, so no guarantees.

1. Install dconf-editor and launch it.

2. Click on 'org' in the left panel, then, successively, 'gnome'->'desktop'->'input-sources'.

3. At 'input-sources', the window on the right will include an entry labeled 'xkb-options' followed by two brackets ('[]').  Put your mouse cursor between the brackets and enter this: 'caps:none'.  Include the single quote marks.   Hit the Enter key and you're done.

---

### Post by grumblebum2 on 2014-07-26
Adding to **buzzingrobot's** post, the entry I use in dconf is
```
['terminate:ctrl_alt_bksp', 'caps:none', 'shift:both_capslock_cancel']
```
Gives... 
[LIST]
[*]ctrl+alt+backspace to kill X
[*]Caps Lock is disabled
[*]Both Shift keys together activate Caps Lock, one Shift key deactivates
[/LIST]

Options can be found in 
```
man xkeyboard-config
```

---

### Post by tad2 on 2014-07-27
Thanks, but THAT DOESN'T WORK in Lubuntu.  

Running xmodmap -e 'Keycode 66 = F8' (with or without the quotes) doesn't work either.

---

### Post by bapoumba on 2014-07-27
Maybe here : [http://ubuntuforums.org/showthread.php?t=1782212&p=11419040#post11419040](http://ubuntuforums.org/showthread.php?t=1782212&p=11419040#post11419040)

---

### Post by egeezer on 2014-07-27
There are two ways.  The first is a quickie:

Make a Leafpad file:

                         [FONT=Liberation Serif][SIZE=3]!
! Swap Caps_Lock and Shift_L
!
remove Lock = Caps_Lock
keysym Caps_Lock = Shift_[/SIZE][/FONT]

and save it as a hidden file called .nocaps, or .killock (any name, just needs the dot to designate a hidden file)

Then run
```
xmodmap /home/yourusername/.nocaps
```

The only problem with that is that each time you sign in you have to run it fresh, unless you can figure out how to get it into autostart (which I haven't found yet for the newest Lubuntu).

Since I couldn't get it to autostart, I used the second method:

Make a Leafpad file like this;
                     
```
                         
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" "us"
        Option "XkbModel" "pc104"
        Option "XkbOptions" "caps:none"
EndSection  
```

    
[FONT=Liberation Serif][SIZE=3]And save it as[/SIZE][/FONT]                                                  
[FONT=Liberation Serif][SIZE=3]/usr/share/X11/xorg.conf.d/10-keyboard.conf

Log out, log in again, and you're in business.
[/SIZE][/FONT]

---

### Post by tad2 on 2014-07-28
> **bapoumba said:**
> Maybe here : [http://ubuntuforums.org/showthread.php?t=1782212&p=11419040#post11419040](http://ubuntuforums.org/showthread.php?t=1782212&p=11419040#post11419040)

No, afraid not. Has no effect at all.

---

### Post by tad2 on 2014-07-28
> **egeezer said:**
> There are two ways.  The first is a quickie:

Make a Leafpad file:

                         [FONT=Liberation Serif][SIZE=3]!
! Swap Caps_Lock and Shift_L
!
remove Lock = Caps_Lock
keysym Caps_Lock = Shift_[/SIZE][/FONT]

and save it as a hidden file called .nocaps, or .killock (any name, just needs the dot to designate a hidden file)

Then run
```
xmodmap /home/yourusername/.nocaps
```

The only problem with that is that each time you sign in you have to run it fresh, unless you can figure out how to get it into autostart (which I haven't found yet for the newest Lubuntu).



Yes! This method works -- thank you -- at last! I will now work on getting it to autorun at each session opening. 
(The second line of the code sould read "[FONT=Liberation Serif][SIZE=3]keysym Caps_Lock = Shift_L"[/SIZE][/FONT])

> **egeezer said:**
> 

Since I couldn't get it to autostart, I used the second method:

Make a Leafpad file like this;
                     
```
                         
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" "us"
        Option "XkbModel" "pc104"
        Option "XkbOptions" "caps:none"
EndSection  
```

    
[FONT=Liberation Serif][SIZE=3]And save it as[/SIZE][/FONT]                                                  
[FONT=Liberation Serif][SIZE=3]/usr/share/X11/xorg.conf.d/10-keyboard.conf

Log out, log in again, and you're in business.
[/SIZE][/FONT]

That one didn't work for me, but thanks for the first method.

---

### Post by bapoumba on 2014-07-28
Glad to see you got it to work !
Please mark your thread as solved (under Thread tools), thanks.

---

### Post by tad2 on 2014-07-28
May I request it stays open for a little while, until I can find a way of starting the command at every session? I'm only halfway there :)

---

### Post by bapoumba on 2014-07-28
> **tad2 said:**
> May I request it stays open for a little while, until I can find a way of starting the command at every session? I'm only halfway there :)

Was not about to close it :)
When you are done, please remember to mark the Thread as solved, thanks !

---

### Post by tad2 on 2014-08-03
Gave up and went back to a KDE desktop which has a simple GUI way of doing this in one click.

---

### Post by buzzingrobot on 2014-08-03
Odd.  The xmodmap solution, as a one-line script made executable (chmod +x) and added to the list of startup apps, seems like the appropriate answer. 

Lubuntu must have an app that edits startup applications? Otherwise, users are left to manually create .desktop files and add them to /etc/xdg/autostart or ~/.config/autostart.

---

