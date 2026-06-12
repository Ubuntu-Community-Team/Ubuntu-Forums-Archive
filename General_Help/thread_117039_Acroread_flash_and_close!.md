---
title: "Acroread flash and close?!"
date: 2006-01-14
forum: General Help
---

### Post by Dislimit on 2006-01-14
I've installed acroread7.0 with synaptic package manager. When opening, it always flashes and then close automaticly. I don't think wiki has included this problem.

---

### Post by aysiu on 2006-01-14
How did you install it?

---

### Post by Dislimit on 2006-01-14
[QUOTE=aysiu]How did you install it?[/QUOTE]
Sorry, just modified my post.

---

### Post by aysiu on 2006-01-14
Can you run the command ```
acroread
``` from the terminal and post the output of that... if any? Applications > Accessories > Terminal, and the type the command.

---

### Post by Dislimit on 2006-01-14
[QUOTE=aysiu]Can you run the command ```
acroread
``` from the terminal and post the output of that... if any? Applications > Accessories > Terminal, and the type the command.[/QUOTE]

Have done that before I post to ask for help. No error displayed. It just starts and quits like a flash.

---

### Post by aysiu on 2006-01-14
How about this?
```
mv ~/.adobe ~/.adobe_backup
acroread
```

---

### Post by Dislimit on 2006-01-14
[QUOTE=aysiu]How about this?
```
mv ~/.adobe ~/.adobe_backup
acroread
```[/QUOTE]
Result is the same...

---

### Post by aysiu on 2006-01-14
Hm.
Only thing I can think of is mark it for "complete uninstall" in Synaptic.
Then post your /etc/apt/sources.list so we can see where you're getting Acrobat Reader from...

P.S. You could also try creating a new user. If that user can open acroread and your user can't, maybe there's something wrong with your user account.

---

### Post by Dislimit on 2006-01-15
su root
acroread
Result is the same with my account.

su guest
acroread
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
(acroread:5290): Gtk-WARNING **: cannot open display:


My sources.list:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://ubuntu.cn99.com/ubuntu-cn/](http://ubuntu.cn99.com/ubuntu-cn/) breezy main restricted universe multiverse
deb [http://ubuntu.cn99.com/backports/](http://ubuntu.cn99.com/backports/) breezy-extras main restricted universe multiverse

---

### Post by aysiu on 2006-01-15
This may be a bit of overkill, but the first step backs up your current sources.list anyway--try uninstalling Acroread completely, then following the instructions in the first link in my signature and reinstalling it.

---

### Post by Dislimit on 2006-01-18
[QUOTE=aysiu]This may be a bit of overkill, but the first step backs up your current sources.list anyway--try uninstalling Acroread completely, then following the instructions in the first link in my signature and reinstalling it.[/QUOTE]
Have done ur instructions and reinstalled Acroread7.0. Problem remains the same. I have to use Gpdf instead right now though its functions r limited. Sb. says that Kpdf is better, is that true?

Btw, is that the problem of Ubuntu or Adobe?

---

### Post by aysiu on 2006-01-18
[QUOTE=Dislimit]
Btw, is that the problem of Ubuntu or Adobe?[/QUOTE] No idea, as I don't have that problem.

---

### Post by joumon on 2006-02-11
I have the same issue on my toshiba a75 laptop. I've faced this problem since I installed some packages. I guess it could be latex packages(I'm not pretty sure, but latex or dvi package was the package that caused this problem, I guess.). I tested acroread and didn't have any problem with it before installing some unknown packages. However, I don't want to remove latex-related packages. Anyway, did you resolve this issue? I couldn't find any thing on the web including wiki...

---

### Post by Thulemanden on 2006-02-14
I've got the same problem and installed via .gz downloaded from Adobe. There is no older version to get there. I am using the shipped cd's. Maybe it's not a problem for downloaded versions?

---

### Post by java8964 on 2006-05-03
I have the exactly same problem, and I don't think latex cause it since I don't have any latex package installed

---

