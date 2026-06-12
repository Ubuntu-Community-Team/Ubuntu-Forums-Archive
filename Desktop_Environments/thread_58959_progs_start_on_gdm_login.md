---
title: "progs start on gdm login"
date: 2005-08-22
forum: Desktop Environments
---

### Post by cannibalbob on 2005-08-22
how can i make imwheel start automatically when i log in with gdm?
thanks, cannibalbob

---

### Post by adwait on 2005-08-22
Please use the search feature of the forum, or even read through the Wiki. 

Anyway, use System>Preferences>Session

---

### Post by cannibalbob on 2005-08-22
thanks. what if i'm using a window manager other than gnome?

---

### Post by adwait on 2005-08-22
Depends on which one you are using, there's gotta be a way anyway....

---

### Post by cannibalbob on 2005-09-01
ok i added 
imwheel -k -b "67" 

with order 50 to startup programs, but it doesnt work, still needs to be started manually..

---

### Post by Maier on 2005-09-01
Just tried adding a command..

system --> preferences --> sessions 

choose started programs (i guess the name is, im running .dk) 

add

write the command in the field (just tried with the default 50)

and ctrl+alt+backspace to check if it works... 

works like a charm here... rdesktop <computername> 

best regards

---

### Post by cannibalbob on 2005-09-01
yea i have other commands that work fine that way.. but not this one. maybe quotation marks.. i'll try some escape characters

---

### Post by Maier on 2005-09-01
Hope you figure it out, would be nice to know whats bugging you..  ;-) 

Btw. You dont need to run this command as root normally ?

---

### Post by cannibalbob on 2005-09-12
no, normal user is fine.

btw, it works if you remove the quotes around 67.

---

