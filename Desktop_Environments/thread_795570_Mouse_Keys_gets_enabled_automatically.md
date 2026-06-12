---
title: "Mouse Keys gets enabled automatically"
date: 2008-05-15
forum: Desktop Environments
---

### Post by Tigge on 2008-05-15
I'm using the latest ubuntu version and I've had this problem since last version. My Mouse Keys (Allows user to control mouse from keypad) is getting enabled every now and then so my key pad doesn't work until i turn it of again. This repeats again and again and is very irritating. I've tried to disable the option that lets you enable these things from the keyboard with no effect. I've also tried to make the off setting mandatory in gconf-editor but also with no effect.

Anyone have any ideas on this one?

---

### Post by kag on 2008-05-15
[http://ubuntuforums.org/showthread.php?t=514554&highlight=keypad](http://ubuntuforums.org/showthread.php?t=514554&highlight=keypad)

---

### Post by Tigge on 2008-05-16
I'll try to play around with the "Enable assistive technologies" setting. If the keyboard settings don't work because of this setting this is clearly a bug.

I'll report back after testing some more. BTW, does anyone know what keyboard shortcut that enables/disables Mouse Keys?

---

### Post by vanadan on 2009-01-09
Control+Shift+NumLock

---

### Post by zerem on 2009-11-20
--- as i posted in [https://bugs.launchpad.net/ubuntu/+bug/192508](https://bugs.launchpad.net/ubuntu/+bug/192508) ---

Hello fellow earthlings daily beaten by this bug.

I used this workaround to permanently disable mousekeys shortcut shift+num-lock, alt+shift+num-lock etc...

gksudo gedit /usr/share/X11/xkb/compat/complete
-or-
sudo nano /usr/share/X11/xkb/compat/complete

and comment out lines for mousekeys and accesx(full) (for full keyboard accessibility purge)

resulting file /usr/share/X11/xkb/compat/complete:
// $XKeyboardConfig$
// $Xorg: complete,v 1.3 2000/08/17 19:54:34 cpqbld Exp $
default xkb_compatibility "complete" {
    include "basic"
    augment "iso9995"
    //augment "mousekeys"
    //augment "accessx(full)"
    augment "misc"
    augment "xfree86"
    augment "level5"
};

Wish you a lot happy days without moving mouse by keypad ;)
Greets Ondrej

---

