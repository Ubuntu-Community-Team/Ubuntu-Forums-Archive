---
title: "VertRefresh in xorg.conf"
date: 2009-11-04
forum: Desktop Environments
---

### Post by smc18 on 2009-11-04
Hey everyone,

I'm having some trouble editing my /etc/X11/xorg.conf

I want to add

```

Section "Monitor"
          VertRefresh 56.0 - 60.0
EndSection
```

The original issue I'm having is when I restart my system, my gnome sets my monitor defaults to 72 Hz refresh rate.  In return, my screen is somewhat distorted until I change it to a lower frequency.

My next issue is when trying to specify my VertRefresh in /etc/X11/xorg.conf  I get an error on reboot saying it isn't a valid setting.

My original xorg.conf is

```

#... Output omitted
Section "Device"
          Identifier "Videocard0"
          Driver "intel"
EndSection

Section "Screen"
          Identifier "Screen0"
          Device     "Videocard0"
          DefaultDepth   24
          SubSection "Display"
               Viewport 0 0
               Depth    24
               Modes    "800x600" "640x480"
          EndSubSection
EndSection
```

Here is my xorg.conf after editing.

```

#... Output omitted
Section "Device"
          Identifier "Videocard0"
          Driver "intel"
EndSection

#I added this section - however it's giving me errors.
Section "Monitor"
          VertRefresh 56.0 - 60.0
EndSection

Section "Screen"
          Identifier "Screen0"
          Device     "Videocard0"
          DefaultDepth   24
          SubSection "Display"
               Viewport 0 0
               Depth    24
               Modes    "800x600" "640x480"
          EndSubSection
EndSection
```

Any help?  I've looked around and adding the Monitor Section is what I've found so far.

---

### Post by smc18 on 2009-11-04
Yay! The FreeBSD handbook came in handy.

[http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html)

I had to type add

```

Section "Monitor"
          Identifier "Monitor0"      #<---- Added this
          VertRefresh 56.0 - 60.0
EndSection

Section "Screen
          Identifier "Screen0"
          Device  "Videocard0"
          Monitor "Monitor0"          #<---- Added this
#... etc etc
```

---

