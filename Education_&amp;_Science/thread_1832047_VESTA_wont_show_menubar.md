---
title: "VESTA wont show menubar"
date: 2011-08-24
forum: Education &amp; Science
---

### Post by mErchamion on 2011-08-24
Hi everybody! I have been trying to run vesta ([http://www.geocities.jp/kmo_mma/crystal/en/vesta.html](http://www.geocities.jp/kmo_mma/crystal/en/vesta.html)) on my laptop, ubuntu natty. At the moment I have been able to run the latest version, but surprisingly, no menu bar is  shown, nor even the vertical toolbar. I have no clue what could be going on, so I will appreciate any suggestions. I will also be thankfull if any of you can point me to a vesta/visualization software forum!

---

### Post by mErchamion on 2011-08-27
Ok, this is the most weird thing I have ever seen. If I open the program via ssh to my own computer, the menubar and toolbar show correctly. I mean,
ssh -X myuser@myhost ' vesta '

and the program works great! 

I have been able to reproduce the problem (and the patch/solution) in two different computers, both running ubuntu natty, one is my laptop and the other is a desktop with a fresh install!

please help!

---

### Post by mErchamion on 2011-10-05
Ok, nobody interested, but just for the record...
Right now, I am pretty sure it has something to do with locale. I realized that (for some reason) my ssh session locale was different than my gnome-terminal locale (maybe something to do with login - nonlogin session?) So I tried the following:
export LANG=en_US.utf8 && <PATH_TO>/VESTA
and everything works flawlessly, even on a fresh OS install and after reproducing the bug.
for the record, too, VESTA roks! :guitar:

---

