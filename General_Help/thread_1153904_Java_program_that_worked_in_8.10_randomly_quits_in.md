---
title: "Java program that worked in 8.10 randomly quits in 9.04"
date: 2009-05-09
forum: General Help
---

### Post by Jokermage on 2009-05-09
For a web-based game I play, I sometimes use a particular java program to automate some of the clicking (the game "Kingdom of Loathing" is turn-based and not time-based, so bot-assisted play is not against the rules of the game). The program can be found at [http://kolmafia.sourceforge.net/](http://kolmafia.sourceforge.net/)

Daily updates to the program are compiled into .jar files that run off of the Java virtual machines. Since upgrading to Jaunty, the program randomly quits as if the process was killed.

I haven't found a common trigger for this problem, so I was wondering if any changes made to Java in 9.04 may be causing this.

Thanks for your time!

---

### Post by kostkon on 2009-05-09
It may be that in 8.10 you used to run it using Sun Java instead of the default OpenJDK or the opposite. Do you remember which one?

To see which JVM is the default in your system and all the available ones, in a terminal give
```
sudo update-java-alternatives -l
```

To change the default JVM, give
```
sudo update-alternatives --config java
```
and follow the prompts.

---

