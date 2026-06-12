---
title: "Add Clear Recent History to panel"
date: 2008-03-16
forum: Desktop Environments
---

### Post by DarinB on 2008-03-16
can i add he clear recent documents to the panel or a drawwr

---

### Post by chewearn on 2008-03-17
Sure, you add a custom application launcher, with this command:
```
rm ~/.recently-used.xbel
```

Note:
~/.recently-used.xbel is the file which store the recent documents list.

---

### Post by DarinB on 2008-04-03
how do you add a launcher with a remove comand

---

### Post by chewearn on 2008-04-03
You right-click on the panel, select "Add to panel"; click on the "Custom Application Launcher" button.  Type in the command as described, except, I discovered you need to replace the tilda ~ with your home directory path.

```
rm /home/<user>/.recently-used.xbel
```

Replace <user> with your username.

---

### Post by DarinB on 2008-04-24
didn't work doesn't clear the recent docs

---

### Post by chewearn on 2008-04-24
Well then, I don't know what's wrong.

In my system, I permanently delete that file, and create a dummy subdir with the same name (to prevent the system from recreating the file again).  Thereafter, the Recent Documents is permanently disabled.

---

### Post by DarinB on 2008-04-24
how do i do that???

---

### Post by chewearn on 2008-04-24
> **DarinB said:**
> how do i do that???

Remove the history file:
```
rm ~/.recently-used.xbel
```Create a subdir:
```
mkdir ~/.recently-used.xbel
```

---

### Post by DarinB on 2008-04-24
should i use /home/darin?
is this reversible?

---

### Post by chewearn on 2008-04-24
When running the commands from terminal, ~ (tilda) is shortcut for your home directory.  To reverse it, simple remove the dummy subdir:

```
rmdir ~/.recently-used.xbel
```

---

### Post by DarinB on 2008-04-24
Works like a charm! THANK YOU
BTW where's the thank you button these days??

---

### Post by chewearn on 2008-04-24
> **DarinB said:**
> BTW where's the thank you button these days??

They upgraded the ubuntuforums software, still working on bringing back the "thank you" feature.

---

### Post by DarinB on 2008-04-24
well i guess you know that i am thankful
D

---

