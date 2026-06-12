---
title: "can't execute binaries"
date: 2009-04-24
forum: General Help
---

### Post by canistel on 2009-04-24
I just upgraded to 9.04, but I can't execute any programs that I've installed anymore.

I have a directory like "/home/local/java/jdk1.6/", where /home is a different partition then / , and this /home partition was not formatted or anything during the install. 

If I try to execute any programs that I had installed under /home, I get "file not found", so for ex:

```
 /home/local/java/jdk1.6/bin/java -version
bash: /home/local/java/jdk1.6/bin/java: No such file or directory
```

... or ...

```
 /home/local/thunderbird/thunderbird
/home/local/thunderbird/run-mozilla.sh: 424: /home/local/thunderbird/thunderbird-bin: not found
```

It's not a permissions thing since I can't execute those programs as root either...

Those file locations are correct; I've been using the bash "tab" command to auto-complete the filename so the files are definitely there.

any ideas?

---

### Post by Monotoko on 2009-04-24
have you tried ```
chmod -x filename.bin
```?

---

### Post by canistel on 2009-04-24
> **Monotoko said:**
> have you tried ```
chmod -x filename.bin
```?


... you mean "+x" right (make it executable) ...

All the binary files are still executable from when I had 8.10 installed... if I do "ls -alsh | grep java" in the directory I get:

```
 48K -rwxr-xr-x  1 canistel canistel  47K 2009-04-07 16:28 java
```

... and if I do "chmod -x java" then try and execute I get "permission denied", so it's definitely not that.

This is very frustrating, the file is there, but bash says it isn't!

---

### Post by surryr on 2009-04-26
hi there.
I got same problem.
My solution was: numpud's symbol "&#8725;" differs from same symbol "/" on keyboard. Just dont use numpud :)

Sorry for my English.

---

