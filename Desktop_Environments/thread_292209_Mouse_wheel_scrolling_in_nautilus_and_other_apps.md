---
title: "Mouse wheel scrolling in nautilus and other apps"
date: 2006-11-03
forum: Desktop Environments
---

### Post by NyquistLimit on 2006-11-03
Any ideas how to adjust the mouse wheel speed in Nautilus and other apps like Liferea? I know how to do it in Firefox via about:config but isn't there a central place in the mouse preferences of the operating system that can control this?

My mouse is a Logitech G5 if that helps. Scrolling only 2 lines at a time in Nautilus etc is far too slow. Also a mouse wheel acceleration option similar to Windows would be nice, where the faster you move the wheel the more lines it will scroll.

---

### Post by ljpm on 2006-11-03
> **NyquistLimit said:**
> Any ideas how to adjust the mouse wheel speed in Nautilus and other apps like Liferea? I know how to do it in Firefox via about:config but isn't there a central place in the mouse preferences of the operating system that can control this?

My mouse is a Logitech G5 if that helps. Scrolling only 2 lines at a time in Nautilus etc is far too slow. Also a mouse wheel acceleration option similar to Windows would be nice, where the faster you move the wheel the more lines it will scroll.

Sorry I can't help with your problem, but, would you be able to post how you changed the speed in Firefox. 

thanks

---

### Post by NyquistLimit on 2006-11-03
In the address bar of firefox type:

```
about:config
```

Then filter the settings for:

```
mousewheel.withnokey.sysnumlines
```
change this to false

then look for:
```
mousewheel.withnokey.numlines
```

and change it to whatever number of lines u want to scroll. I've got it set to 6.

---

### Post by NyquistLimit on 2006-11-04
*bump*

Nobody knows how to set a global mouse wheel speed? Isn't this a rather important feature to have in an operating system? Without some form of mousewheel speed adjustment and acceleration I'm finding scrolling through large directories and web pages almost painful :(

---

### Post by ljpm on 2006-11-04
Thank you, 
Much appreciated.

---

