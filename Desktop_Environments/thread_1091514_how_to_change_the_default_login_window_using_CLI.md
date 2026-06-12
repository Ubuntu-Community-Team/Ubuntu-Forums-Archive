---
title: "how to change the default login window using CLI?"
date: 2009-03-09
forum: Desktop Environments
---

### Post by jestinjoy on 2009-03-09
I am using ubuntu 8.10. How to change the default login/logout window using command line.? Can gconftool -2 can be used to change it?

---

### Post by bluefrog on 2009-03-09
/etc/gdm/gdm.conf
GtkTheme

---

### Post by jestinjoy on 2009-03-10
I tried changing the the login window by editing the file gdm.conf. But when logging in it shows "cant open circles.xml". Circle is the login window theme I selected. After that it loads properly. How is it so?

---

### Post by mobinskariya on 2009-03-10
In ubuntu 8.10, it uses the file /etc/gdm/gdm.conf-custom instead of /etc/gdm/gdm.conf. Edit it and restart the gdm. For more info just refer the above mentioned file.

---

### Post by jestinjoy on 2009-03-10
Thanks.......It worked

---

