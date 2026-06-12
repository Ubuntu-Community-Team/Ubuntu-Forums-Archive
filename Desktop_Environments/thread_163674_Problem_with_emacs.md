---
title: "Problem with emacs"
date: 2006-04-21
forum: Desktop Environments
---

### Post by sas13 on 2006-04-21
this should be simple, but I haven't managed to find the answer online:

I installed emacs, when I try to run it the window opens up ok, I can read the options on the menu bar and see the blue and red graphocal greeting, but all other text is just empty squares.

when I type everything appears as more squares...

is there some configuration file somwhere trying to load nonexistant fonts or something?

using breezy

thanks.

---

### Post by art on 2006-04-21
Try putting this into your ~/.emacs
(set-default-font "-misc-fixed-medium-r-normal--14-100-100-100-c-70-iso8859-1")
Maybe will help. And also see what else you have in this file that might be screwing stuff up.

---

### Post by sas13 on 2006-04-21
hmmm.. 

turns out I have no ~/.emacs

---

### Post by art on 2006-04-21
You can create one... That will become your configuration file

---

### Post by sas13 on 2006-04-21
yeah, I tried to create one with nothing but that line you sent me (the () and everything inside them). 

I'm still just getting the squares but something has changed in the layout of the screen (and no more GNU graphic)

---

### Post by sas13 on 2006-04-21
maybe this helps:

tried running emacs from a terminal - got the following output:

```

Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct

```

so I'm pretty sure it's a font thing, but I don't know how to fix it (I'm new to emacs)

---

### Post by art on 2006-04-21
I am not sure this'll help, but do you have emacs-extra,emacs-intl-fonts(if your default language is not english) and emacs-goodies installed? Also do you have xfonts installed? Try installing them and see what you get...

---

### Post by sas13 on 2006-04-21
yes, I have those installed, no luck.

---

### Post by sas13 on 2006-04-21
okay, 

after some googling I tried this:

```
emacs -fn 10x20
```

and I got the text back.

-fn selects font, but I'm not sure what 10x20 means or how to make a permanent fix.

---

### Post by art on 2006-04-21
The option -fn means font
Google suggests putting 
(add-to-list 'default-frame-alist '(font . "10x20"))
in your .emacs. Does that work?
You might wanna consult this:
[http://www.delorie.com/gnu/docs/emacs/emacs_537.html](http://www.delorie.com/gnu/docs/emacs/emacs_537.html)

---

### Post by sas13 on 2006-04-21
Thanks art.

adding that line to my .emacs didn't make any difference, but for now I'll just go with passing ```
-fn 10x20
``` at the command line.

I've already wasted half a day on this and on getting a matlab shell to run under emacs with no desktop option - turns out there's a typo in the mathworks supplied matlab.el file ](*,)  - but after fixing that (with help from a post by Jerry Chen) it now works and I'll probably try for a more permanent fix in a few days when I have more time.

---

### Post by spaceman_spiff on 2006-04-21
I guess this was solved, I just want to add a solution here since I suddenly saw the same behaviour.

I made a new /etc/X11/xorg.conf when installing a new graphics card driver. It was automatically generated, and after using this to start X I got the same behaviour in emacs if i did not specify a font. I then noticed that in the xorg.conf-file all the FontPath lines were commented out. After I uncommented them (or rather copied the lines I had in my old xorg.conf) emacs works as normal.

---

### Post by potterzot on 2006-09-09
That trick with xorg.conf did it for me, except that mine weren't commented out, but pointed to the wrong directory.  I've seen other people with the box problem in emacs, is there a place to put this info so that it is easier to find?

---

### Post by Wertigon on 2006-09-22
To add to this, (had the exact same problem), make sure your config points to
```
/usr/share/fonts/X11/
```
and not ```
/usr/share/X11/fonts/
```
That solved the font problems nicely. :)

---

### Post by jimmyk on 2006-10-25
This tempory solution works for me

```
emacs -fn 10x20
```

But changing the FontPath lines in my xorg.conf stopped my Xserver from loading when I started Ubuntu.

I can see the font files are located at the FontPaths in xorg.conf i.e. at

```
/usr/share/X11/fonts/
```

Does this mean I should create the directory

```
/usr/share/fonts/X11/
```

and move all the files from the X11/fonts/ directory there and then change the FontPaths in xorg.conf?  Or does any body know if there is just something I can add to .emacs to solve the problem?

---

