---
title: "java"
date: 2006-04-13
forum: Desktop Environments
---

### Post by runefreak on 2006-04-13
where can i download java runtime enviornment?

---

### Post by fng on 2006-04-13
enable the multiverse repository

```
sudo apt-get update
sudo apt-get install j2re1.4
```

---

### Post by Sef on 2006-04-13
To enable the multiverse and universe repositories, follow the link below:

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by runefreak on 2006-04-14
ok i enabled the multiverse what do i do with that code?

---

### Post by fng on 2006-04-14
Open up a terminal : Applications -> Accessories -> Terminal
Copy/paste both lines (1 at a time and press enter) in the terminal 

```
sudo apt-get update
sudo apt-get install j2re1.4
```

The Java runtime is now installed.

---

### Post by Perfect Storm on 2006-04-15
If you want to run applications like Azureus it's advisable to use a Sun's own java.

[https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)

Or [http://ubuntuforums.org/showthread.php?t=76735&highlight=java](http://ubuntuforums.org/showthread.php?t=76735&highlight=java)

---

