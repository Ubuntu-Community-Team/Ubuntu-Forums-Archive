---
title: "Runescape Java problem"
date: 2009-08-18
forum: Gaming &amp; Leisure
---

### Post by Ant on holiday on 2009-08-18
Ok, Im fairly new to linux. Ive had it for a fair 2 weeks or so.
so the problem is, that when i try to play runescape, it comes up with the "you have no java on computer or its not enabled.
But it is enabled, and I downloaded java from the add and remove thing. this is the java I downloaded: Sun Java 6 Runtime. 
So whats the problem?

and whats icedtea?

EDIT: im running linux ubuntu 8.04, havent installed any updates since, and Im using and aspire one. if that info makes any difference...

---

### Post by skunkcar on 2009-08-27
IcedTea is a software intergration project, you dont need to worry about it as far as installing java to play Runescape goes. If you wish to learn more about linux and really get into the programming, then it would probably be nice to know about it.


First off, you will need to be the root user. To do this, follow the following steps:
-open Terminal (under applications>accesories)
-type: **sudo bash**
-enter your user password
    You should now be root user, if you werent already.

In the Terminal, type: 
**apt-cache search jdk** 
this will tell you your current java

Now, type the following command to install Java6 JRE and JDK:
**apt-get install sun-java6-jdk sun-java6-jre**
You should be given a [Y/N] prompt, which you will type Y and press enter.

Next, a blue box including the copyright information and user agreement will appear in your Terminal. Navigate to the bottom and use your arrow keys to highlight the 'Ok' button, and then accept the agreement.

It should then complete the installation process.

The java files should appear in directory: **/usr/lib/jvm/java-6-sun-1.6.0.06**
But you dont have to worry about that.

Type in Terminal:
java -version
This will just prove that the java package has been installed.

VOILA, youre done, go pk some noobs, I'll see you in the wild.

Hope this was helpful, i have just recently been introduced to linux as well and had the 
same problems with my Java. It was working for me, but it wasn't up to par. I have been following my own instructions as I was typing it, so I havent had a chance to see if it improved issues i was having earlier.  feel free to post back some feedback im curious to see just how helpful i can be sometimes. And sorry if the whole thing is a little long-winded, its much simpler than it seems.
     
[FONT=monospace]
[/FONT]

---

