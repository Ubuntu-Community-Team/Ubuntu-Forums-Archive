---
title: "[solved] numeric keypad disabled, only mouse-moves results"
date: 2008-10-16
forum: Desktop Environments
---

### Post by alterpinguin on 2008-10-16
numeric keybad is suddenly disabled, pressing numlock does not work any more, every numeric keystroke only moves the mouse-pointer, reboot and newstart does not help, (shure, using a different keyboard shows same not working numeric keypad).
-
Switching to text-console via Alt-Shift-F1 proves numlock is working.
-
reason: one can disable the numeric keypad with pressing: Shift+Numlock
and it will be disabled until one presses again Shift+Numlock

and i do not know why i could not notice that in the gnome keyboard setup
(that is: system->preferences->Keyboard) the point 
"Enable Mouse Keys" - "Select this option to make the numeric keypad emulate mouse actions...."
should have been enabled. 

if someone finds the file and entry this setting is saved for every session, pls. give a note - i could not find it in the .gnome-user-directories.

how it may happened to me: blender-3d uses a lot the shift-key while editing, and the numeric-keypad keys to switch the view(front, side). While still the shift-key seemed to be pressed, my large fingers may have hit not only the key-7 on numpad, i may hit the numlock-key above the key-7 too... ...

---

### Post by AnyFile on 2009-03-27
I have had the exactly same problem.

Many thanks to you (since I was getting tired for not finding a way to put the system in normal mode, and I solved the problem by reading your post).

Actually this happened on a linux system with gnome, but not with ubuntu. So it is not specific to ubuntu.

I made a backup copy of the several directories where gnome stores config files, and a diff between previous config files and present config files let me find that the place where this setting is store is

~/.gconf/desktop/gnome/accessibility/keyboard/%gconf.xml

in a entry named  

mousekeys_enable

---

### Post by sabmo on 2009-11-28
Thanks, I had this problem as well. 

shift+numlock is strange enough that you'd think you would never hit it, yet it seems that it does happen to a few of us :)

---

### Post by toppy on 2009-12-20
Thanks for the 'fix'.  I was cursing my Microsoft keyboard for this.  :)

Turns out my 1 1/2 year old is much better with the computer than I am.  Now both my kids have somehow changed my system in some way without me figuring out how.

---

### Post by kenorb on 2010-08-10
Thank you! I was struggling with this for couple of weeks. I was wonder how it happened by it-self. I don't understand why all those magic tricks are copied from Windows, it's rubbish. More annoying than helping. Shift+NumLock, it's magic!

---

### Post by alexsmith on 2010-12-24
Awesome! Shift-NumLock! I'd probably never notice that by myself! :-) Thank you so so much!!!

---

### Post by mikerobinson on 2011-02-14
How's this for a brainstorm idea? When you push shift-numlock it pops up an indication that mouse keys are being enabled.

---

### Post by MestreLion on 2011-02-17
> **mikerobinson said:**
> How's this for a brainstorm idea? When you push shift-numlock it pops up an indication that mouse keys are being enabled.

I would DEFINATLY vote for it!!! :D

My 2 cents on this whole issue:

- The "mousekeys" behaviour can be turned ON or OFF using GUI: **Menu -> System -> Preferences -> Keyboard -> Mouse Keys -> Check/Uncheck "Pointer can be controlled using the keypad"**

- Or, using gconf-editor: **Menu -> System Tools -> Configurator Editor **and then navigating to **desktop/gnome/accessibility/keyboard/mousekeys_enable**.

- If the Configurator Editor (gconf-editor actually) is not showing in your menu (it is unfortunaly disabled by default), you can enable it using **Menu -> System -> Preferences -> Main Menu**

- Command-line (useful for scripiting) to check, enable and disable the value:
```

gconftool --get /desktop/gnome/accessibility/keyboard/mousekeys_enable
gconftool --set /desktop/gnome/accessibility/keyboard/mousekeys_enable false --type=bool
gconftool --set /desktop/gnome/accessibility/keyboard/mousekeys_enable true  --type=bool

```

---

### Post by MestreLion on 2011-02-17
Oh, by the way: as for the keyboard shortcut for this, Shift+NumLock, i could not find where it is set, or how to change / disable it. Its not in Preferences > Keyboard Shortcuts. Any clues on that is welcome!

---

### Post by scarf on 2011-07-02
i have mouse keys disabled and i also used the gconf command to ensure it was disabled.  i verified the value is set to false in ~/.gconf/desktop/gnome/accessibility/keyboard/%gconf.xml  but my numpad is still moving the mouse pointer!!

---

### Post by hezuo on 2011-07-14
Thanks a lot, this little problem was driving me crazy

---

### Post by JP Android on 2011-11-15
> **scarf said:**
> i have mouse keys disabled and i also used the gconf command to ensure it was disabled.  i verified the value is set to false in ~/.gconf/desktop/gnome/accessibility/keyboard/%gconf.xml  but my numpad is still moving the mouse pointer!!

the solution above does not work for me neither....

[B]The fix for me on Ubuntu 11.10 is the next:

Menu Applications - System Tools - System Settings - Universal Access - Pointing and Clicking - Control the pointer using the keyboard = OFF
[/B]
for a reason I don't understand the option 
Menu Applications - Universal Access  only show me (onboard and orca screen reader options) and I can't change the setting from there.

regards.

---

### Post by yzf600 on 2012-01-18
> **JP Android said:**
> 
[B]The fix for me on Ubuntu 11.10 is the next:

Menu Applications - System Tools - System Settings - Universal Access - Pointing and Clicking - Control the pointer using the keyboard = OFF
[/B]


Thank you so much for this info! I would have never thought to look under that menu tree! My keypad works well now.

---

### Post by mbuell on 2012-01-20
shift+numlock = happiness!  :)

Thanks. My numeric keypad quit working - I was totally befuddled. I tried shift+numlock and VOILA! It works again!

11:00 and all is well.

---

### Post by verohadad on 2012-12-19
Thanks a lot for this post! You've saved me some more hours of hair pulling... Shift + NumLock did the trick using Ubuntu Gnome

---

