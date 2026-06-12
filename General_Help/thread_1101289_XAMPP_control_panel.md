---
title: "XAMPP control panel"
date: 2009-03-20
forum: General Help
---

### Post by oldcelt on 2009-03-20
I'm new to Ubuntu but I'm trying to set up my web development environment on this machine.  I've installed Xampp and it seems to be working fine.

My problem is that to start the control panel I have to open a terminal and type the command:
sudo /opt/lampp/share/xampp-control-panel/xampp-control-panel

I've tried to add this to the applications menu but without success.  How can I do this please?

Ken

---

### Post by oldcelt on 2009-03-22
Hello!  Am I alone in this forum?

---

### Post by igor. on 2009-03-22
Replace sudo with gksu. sudo is a command line application, you need to use gksu if you don't run the program in a shell.

---

### Post by oldcelt on 2009-03-23
Thanks a million - it's quite difficult to know about these esoteric commands when one is new to Linux.

---

### Post by tebuffer on 2009-06-15
Thanks a bunch.
It helped.

---

