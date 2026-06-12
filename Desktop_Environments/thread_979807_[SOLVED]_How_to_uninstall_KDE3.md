---
title: "[SOLVED] How to uninstall KDE3"
date: 2008-11-12
forum: Desktop Environments
---

### Post by balagod on 2008-11-12
Hai,
I installed KDE4.1 . its nice. But in all applications i have 2 versions
one for kde3 another one kde4.
i want to remove all KDE3 applications and KDE3 also.

so i need only KDE4 in my system how can i do that?

Please give corresponding apt commands.

---

### Post by pPrdrm on 2008-11-12
I don't understand what exactly happened. You said you've installed KDE 4.1. How exactly have you done that. And by saying that you want to remove KDE 3 do you mean that you can login to KDE 3 or KDE 4.1 separately? If not, i think that KDE 4.1 merged with your previous KDE 3 installation and kept your preferences. Try to create a new user account. Does it also have double entries of your apps?

---

### Post by aged hippy on 2008-11-12
How did you install Kubuntu in the first place?

It looks as though maybe you installed Hardy (KDE 3.5 / KDE 4.0) and upgraded.

Is this the case?

---

### Post by dentaku65 on 2008-11-13
See here for kde3 on Itrepid:
[http://ubuntuforums.org/showthread.php?t=963695](http://ubuntuforums.org/showthread.php?t=963695)
:KS

---

### Post by balagod on 2008-11-16
Hi,
thanks for your replies.
I installed KDE4 upgrade method
sudo apt-get install kubuntu-kde4
sudo apt-get update
sudo apt-get dist-upgrade

what i want is i have KDE3 & KDE4.1, i want to uninstall KDE3 and it's applications only.
because if i login with KDE4 i am getting KDE3& KDE4 applications
(example : cvs-Frontend,CVS-Frontend-KDE4....)

---

### Post by GameManK on 2008-11-16
Just removing kubuntu-desktop probably won't grab the dependencies so you might need to just go through and remove the applications that are bothering you.  See aptitude show kubuntu-desktop for a list of the packages included by default in kubuntu.  If you go through and remove the major stuff like konqueror that should grab the other stuff to remove that depend on them, hopefully.

That said, if you prefer KDE4, you're best off upgrading to Intrepid.

---

### Post by balagod on 2008-11-16
so i need to use add/remove programs to get this one.
ok, Thank you.

---

