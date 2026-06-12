---
title: "Java and Minecraft"
date: 2012-08-28
forum: Gaming &amp; Leisure
---

### Post by Moofy on 2012-08-28
Hello! 2 issues.

1: 
I went to Ubuntu Software Center and installed icedtea and OpenJDK Java runtime 6.

I downloaded Minecraft and Tekkit (these are *games* if people don't know them.)
I made them executable and right clicked and opened with the OpenJDK runtime 6 java.

Everything works until i close, i get a grey screen and it sits there for 5 minutes or so, then it closes with a crash report.

2:
When in Minecraft and i right click (placing blocks or stuff) i see my mouse? It's like flickering everytime i click. It's VERY annoying.

 - Any help?
~Moofy

---

### Post by Szor3n on 2012-08-28
You actually need to use Oracl's Java for minecraft. OpenJDK doesn't run so well with it. [http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux](http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux)

---

### Post by Moofy on 2012-08-28
So uninstall OpenJDK java and follow that link?

--

Done, but now Java does not show in my right click menu!

---

### Post by QIII on 2012-08-28
You do NOT need to uninstall OpenJDK since it can coexist with Oracle Java.  That tutorial is FAR too complicated and when a new Java update comes out a reinstallation is required.

In the Oracle Java 7 section of the wiki in my signature, under "command line methods" is a link entitled "Using webupd8.org's strikingly simple method".  Webupd8's PPA is updated so that it downloads and updates Oracle Java 7 as Oracle releases updates.  All you have to do is your normal periodic updates and nothing special.

To choose between versions of Java, including OpenJDK, all you have to do is follow the instructions for doing so in the wiki.

Again:  there is NO reason to use such a complicated method to install Oracle Java 7 in Ubuntu.

---

### Post by Moofy on 2012-08-28
Well i did it that way, should remove everything and do it your way? Can you give me a guide to do it your way? Also i use:

```
cd Desktop
```

then

```
java -jar minecraft.jar
```

Minecraft launches and all but it gives me a black screen.
Help?

---

### Post by sffvba[e0rt on 2012-08-28
*Thread moved to **Gaming & Leisure**.*


404

---

### Post by QIII on 2012-08-28
Although not likely necessary, you could remove the additions made to /etc/profile to allow the webupd8 script to set all of that for you.  However, as I said, that is not likely necessary.

The guide to doing this is contained in the link I cited.  It is simple, consisting of just three commands in the terminal.

---

### Post by drmrgd on 2012-08-28
> **Moofy said:**
> Well i did it that way, should remove everything and do it your way? Can you give me a guide to do it your way? Also i use:

```
cd Desktop
```

then

```
java -jar minecraft.jar
```

Minecraft launches and all but it gives me a black screen.
Help?

I think your confusion is in the fact that there can be multiple versions of java all on your system at the same time.  Following the guide that QIII posted (which is excellent by the way!), you can set up alternatives in order to quickly set which one is executed by default.  For example on my system, I have 5 differnt versions of java installed (which is a bit out of hand...need to clean that up!):

```
sudo update-alternatives --config java
There are 4 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      auto mode
* 1            /opt/java/32/jre1.6.0_31/bin/java               1         manual mode
  2            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      manual mode
  3            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode
  4            /usr/local/java/jre1.7.0_03/bin/java            1         manual mode

Press enter to keep the current choice[*], or type selection number: 

```

I can then just choose which one I want to set as the default, which can be confirmed by running:

```
java -version
java version "1.6.0_31"
Java(TM) SE Runtime Environment (build 1.6.0_31-b04)
Java HotSpot(TM) Client VM (build 20.6-b01, mixed mode, sharing)
```

You'll notice that it matches what I have in my alternatives configuration.

So, all you need to do is to install java as QIII suggested, and then make an alternatives configuration to use it as the default.  No need to remove everything and reinstall and mess around!

---

### Post by Moofy on 2012-08-28
What I just want is to remove everything that has to do with java right now and then do this: [http://www.webupd8.org/2012/06/how-to-install-oracle-java-7-in-debian.html](http://www.webupd8.org/2012/06/how-to-install-oracle-java-7-in-debian.html)

I think. It ruins my OCD to install something on top of something else, I want it as pure as possible!

---

### Post by QIII on 2012-08-28
Make this easy on yourself.

Use the directions I gave you, since they are tailored to Ubuntu.  Why use instructions for Debian that install exactly the same thing I already directed you to -- a package for Ubuntu?  Look carefully at the instructions at the URL you just cited.   "http://ppa.launchpad.net/webupd8team/java/**ubuntu precise** main" is added to the sources list.

You are not installing on top of something else.  You are installing an OPTION, which you can choose.  Although the first instructions you were given said you needed to uninstall OpenJDK to avoid conflicts, that is *incorrect. *You will not have an "impure" installation of Java.  Multiple Java installations do not conflict with each other.  You ensure that by choosing the alternative.
I am not at home to look at the install directories, but I believe those instructions put the Java files in exactly the same directories where the webupd8 scripts will.  That means they will be overwritten.  If you want, remove the lines you added to /etc/profile.

The webupd8 scripts will automagically set your alternative to the Java package installed by them.

---

### Post by Terl on 2012-08-28
> **QIII said:**
> You do NOT need to uninstall OpenJDK since it can coexist with Oracle Java.  That tutorial is FAR too complicated and when a new Java update comes out a reinstallation is required.

In the Oracle Java 7 section of the wiki in my signature, under "command line methods" is a link entitled "Using webupd8.org's strikingly simple method".  Webupd8's PPA is updated so that it downloads and updates Oracle Java 7 as Oracle releases updates.  All you have to do is your normal periodic updates and nothing special.

To choose between versions of Java, including OpenJDK, all you have to do is follow the instructions for doing so in the wiki.

Again:  there is NO reason to use such a complicated method to install Oracle Java 7 in Ubuntu.

Happened to see this (sorry if OT) and wanted to say thanks.  I am running Java 7 now.

---

### Post by Moofy on 2012-08-29
So the link I just provided is incorrect?

---

### Post by QIII on 2012-08-29
The link Szor3n gave you is incorrect in saying that you need to uninstall OpenJDK to avoid conflicts.  That is not true.

The link you provided is for installing the webupd8.org Oracle Java 7 installer on Debian.  Those instructions are pointless, since the package is already tailored for Ubuntu.  Why use instructions for installing on Debian a package tailored for Ubuntu when you are using Ubuntu and not Debian?

Remove the lines you added to /etc/profile.  Use the instructions I directed you to in the wiki in my signature:  "Using webupd8.org's strikingly simple method".

Don't over think this.  The people at webupd8.org worked it all out for you.

---

### Post by Moofy on 2012-08-29
I just want to uninstall java completely before I do the webupd8 one, my OCD tells me to.
And how do I do that?

---

### Post by Moofy on 2012-08-29
So i did the webupd8 way now and i right click my .jar and choose "open with" oracle java runtime 7.

Still when i close i get the black screen and crash report.

---

### Post by QIII on 2012-08-30
This might better be a Minecraft question at this point.

---

### Post by KoolPenguin on 2012-08-30
> **Moofy said:**
> So i did the webupd8 way now and i right click my .jar and choose "open with" oracle java runtime 7.

Still when i close i get the black screen and crash report.

Try java version 6.  I get the same thing with java 7.

---

### Post by QIII on 2012-08-30
Java 6 is subject to vulnerabilities that make it unsafe.

It is also due to reach end of life in November, 2012.

If you install it, be sure you understand how to switch between alternatives (see the wiki in my signature) and only use Java 6 for your game.  Then switch immediately.

---

### Post by xinger on 2012-09-04
If you're trying to run Minecraft, make sure you have latest version of Java (including JDK) installed. Otherwise you will face compatibility issues with modifications like [ModLoader 1.3.2]("http://www.games-utilities.com/minecraft-1-3-2-risugamis-modloader-download/")

---

