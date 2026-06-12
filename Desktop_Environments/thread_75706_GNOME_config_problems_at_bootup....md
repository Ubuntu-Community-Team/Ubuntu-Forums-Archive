---
title: "GNOME config problems at bootup..."
date: 2005-10-14
forum: Desktop Environments
---

### Post by koistar on 2005-10-14
Howdy,

   I've upgraded to Breezy on my old ibook. i'm posting this problem here because it seems to be GNOME related. here we go.

    GNOME fails to start with this message...

"The session you selected does not look valid.
Running the GNOME failsafe session instead"

   i click 'ok' and then i get...

"could not find the GNOME installation.  Running the failsafe xterm session instead"

   i click 'ok'

the xterm shell opens up... i tried apt-get install update/upgrade/dist-upgrade, etc.  to no avail.

   i 'exit' from the shell and the GNOME desktop manager opens with this message

"The configuration file contains an invalid command line for the login dialog.  So running the default command.  Please fix your configuration."

   Any suggestions welcome... i'm a novice at such things, and totally at a loss.  Thanks in advance!

   peace, koistar

---

### Post by koistar on 2005-10-15
Well I installed gnome from xterm, after running dpkg-reconfigure gnome and seeing that gnome was not installed on my machine?!

   sudo apt-get install gnome

   then added the gnome.desktop file as per the info contained here...

[http://lists.debian.org/debian-user/2004/04/msg01628.html](http://lists.debian.org/debian-user/2004/04/msg01628.html)

   now i can load up my desktop.. whew!  but when i go through the login process i still get an error message stating that i don't have GDM_failsafe.XTERM.desktop on my machine.

   i'll keep looking, but any help would be appreciated.

   peace, koistar

---

### Post by notepad on 2005-11-28
greetz koistar. i had the same problem with my machine. ive laboured for hours trying to find the answer and finally i fixed this annoying problem by going to
system > administration > login screen setup

in there you should setup a themed login screen. once youve done that press close and logout to check that it worked =o)

---

