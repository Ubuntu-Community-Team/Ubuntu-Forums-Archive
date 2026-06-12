---
title: "dons save lest session!!!"
date: 2005-11-08
forum: Desktop Environments
---

### Post by erez1012 on 2005-11-08
when i log in to xfce there is amessege
your $home/.dmrc file has incorrect permission 


i change the permision and its do this messege another time
thanks

---

### Post by Who on 2005-11-08
Can you say what it is you actually want to know? Then you are more likely to get some help :)

---

### Post by eyebrowman92 on 2005-11-08
by the looks of the title it seems you want to not save the session when you logout. when you press the quit button uncheck the save session button.

---

### Post by erez1012 on 2005-11-08
this is the full eror:
your$home/.dmrc file is oncorrect permision and is begin ignored.
this prevents the default session and language from being saved.
file sould be owned by user and have 644 permisions.

---

### Post by Who on 2005-11-09
Hi, this is just an off chance suggestion:
If you open nautilus as a root user ($ sudo nautilus --no-deskop --browser), then enable the showing of hidden files, and then rename the file $home/.dmrc to /.dmrc_BACKUP, you may find that next time you login xfce creates the file again with correct permissions. 
----I don't know exactly what this file does, which is why I have suggested you back it up rather than deleteing it. I _guess_ that if you are supposed to have permisiion to edit it but don't then it can't be doing a whole lot. The fact that XFCE doesn't seem to be able to use it suggests to me that it doesn't really matter whether it is there ot not BUT I could _well_ be wrong. If you find that things don't work without it then you can simply put the old file back.-----

HTH
Who

---

### Post by erez1012 on 2005-11-09
its dont work!!!

---

### Post by Who on 2005-11-09
So, even when the file doesn't exist, you still get the message that it has the wrong permissions? 
Does XFCE create a new file with the same name?
Have you tried creating an 'empty file' with the same name and the right permissions? If not, pls post results
Have you tried using synaptic to 'reinstall' the packages related to the problem (namely XFCE)?

What exactly doesn't work?

---

### Post by erez1012 on 2005-11-09
i done all and its dont work
after i move the file it do the same thing:(

---

