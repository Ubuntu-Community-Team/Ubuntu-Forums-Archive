---
title: "Installing Java messed up bash big time, can only do cd and pwd?"
date: 2005-07-29
forum: Desktop Environments
---

### Post by erik-the-red on 2005-07-29
So, I installed the .bin that contained JRE and JDK 1.5.0 with Netbeans.

I then added

```

export JAVA_HOME=/home/alex/Java/jdk1.5.0_04/
PATH="PATH:/home/alex/Java/jdk1.5.0_04/jdk1.5.0_04/bin:./"
export PATH

```

to the end of my .bashrc file after asking this question on Linux Questions and googling the PATH.

I guess java works somewhat now, because when I type java -version

```

Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)

```

displays. However, I can almost do NOTHING in the xterm now. When I do "ls", 

```

bash: ls: command not found

```

shows up.

What did I do wrong?

---

### Post by dave9191 on 2005-07-29
Your PATH contains the location of all the programs that you can run. So programs like ls are stored under /bin/ls. When you export your PATH varible, you are overwrighting the existing path without appending it to the existing one. 

Try 

export PATH="**$**PATH:/home/alex/Java/jdk1.5.0_04/jdk1.5.0_04/bin:./"

And if you need to use other commands like ls till then you have to provide the full path of the location of the bin file. 

Dave

---

