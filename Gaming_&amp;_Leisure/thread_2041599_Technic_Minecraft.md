---
title: "Technic Minecraft"
date: 2012-08-12
forum: Gaming &amp; Leisure
---

### Post by asdk on 2012-08-12
Has anyone managed to get it to work? I'm stuck with a black screen.

---

### Post by NovaAesa on 2012-08-12
There are a few reasons that you could be running into problems. Which version of Java are you using? You will need version 6 (rather than 7). This caused the exact same problem for me. To find your version, run 
```

java -version

```

---

### Post by holastickboy on 2012-08-13
Agreed, Technic needs java 7, not the java 6 which is the usual default installation of java.  To install Java 7, check out this link that I used to get Technic working for me:

[http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

---

### Post by asdk on 2012-08-13
I have tried to run it it posh OpenJDK Java 6 and 7 with no sucess (although, the color alternated between a grey screen and black screen :P)

I am thinking it is an LWJGL problem, did you guys update this some how?

(On normal minecraft I also had a black screen before updating LWJGL)
By the way, does the Technic launcher updated your minecraft.jar or do if you want to run Technic, doyou have to use the Technic launcher?

Sorry, I am new to this so I have a lot of questions.

I will post the results to java --version once I get onto my computer (approx 12 hours). Also, I am running Ubuntu 12.04.

Java version is:
OpenJDK Runtime Environment (IcedTea7 2.1.1pre) (7~u3-2.1.1~pre1-1ubuntu3)
OpenJDK Server VM (build 22.0-b10, mixed mode)

fixed, had to update lwjgl inside of the .techniclauncher

---

### Post by QsoftStudios on 2012-08-13
try updating java and re-downloading the Technic launcher.

---

### Post by stlu on 2012-08-15
Hi,

I am running 12.04 64-bit, and I am delighted to say that it does work on my machine!  I play Tekkit, which I understand to contain even more mods, so I believe that technic should work too.

Last time I tried using openJDK with minecraft was on a 32bit system with limited Ram(512MB) and the game got as far as the logo splash, but never successfully showed the main menu.

Now this has come a long way, but I did notice some odd texture glitches with creepers and skeletons.

```
http://www.servimg.com/image_preview.php?i=21&u=17138028

http://www.servimg.com/image_preview.php?i=22&u=17138028

```Info: Dell Inspiron N7010 (6GB Ram)
**$ java -version**
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.3) (6b24-1.11.3-1ubuntu0.12.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

---

