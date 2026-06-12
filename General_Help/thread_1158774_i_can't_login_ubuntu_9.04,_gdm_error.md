---
title: "i can't login ubuntu 9.04, gdm error"
date: 2009-05-14
forum: General Help
---

### Post by ktakta on 2009-05-14
please help me this error
> 
There already appears to be an X server running on display :0. Should another display number by tried? Answering no will cause GDM to attempt starting the server on :0 again. )You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go console 7. X server usually run on consoles 7 and higher.)

---

### Post by Jive Turkey on 2009-05-14
You should press ctrl+alt+F1 all at the same time.  This will take you to a command prompt where you will need to enter your username and password.  Once you are logged in type ```
sudo /etc/init.d/gdm --restart && startx
```

That should restart gdm and then start the xserver (the graphical interface).

instead, you can also restart the xserver by pressing ctrl+alt+backspace.

---

### Post by ktakta on 2009-05-14
> **Jive Turkey said:**
> You should press ctrl+alt+F1 all at the same time.  This will take you to a command prompt where you will need to enter your username and password.  Once you are logged in type ```
sudo /etc/init.d/gdm --restart && startx
```

That should restart gdm and then start the xserver (the graphical interface).

instead, you can also restart the xserver by pressing ctrl+alt+backspace.

> 
Ubuntu 9.04 nguyenlong-laptop tty2
nguyenlong-laptop login: 
password

when i type above command, i can't login. It show up again.

---

