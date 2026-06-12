---
title: "No sound in Minecraft? try this"
date: 2010-11-05
forum: Gaming &amp; Leisure
---

### Post by homerhomer on 2010-11-05
Recently I've been having strange minecraft sound issues, I noticed by starting minecraft with padsp seems to have fixed it. 


So here's my minecraft startup script. 


padsp java -jar Minecraft.jar 

or try this 

padsp java -Xms1024M -Xmx1024M -Djava.net.preferIPv4Stack=true -jar Minecraft.jar

---

### Post by alogghe on 2010-11-07
This seems to have fixed my issues so far.

I was losing sound after 10-20 minutes of play, thanks for the fix.

---

### Post by lagerdalek on 2010-11-17
Awesome! works a treat, thanks

---

### Post by chec69 on 2011-01-21
Thanks worked perfectly :D

---

### Post by znuxor on 2011-01-22
Thank you. :)
I thought it was unfixable.

---

### Post by mattuFIN on 2011-01-25
It worked! Thank you very much! ;)

---

### Post by Vustom on 2011-02-08
How do I launch Minecraft as 
> padsp java -Xms1024M -Xmx1024M -Djava.net.preferIPv4Stack=true -jar Minecraft.jar
?

---

### Post by Joseph Schwenker on 2011-03-22
> **Vustom said:**
> How do I launch Minecraft as 

?

To launch Minecraft as such, go to Applications>Accessories>Terminal and type cd (the path to where Minecraft is, example: /home/joseph/Downloads/). Then paste in the command by either right clicking or pressing ctrl shift v.

---

### Post by ubudog on 2011-03-23
Thank you!  Gonna try this next time I play.  :-)

---

### Post by kailkitsune on 2011-03-27
i need help i suck a the terminal the .jar is in my documents but it keeps telling me theres no such file any help?

---

### Post by ubudog on 2011-03-27
> **kailkitsune said:**
> i need help i suck a the terminal the .jar is in my documents but it keeps telling me theres no such file any help?

Try this:

```
padsp java -jar $HOME/Documents/minecraft.jar 
```

---

### Post by Joseph Schwenker on 2011-03-30
I've tried all of these commands, but I'm still randomly losing sound in Minecraft SMP.

---

### Post by earthmeLon on 2011-05-12
Thank you.  This (original post) has solved the problem with sound working and randomly stopping working in Minecraft.

Glad to hear creepers again :D


Edit:

Seems it's still not working 100%

---

### Post by jynyl on 2011-05-16
Ditto: still a problem here.
I tried adding padsp at the beginning of the command, but it still randomly cuts out after a varying amount of time.  Sometimes it cuts out after just a minute or so, sometimes it runs fine with sound for 20 or 30 minutes, then cuts out.

---

### Post by jabermony on 2011-07-02
this may not help and may be slightly late but have you tried raising the priority of minecraft while its running seems to work for me.

---

### Post by StartedTheFire on 2011-07-08
I love you OP.

---

### Post by The_Eddster on 2011-07-11
I get this problem when I run that command:


```
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:460)
	at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
	at java.lang.UNIXProcess.<init>(UNIXProcess.java:148)
	at java.lang.ProcessImpl.start(ProcessImpl.java:65)
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:453)
	... 1 more
```


Minecraft still runs, but the sound randomly cuts off like before.

---

### Post by EvilMoose on 2012-02-17
> **Joseph Schwenker said:**
> I've tried all of these commands, but I'm still randomly losing sound in Minecraft SMP.

[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

That combined with padsp works to get rid of lost sound but you'll hear the sound crack within 30 minutes of playing.

---

