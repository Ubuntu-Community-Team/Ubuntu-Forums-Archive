---
title: "Nautilus in XFCE"
date: 2005-04-21
forum: Desktop Environments
---

### Post by Kimm on 2005-04-21
I just installed XFCE and I can simply sau that I love it!
I love the way it looks and how GNOME apps work perfectly. I just dont quite like the filemanager and I was woundering if it is possible to use Nautilus instead? so that nautilus starts automaticly and displays my desktop and so forth (wich happens if I run it  from the console...).

Does anyone know how I can achieve this?

---

### Post by bored2k on 2005-04-21
[QUOTE=Kimm]I just installed XFCE and I can simply sau that I love it!
I love the way it looks and how GNOME apps work perfectly. I just dont quite like the filemanager and I was woundering if it is possible to use Nautilus instead? so that nautilus starts automaticly and displays my desktop and so forth (wich happens if I run it  from the console...).

Does anyone know how I can achieve this?[/QUOTE]
 Of course you can use it.
On the file manager properties on the XFCE panel, simply click properties and change rox-filer or whatever for nautilus --no-desktop (do the same for the other shortcuts).

---

### Post by Kimm on 2005-04-21
thats not quite what I mean, I mean that I acctually want Nautilus to start and display my desktop automaticly when XFCE starts, is that possible?

---

### Post by siebzehn on 2005-04-21
[QUOTE=Kimm]thats not quite what I mean, I mean that I acctually want Nautilus to start and display my desktop automaticly when XFCE starts, is that possible?[/QUOTE]


Sure it is.  Just create a link to nautilus in ~/Desktop

You can do this:

ln -s /usr/bin/nautilus ~/Desktop/

And that's it.  Next time you restart Xfce Nautilus will be there...

---

### Post by wolovids on 2005-04-21
If you use session management, just run "nautilus" without any parameters and it'll take over your desktop.  Logout and save your session.  The next time you log in, nautilus will be started automatically.

---

### Post by Kimm on 2005-04-21
thanks that worked great :D

---

### Post by Kimm on 2005-04-21
wow, the wine docking even works, thats something I allways missed in GNOME :D

---

### Post by Kimm on 2005-04-21
omfg, its even got a flashing task bar!! :D :D :D \\:D/ 

GNOME = out a here
XFCE = Hugged, over and over again :D :razz:

---

