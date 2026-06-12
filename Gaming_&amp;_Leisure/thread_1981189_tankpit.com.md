---
title: "tankpit.com"
date: 2012-05-16
forum: Gaming &amp; Leisure
---

### Post by Twilk73 on 2012-05-16
Has anyone got thjs website working. The game is a java based game and i cant get it to work. Any help would be thanked. I am even a little curious if it will even work with linux i guess. I mean i cant seem to get it to work at all.

---

### Post by regor210 on 2012-05-16
If your using Ubuntu 12.04 make sure you have Openjdk-7 and all the Openjdk-7 extentions.

To open a terminal press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window one line at a time minus the $.

$ sudo apt-get update

$ sudo apt-get upgrade

$ sudo apt-get install ca-certificates-java icedtea-7-jre-cacao icedtea-7-jre-jamvm java-common libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgnome2-0 libgnomevfs2-0 libgnomevfs2-common openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib ttf-dejavu-extra tzdata-java

Seems to be working for me

---

