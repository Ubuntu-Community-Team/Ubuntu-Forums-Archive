---
title: "Java JDK"
date: 2009-04-30
forum: General Help
---

### Post by Vyper06 on 2009-04-30
I'm trying to install the Java JDK onto my ubuntu machine, and whilst I know it's ironic I'm asking for help how to -install- an application considering I'm planning to use it to learn some simple programming tools, I am asking nevertheless.
I downloaded the JDK6 from the official website and was given a .bin file.
I placed this on the desktop and ran a ~sudo chmod +x (or whatever) and then ran a ./"filename" and successfully got a wall of text in the terminal asking if I agree with the TOC e.t.c to which i replied yes, and it seemed as if everything was installing nicely.

But when it had finished I was left with a folder on the desktop just full of files and no application in the Applications menu, so I'm wondering where the application for the JDK has gone?

Sorry if it seems laughably noobie but I'm new to ubuntu and am just wondering how to solve my issue, the files in the folder mean nothing to me :|

---

### Post by michy99 on 2009-04-30
I assume the folder is named jdk1.6.0_13. This is the java development kit and contains several programs and a lot of libraries. The first thing you wnat to do is move it to somewhere more useful like /usr/local. Open a terminal and enter:

```
cd ~/Desktop
sudo mv jdk1.0.6_13 /usr/local/
```

To get started writing programs, you need an editor or IDE. Try Netbeans, Geany, or Eclipse.

---

### Post by phinullfermata on 2009-04-30
The jdk is actually in the repository, packaged under sun-java6-jdk.  As far as the application goes, JDK doesn't really install any graphical applications as far as I know, it only really installs the commands jar, javac, and java in the command line.  If you're looking for a program to edit programs, something like GEdit will probably do you just fine with a few addons, otherwise I suggest learning an editor like vim, or emacs, or something similar.  I'd also suggest looking at IDE's (Integrated Development Environments) once you become a bit more familiar with the language, but some people say start with them right away.  In my experience IDE's can be a bit confusing sometimes, especially for people starting to program.

If you *are* looking for a good IDE, I've used a variant of Eclipse and it was very nice to work with, so I would reccommend using that.

---

### Post by Thelasko on 2009-04-30
[Please read this.]("http://www.psychocats.net/ubuntu/installingsoftware")

---

