---
title: "Trouble with Quake 2"
date: 2007-02-25
forum: Gaming &amp; Leisure
---

### Post by tronDB on 2007-02-25
Hello all. I'm pretty new to Ubuntu and Linux in general. Recently, I tried to install Quake 2. I followed the [Linux Quake Howto]("http://www.linuxdocs.org/HOWTOs/Quake-HOWTO-3.html") Quake 2 installation guide almost to the letter. Everything went fine until I tried to actually "run" it. The howto says to type "./quake2" while in the installation directory, but I immediately get an error: "bash: ./quake2: No such file or directory". Thing is, I KNOW the file exists because I'm looking at it right now (and I'm certain that I'm in the right directory); so what's going on?

Any help would be greatly appreciated.

---

### Post by Stemp on 2007-02-25
```
ls -l
```

---

### Post by tronDB on 2007-02-25
I thought it might be a permission problem myself, but for some reason I can't change them to execute for owner, even using chmod as sudo -i.

---

### Post by Stemp on 2007-02-25
Did you try **sudo chown tronDB:tronDB quake2** ?

---

### Post by tronDB on 2007-02-25
Just tried that and sudo chmod a+rwx  quake2. I'm getting the same message and quake2 doesn't even show up in ls anymore.

---

### Post by tronDB on 2007-02-26
Bump for replies?

---

