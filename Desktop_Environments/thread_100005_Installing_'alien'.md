---
title: "Installing 'alien'"
date: 2005-12-06
forum: Desktop Environments
---

### Post by Rackerz on 2005-12-06
I have a LimeWire Pro rpm and i was told i need to convert it using alien. So im wondering how do i get alien and how do i use it? Im new so be gentle :)

---

### Post by Leif on 2005-12-06
alien should be pre-installed.

"sudo alien foo.rpm"
"sudo dpkg-i foo.deb"

---

### Post by Rackerz on 2005-12-06
sudo: alien: command not found

Im guessing it hasn't been installed.

---

### Post by Ampersand on 2005-12-06
sudo apt-get install alien

---

### Post by Rackerz on 2005-12-06
Thanks! Im just wondering were did LimeWire get installed too?

---

### Post by Leif on 2005-12-06
sorry about that, but I was quite sure alien was installed by default. did this get changed in breezy ?

---

### Post by ArmadaEnder on 2005-12-18
I running into a problem when trying to install alien:

E: dpkg was intrerrupted, you must manually run 'dpkg - - configure -a' to corrent the problem.

I'm sorry but I have no idea what this means. Anyone know what to do?

---

### Post by Leif on 2005-12-19
run "sudo dpkg -- configure -a" and try again

---

### Post by ArmadaEnder on 2005-12-19
Ah, it's working now, thank you so much.

---

### Post by stalefries on 2005-12-19
It should be installed by default. I don't think I've ever installed it, and I had it a while back when I was doing something or other.

---

### Post by Rackerz on 2005-12-19
It's no longer installed by default, you have to install it through Adept or the console. Also thanks to everyone who participated in this topic, I know what to do with (most) rpms now :).

---

