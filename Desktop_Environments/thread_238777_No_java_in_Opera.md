---
title: "No java in Opera?"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Robert Leithe on 2006-08-18
Any ideas as to why Opera won't run java? It works fine in Firefox.

I've been to the Tools>Preferences>Advanced>Content>Java options... and entered (and validated) the java path.

When I enter a site utilizing java (such as my bank) nothing happens. I've made sure that java is enabled. Tried both enabling it globally (in Opera) and setting it specifically for the site in question.

Sincerely
Robert Leithe

---

### Post by bluenova on 2006-08-18
What is the path you are using to java? And are you using default Ubuntu java or the offical Sun java?

---

### Post by Robert Leithe on 2006-08-18
The path to java from inside Opera is set to

/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386

---

### Post by Colonel Kilkenny on 2006-08-18
Maybe you could try to run Opera from console. Check also command opera --help, which lists the debugging modes.
"opera --debugplugin" might help you.

Check also my.opera.com/forums

---

### Post by ralphpc on 2008-04-21
> **Robert Leithe said:**
> Any ideas as to why Opera won't run java? It works fine in Firefox.

I've been to the Tools>Preferences>Advanced>Content>Java options... and entered (and validated) the java path.

When I enter a site utilizing java (such as my bank) nothing happens. I've made sure that java is enabled. Tried both enabling it globally (in Opera) and setting it specifically for the site in question.

Sincerely
Robert Leithe

Having temporalilly given up on trying to get java-sun or icetea to work with firefox on hardy heron i finally found this and managed to get Opera to do it. I had to direct Opera to the Java directory and as my choice wasn't quite right Opera suggested the correct one which has worked, so thanks to the gentleman above. I will put the full procedure that i followed here tomorrow.

---

