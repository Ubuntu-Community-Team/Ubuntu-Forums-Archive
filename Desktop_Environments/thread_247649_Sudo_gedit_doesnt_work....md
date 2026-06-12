---
title: "Sudo gedit doesnt work..."
date: 2006-08-30
forum: Desktop Environments
---

### Post by NoTiG on 2006-08-30
anyone else not able to sudo gedit from console?  . just gedit works fine though.

---

### Post by mssever on 2006-08-30
What error message(s) do you get? Can you start other programs with sudo (for example, sudo nano)?


EDIT: just thought of something...for graphical programs, you should do either ```
sudo -v; sudo programname
``` or
```
gksudo programname
```

---

### Post by aysiu on 2006-08-31
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Still, even though *sudo gedit* isn't "correct," it should still work.

---

### Post by mssever on 2006-08-31
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Still, even though *sudo gedit* isn't "correct," it should still work.

Thanks for the tip. I didn't realize that sudo and gksudo had any differences other than the way they ask for passwords.

---

### Post by Atomic Dog on 2006-08-31
me neither, but it's good to have found out!

---

### Post by NoTiG on 2006-08-31
neither of those commands works for me....

notig@localhost:~$ sudo gedit
(nothing happens)
notig@localhost:~$ gksudo gedit

(gedit:18267): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
notig@localhost:~$

---

### Post by mssever on 2006-08-31
What happens if you type ```
sudo nano
```

---

### Post by NoTiG on 2006-08-31
sudo nano works........

---

### Post by missmoondog on 2006-08-31
i've noticed several apps that don't work out of the box by just clicking the icon or using sudo, since installing dapper. espeically kubuntu dapper.

it seems to help, if it's a new install of anything, to load it up using sudo first, then the icon in kmenu seems to work right.

---

### Post by mssever on 2006-08-31
> **NoTiG said:**
> sudo nano works........
What about ```
gksudo nautilus
```
In case you hadn't guessed already, I really don't know what the problem is; I'm just trying to narrow it down to find out if the problem is with gedit or sudo or something else...

---

### Post by fig_jam_uk on 2006-08-31
Hi just a quickie have you changed the permissions of the /usr/bin folder at all?

---

### Post by NoTiG on 2006-08-31
notig@localhost:~$ gksudo nautilus
(nautilus:10202): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

