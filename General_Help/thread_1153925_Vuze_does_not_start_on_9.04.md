---
title: "Vuze does not start on 9.04"
date: 2009-05-09
forum: General Help
---

### Post by Drengur on 2009-05-09
Hello.

Vuze has seized working after my upgrade to 9.04.

```
drengur@drengur-desktop:~$ vuze 
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found
```
 
Any ideas? Do I need to reinstall Java or what?

Thank you.

---

### Post by Drengur on 2009-05-10
It is a bug.

See [https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/348109](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/348109)

To fix it:

```
For others who like me doesn't want/can't work with openjdk, the current modification (has to be done with root) can be done to /usr/bin/azureus:
#!/bin/sh
## JAVA='/usr/lib/jvm/java-6-openjdk/jre/bin/java -Xmx1024M'
JAVA='/etc/alternatives/java -Xmx1024M'
```

---

### Post by ssk.green on 2009-06-06
thank you so much

---

### Post by colau on 2009-06-06
> **Drengur said:**
> Hello.

Vuze has seized working after my upgrade to 9.04.

```
drengur@drengur-desktop:~$ vuze 
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found
```
 
Any ideas? Do I need to reinstall Java or what?

Thank you.
Transmission bittorrent client is better.

---

### Post by skathmandoo on 2009-06-26
> **Drengur said:**
> It is a bug.

See [https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/348109](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/348109)

To fix it:

```
For others who like me doesn't want/can't work with openjdk, the current modification (has to be done with root) can be done to /usr/bin/azureus:
#!/bin/sh
## JAVA='/usr/lib/jvm/java-6-openjdk/jre/bin/java -Xmx1024M'
JAVA='/etc/alternatives/java -Xmx1024M'
```


I have absolutely no idea what to do. can someone be more specific please

---

### Post by madverb on 2009-06-26
Deluge is the best

---

### Post by devanson on 2009-07-19
> **skathmandoo said:**
> I have absolutely no idea what to do. can someone be more specific please


Hi.. skathmandoo.. Here is a detailed step as u asked....



Open File 
	/usr/bin/azureus

Edit Line
#!/bin/sh
## JAVA='/usr/lib/jvm/java-6-openjdk/jre/bin/java -Xmx1024M'

to
#!/bin/sh	
## JAVA='/etc/alternatives/java -Xmx1024M'

---

