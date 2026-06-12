---
title: "Compiz question,"
date: 2007-09-16
forum: Desktop Effects &amp; Customization
---

### Post by DGentry on 2007-09-16
When I go to a term window and type compiz -replace I get the following.

doug@doug-linux:~$ compiz -replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-replace'


(gtk-window-decorator:20743): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:20743): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:20743): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:20743): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
metacity: Unknown option -replace
doug@doug-linux:~$ 

Does anyone know what I can do to make this work correctly?

Thank you in advance
Doug Gentry

---

### Post by luisromangz on 2007-09-16
Well, the error log self-explains, you are using -replace instead of the correct option, --replace.

Usually, long option names (such --replace) are precceded by --, and short ones, like -h, are preceded by just one -.

---

### Post by DGentry on 2007-09-16
HMmmmmmmmm, I don't understand.... when you wrote this 
"self-explains, you are using -replace instead of the correct option, --replace."

They look exactly the same to me.

Could you tell me exactly what to type and heck, where to type it at? LOL, Sorry

---

### Post by jocko on 2007-09-16
It should be "--replace" with two "-", not "-replace" with only one "-".

---

### Post by st33med on 2007-09-16
Type two dashes instead of one before replace.
Example:
```
compiz --replace
```

Not:
```
compiz -replace
```

However, if it still doesn't work, try this in the terminal:
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp &
```
That will set it in the background, but **don't close that terminal!!**

---

### Post by hyperair on 2007-09-16
You can close the terminal, but you need to use the command "exit" instead of clicking the "x" button. Another way is to "disown" the application first.
```

disown -a

```

---

### Post by DGentry on 2007-09-16
Oh Oh, when I did the LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp & command I got this output on my term window. Which does seem wierd, I know I have an ATI card.

doug@doug-linux:~$ LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp &
[1] 24349
doug@doug-linux:~$ Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

doug@doug-linux:~$ 
(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:24373): Wnck-WARNING **: Unhandled action type (nil)

---

