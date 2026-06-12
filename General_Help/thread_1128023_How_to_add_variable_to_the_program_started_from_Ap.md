---
title: "How to add variable to the program started from Application menu"
date: 2009-04-17
forum: General Help
---

### Post by abcuser on 2009-04-17
Hi,
on Ubuntu 8.10 using English locale I have installed KolourPaint program:
sudo apt-get install kolourpaint
sudo apt-get -y install kde-l10n-sl  # to get Slovenian language support

I see that from Application | Graphic | KolourPaint it is executed command:
kolourpaint %u

but I would like to start program with Slovenian translation (by the way I don't like to use Slovenian language for all environment, just for this program), so I can execute from Terminal:
LANG=sl_SI.UTF8 kolourpaint %u
so adding LANG variable at the front of the command.

But writing this command to Application menu "Command" field and running program from menu I get error:
*Could not launch menu item. Failed to execute child process "LANG=sl_SI.UTF8" (No such file or directory)*

Any idea how to add variable in menu?
Regards

---

### Post by sisco311 on 2009-04-17
try:
```
bash -c "LANG=sl_SI.UTF8 kolourpaint %u"
```

---

### Post by kpkeerthi on 2009-04-17
Or create a script and add shortcut to it in the menu.

---

### Post by abcuser on 2009-04-17
sisco311, thanks a lot. It works fine.

---

