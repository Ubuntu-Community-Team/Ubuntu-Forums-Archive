---
title: "Breezy No Login"
date: 2006-01-19
forum: Desktop Environments
---

### Post by jla on 2006-01-19
I was using Gnome and Kpackage manager and it froze up. I went to tty0 and tried to kill Kpackage, which it wouldn't let me do.Now it won't let me log back into a desktop. I tried startx and ^c Alt Backspace, ^c alt F7, plus the normal log in screen.It says that I don't have permission or something to that effect."home/jla/iceauthority" and 'could not start kmserver". Gnome was acting strange and didn't start the password dialog box for my root password when I went to use an administrative type program before this happened.How do I get my permissions back? (Failsafe os single user mode.) It does start a terminal fine.

---

### Post by stevea1210 on 2006-01-20
There is a bug in ubuntu where sometimes the permissions of ~/.ICEauthority get changed.  One of the main things that seems to cause it is when running a KDE app in Gnome using sudo.  

Drop to a console (ctrl-alt-F1) and type

```
rm .ICEauthority
```

Then go back to GDM (ctrl-alt-F7) and try logging in.

---

### Post by misconfiguration on 2007-04-27
> **stevea1210 said:**
> There is a bug in ubuntu where sometimes the permissions of ~/.ICEauthority get changed.  One of the main things that seems to cause it is when running a KDE app in Gnome using sudo.  

Drop to a console (ctrl-alt-F1) and type

```
rm .ICEauthority
```

Then go back to GDM (ctrl-alt-F7) and try logging in.

Thanks **stevea1210** this solved my issue quickly and efficiently!

---

