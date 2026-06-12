---
title: "Problem with log out, suspend and hibernate functions"
date: 2009-03-11
forum: General Help
---

### Post by thermobee on 2009-03-11
Ok i have ATI Radeon 850XT and im pretty sure that is the problem, but i dont know how to fix it. The log out suspend and hibernate functions dont work. Also some times just before the log in screen i see my screen all messed up with different colours and it doesnt even get to the log in screen it just stops. All the problems result in the same thing as my screen is just black and nothing is happening.

---

### Post by thermobee on 2009-03-11
Help :)

---

### Post by mhgsys on 2009-03-11
I'm not absolutly sure if this also works for newer distro's but maybe it could help you

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by thermobee on 2009-03-11
> **mhgsys said:**
> I'm not absolutly sure if this also works for newer distro's but maybe it could help you

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
Thank you very much, i will try it out

---

### Post by thermobee on 2009-03-11
ok i did follow the guide and confirmed at the end that it works, but i still ahve the same problem

---

### Post by thermobee on 2009-03-11
anyone ever dealt with the same issue?

---

### Post by mhgsys on 2009-03-11
just a stupid guess.


Note: You could also edit your /usr/X11/xorg.conf file to change your driver to fglrx

---

### Post by thermobee on 2009-03-11
> **mhgsys said:**
> just a stupid guess.


Note: You could also edit your /usr/X11/xorg.conf file to change your driver to fglrx

how do i do that? and do you think it will fix the problem?

---

### Post by mhgsys on 2009-03-11
open a terminal.

typ: sudo nano /etc/X11/xorg.conf

Scroll down to section "Device" 

and change the "driver" to fglrx

hit ctrl+O to write out , press enter

then ctrl+X to exit

then type: sudo /etc/init.d/gdm restart 
to restart X again and see if it works.

(or hit ctrl+alt+backspace to restart X)

---

### Post by thermobee on 2009-03-11
> **mhgsys said:**
> open a terminal.

typ: sudo nano /etc/X11/xorg.conf

Scroll down to section "Device" 

and change the "driver" to fglrx

hit ctrl+O to write out , press enter

then ctrl+X to exit

then type: sudo /etc/init.d/gdm restart 
to restart X again and see if it works.

(or hit ctrl+alt+backspace to restart X)
it works Thank you for your help

---

### Post by mhgsys on 2009-03-11
great, 

enjoy your linux.

take a peek at compiz, just for fun.

---

