---
title: "Forgotten Ununtu Login details"
date: 2009-03-21
forum: General Help
---

### Post by Bazman on 2009-03-21
Hi there,

I have forgotten my Ubuntu log-in details!

I am the administrator!! Is there anything I can do?

Baz

---

### Post by mhgsys on 2009-03-21
Type 

```
passwd <username>. 
```
Set your password.

 .
* don't type in the < 
*replace username with your username

reboot

---

### Post by Bazman on 2009-03-23
Hi thanks for that,

But I don;t know my username or password and I cannot log in at all.

Can you please explain further.

---

### Post by Lunx on 2009-03-23
Not sure this helps much, but if you have all your data backed up you could do a reinstall and set up a new username and password (and then write it down so you don't forget it!!!)

---

### Post by Bazman on 2009-03-23
Well that was the option I was hoping to avoid.

Its a dual boot PC. 

Is it possible to just format the Ubuntu part, and reinstall?

---

### Post by stevoo on 2009-03-23
[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

Not sure if this still works !

---

### Post by SteelWo1f on 2009-03-23
This is never a fun situation. To fix it, I would put in a live cd to load up ubuntu. Then mount your / partition and you should be able to su into it. If you don't have access to root, you can change your sudoers file on the hard drive before you su so that you don't need a password to login as root. Once you are in as root you can set the password for your main account. Then cleanup the sudoers file when you are done.

I know this is kind of tricky, but something along these lines is usually what you have to do.

---

### Post by drs305 on 2009-03-23
Can you boot to the recovery mode? If so, select "drop to root shell" and then:
```
ls /home
```
That should display the /home folders for all the users. If you recognize your username you can then use the previously mentioned "passwd *username*", using your username, to reset the password.

---

### Post by Bazman on 2009-03-23
> **drs305 said:**
> Can you boot to the recovery mode? If so, select "drop to root shell" and then:
```
ls /home
```
That should display the /home folders for all the users. If you recognize your username you can then use the previously mentioned "passwd *username*", using your username, to reset the password.

ah that did it.

Thank you thank you thank you!!!

Thanks to all of you I really appreciate your help

---

