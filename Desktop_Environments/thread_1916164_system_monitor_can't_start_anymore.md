---
title: "system monitor can't start anymore"
date: 2012-01-27
forum: Desktop Environments
---

### Post by Hreinsi on 2012-01-27
Recenly I noticed that system monitor can't start anymore. Anyone had this prob tryed reinstall no luck
ubuntu 11.10 64 bit

---

### Post by sudodus on 2012-01-27
Maybe you can use htop until it is up and running again?

```
sudo apt-get install htop
```

---

### Post by Hreinsi on 2012-01-27
> **sudodus said:**
> Maybe you can use htop until it is up and running again?

```
sudo apt-get install htop
```

will try that thanks

---

### Post by raja.genupula on 2012-01-27
whats its giving you when you trying to launch from terminal

```
gnome-system-monitor
```

---

### Post by Hreinsi on 2012-01-27
> **raja.genupula said:**
> whats its giving you when you trying to launch from terminal

```
gnome-system-monitor
```

ERROR:proctable.cpp:134:void proctable_set_columns_order(GtkTreeView*, GSList*): assertion failed: (id >= 0 && id < NUM_COLUMNS)
Aborted

---

### Post by Hreinsi on 2012-01-27
> **Hreinsi said:**
> ERROR:proctable.cpp:134:void proctable_set_columns_order(GtkTreeView*, GSList*): assertion failed: (id >= 0 && id < NUM_COLUMNS)
Aborted
 there are some bug reports here
[http://ubuntu.5.n6.nabble.com/Bug-700900-Re-Some-applications-crash-system-monitor-td4335688.html](http://ubuntu.5.n6.nabble.com/Bug-700900-Re-Some-applications-crash-system-monitor-td4335688.html)


[http://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg68887.html](http://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg68887.html)

dont have searchmonkey

---

### Post by Hreinsi on 2012-01-27
now it working in terminal sudo gnome-system-monitor but still cant launch

but geting this message

** (gnome-system-monitor:20978): WARNING **: SELinux was found but is not enabled.

---

### Post by Hreinsi on 2012-01-27
Just gona wait for bug fix so marking thi solved until ?

---

### Post by raja.genupula on 2012-01-28
what i know is sometimes BUGS like this can be fixed by new kernel updates . So please be patient until that . 

Thank you :)

---

### Post by Hreinsi on 2012-01-29
> **raja.genupula said:**
> what i know is sometimes BUGS like this can be fixed by new kernel updates . So please be patient until that . 

Thank you :)

Got new kernel update didnt fixit so i deleted some files in home witch is seperate from system, most of them and did fresh install its up and running no probs :)

---

