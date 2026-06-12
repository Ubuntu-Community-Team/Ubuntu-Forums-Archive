---
title: "Minecraft Problems in Ubuntu 13.04"
date: 2013-05-17
forum: Gaming &amp; Leisure
---

### Post by Anathema05 on 2013-05-17
Hello everyone. I don't usually post much, but I've got a strange problem I can't seem to fix on my own. I'm wondering if anyone else is having this issue and if it has anything to do with the latest Ubuntu update. I am using Unity for those who might be wondering. Here's the story so far:

In 12.10, I was able to run Minecraft smoothly with no issues. I stopped playing for a while and recently upgraded Ubuntu to 13.04. Since the upgrade to 13.04, Minecraft also updated to version 1.5.2. I was able to start the game, but every 20 seconds or so the game would lag and stutter, each time getting progressively worse until the game completely froze up. 

I immediately blamed the Minecraft update for the problem, so I downgraded to 1.5.1, 1.5 and then 1.4.7 (all previously working versions) and had the same problem in each version.

Knowing Minecraft itself was not the problem, I tried the following:

Reinstalled OpenJDK 6/7
Reinstalled Oracle Java 7
Removed all Java and reinstalled just OpenJDK
Removed all Java and reinstalled just Oracle Java

Still broken. So, Java is most likely not the problem. Next I tried:

Installed proprietary ATI/AMD drivers
Switched back to open source driver
Updated LWJGL to latest version
Tried OptiFine to improve performance / change autosave interval

These didn't help. Thus far, I'm convinced it's not the video driver, LWJGL or the autosave "lag of death".

Next, I wiped my drive clean and reinstalled Ubuntu 13.04. Installed Java. Installed Minecraft. Still broken. Then, I gave up and finally downgraded Ubuntu back to 12.10, reinstalled everything and it works!

My question is... what changed between 12.10 and 13.04 that would cause this problem? I would appreciate any suggestions or things I might have overlooked, because - even though it is nice - I don't want to be stuck using 12.10 forever. Thanks in advance!

---

### Post by King Dude on 2013-05-17
Did you get an error message at all?

---

### Post by Anathema05 on 2013-05-17
I didn't get any error popups. There may have been clues in a log file somewhere, but it's long gone now.

---

### Post by King Dude on 2013-05-18
What are your computer specifications?

---

### Post by Anathema05 on 2013-05-18
Currently:

Phenom II x3 720 @ 2.8GHz
4 GB DDR3 1600
1GB Radeon HD 5570 Graphics

60GB SSD for OS
1TB HDD (Mounted as /home. This is the drive Minecraft is installed on.)
1TB HDD for backup / storage.

---

