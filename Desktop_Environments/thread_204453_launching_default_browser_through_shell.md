---
title: "launching default browser through shell"
date: 2006-06-27
forum: Desktop Environments
---

### Post by rkakkar on 2006-06-27
i want to open a url using a default browser through the shell, on a remote machine. i have no idea as to what the default browser is.. so what is the command i should execute?

something like:

$ launch_default_browser [http://www.ubuntuforums.org](http://www.ubuntuforums.org)

---

### Post by userundefine on 2006-06-27
Install links, a terminal browser.

$ links [http://www.ubuntuforums.org](http://www.ubuntuforums.org)

---

### Post by rkakkar on 2006-06-27
nah.. i actually want to launch the GUI browser.. which could either be nautilus, konqueror or firefox or any other.

---

### Post by userundefine on 2006-06-27
Ah.

```
$ x-www-browser ubuntuforums.org
```

At least in gnome.

---

### Post by rkakkar on 2006-06-27
Thanks!

---

### Post by EddySanders on 2008-01-30
how do i install links the terminal browser?

---

### Post by Tenken on 2008-01-30
To install links, open a terminal and type:

```
sudo apt-get install links
```

---

