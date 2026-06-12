---
title: "Error: no display specified"
date: 2009-09-10
forum: Desktop Environments
---

### Post by TheSgrash on 2009-09-10
Hi people i have a problem...

when i write in terminal "xdg-open http://www.google.it" or "gnome-open http://www.google.it" for example, it returns the error:

Error: no display specified

how can i solve this problem?

i understand that it's about the DISPLAY variable (i have it setted to :0.0)

help me please...

sorry for my bad english

---

### Post by wojox on 2009-09-10
Try:

```
xdg-open 'http://www.google.it'
```

See if that makes a difference.

Is your browser open when you do this?

---

### Post by TheSgrash on 2009-09-10
> **wojox said:**
> Try:

```
xdg-open 'http://www.google.it'
```

See if that makes a difference.

Is your browser open when you do this?

it's the same...

firefox is open...why?

---

### Post by TheSgrash on 2009-09-10
i tried also with firefox closed... it's always the same

---

### Post by mcduck on 2009-09-10
Are you trying to do this from a terminal emulator (like Gnome-terminal) or from TTY?

Doing it from terminal emulators running inside your desktop should work, but if you try to do it from TTY you'll need to set the display variable in that TTY first, otherwise it will try to launch the command inside that TTY..

---

### Post by TheSgrash on 2009-09-11
> **mcduck said:**
> Are you trying to do this from a terminal emulator (like Gnome-terminal) or from TTY?

Doing it from terminal emulators running inside your desktop should work, but if you try to do it from TTY you'll need to set the display variable in that TTY first, otherwise it will try to launch the command inside that TTY..

i do it in Gnome-Terminal :(

---

### Post by Linux BASHer on 2010-02-16
Hello. I'm trying to launch X-Window apps from the console (tty) and get the same error. How do I set the $DISPLAY variable in order to do this?

---

### Post by pi/roman on 2010-02-16
You could try DISPLAY=:0 before your command.

---

### Post by Linux BASHer on 2010-02-16
> **pi/roman said:**
> You could try DISPLAY=:0 before your command.

Thank you. That worked perfectly.

Now, can I set this variable permanently so I do not have to enter it again every time?

---

### Post by imon214 on 2011-03-03
export DISPLAY=ipaddressofyourmachineorpc:0.0

0.0 means the version of the XMing Server like (XMing Server:0.0)

that's it then re-run the application on X Display


Goodluck!
imon...:)

---

