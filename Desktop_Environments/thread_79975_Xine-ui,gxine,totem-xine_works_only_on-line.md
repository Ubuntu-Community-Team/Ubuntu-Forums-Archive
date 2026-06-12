---
title: "Xine-ui,gxine,totem-xine works only on-line"
date: 2005-10-21
forum: Desktop Environments
---

### Post by erbogasto on 2005-10-21
Hi everybodi,I've installed xine-ui,gxine and totem-xine(from universe/multiverse repos) with all the codecs (I had them perfectly working on Hoary,and actually on My Debian Sarge), and they perfectly work (divx,mp3,dvd ecc.) only if I'm on line (in internet) .
I use a dsl ethernet modem connection (pay for minute) so when I need connection $pon dsl-provider then $poff ,eth0 is automatically configured by dhcp with dynamic address at boot-time .
If I launch xine-ui gxine ... not on line they crash just after the bootsplah .
By comman-line the result is :

chicco@ubuntubox:~$ gxine
ERROR: Could not determine network interfaces, you must use a interfaces config line
chicco@ubuntubox:~$ xine
Questo Ã¨ Xine (X11 gui) - un riproduttore video libero v0.99.3.
(c) 2000-2004 Il team di Xine.
chicco@ubuntubox:~$ totem

(totem:9447): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:9447): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
ERROR: Could not determine network interfaces, you must use a interfaces config line

Where do I have to put this "interfaces config line" ?
I've tried reinstalling, purging,reconfiguring,on-line and not on-line, but the result is alwais the same ...xine... need an "interfaces config line" !!!

Can somebody help me please ?
Ciao Andrea from Italy :D

---

### Post by Nefarous on 2005-10-21
I've experienced the same behavior ... whenever I Control-C during boot up to skip network detection, and thus boot with no network interface.  Xine will not run.  It appears to have something to do with the fact that not even the "lo" interface is up in that situation.  I spent some time looking into it, but eventually just rebooted, and 
let my network timeout.  I'm guessing there is a simple work around.

Sorry I couldn't be of more help.

---

### Post by erbogasto on 2005-10-21
Thanks,I hope there is  someone who knows what to do to solve the problem.
Ciao Andrea :D

---

### Post by erbogasto on 2005-11-22
Hi everibody,I solved the problem, may be this helps someone else...
I simply changed my ip address from dynamic with dhcp ,to static ip address, and everything goes right its way.(I think there is a little bug in all this but don't really know where...)
Bye Andrea :p :p :p

---

