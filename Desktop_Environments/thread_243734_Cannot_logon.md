---
title: "Cannot logon"
date: 2006-08-25
forum: Desktop Environments
---

### Post by kilps on 2006-08-25
Hi all - overnight I downloaded the latest Ubuntu updates, this morning when I restarted my computer (incidently due to trouble with FireFox loading) I found that when I typed in my correct login details the screen goes blank for a second or two displaying:
```
* Running local boot scripts (etc/.rc.local)
```
on the last line, before the login screen was just displayed again

I tried following the instructions for people who are having problems with the latest updates but it doesn't make a difference ](*,) 

Is there anything I can do here, or must I reinstall (please no!) - I can access the command line through a safe startup (or something like that, mabye it was recovery :confused: ) option from the bootloader...

thanks

---

### Post by Ziox on 2006-08-25
> **kilps said:**
> Hi all - overnight I downloaded the latest Ubuntu updates, this morning when I restarted my computer (incidently due to trouble with FireFox loading) I found that when I typed in my correct login details the screen goes blank for a second or two displaying:
```
* Running local boot scripts (etc/.rc.local)
```
on the last line, before the login screen was just displayed again

I tried following the instructions for people who are having problems with the latest updates but it doesn't make a difference ](*,) 

Is there anything I can do here, or must I reinstall (please no!) - I can access the command line through a safe startup (or something like that, mabye it was recovery :confused: ) option from the bootloader...

thanks

You can try reinstalling gdm:

```
sudo aptitude purge gdm && sudo aptitude install gdm
```

---

### Post by kilps on 2006-08-25
> **Ziox said:**
> You can try reinstalling gdm:

```
sudo aptitude purge gdm && sudo aptitude install gdm
```
Not working I am afraid :(

any other ideas? :( 

thanks

---

### Post by ohgod on 2006-08-25
Did you add any commands to rc.local that might be causing problems for you?  I believe rc.local is empty by default.

---

### Post by kilps on 2006-08-25
> **ohgod said:**
> Did you add any commands to rc.local that might be causing problems for you?  I believe rc.local is empty by default.
I'm not too sure what you mean by this, I am still getting into linux ... how do I check that?

btw I get the feeling that that last line I see is part of the boot process (although I wouldn't know) - because much of the other stuff seems to be boot stuff such as starting gnome, and there is always only one entry regardless of how many times i try to login

---

### Post by kilps on 2006-08-25
As an update, I am able to login in via the command line when i run 'login'

but it looks like I am going to have to go for a reinstall, bit of a pain - so it just means no system updates for me :(

---

### Post by Ares Drake on 2006-08-25
I got the same problem. Tried to reinstall xserver, no success though. Searching for the root, i found my sources.list to be messed up with breezy sources - maybe 'cause of EasyUbuntu or Automatix. I am reinstalling right now...

---

### Post by powerroot on 2007-12-27
I'm having the same problem. could you please share how you solved this problem? 
I reinstalled gdm but it didn't work. 

thanks,
js

---

### Post by powerroot on 2007-12-27
I think it was the problem with gdm. after I erased it, I could log in with my id and password. 

thanks,
js

---

