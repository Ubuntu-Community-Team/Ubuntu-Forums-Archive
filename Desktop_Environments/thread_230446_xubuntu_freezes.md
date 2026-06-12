---
title: "xubuntu freezes"
date: 2006-08-05
forum: Desktop Environments
---

### Post by zeropaid on 2006-08-05
Just finished installing the latest version of xubuntu and everthing runs smoothly except for it randomly freezes when i perform various tasks. 

xubuntu is running on IBM thinkpad X22 800 128m system.

Should i reinstall the OS?

Also, when I try to run admin tasks, it asks for a password, i enter the root password but that doens't work. What password should i use?

Please help a noob.
Thanks

---

### Post by hmagoo on 2006-08-06
hi, when it asks you for a password to run administration tasks you should enter your own user password that you logged on with.  The use of the root password or root identity is disabled by default, as far as I know.

as far as stability, I recall experiencing something like that (random lockups, etc) before upgrading to the final xubuntu 6.06 LTS version.  But, one of the first things I would check out would be heat developing in your computer or flaky components. You can also use the boot option from the Boot menu to test the memory to see if it develops any errors over the course of a couple of hours.

did you do a clean install from a xubuntu ISO, or from an existing gnome or KDE system.  Although many try to minimze the importance of desktops I think that may have also made a stability difference for me when I first started experimenting with XFCE.

---

### Post by K.Mandla on 2006-08-06
You might try removing powernowd. I have a couple of older laptops running Xubuntu and powernowd gives me all kinds of grief ... spotty touchpad operation, system skips, stutters, two- and three-second freezeups ... you name it.

I know there are ways to configure it properly, but I only ever use AC power, so scaling my processor isn't really necessary.

If you want to give it a whirl, you can remove it with ...

```
sudo aptitude remove powernowd
```

---

### Post by zeropaid on 2006-08-06
when i try to access the update manager i am prompted for a password, when i enter my user password, i get this message: "failed to run bla bla,  the underlying authentication mechanism does not allow you to run this program."

---

