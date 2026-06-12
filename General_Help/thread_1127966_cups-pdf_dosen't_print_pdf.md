---
title: "cups-pdf dosen't print pdf"
date: 2009-04-17
forum: General Help
---

### Post by sam1948 on 2009-04-17
**_first_**: make sure u have folder called PDF in u'r home folder
if not make one and try it

**_second_**: open terminal and type
```
sudo chmod 777 /home/U'r_userName/PDF
``` 
obviously replace U'r_userName with u'r user name
try it

**_third_**: many thanks for  [_[COLOR="Blue"]Eric[/COLOR]_]("https://bugs.launchpad.net/~ubuntu-zorglub")
who brought [_[COLOR="Blue"]this solution[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/295536/comments/30")

> 

I'm pretty sure that it's not a bug in cups-pdf but a bug in the AppArmor configuration for cups-pdf.

Workaround (and proof that it's an AppArmor configuration issue):

open the file /etc/apparmor.d/usr.sbin.cupsd

and edit the line:
    /usr/lib/cups/backend/cups-pdf {
in order to get:
    /usr/lib/cups/backend/cups-pdf flags=(complain) {

restart AppArmor with 'sudo /etc/init.d/apparmor restart'

CUPS-PDF works again, QED!

As far as I understand it, the workaround removes the protection around cups-pdf, someone with more knowledge can probably fix the config file in a more sensitive manner.

As the file /etc/apparmor.d/usr.sbin.cupsd comes with the 'cups' package, this bug should be reassigned.

Hope this helps, Eric


---

