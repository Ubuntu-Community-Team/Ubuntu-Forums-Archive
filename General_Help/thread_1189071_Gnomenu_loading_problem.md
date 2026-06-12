---
title: "Gnomenu loading problem"
date: 2009-06-16
forum: General Help
---

### Post by Bubblebeard on 2009-06-16
Hi,

I recently installed gnomenu and added it to my panel, replacing the default menu system.  It works fine, but every time I log in, an error pops up that says "the panel encountered a problem while loading oafiid gnome_gnomenu" and gives me the option to delete it or not delete it.  If I do not delete it, the gnomenu remains in the panel and works fine.  If I delete it it is removed from the panel.

Does anyone know why this error pops up or how I could fix it?

Thanks!

---

### Post by quispy on 2009-07-08
I got this error, too.

I'm posting the fix suggested in the README.txt file:

OAFIID ERROR:

The OAFIID error is not a GnoMenu bug... its a gnome-panel bug.
However Shaun Marolf found a workarround
If you get this error on system startup create a file containg a the code below and add the file to session startup

#!/bin/sh
# Trying a GnoMenu startup to clear OAFIID

case "$1" in
'start')
       GnoMenu.py
       ;;
'stop')
       ;;
*)
       echo "Usage: $0 { start | stop }"
       ;;
esac
exit 0

---

### Post by knipp21 on 2009-07-31
would you please be so kind as to tell us how to do this, im somewhat new to ubuntu. how do i add that to startup.

---

### Post by wotsit on 2009-08-12
You can do it this way -

gedit .gnomenu_start.sh

then copy and paste and save the file

then to make it executable for your user

chmod a+x .gnomenu_start.sh

then system>preferences>sessions>add

name it what you want, then in the command field, type in /home/username/.gnomenu_start.sh (where username is the name of your home directory)

But it doesnt seem to work for me. You may be able to delay it however, as the error appears to be since python is not fully loaded before the app starts. Or so the guru's say.

---

### Post by User_Name_Taken on 2009-08-18
Ya, I tried this and it worked until I powered my system down.  Once it booted back up, I received the same error again.  Really getting annoying now.  I just want it to work so I can make an OS image. 
Anyone else have ideas on how to get this to work and stay working?

---

### Post by knipp21 on 2009-08-21
thanks wotsit, this works well for me!

---

### Post by User_Name_Taken on 2009-08-22
well I'm glad it works for you knipp.  I'm still having problems.  Can someone help with it? Please?

---

### Post by abu salma on 2009-10-22
tank for your suggest that's look fine for me. :)

---

