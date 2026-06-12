---
title: "Minecraft installer Gets Stuck On Starting Launcher."
date: 2016-01-24
forum: Gaming &amp; Leisure
---

### Post by devon11 on 2016-01-24
Running Ubuntu 15.10
OpenJDK Java 7 Runtime installed 
Nothing happens after it says that its "starting launcher." 

Running java -jar '/home/devon/Desktop/Minecraft.jar' outputs : 

```
Bootstrap (v5)Current time is Jan 24, 2016 12:09:24 AM
System.getProperty('os.name') == 'Linux'
System.getProperty('os.version') == '4.2.0-25-generic'
System.getProperty('os.arch') == 'amd64'
System.getProperty('java.version') == '1.7.0_91'
System.getProperty('java.vendor') == 'Oracle Corporation'
System.getProperty('sun.arch.data.model') == '64'


Looking for update
Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma
Got reply in: 1233ms
No update found.
Reversing LZMA on /home/devon/.minecraft/launcher.pack.lzma to /home/devon/.minecraft/launcher.pack
Unpacking /home/devon/.minecraft/launcher.pack to /home/devon/.minecraft/launcher.jar
Cleaning up /home/devon/.minecraft/launcher.pack
Starting launcher.
```

---

### Post by 2ndthief on 2016-01-24
I have checked my console, and the only difference I can see between my output and yours is the Java version. Maybe try going to java 1.8 and seeing if it will go. 

~/Desktop$ java -jar ./Minecraft.jar 
Bootstrap (v5)
Current time is Jan 24, 2016 4:03:36 PM
System.getProperty('os.name') == 'Linux'
System.getProperty('os.version') == '4.2.0-25-generic'
System.getProperty('os.arch') == 'amd64'
System.getProperty('java.version') == '1.8.0_66-internal'
System.getProperty('java.vendor') == 'Oracle Corporation'
System.getProperty('sun.arch.data.model') == '64'


Looking for update
Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma)
Got reply in: 497ms
No update found.
Reversing LZMA on /home/secondthief/.minecraft/launcher.pack.lzma to /home/secondthief/.minecraft/launcher.pack
Unpacking /home/secondthief/.minecraft/launcher.pack to /home/secondthief/.minecraft/launcher.jar
Cleaning up /home/secondthief/.minecraft/launcher.pack
Starting launcher.
[16:03:39 INFO]: Minecraft Launcher 1.6.44 (through bootstrap 5) started on linux...
[16:03:39 INFO]: Current time is Jan 24, 2016 4:03:39 PM
[16:03:39 INFO]: System.getProperty('os.name') == 'Linux'
[16:03:39 INFO]: System.getProperty('os.version') == '4.2.0-25-generic'
[16:03:39 INFO]: System.getProperty('os.arch') == 'amd64'
[16:03:39 INFO]: System.getProperty('java.version') == '1.8.0_66-internal'
[16:03:39 INFO]: System.getProperty('java.vendor') == 'Oracle Corporation'

---

### Post by maxinstuff2 on 2016-01-24
Doesn't MineCraft have a non-java launcher now?

---

### Post by devon11 on 2016-01-25
Not that I know of.. its still comes as a .jar

I tried that. I just went back to 14.04 LTS mainly because I was having a lot of issues running all kinds of programs.

---

