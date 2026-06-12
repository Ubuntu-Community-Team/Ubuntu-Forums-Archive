---
title: "Error Message ' Deskop Effects Could Not Be Enabled '"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by TombstoneX on 2008-02-18
Getting Error Message of " Deskop Effects Could Not Be Enabled ". 
Here is the output of the compiz command in terminal:

```
user@user-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:01d1 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "<Alt>Button1" found in configuration database is not a valid value for keybinding "begin_move"
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=60015&stc=1&d=1203348869[/IMG]

---

### Post by FuturePilot on 2008-02-18
What graphics card do you have?
```
lspci | grep VGA
```

---

### Post by chavanak on 2008-02-18
Ya give some info about your card before asking any question

---

### Post by TombstoneX on 2008-02-18
```
lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
```

I also have the restricted driver enabled. It stopped working only recently after an upgrade to the compiz. I am running Ubuntu 8.04 with all the latest updates.

---

### Post by chavanak on 2008-02-18
Mate you are on the alpha of hardy!!! The best thing you can do is downgrade compiz or wait for the next patch/release!!!! you can type in compiz in the terminal and post the output here...

---

### Post by TombstoneX on 2008-02-18
So basically just wait for more updates to come out.. nothing i can do.. i know its alpha, its just that it was working fine prior to the last update.

---

### Post by TombstoneX on 2008-02-21
Looks like the last set of updates fixed the issue.. sorry for the time wasting.

---

