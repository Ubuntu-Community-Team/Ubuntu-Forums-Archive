---
title: "Where is the autostart folder on a LiveCD ?"
date: 2007-08-04
forum: Development CD/DVD Image Testing
---

### Post by booza on 2007-08-04
Hi everybody ,

where is the "autostart" folder on a live cd ? i want start firefox with my custom live cd , but i didn´t
found a autostart folder on the livecd ?

Greetz Booza :confused:

---

### Post by honeydew on 2008-06-18
I am also looking for something like this..  I am using remastersys to create the iso.. any ideas how I would autostart firefox on the livecd?

---

### Post by Fertech on 2008-06-21
look for something like this
in autorun.inf
[autorun]

open=start.exe

icon=ubuntu.ico

---

### Post by honeydew on 2008-06-24
hey thanks for looking into this for me fartech, however I am not looking to autostart things when in windows.  I am trying to figure out how the home folder of the liveuser is created during use of the liveCD this way I can edit the configurations it pulls these from.

---

### Post by Fertech on 2008-06-25
check this link for more info::[http://www.livecdlist.com/wiki/index.php/LiveCD_Creation_Resources](http://www.livecdlist.com/wiki/index.php/LiveCD_Creation_Resources)

---

### Post by honeydew on 2008-06-26
> **Fertech said:**
> check this link for more info::[http://www.livecdlist.com/wiki/index.php/LiveCD_Creation_Resources](http://www.livecdlist.com/wiki/index.php/LiveCD_Creation_Resources)



Thanks I found something that did the trick..    editing /usr/share/gnome/default.session and adding firefox to the list, allowed it to auto start firefox on the live cd.

---

