---
title: "Need help installing a game,"
date: 2017-04-21
forum: Gaming &amp; Leisure
---

### Post by maddmoh on 2017-04-21
The game in question is Runescape. I have installed the game, but when I open it my screen flashes black, and once it's "loaded" it just displays a black screen like so: [https://i.imgur.com/HGMXt4F.png](https://i.imgur.com/HGMXt4F.png)

Just getting into ubuntu recently, so I am at a bit of a loss where to begin, I tried to irc channel but I couldn't get anywhere at the time.


It's sort of an odd laptop, if you need any more info to help diagnose you will have to tell me what you need, along with what terminal prompts I will require to show you.

---

### Post by howefield on 2017-04-21
Thread moved to the "*Gaming & Leisure*" forum for a better fit.

---

### Post by maddmoh on 2017-04-21
Thank you.

---

### Post by Perfect Storm on 2017-04-21
Which version of java have you installed?

---

### Post by maddmoh on 2017-04-21
-VPCS13AGJ:~$ java &#8211;version
Error: Could not find or load main class &#8211;version

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openjdk-6-jre-headless is a virtual package provided by:
  oracle-java9-installer 9b162-1~webupd8~0
  oracle-java8-installer 8u121-1~webupd8~2
  oracle-java6-installer 6u45-0~webupd8~8
  oracle-java7-installer 7u80+7u60arm-0~webupd8~1
You should explicitly select one to install.

E: Package 'openjdk-6-jre-headless' has no installation candidate


which one should I select to install? and how?

---

### Post by Perfect Storm on 2017-04-21
Jeez you have a lot of different version installed.

try with:
```
sudo apt-get install oracle-java9-set-default
```
If it's already installed try:
```
sudo update-alternatives --config java
```

---

### Post by maddmoh on 2017-04-21
Java installed, still same problem.

---

### Post by Perfect Storm on 2017-04-21
Maybe this workaround will work:

[http://services.runescape.com/m=forum/forums.ws?409,410,414,65748539,goto,90](http://services.runescape.com/m=forum/forums.ws?409,410,414,65748539,goto,90)
> Might be related: Linux Black game after update
I experience the black screen every time I launch the game.
Sometimes it's garbled graphics or "something colorful" instead of black screen.
Workaround for this case is to change window size (and then change back), and the graphics reset themselves... until rendering becomes all messed up after awhile, or after switching location.
Then you have to change window sizes again, switch to lobby and back into game, and no more graphical issues until I close the client.
And then later kicks in the audio issue... but this is a story for another rant 

---

### Post by maddmoh on 2017-04-21
Doesn't appear to be the same issue as mine.

all the java stuff is updated...

---

### Post by mörgæs on 2017-04-27
What does ```
java –version
``` now return?

---

### Post by maddmoh on 2017-04-27
AHhh maybe I installed it wrong 

```
Error: Could not find or load main class –version
Caused by: java.lang.ClassNotFoundException: –version
```

---

### Post by mörgæs on 2017-04-27
That was what I suspected. 

Your Java environment seems to have been through a lot of changes. 6u45 is from 2013, and much installation and uninstallation has been going on. Is it time for a reinstall of Ubuntu?

---

### Post by maddmoh on 2017-04-27
Well this was a fresh instal. I just need to know how to get rs working

---

### Post by mörgæs on 2017-04-27
Reading the thread again I now see that the Java versions mentioned in post five are not installed, they are only installation candidates. No mess here, as I first thought. 

Still I think that the missing Java is the problem for Runescape. I don't know if the version from Oracle or OpenJDK is the best to use so here is a topic for you to study.

---

### Post by maddmoh on 2017-04-27
Been looking at java for weeks. I havnt' a clue

No idea. Going to re-install and start again.

I tried windows, but that didn't work, I was hoping I might actually be able to install it on ubuntu.

Ok. So I re-installed. Then I got banned from #ubuntu whilst stating my problem. How is that a solution?

---

### Post by QIII on 2017-04-27
How did you get banned?

---

### Post by maddmoh on 2017-04-27
+b mode

tried here too: [http://services.runescape.com/m=forum/a=97/c=4EYZ5EmdMuk/forums.ws?409,410,414,65748539,goto,104](http://services.runescape.com/m=forum/a=97/c=4EYZ5EmdMuk/forums.ws?409,410,414,65748539,goto,104)

---

### Post by wildmanne39 on 2017-04-27
I think he meant for what. We do not administer that channel on irc, I do not believe we have any control over the running of that channel at all.

---

### Post by QIII on 2017-04-27
> **maddmoh said:**
> +b mode

Of course.  But that's not what I was asking.  That didn't just happen because a star randomly went supernova in your zodiacal sign.

Please don't come here and badmouth #ubuntu because you were not provided an answer.

---

### Post by mörgæs on 2017-04-28
> **maddmoh said:**
> Been looking at java for weeks. I havnt' a clue


Then you need to find one. Please search and post the Java requirements you have found. What exactly does Runescape need?

---

### Post by maddmoh on 2017-04-28
Going to read thru these posts later.

---

### Post by Perfect Storm on 2017-04-28
Ithink you should uninstall all the javas youhave installed and start with fresh new java 9.

Then
```
sudo update-java-alternatives --set java-9-oracle
java &#8211;version

```

---

### Post by maddmoh on 2017-05-01
> **QIII said:**
> Of course.  But that's not what I was asking.  That didn't just happen because a star randomly went supernova in your zodiacal sign.

Please don't come here and badmouth #ubuntu because you were not provided an answer.


Did not. Wasn't even a ban, I misread my irc console. I was banned from wikipedia, but I havn't even talked in that channel so that makes no sense. 

I think I was just kicked. Spoke to opers.

---

### Post by maddmoh on 2017-05-01
> **mörgæs said:**
> Then you need to find one. Please search and post the Java requirements you have found. What exactly does Runescape need?

I don't even know if I need java! This is just infomation that I am trying to gather. I have a feeling like this is simpler than it is appearing. 

> I install rs from here: [https://www.runescape.com/download](https://www.runescape.com/download) following the download instructions for linux

> Was missing: Package 'libglew1.10' has no installation candidate ; so I installed it

> When I try to run runescape the screen is black. And as the client is loading, the entire laptop monitor flashes black a few times before the client is finished loading.

> I do not know if I even need java, if I do then: ```
mike@mike-VPCS13AGJ:~$ java &#8211;version
Error: Could not find or load main class &#8211;version


```

> please refer to image on the first post referencing that my game client is just a black screen

---

### Post by QIII on 2017-05-01
> **maddmoh said:**
> Then I got banned from #ubuntu whilst stating my problem. How is that a solution?


I reckon it is not in your best interest to argue with the Forums Staff.

---

### Post by maddmoh on 2017-05-01
I like your sig.


i need an assist plz

---

### Post by mastablasta on 2017-05-03
runescape uses java to run, so yes, you do need java.

---

