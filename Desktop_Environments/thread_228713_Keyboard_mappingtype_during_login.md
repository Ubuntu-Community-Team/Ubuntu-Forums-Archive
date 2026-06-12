---
title: "Keyboard mapping/type during login"
date: 2006-08-03
forum: Desktop Environments
---

### Post by MasterZ on 2006-08-03
Hello, 

I recently installed compiz on top of my gnome Desktop, and I'm experiencing a strange keyboard behavior since then, but only on the login screen. 

The special characters on the numeric keypad are not working anymore if the 'num lock' light is 'on'. 
It means that I cannot type "+" "-" "/", ... etc at login time except if I disable numlock first; which I do not want to do because I need numbers too (go figure ;) ).

After entering the gnome session, it works ok, like before (ie. "+" "-" "/" keys are not affected by numlock status). 

I know that just after installing compiz, I had to go to the keyboard preferences again and re-choose the correct layout which had dissapeared, but it seems that the pre-login layout might be influenced by something else. 

Could somebody help ? 


Thanks, 

MasterZ

---

### Post by MasterZ on 2006-08-05
Hi again, 

I did some research and here's the current status : 

First to put a bit of context here is my xorg.conf keyboard config : 
```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "logiink"
    Option         "XkbLayout" "be"
EndSection
```
The "XkbModel" was "pc(pc105)" before but I changed it to match the actual keyboard. this does not change the issue. 

I know that what happen before logon, at the login screen is defined in /etc/gdm/Init/Default. 
I added some debug lines in this part : 
```
SETXKBMAP=`gdmwhich setxkbmap`
echo SETXKBMAP is - $SETXKBMAP >> /tmp/gmdinit.txt #masterz
if [ x$SETXKBMAP != x ] ; then
  # FIXME: is this all right?  Is this completely on crack?
  # What this does is move the xkb configuration from the GDM_PARENT_DISPLAY
  # FIXME: This should be done in code.  Or there must be an easier way ...
  if [ -n "$GDM_PARENT_DISPLAY" ]; then
    XKBSETUP=`( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $SETXKBMAP -v )`
    echo XKBSETUP is - $XKBSETUP >> /tmp/gmdinit.txt	#masterz
    if [ -n "$XKBSETUP" ]; then
      XKBKEYMAP=`echo "$XKBSETUP" | grep '^keymap' | awk '{ print $2 }'`
      XKBTYPES=`echo "$XKBSETUP" | grep '^types' | awk '{ print $2 }'`
      XKBCOMPAT=`echo "$XKBSETUP" | grep '^compat' | awk '{ print $2 }'`
      XKBSYMBOLS=`echo "$XKBSETUP" | grep '^symbols' | awk '{ print $2 }'`
      XKBGEOMETRY=`echo "$XKBSETUP" | grep '^geometry' | awk '{ print $2 }'`
	    echo XKBKEYMAP is - $XKBKEYMAP >> /tmp/gmdinit.txt	#masterz
	    echo XKBTYPES is - $XKBTYPES >> /tmp/gmdinit.txt	#masterz
	    echo XKBCOMPAT is - $XKBCOMPAT >> /tmp/gmdinit.txt	#masterz
	    echo XKBSYMBOLS is - $XKBSYMBOLS >> /tmp/gmdinit.txt	#masterz
	    echo XKBGEOMETRY is - $XKBGEOMETRY >> /tmp/gmdinit.txt	#masterz
      if [ -n "$XKBKEYMAP" ]; then
        $SETXKBMAP -keymap "$XKBKEYMAP"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" -a -n "$XKBGEOMETRY" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS" -geometry "$XKBGEOMETRY"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS"
      elif [ -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -symbols "$XKBSYMBOLS"
      fi
    fi
  fi
fi
```
it appears that it does not enter in the condition
```
 if [ -n "$GDM_PARENT_DISPLAY" ];
```
I do not know if this is normal or not... 
Anyway, Something does not work there and it worked before. 

I added this line at the bottom of /etc/gdm/Init/Default
```
/usr/bin/setxkbmap -model logiink -rules xorg -layout be
```

This solves the problem an now my numpad keys are correctly recognized in the login screen. It means that the code in /etc/gdm/Init/Default has a flaw. 

How come my keyboard was configured allright by that code before installing compiz, and not now ? 

I do not think my xorg.conf has changed. 
And the only customization i did for the install is in gdm.conf-custom where I added:
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true
```
But this should not matter, right ? 

So the issue is partially solved, but I do not want to leave things like that, it's not a good way of working. 
So if anyone has an idea :)  please help. 


MasterZ

---

