---
title: "Java GUI Freezes when run in Eclipse"
date: 2009-01-29
forum: General Help
---

### Post by godspeed_72 on 2009-01-29
Hi everyone.

I'm trying to run a small java program in Eclipse (v. 3.4.1).  I know the code is functional, as I have successfully run it on other machines, but when I try to run it on my laptop (Ubuntu 8.10) the GUI is totally frozen.  Similar problems do not arise when I try to run programs without a GUI.

Any advice?

Thanks

---

### Post by prince_niceguy on 2009-01-29
can you run it from the terminal and post the output of the terminal, it should give error if any occuring during eclipse boot.

---

### Post by godspeed_72 on 2009-01-30
Sorry, I don't understand.  Do you want me to try running Eclipse or the java program itself from the terminal?  To be honest, I wouldn't know how to do either.

---

### Post by prince_niceguy on 2009-01-30
No problem.

Just open a terminal and type the following command

<code>eclipse</code>

Terminal is located in application -- > accessories I think

---

### Post by godspeed_72 on 2009-01-30
Ok.  I tried running eclipse from the terminal.  I didn't install eclipse through the package manager, so the command I eventually figured out was just ~/eclipse/eclipse, but that just launches the IDE as I'm used to using it, and no extra information was printed to the terminal.  Am I doing something wrong?

Thanks for your patience.

---

### Post by prince_niceguy on 2009-01-30
what is the java version you are using??

again in terminal type java --version

that should give some info. if it is not sun java then download the same.

---

### Post by godspeed_72 on 2009-01-30
output from java -version:

java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Server VM (build 1.6.0_0-b12, mixed mode)

---

### Post by prince_niceguy on 2009-01-30
Ok. get the java version from sun, and then install it on your comp. change your eclipse.ini to point to sun vm and then again run the eclipse, it should work.

---

### Post by godspeed_72 on 2009-01-30
Ok, how can I get the Sun version of Java?  Is it in the package manager?  If so, what is the package called (a search for "sun java" returns tons of hits)?

What exactly should I be changing in the eclipse.ini file?  There isn't anything in there that obviously points to my current vm, as far as I can tell.

---

### Post by prince_niceguy on 2009-01-30
Package to install would be sun-java6-jdk. and search for icedtea java and remove it.

that should hopefully resolve the issue.

---

