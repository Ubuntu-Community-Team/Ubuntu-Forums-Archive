---
title: "JDK not recognized-found"
date: 2007-10-09
forum: Desktop Environments
---

### Post by anna611 on 2007-10-09
I am totally messed up:
did ```
apt-get install sun-java6-jdk
```

Result: it was already installed.

If I type```
 java -version
```, I get the following: 
```
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found
```

But all these programs are not on my computer.

If I do the following:
```
update-alternatives --config jaupdate-alternatives --config java
```

```
There are 0 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------

Press enter to keep the default[*], or type selection number:
```


I added the following lines into .bashrc:
```
#java environment variable
JAVA_HOME=/usr/lib/jvm
JDK_HOME=/usr/lib/jvm
PATH=$JAVA_HOME/bin:$PATH
export JAVA_HOME JDK_HOME PATH
```

All with no avail.

Can someone please help me?

I need the JDK for development, and it's quite urgent.

(am using Feisty)

---

### Post by jnorthr on 2007-10-09
look here: [http://wiki.serios.net/wiki/Main_Page](http://wiki.serios.net/wiki/Main_Page)
and
here: [http://www.open-xchange.com/forum/archive/index.php/t-112.html](http://www.open-xchange.com/forum/archive/index.php/t-112.html)

---

### Post by anna611 on 2007-10-09
> **jnorthr said:**
> look here: [http://wiki.serios.net/wiki/Main_Page](http://wiki.serios.net/wiki/Main_Page)
and
here: [http://www.open-xchange.com/forum/archive/index.php/t-112.html](http://www.open-xchange.com/forum/archive/index.php/t-112.html)

no, this all didn't help.
Will the only solution be to backup all my data and reinstall ubuntu?

---

### Post by taurus on 2007-10-09
What's the output of this command from a terminal?

```
sudo find / -name java -print
```

---

