---
title: "Allocating More RAM to Minecraft.jar ?"
date: 2012-06-27
forum: Gaming &amp; Leisure
---

### Post by danieldiazdon on 2012-06-27
I was looking around and found a sh file that was supposed to give the Minecraft.jar more ram as it started up. It is as follows:

 > #!/bin/sh
 BINDIR=/home/daniel/.minecraft
 cd ""
 java -Xmx2048M -Xms1024M -jar Minecraft.jar
 EOF
 chmod +x Minecraft.shWhen I run, the Minecraft.jar starts up and everything, however once I log in, the screen goes black and does nothing else. This is right before the "Mojang" screen is supposed to pop up. I think the issue has to do with the version of java that the 'sh' file is using to run the "minecraft.jar" As of right now, I have installed:

-Sun Java 5.0 Runtime
-Oracle Java 7 Runtime
-OpenJDK Java 7 Runtime
-Sun Java 6 Runtime

To open the Minecraft.jar I have been using the "sun java 6 runtime" and its worked flawlessly. Ive noticed that when I open it with OpenJDK Java 7 runtime, I am able to log in and then the screen goes black just as with the 'sh' file. In addition, it wont even open with Oracle Java 7 Runtime, and it will work with Sun Java 5.0 Runtime.

I think the problem with the 'sh' file is that its trying to run the Minecraft.jar using OpenJDK Java 7 runtime. For it to work effectively, I need it to open using 'Sun Java 6 Runtime'. How would I incorporate the code to do this? 

And if you guys think that this isnt the problem, then what would your best guess be? Im just trying to figure it out. Thanks

---

