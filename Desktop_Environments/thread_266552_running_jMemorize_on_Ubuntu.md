---
title: "running jMemorize on Ubuntu"
date: 2006-09-27
forum: Desktop Environments
---

### Post by d3dtn01 on 2006-09-27
I'm trying to get a flash card application called jMemorize to run on Ubuntu. The program is a java app. The download page ([http://riad.de/jmemorize/download/]("http://riad.de/jmemorize/download/")) says that you need to install the java runtime environment first. Then, you just save the jMemorize .jar file to your computer and double-click it. Or from the command line, it tells you to use the javaw command to run the program. I've had no success with this.

Here's what I did:
First, I manually installed J2SE v1.4 as suggested on the jMemorize site. Neither the double-click nor the javaw command worked. When I tried javaw I got an error message that the command could not be found.

Next, I used apt-get to install sun-java5-jdk. That installed fine. But still, javaw doesn't work, nor does double clicking on the .jar file. 

As you can see, I know nothing about jre. Am I installing jre wrong?

---

### Post by d3dtn01 on 2006-09-27
UPDATE

I right clicked on the file and discovered a option to "Open application with Sun Java5 Runtime." Now it works. I'm not sure why I couldn't use the command line method, but oh well, at least it works.

---

### Post by dinin_1985 on 2007-03-07
I don't know why they put that command line, but the one that (almost...) worked for me was: cd Desktop && java -jar jMemorize-1.2.2.jar    
Yes, somewhere I read that the right command was "java" and not "javaw".
Anyway it didn't worked quite well because I can't create a icon or shortcut for this (I've even tried a shortcut for the command line........actually, I'm trying it yet..... ; ) .....)

---

