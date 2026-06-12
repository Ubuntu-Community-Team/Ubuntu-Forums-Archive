---
title: "How to set Java as a default application in Ubuntu 13.04 &amp; 13.10"
date: 2013-10-21
forum: Gaming &amp; Leisure
---

### Post by Teethdude on 2013-10-21
It took me forever to find this, so I'm posting it so others will benefit from it in the future. It is really helpful for anyone that plays Minecraft.

Step 1: Open your file manager and locate ```
/usr/share/applications/
```
Step 2: Find your Java Runtime. This will either be OpenJDK or Oracle. Mine is "Oracle Java 7 Runtime"
Step 3: Keeping this window open, use the Terminal to open gedit as Root. ```
sudo gedit
```
Step 4: Drag your Java Runtime into the gedit window. You should see this: ```


[Desktop Entry]
Encoding=UTF-8
Name=Oracle Java 7 Runtime
Comment=Oracle Java 7 Runtime
Exec=/usr/lib/jvm/java-7-oracle/bin/java -jar %f
Terminal=false
Type=Application
Icon=oracle_java7
MimeType=application/x-java-archive;application/java-archive;application/x-jar;
NoDisplay=true

```

Step 5: Change "NoDisplay=true" to "NoDisplay=false"
Step 6: Save the file. Now you should be able to set the Java Runtime as the default Application.
Hope you benefit from it!

---

