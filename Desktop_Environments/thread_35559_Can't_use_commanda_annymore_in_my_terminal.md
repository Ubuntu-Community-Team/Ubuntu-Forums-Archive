---
title: "Can't use commanda annymore in my terminal"
date: 2005-05-19
forum: Desktop Environments
---

### Post by darkdwarf13 on 2005-05-19
I changed some lines in sudo visudo on the wrong place and now i am getting the same error messages :

wouter@darkdwarf:~$ sudo visudo
Sorry, user wouter is not allowed to execute '/usr/sbin/visudo' as root on localhost.localdomain.
wouter@darkdwarf:~$

and i don't now how to change so please help me

---

### Post by poofyhairguy on 2005-05-19
Sorry I can't help really, but since I have never heard of that in my life I know this isn't a beginner question.

If fact, that seems to be a question that would be best answered on the IRC channel (but hopefully someone on the forum knows).

---

### Post by alastair on 2005-05-19
If you are locked out, the easiest thing to do might be to boot off a CD e.g. the LiveCD, Knoppix or something.

Mount your root partition somewhere, then revert your changes.

---

### Post by Stormy Eyes on 2005-05-19
[QUOTE=alastair]If you are locked out, the easiest thing to do might be to boot off a CD e.g. the LiveCD, Knoppix or something.

Mount your root partition somewhere, then revert your changes.[/QUOTE]

Alastair's right.

---

### Post by testingubuntu on 2005-05-19
ALT CNTL F1 

log in as root 

make your changes 

exit 

ALT CNTL F7

---

### Post by testingubuntu on 2005-05-19
ALT CNTL F1 

log in as root 

make changes 

exit 

ALT CNTL F7 

all done

---

### Post by Xian on 2005-05-19
You could try booting using the 'recovery mode' option in grub.
It should drop you into a root shell.

---

