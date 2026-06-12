---
title: "Minecraft Problems"
date: 2010-11-19
forum: Gaming &amp; Leisure
---

### Post by Kranix on 2010-11-19
I am considering buying Minecraft, but I want to try classic to see if I'm interested first.
I have installed sun java and removed icedtea-plugin, as was said in another thread.
Whenever i try to start, it loads and then java popups this message:

```
failed to start minecraft java.lang.illegalstateexception
```

What to do?

I am on 10.10 and have tried in Firefox and Chrome, same thing happens in both.

---

### Post by lol768 on 2010-11-20
Hi,

I have Minecraft Alpha running fine on my maverick installation.
For me the applet downloads the packages and then I get a black screen.

Try running this command to ensure you are using sun java and not the open source alternative (won't work):
```
sudo update-alternatives --config java
```

Double check that sun java is selected. You may have to install a separate plugin for firefox if you want to use sun java in firefox. I will check.

Minecraft alpha, for me works fine, although you need to start it with this command if you want sound: 
```
aoss java -jar /path/to/minecraft.jar
```

I think the aoss bit tells java to output through ALSA (sound).

Good luck,
Lol768

---

### Post by Kranix on 2010-11-21
Running the first command gives:
```

There is only one alternative in link group java: /usr/lib/jvm/java-6-sun/jre/bin/java
Nothing to configure.

```

I can't do the second command as I am talking about classic.

---

### Post by Perfect Storm on 2010-11-21
Then you properly need to install sun (oracle) java first.

---

### Post by Kranix on 2010-11-21
> **Artificial Intelligence said:**
> Then you properly need to install sun (oracle) java first.

I already did that...

Also, I can't run any commands or try out anything else until probably Wednesday.

---

### Post by Kranix on 2010-12-03
Still isn't working.

---

### Post by Kranix on 2010-12-10
Works now, thread can be locked.

---

### Post by Cousjava on 2010-12-11
What did you do to get it working?

---

### Post by djeikyb on 2011-03-11
Aye! Don't mark the thread as solved just because you no longer have a problem. If it magically went away, the problem isn't solved. If you're no longer interested in the problem, it isn't solved. Give back to the community, what did you do to get the dang thing working?

---

### Post by jaketay13 on 2011-07-29
he fixed it by getting the java sun plugin

---

### Post by cbennett926 on 2011-08-02
How did he get sun java?

---

### Post by cbennett926 on 2011-08-03
Nevermind I found my problem, I had JDK installed which messed it up

---

