---
title: "Running program at X windows startup"
date: 2007-10-04
forum: Desktop Environments
---

### Post by gaja on 2007-10-04
Hi Friends,

I want to run a program (X-windows) after the desktop is loaded in Ubuntu. I don't want to go $HOME/.config/autostart/. Instead, i want to control it by a script. This means that I want to put a entry to the session. Please help me out to solve this issue.

All comments are welcome.

Regards,
Gaja

---

### Post by renzokuken on 2007-10-04
create a bash script to launch the program then add that script to "startup sessions"

System - Preferences - Sessions

---

### Post by gaja on 2007-10-04
Thanks for your reply. Plz tell me where is the startup sessions file.

Regards,
Gaja

---

### Post by gaja on 2007-10-04
I don't want to set the startup program through System - Preferences - Sessions. I need to put entry to the configuration file where the startup programs are defined. So please tell me the configuration file where the startup programs are defined.

Regards,
Gaja

---

### Post by renzokuken on 2007-10-04
$HOME/.gnome2/session

....possibly, not really sure

---

### Post by undecidable on 2007-10-04
In kde you add the scripts to:
  ~/.kde/Autostart

According to [http://gentoo-wiki.com/HOWTO_Autostart_Programs](http://gentoo-wiki.com/HOWTO_Autostart_Programs)
you need to modify    ~/.gnome2/session-manual
though on my Ub 7.04 there is no such file,
it is instead called:
    ~/.gnome2/session

But, looks like a tricky file to edit. 
Also, one prog I added to autostart (tilda)
does not appear to be autostarted from here
(I dont know from where as I added it using the gui)
but another I added (brightside) is started from here.

---

