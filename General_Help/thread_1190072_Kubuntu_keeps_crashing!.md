---
title: "Kubuntu keeps crashing!"
date: 2009-06-17
forum: General Help
---

### Post by Java Geek on 2009-06-17
Hello, I recently changed my visuals in Kubuntu. However, periodically, my monitor stops getting a signal from the computer. I think that kubuntu may be crashing or just the monitor. It occurs whenever music is playing or I am using the terminal...among other times. Please, this problem is annoying me, so please help.

Additionally, are there monitor logs where i may be able to trace the problem?

---

### Post by Java Geek on 2009-06-17
Im on windows now... :(

---

### Post by overdrank on 2009-06-17
> **Java Geek said:**
> Hello, I recently changed my visuals in Kubuntu. 

Please be patient. what did you change?  What is the model of the graphics card, I assume you are using Jaunty 9.04?

---

### Post by wpshooter on 2009-06-17
> **Java Geek said:**
> Hello, I recently changed my visuals in Kubuntu. However, periodically, my monitor stops getting a signal from the computer. I think that kubuntu may be crashing or just the monitor. It occurs whenever music is playing or I am using the terminal...among other times. Please, this problem is annoying me, so please help.

Additionally, are there monitor logs where i may be able to trace the problem?

Change the visuals back to what they were before and see if the crashes stop !!!

---

### Post by Java Geek on 2009-06-17
I changed where I began to use Compiz and desktop effects. Graphics card is RV350 AP [Radeon 9600](ATI) and yes im using 9.04

---

### Post by overdrank on 2009-06-17
> **Java Geek said:**
> I changed where I began to use Compiz and desktop effects. Graphics card is RV350 AP [Radeon 9600](ATI) and yes im using 9.04

Ok I have seen issue where kwin and compiz do not act well together. If you can see the desktop and use the alt, F2 key and enter ```
kwin --replace
``` If not you can use the command line by using the ctrl, alt, F1 keys and enter the command then use the ctrl,alt, F7 keys to return to the desktop.  Hopefully this will disable compiz to stabilize your desktop till you can find the correction.

---

### Post by Java Geek on 2009-06-17
I am given this error:
```
kwin: cannot connect to the X server
```

---

### Post by Java Geek on 2009-06-17
All right, I've found that the problem occurs when enabling Desktop Effects.  How do I enable them without constant crashing?

---

### Post by xebian on 2009-06-17
> **Java Geek said:**
> All right, I've found that the problem occurs when enabling Desktop Effects.  How do I enable them without constant crashing?

It's your choice but KDE Desktop effects are superior to compiz and doesn't need compiz at all.

---

### Post by Java Geek on 2009-06-17
> **xebian said:**
> It's your choice but KDE Desktop effects are superior to compiz and doesn't need compiz at all.

Then how do I get rid of Compiz completely to fix these errors?

---

### Post by xebian on 2009-06-17
> **Java Geek said:**
> Then how do I get rid of Compiz completely to fix these errors?

Not sure what package manager you use but search for compiz and then mark them for removal/purge.

Then go to the SystemSettings and enable Desktop effects.  Chose whatever eyecandy you want - desktop cubes, animated, etc..

---

### Post by Java Geek on 2009-06-17
Thanks.

---

