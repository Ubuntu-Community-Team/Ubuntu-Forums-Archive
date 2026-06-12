---
title: "setting up java for openoffice 2"
date: 2006-09-05
forum: Desktop Environments
---

### Post by fishacre on 2006-09-05
I'm trying to set up java 1.5 in openoffice 2 (I'm running dapper)...

I have j2dk1.5-sun and j2re1.5-sun installed, but when I point the Tools->Options->OpenOffice.org->Java->Add dialog at /usr/lib/j2dk1.5-sun or /usr/lib/j2re1.5-sun (or their contents) I'm told 

'The folder you selected does not contain a Java runtime environment. Please select a different folder.'

I guess I'm missing something or other - can anyone suggest what that might be?

---

### Post by taurus on 2006-09-05
You don't have to install both j2dk1.5-sun and j2re1.5-sun at the same time.  One version is good enough.  The executable java should be in /usr/lib/j2re1.5-sun/bin...

---

### Post by fishacre on 2006-09-05
I installed j2sdk because j2re wasn't being recognised as a Java runtime environment by OOo, so I guessed something was broken. I'm still not sure what though!

---

### Post by taurus on 2006-09-05
I have j2re on my machine and don't have any problem using OpenOffice at all.  What is the output of this command at the prompt?

```
java -version
```

---

### Post by fishacre on 2006-09-05
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

---

