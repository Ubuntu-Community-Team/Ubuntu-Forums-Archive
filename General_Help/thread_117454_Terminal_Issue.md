---
title: "Terminal Issue"
date: 2006-01-14
forum: General Help
---

### Post by Cade on 2006-01-14
i have been trying to run a program that i wrote and compiled on jGRASP but the terminal is unable to locate my java program. 

javac Hello.java
error: cannot read: Hello.java
1 error

i apologize if this is a dumb question. im super new to linux.

Cade

---

### Post by schilcha on 2006-01-15
I'll try to help, although I know as little about java as you probably know about linux:)
So, from the error message I can tell (by looking into my crystal ball) that the file Hello.java cannot be read by the compiler. So, either the permissions are screwed or something else is messed.
Try the command ```
ls -l Hello.java
``` in the directory, where you executed "javac Hello.java".
You'll get something like this:
> -rw-r--r--  1 schilcha users 383331 2006-01-14 20:46 Hello.java
First, look at the first column: does it have 3 r's in it? If so, my guess was wrong. If not, try ```
chmod a+r Hello.java
```This gives read permission to everyone for this file. (This might not work, if you're not the owner -- see below)

Secondly, look at the columns 3 and 4 -- the owning user and group. Is this you? If not try the command ```
chown YourUserName Hello.java
```
You might have to prepend "sudo" to this command, since stealing a file is not allowed. Only root may change ownerships.

BTW: There're no dumb questions, just stupid answers -- I hope this is not one of them :)

Good Luck!

---

