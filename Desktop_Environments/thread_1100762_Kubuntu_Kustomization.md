---
title: "Kubuntu Kustomization?"
date: 2009-03-19
forum: Desktop Environments
---

### Post by Steelfan555 on 2009-03-19
I recently followed [this]("http://ubuntuforums.org/showthread.php?t=856190")thread on how to customize Ubuntu, and loved it. A quick search on google shows nothing for Kubuntu, which i just installed a session. Could someone point me to or write a guide of how to customize Kubuntu?
Thanks in Advance
-Steel

---

### Post by cptr13 on 2009-03-19
which kde?  3.5, 4.1, or 4.2?

---

### Post by Steelfan555 on 2009-03-21
How can i tell? I just installed it two days ago, from synaptic, if that helps?

---

### Post by inobe on 2009-03-21
as for medi, i borked and installation and took quite some time to fix adept after adding the medi repo..... after all was fixed and adept stopped crashing lol's' i added the packages individually with wget.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

as for appearance' i searched **crystal** in adept and installed "kwin-style-crystal"

you can then go system settings> appearance> windows and change anything with existing themes or apply your own.

as for restricted extras

```
sudo apt-get install kubuntu-restricted-extras
```

that will take care of flash plugin etc......

i noticed installing kubuntu 8.10 from the live cd' firefox web browser wasn't installed !

so in terminal

```
sudo apt-get install firefox
```

i then had firefox

networking in kubuntu was quite different, i did not like setting up smb, i did it though' but i wont go there.

---

### Post by Steelfan555 on 2009-03-21
Dont understand Medi. I am running 4.1
I am about to try the rest of your suggestion, bt i have no need to install firefox, as i am already running Gnome.
I could not find crystal in adept. Edit: Its in symantic
If i already got the restricted extras in Gnome, i dont need them again, do i?
EDIT: Never mind this, im going back to Gnome.

---

### Post by inobe on 2009-03-21
that was a tip based on a clean kubuntu installation ...

even if you didn't ask for it' out of kindness i posted the info as a reference :)

but' my bad, i should have clarified that.

---

