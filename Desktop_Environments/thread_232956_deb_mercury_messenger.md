---
title: "deb mercury messenger"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Razer(x) on 2006-08-09
i am using ubuntu dapper..somebody should give me the deb of merury messenger that WORKS?

---

### Post by jincast90 on 2006-08-09
> **Razer(x) said:**
> i am using ubuntu dapper..somebody should give me the deb of merury messenger that WORKS?

I just looked at the homepage, and it looks to be more original msn messenger like. I might give it a try. Does it come as a rpm package? If so, theres a program called alien I belive, which can install some rpm packages.

---

### Post by jincast90 on 2006-08-09
I just found out you can download the debian installer from here:

[http://www.mercury.to/index.php?page=Downloads](http://www.mercury.to/index.php?page=Downloads)

---

### Post by Razer(x) on 2006-08-09
when i run in the shell mercury...see the screen

---

### Post by Razer(x) on 2006-08-10
nobody can help me?

---

### Post by adam.tropics on 2006-08-10
I don't use this but would imagine it's a java issue.

Try from a terminal

 sudo update-alternatives --config java

and check you are using /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

---

### Post by lettas on 2006-08-19
XGL on? Some say that xgl has to be up to date to run mercury.

---

### Post by ReiKn on 2006-11-26
> **Razer(x) said:**
> when i run in the shell mercury...see the screen

Edit your startup.linux.sh by adding an option -Dawt.toolkit=sun.awt.motif.Mtoolkit to the java-line making it look like this

```
java -Dawt.toolkit=sun.awt.motif.MToolkit -Djava.library.path=jni/linux:jni/linux/jmf -Xmx512m -classpath $classpath com.dMSN.Main
```

---

### Post by flamingdragon on 2007-11-03
Where abouts is startup.linux.sh? I can't seem to find it...

---

