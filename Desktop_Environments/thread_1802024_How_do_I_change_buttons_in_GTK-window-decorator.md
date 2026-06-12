---
title: "How do I change buttons in GTK-window-decorator?"
date: 2011-07-11
forum: Desktop Environments
---

### Post by Mortesins93 on 2011-07-11
Hello,
I have an Xubuntu 11.04 installation with compiz and GTK-window-decorator, how do I change the window buttons because there is no gconf in Xubuntu?

---

### Post by Toz on 2011-07-11
Do you mean the location and type of button? If so, see: [http://ubuntuforums.org/showthread.php?t=1704596]("http://ubuntuforums.org/showthread.php?t=1704596")

Or do mean the actual graphic of the button?

---

### Post by Mortesins93 on 2011-07-12
I mean the actual graphics.

---

### Post by Toz on 2011-07-12
Just change the Window Manager theme (Settings->Window Manager)? Is that what you mean, or are you talking about creating your own or editing and existing theme?

---

### Post by Mortesins93 on 2011-07-13
I've tried that but it doesn't change the buttons. I have compiz enabled and have GTK as the window decorator and whatever theme I choose I always have the same buttons which I don't like. I'll send a picture when I can to explain better.

---

### Post by Toz on 2011-07-13
Looks like you need emerald installed (see: [http://ubuntuforums.org/showthread.php?t=1738868]("http://ubuntuforums.org/showthread.php?t=1738868")). Unfortunately, there is an issue with getting emerald to work in xfce. However, it looks like a fix has been found ([http://ubuntuforums.org/showpost.php?p=10757398&postcount=11]("http://ubuntuforums.org/showpost.php?p=10757398&postcount=11"))

---

### Post by DoubleClicker on 2011-07-13
This may sound counter-intuitive,  but if you are using Compiz with GTK-window-decorator.  You want to change the Metacity settings in gconf.  Iif you have GNOME installed, you can uses the gnome-appearance-properties  application.

---

### Post by Mortesins93 on 2011-07-14
I don't want to use emerald and I don't have GNOME installed. I cannot believe there is no way to change GTK-window-decorator without GNOME installed.

---

### Post by DoubleClicker on 2011-07-14
> **Mortesins93 said:**
> I don't want to use emerald and I don't have GNOME installed. I cannot believe there is no way to change GTK-window-decorator without GNOME installed.

The suggestion I gave above will still work without gnome, you will just have to use gconf-editor to make the change.

---

### Post by Toz on 2011-07-14
Have a look here as well: [http://ubuntuforums.org/showpost.php?p=10936111&postcount=19]("http://ubuntuforums.org/showpost.php?p=10936111&postcount=19")

---

### Post by Mortesins93 on 2011-07-15
Ok, so I solved it by installing gconf-editor. Thanks I did not know that I could only install it without installing GNOME.

---

