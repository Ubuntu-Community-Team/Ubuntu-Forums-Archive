---
title: "CD Burner software"
date: 2005-02-01
forum: Desktop Environments
---

### Post by Chrisb319 on 2005-02-01
How will I burn my CD's with Ubuntu. 8-[

---

### Post by dhonn on 2005-02-01
If you want burn an ISO, right click the .iso and choose "Burn"

If you insert a blank cd it should have a window that popups so you can dump files into that folder then "File-> Burn to cd"

You can also go to your root terminal and run:

** apt-get install xtoast**
or
** apt-get install k3b**

You can then run xtoast or k3b, frm the prompt, run application action or from the application menu.

If you need more help then just ask.

---

### Post by pumpkinpatch on 2005-02-02
I tryed this and I got error Cannot display location 'file://kb3.

---

### Post by valadil on 2005-02-02
Try sudo k3bsetup

---

### Post by neilmc on 2005-02-02
[QUOTE=valadil]Try sudo k3bsetup[/QUOTE]

My memory is a little fuzzy on this, but I think K3B or parts of have to run as root. If you run k3bsetup without sudo it will ask for the root password and ask if it can remember it.

If you dont do this you will need to launch k3b with sudo. If you create a launcher you willl need to add gksudo.

By running k3bsetup without sudo you will be able to set up a launcher that will not ask for a password everytime you want to burn a cd.

Of course you will need to specify a root user password first. sudo passwd root

---

