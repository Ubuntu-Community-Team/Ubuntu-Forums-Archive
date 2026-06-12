---
title: "mounting Windows Vista ntfs partitions"
date: 2008-12-14
forum: General Help
---

### Post by TMachado on 2008-12-14
Hi,

I want to put in my /etc/fstab the line so when I run my Ubuntu 8.10 I have my both partitions C: and D: ( /media/disk and /media/Dados after mounted in "computer"), and I want to read and write.

Anyone can help me?

---

### Post by taurus on 2008-12-14
Just install ntfs-config and use it to configure those two ntfs partitions.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by TMachado on 2008-12-14
> **taurus said:**
> Just install ntfs-config and use it to configure those two ntfs partitions.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

If I do *sudo apt-get update* I get *E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.*

So I do *sudo dpkg --configure -a* and I have a problem I'm having days ago:

```
&#296;nstalling sun-java6-doc (6-10-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation


```

I'm trying to install java doc, but I honestly can't do ti... I downloaded the file jdk-6u11-linux-i586.bin, but I can't install it.. I even dont know if I install it, i have the java doc problem solve..

Anyone can help me? What should I do?

---

### Post by TMachado on 2008-12-14
> **TMachado said:**
> If I do *sudo apt-get update* I get *E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.*

So I do *sudo dpkg --configure -a* and I have a problem I'm having days ago:

```
&#296;nstalling sun-java6-doc (6-10-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation


```

I'm trying to install java doc, but I honestly can't do ti... I downloaded the file jdk-6u11-linux-i586.bin, but I can't install it.. I even dont know if I install it, i have the java doc problem solve..

Anyone can help me? What should I do?

ok, I finally installed the Javadoc and could configure my ntfs partitions :)

By the way, just a little off-topic with 2 questions: what does sudo apt-get update exactly?

Is is possible to terminate a process in console?

---

### Post by RomanIvanov on 2008-12-14
try to install Java doc from Synaptic Package Manager, type "sun java" in filter field and select appropriate package.

---

### Post by albinootje on 2008-12-14
> **TMachado said:**
> 
By the way, just a little off-topic with 2 questions: what does sudo apt-get update exactly?

Is is possible to terminate a process in console?

The command "sudo apt-get update" updates the information about packages from the repositories which are enabled in /etc/apt/sources.list

To terminate a process in the console you can press ctl-c
but be a little careful before using this.

---

### Post by TMachado on 2008-12-14
> **albinootje said:**
> The command "sudo apt-get update" updates the information about packages from the repositories which are enabled in /etc/apt/sources.list


Many thanks :)



> **albinootje said:**
> 
To terminate a process in the console you can press ctl-c
but be a little careful before using this.

No, I mean, terminate a program that is already running. For example, I run firefox from console, and how do I termine from console?

---

### Post by albinootje on 2008-12-14
> 
No, I mean, terminate a program that is already running. For example, I run firefox from console, and how do I termine from console?

Maybe i misunderstand your question, but if i run Firefox from a terminal (like gnome-terminal or xterm), then it's a matter of getting the (mouse or keyboard) focus on that terminal and ctl-c should shutdown Firefox then.

There are a few exceptions for that however.
vlc usually needs several ctl-c presses before it finally "dies".
It does actually have a message for that something like "user insisted too much, dying badly"

---

