---
title: "Java using lots of memory"
date: 2009-04-10
forum: General Help
---

### Post by dadedo123 on 2009-04-10
[http://img264.imageshack.us/img264/8171/screenshoteoz.png](http://img264.imageshack.us/img264/8171/screenshoteoz.png)
What should I do ?

---

### Post by Slim Odds on 2009-04-10
Looks normal to me. Java does use lots of memory. Also, what you show is not that much.

---

### Post by cariboo on 2009-04-10
From your screenshot java is only using 12.2Mb while Firefox is using twice that. It is using 88% of your cpu cycles. I see at the bottom something about a java memory leak what was it you were doing?

Jim

---

### Post by dadedo123 on 2009-04-11
> **Slim Odds said:**
> Looks normal to me. Java does use lots of memory. Also, what you show is not that much.

It is using 88% percentage of the CPU. My system got really slow, and when I have stopped Java it got much faster. For some reason my machine is running slower than windows XP. Youtube videos are lagging alot, in normal mode not hq. System Specs
.Pentium 4 3.2GHz
.1.5 GB Ram

---

### Post by Slim Odds on 2009-04-11
> **dadedo123 said:**
> It is using 88% percentage of the CPU. 

Your title says: "Java using lots of memory".

It would be quite helpful if you would make your title actually match the problem that you're trying to solve.

---

### Post by dadedo123 on 2009-04-12
> **Slim Odds said:**
> Your title says: "Java using lots of memory".

It would be quite helpful if you would make your title actually match the problem that you're trying to solve.

Oh, sorry, not an expert in these things. But isn't it the more memory it uses, the higher CPU :s?

---

### Post by dadedo123 on 2009-04-12
Oh here is another screenshot of the CPU usage, it is almost 100% even though nothing is running. Is this what is causing my pc to go very slow? How can I fix this? 
[http://img17.imageshack.us/img17/7776/screenshotpzx.png](http://img17.imageshack.us/img17/7776/screenshotpzx.png)

.Someone please help, I'm kinda new to ubuntu, and I don't like to switch back to windows.

---

### Post by Slim Odds on 2009-04-12
> **dadedo123 said:**
> But isn't it the more memory it uses, the higher CPU :s?

No, the two are not directly related.

---

### Post by paradigm2 on 2009-04-12
> **dadedo123 said:**
> Oh here is another screenshot of the CPU usage, it is almost 100% even though nothing is running. Is this what is causing my pc to go very slow? How can I fix this? 
[http://img17.imageshack.us/img17/7776/screenshotpzx.png](http://img17.imageshack.us/img17/7776/screenshotpzx.png)

.Someone please help, I'm kinda new to ubuntu, and I don't like to switch back to windows.

^ As slim Odds said....

What java application are you using?  In my experience sometimes using th default openjdk as opposed to sun java can cause problems. But it is this way only with certain applications.

---

### Post by soltanis on 2009-04-12
You might consider using a different jre. Perhaps you have one of the crappy open-source substitutes running (low quality). I would suggest you install and use the sun-java6-jre.

```

sudo apt-get install sun-java6-jre
cd /etc/alternatives
sudo rm ./java
sudo ln -s /usr/lib/jvm/java-6-sun/bin/java java

```

Those last few lines tell your system to use the sun version of java. That's generally the best.

---

### Post by txcrackers on 2009-04-12
I would strongly recommend **not** manually adjusting alternatives - that can be hazardous to system updates and upgrades. Most packages, when properly installed, will have the pre-requisite alternatives automatically set up.

Instead of the last three lines of soltanis' solution (yes, install sun-java6-jre), use this command from a terminal:
```

sudo update-java-alternatives

```
If you only have one JRE installed, it will be selected. If you have more than one, you can select which one to use. This script takes care of adjusting **all** the java alternatives (including the browser plug-in) and makes it the default "java" program.

---

