---
title: "Running GUI program through console command.... how do you disappear console window?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by NoTiG on 2006-09-24
say you wanted to run a program like sudo gedit ... and then the console stays  there.... but how do you run the program while closing that console immediately after the command ? or at least get a command prompt

---

### Post by croak77 on 2006-09-24
Alt-F2 gives you the GNOME run dialog.

---

### Post by fstab on 2006-09-24
```
sudo gedit &
```

will launch gedit and continue the command prompt.

---

### Post by aysiu on 2006-09-24
Alt-F2 and the ```
gksudo gedit
```

---

### Post by NoTiG on 2006-09-24
did my bad grammar attract you to this thread aysiu ? :P

PS. thanks for the tips

---

