---
title: "Ratpoison problem"
date: 2009-05-25
forum: Desktop Environments
---

### Post by NeoDevin on 2009-05-25
I'm running Ubuntu Jaunty on my laptop (Toshiba Satellite A100, if that matters), installed ratpoison with "sudo apt-get install ratpoison".  It doesn't show up in the GDM sessions list, so I opened a failsafe terminal, typed "ratpoison" to open it.  "ctrl+t c" gives me the error message "Failed to contact the GConf daemon; exiting", and displays the not "/bin/sh -c "x-terminal-emulator" finished".

Any advice on how to get this working?

Thanks in advance.

Devin

---

### Post by ad_267 on 2009-05-25
Try creating a ratpoison.desktop file in /usr/share/xsessions/. Just copy the Gnome one and change what you need. That way you can log in from GDM.

---

### Post by NeoDevin on 2009-05-25
Done, thanks.  That lets me log in from there, but I still can't open a terminal in ratpoison.

---

### Post by konard on 2009-05-29
I just updated to Jaunty and had the same problem. The reason you can not  get a terminal is because C-t c is bound to "exec x-terminal-emulator" which does nothing because there is no executable called on you system x-terminal-emulator. So all you need to do to get it working  is bind C-t c to terminal emulator like xterm. To do this create a text file in your home directory called .ratpoisonrc, ex. /home/yourusername/.ratpoisonrc and write in it:
```
bind c exec xterm
```This file executes what ever commands are in it when ratpoison starts. You can use to bind other programs to keys in ratpoison as well,l just add ```
bind "key" exec "name of program"
``` or run programs on start up like ```
exec xterm
``` to start with a terminal.

---

### Post by NeoDevin on 2009-06-02
Thanks, works perfectly!

---

### Post by yolcoyama on 2009-06-04
You can boot x-terminal-emulator by adding this line to your "~/.ratpoisonrc":

```
exec /usr/lib/libgconf2-4/gconfd-2 &
```(gconfd path has to be changed for your environment)


also, I found xterm a little unconsistent when other xterm process running back the ground, it freezes a minute on every shift to the frame.

---

