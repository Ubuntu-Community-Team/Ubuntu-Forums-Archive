---
title: "How does Ubuntu know what to run?"
date: 2009-04-18
forum: General Help
---

### Post by r1ch on 2009-04-18
A slightly odd question...
When I type 'Firefox' or another program name into the terminal, how does Ubuntu know to run the correct application? Is there a list/database of program links, names and compiled program locations lying about somewhere?

Thankyou

---

### Post by matrixblue on 2009-04-18
As far as I know there is a $path listing directories with executable files and when you type in a command it looks at all those directories and runs the program with that name.

---

### Post by Aizawa on 2009-04-18
In usr/local/bin you have scripts. You run these by typing the name of it from ANY directory. If you want to add something manually, just put a script in /usr/local/bin, and you can run it by typing "name-goes-here-without-quotation-marks" from any directory :)

Hope that helped!


EDIT: I guess I was wrong, heh.

---

### Post by Simian Man on 2009-04-18
In a terminal type:
```

echo $PATH

```

You will see something like this:
```
/usr/lib/qt-3.3/bin:/usr/kerberos/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/simian/bin:.

```

Each section separated by a ':' is a different directory.  If your program is in any of those directories, it will be run.  It also searches in the PATH order so if you have two programs in your path with the same name, the first one will run.  You can see I added my own bin directory for scripts I write and also '.' so that I can always run programs from the current directory.  Hope that makes sense.

---

### Post by r1ch on 2009-04-18
That's great, thanks for your help everyone. 
And to think I've been keeping my own scripts in /home/random/directory/structure/pain/to/type/ , this will be very useful!

---

### Post by dcstar on 2009-04-18
> **r1ch said:**
> A slightly odd question...
When I type 'Firefox' or another program name into the terminal, how does Ubuntu know to run the correct application? Is there a list/database of program links, names and compiled program locations lying about somewhere?

Thankyou

```
locate *name*
whereis *command*
```

---

