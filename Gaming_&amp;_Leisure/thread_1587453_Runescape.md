---
title: "Runescape"
date: 2010-10-03
forum: Gaming &amp; Leisure
---

### Post by Benup on 2010-10-03
Just downloaded java 6 and the file name is.

JDK-6u21-Linux-i586.bin

So i went to the terminal and put

./JDK-6u21-Linux-i586.bin and then tried it with Sudo infront but still get the same problem command not found or no such file or directory.

Anyone know how to sort this as i need it to make another program run

---

### Post by Naiki Muliaina on 2010-10-03
Did you download it into you home folder or your downloads folder?

If it is in your home folder you will need to run :

```
chmod +x JDK-6u21-Linux-i586.bin
sudo ./JDK-6u21-Linux-i586.bin
```

If it is in your Downloads folder

```
cd Downloads 
chmod +x JDK-6u21-Linux-i586.bin
sudo ./JDK-6u21-Linux-i586.bin
```

The main thing you need though is the java browser plugin. Search the Ubuntu Software Centre for **Java Plugin**. Install it from there, should be called **IcedTea java plug-in**. That should install everything you need.

---

### Post by chewit on 2010-10-03
Why you doing that!?!

Just get java from the ubuntu repos!

sunjava-6 plugin

---

### Post by Naiki Muliaina on 2010-10-03
Might want the most up to date version of Java? :) Repo one plays fine with Runescape though.

---

### Post by kaldor on 2010-10-04
OpenJDK is the default in Ubuntu and it's also less reliable. Using the software manager, remove OpenJDK and install the package called "sun-java6-plugin".

Or, you can copy-paste this:

```

sudo apt-get remove openjdk-6-jre
sudo apt-get install sun-java6-plugin

```

I believe that's the correct one to remove. If not, try "jdk" instead of "jre" at the end. It's been a while :)

This isn't Windows; the repositories should take care of you.

---

### Post by Naiki Muliaina on 2010-10-04
JDK 'was' more unstable. Not had any problems with current JDK in ages. :)

---

