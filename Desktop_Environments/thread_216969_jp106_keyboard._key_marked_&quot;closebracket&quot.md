---
title: "jp106 keyboard. key marked &quot;closebracket&quot; makes backslash"
date: 2006-07-16
forum: Desktop Environments
---

### Post by zeimusu on 2006-07-16
Hello all. I have a Japanese keyboard. I have xorg.conf set as jp106. All the keys work correctly with the exception of the key marked as "close square bracket" When I press it I get a "\" character. 

Here is the keyboard section from xorg.cong

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "jp"
        Option          "XkbVariant"    "jp106"
EndSection


And here is the output of xev showing keypress and keyrelease events.

KeyPress event, serial 29, synthetic NO, window 0x2a00001,
    root 0x64, subw 0x0, time 2011340846, (447,414), root:(452,487),
    state 0x10, keycode 51 (keysym 0x5c, backslash), same_screen YES,
    XLookupString gives 1 bytes: (5c) "\"
    XmbLookupString gives 1 bytes: (5c) "\"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2a00001,
    root 0x64, subw 0x0, time 2011340902, (447,414), root:(452,487),
    state 0x10, keycode 51 (keysym 0x5c, backslash), same_screen YES,
    XLookupString gives 1 bytes: (5c) "\"

It seems that keycode 51 is being incorrectly mapped to keysym 0x5c. How can I fix this? I guess I need to do something with xmodmap, but what exactly? 

Thank you for any guidance

---

### Post by mogliii on 2006-07-16
Hi,

actually I had the same problem. And just found a thread where somebody posted the answer... but not so very comprehensible:

[http://ubuntuforums.org/showpost.php?p=141885&postcount=3]("http://ubuntuforums.org/showpost.php?p=141885&postcount=3")

So here is what you do:

edit the file /etc/X11/xorg.conf as root
```
$ sudo nano /etc/X11/xorg.conf
```
find the Section "InputDevice", Identifier "Generic Keyboard"

do the following change:
```
Option "XkbModel" "pc[COLOR="Orange"]105[/COLOR]"
     
==> Option "XkbModel" "pc[COLOR="DarkOrange"]106[/COLOR]"
```

after that reload the key definitions by typing (as normal user)
```
$ setxkbmap ja
```

for me he delivered an error: Error loading new keyboard description, But the ] and } work now.

...Maybe a bugreport should be issued?!?

---

### Post by mogliii on 2006-07-17
Hi,

my post is wrong. After a restart it was back to wrong.

But I typed as user:
```
$ setxkbmap -model jp106 -layout jp
```

and now it keeps even after restart.

I issued a bug report (Bug #53206). But I dont know if every user has a private key config file.

---

### Post by zeimusu on 2006-07-17
Acting on that hint I changed my xorg.conf to :

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "jp106"
Option "XkbLayout" "jp"
Option "XkbVariant" "jp106"
EndSection

(that is s/pc105/jp106/)

This works after ctrl-alt-backspace, and I'll see if it works after a reboot.

---

