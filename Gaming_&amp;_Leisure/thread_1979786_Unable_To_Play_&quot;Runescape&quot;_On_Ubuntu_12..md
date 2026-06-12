---
title: "Unable To Play &quot;Runescape&quot; On Ubuntu 12.04LTS - No Java"
date: 2012-05-14
forum: Gaming &amp; Leisure
---

### Post by Insert Cool Username Here on 2012-05-14
I was able to play [Runescape](www.Runescape.com) on Ubuntu 11.10 after some simple Java installations via the terminal, I've recently upgraded to 12.04LTS and no matter what I try It still says I need to install java when I go to play Runescape, any help please?

---

### Post by Insert Cool Username Here on 2012-05-14
Installed Icedtea in the software center, runescape is up and running now, but i'd forgotten how much is sucked.

---

### Post by Carpentr on 2012-05-14
Follow this guide:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

I could not get the game to render using OpenGL. It would always default to software mode. You may have better luck.

---

### Post by phYnc on 2012-05-14
> **Carpentr said:**
> Follow this guide:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

I could not get the game to render using OpenGL. It would always default to software mode. You may have better luck.

Using OpenJDK-7 and Icedtea-7-plugin I was also unable to get the game to run in OpenGl mode.

---

### Post by Sumaxi on 2012-05-14
Instead of OpenJDK7 try OpenJDK6.
Might work.
And use something you have java with, like chromium ( I BELIEVE- it's supported with it)

---

### Post by phYnc on 2012-05-14
> **Sumaxi said:**
> Instead of OpenJDK7 try OpenJDK6.
Might work.
And use something you have java with, like chromium ( I BELIEVE- it's supported with it)

[FIXED] Using OpenJDK-6 and Icedtea-6-plugin with Google Chrome stable browser. OpenGl works.

edit: Still gets FPS drops to 9 even running on a i5 2500k and nvidia 560ti. But working at least.

---

