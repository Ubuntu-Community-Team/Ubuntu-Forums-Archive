---
title: "root terminal in jaunty"
date: 2009-05-09
forum: General Help
---

### Post by mosaic2s on 2009-05-09
when i click the icon to start root terminal in jaunty - the program appears for 5 seconds on the panel. then it disappears. gives no error - but does not appear.
any suggestions?

---

### Post by Panzor on 2009-05-09
Well, this certainly is a workaround, but I've never clicked the root terminal icon in my life, so I think it's just more of a good practice :P.

To get the equivalent of a root terminal, open up a regular terminal and type ```
sudo su -
``` and enter in the password you use to log on - not the root password that isn't even set by default in ubuntu (mine still isn't set >_>). "sudo" gives you superuser permissions to log in as root (where the "su" comes in), and the "-" keeps you in the current directory...I think, hold on. 

From the man page:  Provide an environment similar to what the user would expect had the user logged in directly.

Hmmm. It's just been such a habit to type that last '-' that I've forgotten why I do o_o. I'm not gonna stop cause then I suspect something I've been used to happening won't >_>. I won't tempt the Gods.

---

### Post by mosaic2s on 2009-05-09
THANKS for the tip.
In 8.04, I could use either as needed. will look at bug reporting.

---

### Post by irv on 2009-05-09
one added thing. When you are done using su just type:
```
exit
```
and you will go back to user mode.

---

