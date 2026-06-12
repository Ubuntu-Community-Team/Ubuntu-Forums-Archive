---
title: "Open .rar files"
date: 2009-01-31
forum: General Help
---

### Post by DeadRobot on 2009-01-31
I want to open a .rar file.

I installed unrar.

I have the rar file on my desktop.

I went to terminal and typed cd Desktop and unrar [filename].  It listed each file in the .rar and said failed next to each one. 

How do I get it to work?

---

### Post by binbash on 2009-01-31
unrar e filename

---

### Post by jocko on 2009-01-31
Have you tried double-clicking the file?
Or right-click it and select "extract here"
Otherwise, if you can't extract it with unrar installed, perhaps the file is corrupt?

---

### Post by Bablefish on 2009-01-31
7zip works for me and you can get it in add/remove

---

### Post by taurus on 2009-01-31
```
unrar x filename.rar
```

---

### Post by DeadRobot on 2009-01-31
I tried extract here but it just made an empty folder with the same filename.

unrar x filename doesnt work.
neither does unrar e filename.
both just list the files and say "failed".


And the file is not corrupt.  Its done the same thing with 3 other .rar files.

---

### Post by Tomatz on 2009-01-31
Open a terminal and type:

```
sudo apt-get install rar unrar
```

**Logout and log back in**

Now you will be able to add a file to a rar archive by either **r-clicking on the file and clicking "add to archive"** or by using file roller. You can extract the same way too.

---

### Post by DeadRobot on 2009-01-31
> **Tomatz said:**
> Open a terminal and type:

```
sudo apt-get install rar unrar
```

**Logout and log back in**

Now you will be able to add a file to a rar archive by either **r-clicking on the file and clicking "add to archive"** or by using file roller. You can extract the same way too.

Thanks, it works now! ;):D

---

### Post by Udibuntu on 2009-02-01
> **Tomatz said:**
> Open a terminal and type:

```
sudo apt-get install rar unrar
```

**Logout and log back in**

Now you will be able to add a file to a rar archive by either **r-clicking on the file and clicking "add to archive"** or by using file roller. You can extract the same way too.

Thanks, worked for me also (R-clicking and extracting).

Udi

---

