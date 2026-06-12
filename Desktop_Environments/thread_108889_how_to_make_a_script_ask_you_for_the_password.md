---
title: "how to make a script ask you for the password?"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Bou on 2005-12-27
I just made a script to automatically install all the programs I need from a fresh installation of Ubuntu. However, I need to execute it from the console for it to ask me my admin password.

Can this be scripted so that it asks me for the password graphically?

Thanks a lot.

---

### Post by fordfan753 on 2005-12-27
[QUOTE=Bou]I just made a script to automatically install all the programs I need from a fresh installation of Ubuntu. However, I need to execute it from the console for it to ask me my admin password.

Can this be scripted so that it asks me for the password graphically?

Thanks a lot.[/QUOTE]

You mean like gksu and gksudo ?

---

### Post by meborc on 2005-12-27
for example this is the contents of a script opening nautilus in sudo and asking pw before```
#!/bin/bash

# Opens a nautilus window as root.

foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI
```
it was distributed here in forums, but who was the original owner i don't know...

may be it came with automatix :rolleyes: ... anyway - gratz

---

### Post by Bou on 2005-12-27
[QUOTE=fordfan753]You mean like gksu and gksudo ?[/QUOTE]

Yeah, something like gksudo, but I don't want it to ask for the password before each command, just once when I execute the script.

So, is there a way for gksudo to affect ALL the commands in the script, and not just the one that follows?

---

### Post by fordfan753 on 2005-12-27
gksudo should remain active for a while, 5 minutes or something, before you'll need to input your password again, but if you want longer than that, well, I have no idea unless you run the whole script with gksudo, but that could get dangerous if it was complex.

---

### Post by Bou on 2005-12-27
Well, in the end I created a second script with gksudo -> first script. I don't know if this is the cleanest method possible, but it works with just one click.

I'll leave the whole thing here, just in case anyone wants to take a look at it and maybe make some suggestions.

I took some lines of code from Automatix, so thanks to the author too.

---

### Post by Bou on 2005-12-28
There's another question I would like to make... does anyone look how to make a zenity window look like this, complete with the console info?

[IMG]http://img455.imageshack.us/img455/2171/pantallazoinstalandoactualizac.png[/IMG]

---

