---
title: "R Statistical software has font problems"
date: 2007-04-14
forum: Education &amp; Science
---

### Post by O-pos on 2007-04-14
Hello,

I've installed R on my ubuntu 6.10. and it can't make graphs. When I give order to make graphs, it gives the message: 

Error in X11() : could not find any X11 fonts
Check that the Font Path is correct.

I found the solution in Ubuntu archives, but as I'm new Ubuntu user, I don't know how to do that. can someone explain to me in a primitive language what to do? Here's what should be done (quoted):


>  I have fixed this problem in the following way, which I saw on a thread somewhere. So now when I type R the graphics work. No "LANG=" specification is needed.

In Edgy the xfonts are in /etc/share/fonts/X11. But the automatic configuration of /etc/X11/xorg.conf has lines specifying the fontpaths as in /etc/share/X11/fonts .

I edited /etc/X11xorg.conf to change every instance of X11/fonts to fonts/X11.

So now that section is

I have fixed this problem in the following way, which I saw on a thread somewhere. So now when I type R the graphics work. No "LANG=" specification is needed.

In Edgy the xfonts are in /etc/share/fonts/X11. But the automatic configuration of /etc/X11/xorg.conf has lines specifying the fontpaths as in /etc/share/X11/fonts .

I edited /etc/X11xorg.conf to change every instance of X11/fonts to fonts/X11.

So now that section is

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/usr/share/fonts/X11/misc"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


whereas the automatic configuration from my clean installation of Edgy was
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

The new configuration takes effect after rebooting. 

---

### Post by machoo02 on 2007-04-14
Press Alt+F2, and type in```
gksudo gedit /etc/X11/xorg.conf
```
When xorg.conf opens, look for the section in your quoted description (hint - it's usually near the top of the file) and change /usr/share/X11/fonts to /usr/share/fonts/X11.  You could easily do this by pressing Ctrl+H to open up the Find/Replace dialog, and entering the two strings into the search and replace boxes.

---

