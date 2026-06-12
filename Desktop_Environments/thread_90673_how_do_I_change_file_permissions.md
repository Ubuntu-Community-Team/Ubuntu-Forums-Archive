---
title: "how do I change file permissions ?"
date: 2005-11-15
forum: Desktop Environments
---

### Post by HarryMangurian on 2005-11-15
Firefox keeps giving me an error about not being able to get a .png file.
I tried to change permissions, but I can't change properties.  How do I do this ?
Is the a "sudo  ????  filename" I can use ?

[IMG]http://www.pbase.com/image/52309538.jpg[/IMG]

---

### Post by Leif on 2005-11-15
start nautilus with root privileges from the terminal : "gksudo nautilus"

then try again

---

### Post by lutrafobic on 2005-11-15
sudo chmod 777 $1 = Will give ALL right for everyone.
sudo chmod 755 $1 = Will give OWER ALL rights, rest Write/Execute.

sudo chmod 700 $1 = The way you have it now
(wich means that root can do anything, Everyone else can do NOTHING, not even read the file)

I would suggest that you use: 
sudo chmod 755 $1

Note:   $1 = filename.  If you mean all the files you can use *

Also, don't mess with the right to much without knowing what you do.

---

### Post by linbetwin on 2005-11-15
Wouldn't it be nice if you could tipe the root password somewhere in that Properties box so that you can change permissions by (un)checking those boxes?

---

### Post by Ruso on 2005-11-15
linbetwin this feature (or something similar) is realized in Kubuntu, and I persoanlly did not like it. You always can enable a root login in gdm properties "gdmsetup" to have the full access to your system.

---

