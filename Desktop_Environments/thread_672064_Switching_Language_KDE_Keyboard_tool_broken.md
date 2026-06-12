---
title: "Switching Language KDE Keyboard tool broken?"
date: 2008-01-19
forum: Desktop Environments
---

### Post by Newbie123 on 2008-01-19
I have kubuntu 7.10, and it seems that the KDE keyboard switching tool is not working. I can still manually click on the icon and have it switch languages, but this is too slow when I need to switch back and forth all the time.

The default CTRL+ALT+K shortcut works only 1 way, from English into the other language, but i cannot switch back.

Also, I tried changing the shortcut to ALT+SHIFT, but it completely ignores the settings I change under the preferences dialog box. I didn't have this problem before with older versions of kubuntu.

Any ideas?

Thanks

---

### Post by vsk on 2008-02-17
Same problem here!

Any help, plz?

---

### Post by flangemonkey on 2008-02-17
Right, I think this is related to the issue I have on my machine (Xubuntu 7.10)
 
In UK english (set in my xorg.conf) shortcut keys using the 'windows' or super key stop working, they only seem to work in US English

So, with your information, I am guessing there is something missing in the non-US keymaps.

This can be demonstrated by trying to create a new keyboard shortcut and you'll see the combinations are not being recognised, although ctrl-alt-k does add on mine.

fwiw, below is my xorg.conf, although the problem persists whether X manages my keyboard or not.

```

(snip)
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "uk"
EndSection

(snip)

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection


```

---

### Post by flangemonkey on 2008-02-29
right, this is probably due to keymappings

the keymaps can be viewed and edited in a text editor; for some reason I had no uk keymap, it's quite likely the languages you are switching to aren't mapping, for example, the 'alt' key.

The symbol keymaps are in /etc/X11/xkb/symbols

I ran
```
cp /etc/X11/xkb/symbols/us /etc/X11/xkb/symbols/uk 
```

and everything works again.

It might be worth trying similar on your computer, checking first the symbols file for the language you are changing to.  

(this troubleshooting acquired from [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/9364](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/9364))

Phill


UPDATE:
The symbols map for 'uk' is called 'gb' so it was my wrongful editing of the xorg.conf that caused this; but I still think the symbols directory could be a cause of your problem...

---

### Post by thatsnice on 2008-03-11
I had this same problem, where the default CTRL+ALT+K switched the input language only one way.  Fortunately I found a very simple solution.  If you look at Configure --> Layout, there is a box called Active Layouts.  If you highlight your non-English layout, you will see a checkbox appear below saying "Include Latin layout." Click this box.  It should now work (well, it did for me...).

---

