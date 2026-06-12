---
title: "screensaver lock does'nt recognize my password"
date: 2005-12-21
forum: General Help
---

### Post by lucascr on 2005-12-21
Hi all,
I'm an happy kubuntu 5.10 user, but lately I have the following problem: when the screensaver lock the screen and to reactivate it you must provide the password, then the passaword is not recognized. Of course, the password is correct. So, the only thing I can do is to open a new session and kill the application, or alt-ctr-backspace and re-open the session from kdm. 
Has anyone faced this problem? Many thanks for any hint.
Luca

---

### Post by 23meg on 2005-12-21
Do you have password problems in other places, such as while running administrative apps or using sudo in the command line?

---

### Post by jferrando on 2005-12-21
I had this same problem when I modified some files /etc/pam.d directory for use of my ldap server. After restoring them to appropiate values, it worked again.
It was courious, because when I had that miss-configuration I could log into kde, but I could not change the user's password form the command line
$ passwd
... some error

---

### Post by lucascr on 2005-12-22
I have no other problem with the password, it works in kdm, ok with sudo and what else... I haven't checked with passwd but I'll do it and let you know. 
Thanks for the reply.
Luca

---

### Post by tauruswho on 2005-12-22
This worked for me:---

[http://www.ubuntuforums.org/showthread.php?t=105071](http://www.ubuntuforums.org/showthread.php?t=105071)

:)

---

