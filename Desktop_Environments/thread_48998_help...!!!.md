---
title: "help...!!!"
date: 2005-07-14
forum: Desktop Environments
---

### Post by thancarlos on 2005-07-14
hi.. im trying to install ubunto in a  p2 400 mhz  proccesser but my mouse seems to be dead........

it doesn´t recognize it-.....  what can i do??

---

### Post by alastair on 2005-07-14
Are you sure it isn't just sleeping? :-)

Anyway ... details would help. What type of mouse? serial? PS/2?
Have you tried another mouse?

Check the logs :

/var/log/syslog
/var/log/Xorg.0.log

---

### Post by Nikola Kasabov on 2005-07-14
I had same problem and made howto into the wiki. But it is in bulgarian and for mouse connected on COM1!
Here is the link - [https://wiki.ubuntu.com/BulgarianDocumentation/COM_mouse](https://wiki.ubuntu.com/BulgarianDocumentation/COM_mouse)
Just follow the commands and ask if there is a problem with the understanding - just open /etc/X11/xorg.conf and edit the mouse section the same way.
Point 3 the original section, point 4,5 the changes.

---

