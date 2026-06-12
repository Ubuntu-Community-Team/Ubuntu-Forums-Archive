---
title: "running java game through shell script"
date: 2008-02-04
forum: Gaming &amp; Leisure
---

### Post by linux noooob on 2008-02-04
When i try to run moparscape with the shell script i get this error:
> # sh /home/andy/Desktop/pendrivestuff/runMoparScape-linux.sh
Exception in thread "main" java.lang.NoClassDefFoundError: Bot


And yes i am at full permissions (sudo)

so how can i fix this?

---

### Post by Vadi on 2008-02-04
That error has nothing to do with permissions. And tsk for running the program as sudo.

The program is bugged, email the author and let me know so they'll fix it.

---

### Post by linux noooob on 2008-02-05
meh i trust the makers of the software

---

### Post by linux noooob on 2008-02-05
after googling the error it says i have to add .; to a code but i can't find which one :confused:

---

### Post by SupaSonic on 2008-02-05
Find the line in the shell script which says
```
java <rest of the line>
```

Replace it with 
```
java -cp . <rest of the line>
```

That'll most probably fix your error

---

### Post by linux noooob on 2008-02-05
> bash: syntax error near unexpected token `newline'

I receive this error

---

### Post by linux noooob on 2008-02-05
The error is probably in the programming and i don't know anything i can use to edit the java file .class  in the program .jar file

---

### Post by frenchn00b on 2008-02-05
Isnt it java -e or jar - something ?
```
java --help 
jar --help
```

---

### Post by SupaSonic on 2008-02-06
It should be java -cp . -jar jarname

It's hard to help if I don't have the script.

---

### Post by aliayaz on 2008-06-23
it's actually very easy just install java runtime (not the mozilla plugin) and right-click the moparscape.jar and click run with java runtime x.xx

---

### Post by JudgeFudge on 2008-06-23
The process can't find the jar file. That is probably because the classpath hasn't been setup correctly in the script, or assumese you are in the same directory when you run it. I'm guessing (since you didn't post the script) that you may need to cd to the directory where the script is and invoke it from there. There is probably a jar file in the same directory and the classpath on the script likely usees the current directory.

---

