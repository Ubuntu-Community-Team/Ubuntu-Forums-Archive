---
title: "Ktorrent locations"
date: 2008-12-29
forum: General Help
---

### Post by AryanAngel on 2008-12-29
I installed the Ktorrent package on ubuntu 8.4 via the add/remove apps program and now when I type Ktorrent into the terminal it tells me it isnt instaled which is ofc not true. I need to know how to run it because I want to add it to my session startup preferences.

---

### Post by ajgreeny on 2008-12-29
It's ktorrent, not Ktorrent.  All lower case. Try the full ```
ktorrent %i %m -caption "%c" %u
``` which is what is in my menu command.  You may find that ktorrent is there in your menu, but not showing until you edit the menu by right clicking on the menu button or bar.  Ktorrent should be in the *internet* section.

---

### Post by AryanAngel on 2008-12-29
I meant that I tried it in lowercase sorry for mistyping it here. I currently start it through the menu and editing it doesnt make a difference. It clearly has a name different that ktorrent.

---

### Post by linux_tech on 2008-12-29
Any clues in the log file?

---

### Post by snova on 2008-12-29
Running it as 'ktorrent' should work. What exactly are you typing?

---

### Post by oldos2er on 2008-12-29
> **AryanAngel said:**
> I meant that I tried it in lowercase sorry for mistyping it here. I currently start it through the menu and editing it doesnt make a difference. It clearly has a name different that ktorrent.

 Mine's /usr/bin/ktorrent

---

### Post by frenchn00b on 2008-12-29
> **AryanAngel said:**
> I meant that I tried it in lowercase sorry for mistyping it here. I currently start it through the menu and editing it doesnt make a difference. It clearly has a name different that ktorrent.

try to install : mc 
 
```
find /var -iname "*ktorrent*"
mc 
```
and go into this deb to see where is the ktorrent 


mine is :
```
$ whereis ktorrent
ktorrent: /usr/bin/ktorrent
```

otherwise 
```
cd /usr/bin
ls -la ktorrent
./ktorrent
```

---

### Post by AryanAngel on 2008-12-29
I've decided to remove the one via package installer and just use the one via sudo apt-get install ktorrent

thanks for replies

---

### Post by oldos2er on 2008-12-30
> **AryanAngel said:**
> I've decided to remove the one via package installer and just use the one via sudo apt-get install ktorrent

thanks for replies

 apt-get is the "package installer."

---

### Post by AryanAngel on 2008-12-30
> **oldos2er said:**
> apt-get is the "package installer." applications > add/remove is what i was referring to hotshot

---

### Post by snova on 2008-12-30
> **AryanAngel said:**
> applications > add/remove is what i was referring to hotshot

It's still the same thing...

---

### Post by oldos2er on 2008-12-30
> **AryanAngel said:**
> applications > add/remove is what i was referring to hotshot

 All the GUI package managers (Synaptic, Add/Remove) are front-ends for apt-get.
If you already installed ktorrent with one of Ubuntu's package managers, something's wrong if you don't have /usr/bin/ktorrent.

---

