---
title: "xubuntu with japanese but without gnome"
date: 2006-06-25
forum: Desktop Environments
---

### Post by dmizer on 2006-06-25
i have a computer i'm working on for a special needs community in japan.

it's an ancient (500mhz pii) nec desktop that was running win98, but because it's regular users don't have the cognitive ability to use discretionary browsing (though this doesn't appear to be an affliction limited to the special needs community), it was full of bugs.

i was able to get xfce up and running with japanese support enabled, but gnome came along with it.  is there any way to get full japanese support without installing gnome?

i've searched around the ubuntulinux.jp site, but i couldn't find much on xfce.

also, firefox doesn't have japanese in the program menus ... is there a way to fix this?

---

### Post by dmizer on 2006-06-26
got it fixed by installing the rest of the japanese packages on restart via the language support option in the xfce menu.

---

### Post by hanzj on 2006-08-03
dmizer,
1) How did you first get Japanese language support, if not via Applications/System/Language Support?

2) I'm a bit confused between the roles of "Language Support" in System and
"SCIM Input Method Setup" in Settings. What do they do?  How do they differ?

---

### Post by dmizer on 2006-08-11
hanzj, hope this isn't too late to be of help to you but i just now noticed your reply.

to install japanese support initially, i just searched for "japanese" in synaptic and installed what i remembered to be the appropriate packages.

the difference between the language support option and the scim input method setup is that the language support option configures the overall system such that you can log in with japanese program menus or english program menus or whatever other language menus you so desire.  this provides you with 100% language viewability support.

the scim input method setup allows you to configure the options available to type in the language desired.  so, you can type in japanese in your english environment or in english in your japanese environment.

---

### Post by dolby on 2006-08-11
[this](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Chinese_Input_Method_.28SCIM.29) probably solves it

---

