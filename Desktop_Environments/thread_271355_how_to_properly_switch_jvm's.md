---
title: "how to properly switch jvm's?"
date: 2006-10-04
forum: Desktop Environments
---

### Post by revoohc on 2006-10-04
I have both Sun's 1.4 and 1.5 java environments.  What is the proper way to switch between them?  I have some projects that are based on 1.4 and are not currently on the plate to be upgraded.  However, all new development is being done in 1.5.  So, I need to be able to switch between the 2 environments (hopefully without to much blood, sweat, and tears).  

How do I do this?  I believe it is something in the /etc/alternatives?  

Thanks,

Chris

---

### Post by Delkster on 2006-10-04
> **revoohc said:**
> I have both Sun's 1.4 and 1.5 java environments.  What is the proper way to switch between them?

If you use an IDE, the JDK may well be selectable in its setting. If you just use the command-line tools, those are changed using the alternatives system as you correctly believe.

You can run `sudo update-alternatives --config java' and `sudo update-alternatives --config javac' (and so on) to select which program providing the functionality of each command you want to use.

---

### Post by skymt on 2006-10-04
The automagic way is to use the update-java-alternatives command:```
$ update-java-alternatives -l
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-gcj 1041 /usr/lib/jvm/java-gcj
$ sudo update-java-alternatives -s java-gcj
Password:
< snip output switching alternatives>
```See `man update-java-alternatives` for details.

---

