---
title: "minecraft gets no keyboard input on 12.04"
date: 2012-05-12
forum: Desktop Environments
---

### Post by akos.maroy on 2012-05-12
Hi,

I just upgraded to ubuntu 12.04, and I'm trying to run minecraft, as earlier on 11.10. Minecraft used to run properly on 11.10, with a number of JDKs.

But, when I run the same thing on 12.04, the minecraft windows doesn't seem to get any keyboard events - after logging in. I can still enter my login details via keyboard, but as soon as I enter the game, no keyboard input gets through. This means one is unable to move using the WASD keys, but ESC doesn't work either, to get out into the menu.

I've tried with the following JDKs:

* OpenJDK 6
* OpenJDK 7
* Oracle JDK 7

I know of the need to fix the java GL .so, so this is how I run minecraft"

```

JDK_HOME=/usr/lib/jvm/java-7-openjdk-amd64/jre
JAVA=$JDK_HOME/bin/java

export LD_LIBRARY_PATH=$JDK_HOME/lib/amd64

$JAVA -jar minecraft.jar

```

what could have gone wrong?

---

### Post by akos.maroy on 2012-05-13
some additional info: the above symptoms happen only if ibus is used for input. if I kill ibus, minecraft gets the keyboard input fine

---

### Post by overclucker on 2012-06-06
Same here, I usually just kill ibus-daemon when i want to stack cobble. Makes navigating through files and folders with japanese unicode chars hard though.

---

