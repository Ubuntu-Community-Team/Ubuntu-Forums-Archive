---
title: "gnome-terminal behaves strange"
date: 2010-06-06
forum: Desktop Environments
---

### Post by floogy on 2010-06-06
My gnome-terminal bash session cannot delete chars before the cursor by hitting the backspace key (this works everywhere else).

Secondly - If I use the Arrow keys it sometimes deletes the $ or more chars of the prompt:
```
user@ubuntu:~ ls WDR3\ ©\ Westdeutscher\ Rundfunk\ Köln\ 2010/
s: command not found
user@ubuntu:~$ s WDR3\ ©\ Westdeutscher\ Rundfunk\ Köln\ 2010/
```
If so it's not easy to get the right position in the commandline. Everything is turned a char left (or right?). Anyway: the cursor doesn't fit to the position it has for the bash. In other words: We don't see what we get.  

```
user@ubuntu:~l ls   WDR3\ ©\ Westdeutscher\ Rundfunk\ Köln\ 2010/
ls: cannot access ls: No such file or directory
ls: cannot access R3 © Westdeutscher Rundfunk Köln 2010/: No such file or directory

```

3rd Issue: If I copy and paste (byX method - select (copy) and middle mouse key insert (paste)) I get some chars wrong:
```
user@ubuntu:~$ ls WDR3\ &#65533;&#65533;\ Westdeutscher\ Rundfunk\ K&#65533;&#65533;ln\ 2010/ 
incomplete
```
Nevertheless ls works properly with this: incoming is an existing folder in that directory.

Also ls, less and some other application doesn't handle these (utf8 ?) chars properly, while cat does:
```

~$ less /usr/share/X11/locale/en_US.UTF-8/Compose
# UTF-8 (Unicode) compose sequence
# David.Monniaux@ens.fr
#
# $XFree86: xc/nls/Compose/en_US.UTF-8,v 1.11 2004/01/06 13:14:04 pascal Exp $

# Part 1 - Manual definitions

# Spacing versions of dead accents
<dead_tilde> <space>                    : "~"   asciitilde # TILDE
<dead_tilde> <dead_tilde>               : "~"   asciitilde # TILDE
<dead_acute> <space>                    : "'"   apostrophe # APOSTROPHE
<dead_acute> <dead_acute>               : "<C2><B4>"   acute # ACUTE ACCENT
<dead_grave> <space>                    : "`"   grave # GRAVE ACCENT
<dead_grave> <dead_grave>               : "`"   grave # GRAVE ACCENT
<dead_circumflex> <space>               : "^"   asciicircum # CIRCUMFLEX ACCENT
<dead_circumflex> <dead_circumflex>     : "^"   asciicircum # CIRCUMFLEX ACCENT
<dead_abovering> <space>                : "<C2><B0>"   degree # DEGREE SIGN
<dead_abovering> <dead_abovering>       : "<C2><B0>"   degree # DEGREE SIGN
<dead_macron> <space>                   : "<C2><AF>"   macron # MACRON
<dead_macron> <dead_macron>             : "<C2><AF>"   macron # MACRON
```

```
~$ cat /usr/share/X11/locale/en_US.UTF-8/Compose|head -n20
# UTF-8 (Unicode) compose sequence
# David.Monniaux@ens.fr
#
# $XFree86: xc/nls/Compose/en_US.UTF-8,v 1.11 2004/01/06 13:14:04 pascal Exp $

# Part 1 - Manual definitions

# Spacing versions of dead accents
<dead_tilde> <space>             	: "~"   asciitilde # TILDE
<dead_tilde> <dead_tilde>        	: "~"   asciitilde # TILDE
<dead_acute> <space>             	: "'"   apostrophe # APOSTROPHE
<dead_acute> <dead_acute>        	: "´"   acute # ACUTE ACCENT
<dead_grave> <space>             	: "`"   grave # GRAVE ACCENT
<dead_grave> <dead_grave>        	: "`"   grave # GRAVE ACCENT
<dead_circumflex> <space>        	: "^"   asciicircum # CIRCUMFLEX ACCENT
<dead_circumflex> <dead_circumflex> 	: "^"   asciicircum # CIRCUMFLEX ACCENT
<dead_abovering> <space>         	: "°"   degree # DEGREE SIGN
<dead_abovering> <dead_abovering> 	: "°"   degree # DEGREE SIGN
<dead_macron> <space>            	: "¯"   macron # MACRON
<dead_macron> <dead_macron>      	: "¯"   macron # MACRON
```

reset or clear didn't help.

---

