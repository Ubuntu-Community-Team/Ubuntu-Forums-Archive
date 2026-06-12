---
title: "How to install sun java?"
date: 2005-11-07
forum: Desktop Environments
---

### Post by Darrin on 2005-11-07
I tried doing the steps i found on the ubuntu guide.
```
sudo apt-get install sun-j2re1.5
java -version
``` 

When doing this I get this message.

[SIZE="1"]Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2re1.5 has no installation candidate[/SIZE]

How do I get this to work?

---

### Post by Xian on 2005-11-07
1. Wiki entry: [How-To Install Sun Java 1.5](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)
2. Use the [PLF Repository](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by jvictor on 2005-11-07
There are many posts in this forum saying how to .. are u talking of JDK or JRE ?

---

### Post by Darrin on 2005-11-07
Ok thanks. 
Still struggling a bit with the terminal terms.
If I download the file to my desktop, how do I change the following code to point to the file on the desktop?
```
chmod +x jre-1_5_0_05-linux-i586.bin
```

---

### Post by Xian on 2005-11-07
In the future make it easy on yourself and download things to your /home/username directory. The terminal opens there by default and there is no need to goto another path just to execute a file.

This time issue the command below to get your Desktop.
Then issue the chmod command again.

When you 'ls' you should see the file listed.

```
$ cd /home/username/Desktop
$ ls
```

---

### Post by jvictor on 2005-11-07
yes perfectly right

and then go in a terminal to the folder where u have downloaded the bin 
and then ./j2XXXXXXXXXXX.bin

that will bring up a lic agreement type **yes**

the bin will self extract itself and u get the JDK 

next modify ~/.bashrc and  add

export JAVA_HOME=<the place where u have extracted the JDK>
PATH=${JAVA_HOME}/bin:$PATH

tahts should get things working

---

### Post by RAOF on 2005-11-08
[QUOTE=jvictor]yes perfectly right

and then go in a terminal to the folder where u have downloaded the bin 
and then ./j2XXXXXXXXXXX.bin

that will bring up a lic agreement type **yes**

the bin will self extract itself and u get the JDK 

next modify ~/.bashrc and  add

export JAVA_HOME=<the place where u have extracted the JDK>
PATH=${JAVA_HOME}/bin:$PATH

tahts should get things working[/QUOTE]
Ignore this, just follow the howto linked and everything will be fine.  You don't need to do any more fiddling around.

---

### Post by Darrin on 2005-11-08
Thanks. I used the PLF repositories and it worked great. I tested it at the java site and everything is running.

---

