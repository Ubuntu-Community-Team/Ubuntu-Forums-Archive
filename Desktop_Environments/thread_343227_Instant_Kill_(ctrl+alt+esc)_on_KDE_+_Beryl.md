---
title: "Instant Kill (ctrl+alt+esc) on KDE + Beryl?"
date: 2007-01-21
forum: Desktop Environments
---

### Post by CyberAngel on 2007-01-21
In KDE if you press Ctrl+Alt+Esc it comes up a skull with crossbones and if you click on an application it instantly kills this application (Even if it is hanged up).
If you start beryl-manager how can you use this ultimate kill?
The above shortcut does not working :(

---

### Post by kc0dhb on 2007-02-05
the program you want is xkill...

I replicated that behavior using xbindkeys
```

sudo apt-get install xbindkeys-config xbindkeys

```

and then added this to the .xbindkeysrc file


```

###########################
# xbindkeys configuration #
###########################
#
# Version: 0.1.3
#
# If you edit this, do not forget to uncomment any lines that you change.
# The pound(#) symbol may be used anywhere for comments.
#
# A list of keys is in /usr/include/X11/keysym.h and in
# /usr/include/X11/keysymdef.h 
# The XK_ is not needed. 
#
# List of modifier (on my keyboard): 
#   Control, Shift, Mod1 (Alt), Mod2 (NumLock), 
#   Mod3 (CapsLock), Mod4, Mod5 (Scroll). 
#
# Another way to specifie a key is to use 'xev' and set the 
# keycode with c:nnn or the modifier with m:nnn where nnn is 
# the keycode or the state returned by xev 
#
# This file is created by xbindkey_config 
# The structure is : 
# # Remark 
# "command" 
# m:xxx + c:xxx 
# Shift+... 




#keystate_numlock = enable
#keystate_scrolllock = enable
#keystate_capslock = enable



#xterm
"xterm -bg black -fg green"
    m:0xc + c:28
    Control+Alt + t 

#Firefox
"firefox"
    m:0xc + c:41
    Control+Alt + f 

#xkill
"/usr/bin/killall xkill || /usr/bin/xkill"
    m:0xc + c:9
    Control+Alt + Escape 

#
# End of xbindkeys configuration

```

(You can see how easy this is to edit, you can also you xbindkeys-config to edit it)

"/usr/bin/killall xkill || /usr/bin/xkill"


the || is important, it means if and only if the first one doesn't work, do the second, that way you get the toggle effect

you then have to make sure that xbindkeys run on login

simple run the following

```

 ln `which xbindkeys` ~/.kde/Autostart/

```

which will create a simlink to xbindkeys so that it will start on login. (This is of course assuming you haven't changed the Autostart directory from within KDE...)

Enjoy

---

