---
title: "How to install jdk1.5.0_05 please??"
date: 2006-01-04
forum: General Help
---

### Post by jrios_03 on 2006-01-04
Hi everyone...

I'm new in UBUNTU and Linux, I'm a java programer and I want to know how to install the jdk1.5.0_05 and run it...

I try to install the .bin file, but when I try to compile or run a file the terminal give me an error, and I don't understand the error...

Please help me... it's very important to me...

Sorry for my english, I'm Chilean...

Grettings...

---

### Post by oakz on 2006-01-04
Try following the directions under "Sun Java" at the bottom of this page:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

If that doesn't work post the error you are getting, someone may be able to help

---

### Post by ape on 2006-01-04
These steps should work:

1. Download the latest JDK from Sun. (the latest is now 1.5.0_06)

2. Make sure that you have the java-package and fakeroot packages installed.

3. Run the following command:

       `fakeroot make-jpkg <path to Sun jdk .bin file>`

This will produce a .deb file containing the jdk bits.  You can then install it using `sudo dpkg -i <.deb file that was produced>`

---

### Post by briancurtin on 2006-01-04
[http://java.sun.com/j2se/1.5.0/install-linux.html](http://java.sun.com/j2se/1.5.0/install-linux.html) right on the sun website, probably right where you downloaded it. this is the easiest way to do it.

---

### Post by briancurtin on 2006-01-04
[QUOTE=ape]This will produce a .deb file containing the jdk bits.  You can then install it using `sudo dpkg -i <.deb file that was produced>`[/QUOTE]
why take that extra step though? just use the bin in the 3 steps listed on suns site

---

### Post by jrios_03 on 2006-01-04
Thanks to everyone...

I go home and try to do this....

If it fails... I come whit the error for you...

Thanks again... Bye...

---

### Post by healychan on 2006-01-04
Please read this guide
[http://www.ubuntuforums.org/showthread.php?t=107569](http://www.ubuntuforums.org/showthread.php?t=107569)

hope it helps:razz:

---

### Post by Hikaru79 on 2006-01-04
[quote=briancurtin]why take that extra step though? just use the bin in the 3 steps listed on suns site[/quote]

Because doing it with the extra step makes it part of the Debian packages ubuntu recognizes, meaning packages that have it as a dependency will be able to use it. It's just much cleaner to do it his way, even if it is slightly longer.

---

### Post by oakz on 2006-01-04
The bin is much easier...but installing the deb gives you a couple advantages that I know of:
1. You don't need to add the Java bin directory to your PATH (or sym link into it)...the deb uses the "alternatives" symbolic links for java, javac, etc in /usr/bin.
2. Because of (1) you can easily switch between multiple versions of gcj and Sun's Java using "sudo update-alternatives --config java" if you need to
3. The deb method will automatically install the java plugin for mozilla/firefox

---

### Post by jrios_03 on 2006-01-10
Hi again...

I have a problem with this:
```
With the fakerrot in Ubuntu 5.04 and 5.10:

root@Kubuntu:~/Desktop# chmod -x jdk-1_5_0_05-linux-i586.bin 
root@Kubuntu:~/Desktop# fakeroot make-jpkg jdk-1_5_0_05_-linux-i586.bin 
fakeroot: preload library not found, aborting.


And when I execute this:
root@Kubuntu:~/Desktop# sudo apt-get install java-package fakeroot 
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias... Hecho 
E: No se pudo encontrar el paquete java-package

```

I need your help please...

---

