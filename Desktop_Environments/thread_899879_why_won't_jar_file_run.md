---
title: "why won't jar file run ??"
date: 2008-08-24
forum: Desktop Environments
---

### Post by neill on 2008-08-24
hi

on my system

```
neill@ubuntu-desktop:~$ echo $PATH
/home/neill/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

and

```
neill@ubuntu-desktop:~/bin$ java -jar dirsyncpro.jar
```

works fine, but

```
neill@ubuntu-desktop:~$ java -jar dirsyncpro.jar
Unable to access jarfile dirsyncpro.jar
```

doesn't - why not if ~/bin is in the PATH

:confused:

am i being thick ???

---

### Post by txcrackers on 2008-08-25
The actual command (which is when $PATH gets searched and used) is "java". $PATH is not used for command-line parameters.

---

### Post by neill on 2008-08-25
so i symlink the java executable to my $PATH and that will work ?

where is said executable normally ?

ta

/neill

now you mention it that was me being thick BTW

:lolflag:

---

### Post by amo-ej1 on 2008-08-25
Try specifying ./dirscynpro.jar instead of dirsyncpro.jar and java will search for archives only if they're added to your $CLASSPATH variable, $PATH doesn't influence the search paths for java archives.

---

### Post by neill on 2008-08-25
actually now i look more closely java *is* symlinked to /usr/bin already, which is in the PATH

the link points to /etc/alternatives/java

there is also a folder /usr/share/java

now i'm confused *and* thick !

/neill

---

### Post by amo-ej1 on 2008-08-25
it's not the location of java which is  faulty, it's the location of the jar which is the problem. The error 'unable to access' is created by java. (And while you're at it, don't forget to check your permissions of the jar

---

### Post by neill on 2008-08-25
OK thanks

So ...

if the dirsyncpro.jar file is located at ~/bin what command do i issue at the CLI to run that jar *regardless* where in the filesystem i am at the time

(ie to avoid having to cd ~/bin every time)

---

### Post by amo-ej1 on 2008-08-25
Try 

java -jar ~/bin/dirsyncpro.jar

---

### Post by neill on 2008-08-25
Perfect - thank you 

:-)

---

### Post by ruturajpatil on 2009-08-26
hi ,

i am ruturaj

how run google talk.jar file 

Can you help me ?

Thanks. ... .... ... :confused:

---

### Post by Dullstar on 2009-08-26
Try

```
java -jar /path/to/desired/jar/file.jar
```

It worked when I had trouble installing Lemmini.  It was SOMETHING like the above code, anyways.  I believe there are directions for running Lemmini in Linux on the Lemmini web site that should work for any jar file as long as you make sure you point the OS to the file.

---

