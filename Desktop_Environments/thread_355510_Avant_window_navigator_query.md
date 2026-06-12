---
title: "Avant window navigator query"
date: 2007-02-07
forum: Desktop Environments
---

### Post by PaulFXH on 2007-02-07
Using Beryl svn/xgl with Ubuntu 6.10 with a nVidia GeForce 7300 LE card.
Today I got Awn working using the installation guide in [HTML]http://code.google.com/p/avant-window-navigator/[/HTML].
It works great without problems so far (I couldn't get it installed using the compile or deb methods suggested in this thread [HTML]http://www.ubuntuforums.org/showthread.php?t=351186&highlight=avant-window+navigator[/HTML])

However, I did not comply with the advice given in the Googlecode site which states that prior to installation of Awn:
```
You will almost definatley need to build libwnck again due to one silly change you need to make in the source: 

in libwnck/private.h change 
#define DEFAULT_ICON_WIDTH          XX - this could be any number, most likely 32
#define DEFAULT_ICON_HEIGHT         XX

to 
#define DEFAULT_ICON_WIDTH          48
#define DEFAULT_ICON_HEIGHT         48

you need to update & install libwnck with these changes before you install Awn
```

Now I cannot find any file named libwnck/private.h on my system. What does this imply?
If I do find it or can download/install it from somewhere, what exactly do I need to do? Is it just to make the suggested change in a text editor and save over the existing copy or what?

Thanks for any suggestions
Paul

---

