---
title: "[SOLVED] Playing around with theme and font... terminal in black?"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by incen on 2008-02-18
I was playing around with the themes and fonts. I got a large font, which almost killed me. :( Well... anyway, I got it back to normal font size (I guess it's 10?! 'cause I didn't really pay attention to it before). Since I'm not sure, could anyone tell me what's the default Ubuntu font and font size?

Also, what's the theme you use? Just say how you feel for sharing though. :P

The reason that I started to play the theme is that I want the background of the terminal is in black, as what I have on my Xubuntu. Anyone knows how to do so? Thanks!:)

---

### Post by Tenken on 2008-02-18
You can change the terminal appearance independent of your theme. Go to File->Edit Current Profile-> Colors tab and uncheck the box next to "Use colors from the system theme", and under built in schemes there is a white on black option.

EDIT: The default font is Sans 10 for everything but Window title which is sans 10 bold and Fixed width which is monospace 10.

---

### Post by incen on 2008-02-18
HAHA, now I got my terminal in black! It's really cool! Thanks!

I'm searching around to see how to change theme, too. It's kinda tricky to me. I don't even know how to add it if I have one downloaded. (I just downloaded some fonts after reading some thread. However, I don't know how to install though. :P)

---

### Post by Tenken on 2008-02-18
Your fonts go in /usr/share/fonts then into their respective directory. And most themes are just drag and drop into the System-> Preferences-> Appearance window.

---

### Post by incen on 2008-02-18
The one I downloaded is ttf-liberation_1.0-0.0_all.deb. It's neither a tar file nor a ttf file. Should I install this!?!? by dpkg?

---

### Post by Tenken on 2008-02-18
You could use
```
cd /location/of/deb/file
dpkg -i ttf-liberation_1.0-0.0_all.deb
```

or you could just double click the .deb in the file browser.

---

### Post by SIXAXIS on 2008-02-18
When I try to change the background colour in my terminal window, it doesn't change. It says that the colours are black and white though.

---

### Post by Tenken on 2008-02-18
Do you have multiple profiles for the terminal?

---

