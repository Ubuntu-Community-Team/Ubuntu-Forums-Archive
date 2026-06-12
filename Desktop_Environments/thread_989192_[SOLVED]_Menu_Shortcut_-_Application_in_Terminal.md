---
title: "[SOLVED] Menu Shortcut - Application in Terminal"
date: 2008-11-21
forum: Desktop Environments
---

### Post by uppercrustie on 2008-11-21
Hello,
n00b here. Right first of all thank you to the Ubuntu community for making this possible. Just switched from windzzzzzz and can't believe it took me so long to ditch the lame OS. I like Ubuntu, I like the open source philosophy, I like the forums, I like the tongue-in-cheeckness of it all as opposed to the tedious smuttering of corporate sobriety of Macs and Windzz. So, well done and thanks again for making this possible.

Now my question:

I am trying to make a menu shortcut to run a program. The program is javaFIBS and it needs java to run. For the program to run correctly I have to type

java -jar JavaFIBS-1.0.11_JDK13.jar

but the program only runs correctly if I open terminal within the javafibs directory (or go there before I run java).
So what I am trying to do is have my Application in terminal to run two commands:

1. cd /home/pietro/JavaFIBS2001/
2. java -jar JavaFIBS-1.0.11_JDK13.jar

I tried 

java -jar /home/pietro/JavaFIBS2001/JavaFIBS-1.0.11_JDK13.jar

but it does not seem to work as javaFIBS does not know where to look for its files and lots of buttons do not get loaded up. As in, the program run, but not correctly.

Any help would be greatly appreciated.

oh.. I was also wondering if there is an appropriate directory where to store software. In windzzz used to be Program Files, in Ubuntu I am using /home/pietro but I am not sure this is the appropriate one. Any suggestion?

Thank you for your help

p.

---

### Post by sancho panza on 2008-11-21
I cannot answer most of your queries, but regarding storing/installing software, the ideal place specifically meant for all software manually installed by you is /usr/local/

---

### Post by Keith Hedger on 2008-11-21
try saving the following as a script and then run the script, (don't forget to set the executable bit right click on the script select properties and check the box)
```
#!/bin/bash
cd /home/pietro/JavaFIBS2001/
java -jar JavaFIBS-1.0.11_JDK13.ja
```

---

### Post by uppercrustie on 2008-11-21
> **Keith Hedger said:**
> try saving the following as a script and then run the script, (don't forget to set the executable bit right click on the script select properties and check the box)
```
#!/bin/bash
cd /home/pietro/JavaFIBS2001/
java -jar JavaFIBS-1.0.11_JDK13.ja
```

Perfect! Thank you so much Keith. Just to understand better what's the "#!/bin/bash" line all about?



> **sancho panza said:**
> I cannot answer most of your queries, but regarding storing/installing software, the ideal place specifically meant for all software manually installed by you is /usr/local/

Thanks Sancho. I tried to copy and paste there but no luck.. I seem to have no permission of doing anything in there??? Do I have to do it through terminal?

---

### Post by Keith Hedger on 2008-11-22
the #! at the front of a script tells the system to run the script using a specific shell in this case 'BASH' there are other ones you can use ie #!/bin/sh, #!/bin/python (I think!).
Different shells have slightly different capabilities, the #! MUST be the first line of the script and no leading spaces/tabs.

---

### Post by Keith Hedger on 2008-11-22
> **uppercrustie said:**
> I tried to copy and paste there but no luck.. I seem to have no permission of doing anything in there??? Do I have to do it through terminal?
Yes you need root permissions to alter anything in the /usr directory open a terminal and type (for instance ) ```
sudo cp /path/to/script /usr/local/bin
```
Please check the man pages for any command you don't fully understand as you can damage your system with the wrong commands being run with root permissions.

---

### Post by uppercrustie on 2008-11-23
Brilliant! All solved. TY K.

---

