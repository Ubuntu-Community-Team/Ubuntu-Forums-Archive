---
title: "trash wont empty"
date: 2009-03-09
forum: General Help
---

### Post by libihero on 2009-03-09
i was trying to delete a 4 gig file in my trash, and in the middle of the deletion i accidently interrupted it.  now every time i try to delete it, it says "error in deletion"

---

### Post by taurus on 2009-03-09
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~/.local/share/Trash/files
```

---

### Post by scphan on 2009-03-09
uh oh, it still see there's trash to be cleaned out, must be a way

---

### Post by Neo_The_User on 2009-03-09
gksudo nautilus or sudo rm -rf (drag all trash items here)

---

### Post by Jimmynemo2 on 2009-03-09
Just cuase I am not aware, what is GKsudo as opposed to sudo?

---

### Post by pennacook on 2009-03-09
gksudo:  GTK+ frontend for su and sudo

---

### Post by Jimmynemo2 on 2009-03-09
ah, ok thanks. So I should use GKsudo for any gtk+ program?

---

### Post by pennacook on 2009-03-09
The primary purpose is to run graphical commands that need root without  the need to run an X terminal emulator and using sudo directly.

---

### Post by Seq on 2009-03-09
> **pennacook said:**
> The primary purpose is to run graphical commands that need root without  the need to run an X terminal emulator and using sudo directly.

It also sets up the environment a little bit differently than sudo so you won't have things like ~/.ICEauthority being owned by root.

You should always use gksudo when running a graphical application as root.

---

### Post by Jimmynemo2 on 2009-03-09
awesome, thank you both very much.

---

### Post by libihero on 2009-03-10
this was my output:
hamza@Hamza-laptop:~$ ls -la ~/.local/share/Trash/files
total 24
drwx------ 4 hamza hamza 12288 2009-03-09 22:36 .
drwx------ 4 hamza hamza  4096 2009-01-21 14:52 ..
drwx------ 5 hamza hamza  4096 2009-03-09 14:06 backup
drwx------ 3 hamza hamza  4096 2009-03-09 09:17 libya docs

i tried gksudo nautilus and sudo rm -rf but neither would work

---

