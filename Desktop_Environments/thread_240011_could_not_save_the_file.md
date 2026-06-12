---
title: "could not save the file ?????"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Mark_V on 2006-08-20
I've changed the /etc/apt/sources.list, but now i can't save it.
It says: 
- You do not have the permissions necessary to save the file.
- Please. check that you typed the location correctly and try 
- again.

I had this problem also with writing a unpacked program from my desktop to the /etc directory.
Further i cant change the write/read permissions in the file manager.

Hows that and what can i do to change it?

Please in Newbe language.. :-)

---

### Post by Iarwain ben-adar on 2006-08-20
Hi,
i think it's just because you don't act as a root...

Try 
```
kdesu kate /etc/apt/sources.list (for Kubuntu)
or gsudo gedit /etc/apt/sources.list (for Ubuntu)
```

Please note that i am not at my linux box atm, so i don't know for sure...


Iarwain

---

### Post by Mark_V on 2006-08-20
oke thx i will check it now

---

### Post by Mark_V on 2006-08-20
i'm using ubuntu desktop but it didn't work

This worked:

sudo gedit /etc/apt/sources.list

thx for the reaction.

How can i change the file/dir acces permission, because it isn't possibly through the system menu

---

### Post by Iarwain ben-adar on 2006-08-20
You shouldn't do that,
the permissions are there for a reason :D

Just using sudo is waaaay better than making it writeable for your user account. (Unless you know what you're doing, but still... )


Iarwain

---

### Post by Mark_V on 2006-08-20
oke but i dont know al the sudo commands, just been playing with ubuntu for 3 days.

If i get a application (tar package) en i unpack it on my desktop where do you set this program dir on my filesystem?

I tryed the /etc (most of the programs are there) but couldnt write to it, so now i write them to /opt/....

is this correct?

---

