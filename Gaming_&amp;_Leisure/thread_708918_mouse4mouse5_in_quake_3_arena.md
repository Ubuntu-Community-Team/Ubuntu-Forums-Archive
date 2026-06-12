---
title: "mouse4/mouse5 in quake 3 arena"
date: 2008-02-26
forum: Gaming &amp; Leisure
---

### Post by ykram on 2008-02-26
I used to have mouse4 and mouse5 working in Quake 3 Linux (ubuntu dapper) and I've sinced reinstalled back to Dapper and have Quake 3 working, my only problem is mouse4/mouse5 don't do anything. 

```

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver        "evdev"
    Option        "CorePointer"
    Option        "Dev Name"        "Logitech USB Gaming Mouse"
    Option        "Dev Phys"        "usb-0000:00:10.2-2/input0"
    Option        "Device"          "/dev/input/event1"
    Option        "Buttons"         "10"
    Option        "ZAxisMapping"    "4 5"
#    Option       "ButtonMapping"   "1 2 3 6 7"
EndSection

```

Thing is, mouse4 and mouse5 both work in Firefox and irssi; that is mouse4 makes the window move back and mouse5 makes the window go forward. Any thoughts?

This would be a logitech G5.

---

### Post by ykram on 2008-02-27
Got it. Turns out I needed:

"~/.click/click 4"
  m:0x0 + b:11
"~/.click/click 5"
  m:0x0 + b:12

in my .xbindkeysrc :)

---

### Post by Shadowmeph on 2008-03-18
> **ykram said:**
> Got it. Turns out I needed:

"~/.click/click 4"
  m:0x0 + b:11
"~/.click/click 5"
  m:0x0 + b:12

in my .xbindkeysrc :)

Did you make that Dir or where is it?

---

### Post by ykram on 2008-07-25
Yes. I made the ".click" directory with the 'click' executable in there.

```

/* gcc -g -Wall -o click click.c -L /usr/X11R6/lib/ -lX11 -lXtst */

#include <X11/Xlib.h>
#include <X11/extensions/XTest.h>
#include <stdio.h>
#include <stdlib.h>

int main( int argc, char *argv[] ) {
    Display *dpy = XOpenDisplay( NULL );
        int butnum;
        int click;
        butnum=1;
        click=0;
        if (argc > 2) {
                butnum = atoi(argv[1]);
                click = atoi(argv[2]);
        } else if (argc > 1) {
                butnum = atoi(argv[1]);
        }
        if ((click == 0) || (click == 1)) {
                printf ("Faking button %d down\n", butnum);
            XTestFakeButtonEvent( dpy, butnum, True, CurrentTime );
        }
        if ((click == 0) || (click == 2)) {
                printf ("Faking button %d up\n", butnum);
            XTestFakeButtonEvent( dpy, butnum, False, CurrentTime );
        }
        
    XCloseDisplay( dpy );
    return 0;
}


```

is what it consists of, click.c that is.

---

