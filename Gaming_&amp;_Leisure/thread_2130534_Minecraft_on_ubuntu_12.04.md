---
title: "Minecraft on ubuntu 12.04"
date: 2013-03-29
forum: Gaming &amp; Leisure
---

### Post by Tucker1 on 2013-03-29
I can't get minecradt to run on Ubuntu 12.04 either on line or even how to install the download. 

Can someone tell me in VERY simple terms how to fix the following... I have used Ubuntu for a couple of years as an OS but just to surf the web etc... so I really don't understand much beyond that, so any instructions beyond that you would give to your granny will be over my head! 

1) When I try to run minecraft for the kids on line it gives me a blank screen. I have tried downloading different Java downloads from the software centre and none make any difference! 

2) When I opt to download minecraft, it downloads in chrome and when I then open the zip file I have no idea how to execute it and install the thing? 

I've done all of the above in via my windows log in, but would like to run it on Ubuntu, but I as it's not sort of just done automatically via following a simple on screen instruction, I can't get going? 

Is there a simple man's way of running minecraft or do I just give up with Ubuntu all together as it just seems hard work with stuff like this?

---

### Post by Reina on 2013-03-29
What you downloaded was a jar file, which unfortunately when executed in chrome is unpackaged like a zip file on linux. Go to your downloads folder, rightclick minecraft.jar go to properties, then permissions, and set execute to "anyone". Try opening minecraft with openjre now (right click on it because it might open with the unzip program by default) It should work.

---

### Post by Tucker1 on 2013-03-29
Thanks for the reply and that has helped with part two :)

I have managed to change the properties and I opened it with OpenJDK and I have now managed to save it to my desk top and it runs. 

I still can't run it in the web browser at the minute!!

---

### Post by Reina on 2013-03-30
Go to the ubuntu software center app on your computer and find "icedtea java plugin" and install it, along with any other things it asks to install with it (which you wont need to search out for since it will download them with it). Just to be safe I should probably say this too (sorry): Restart your browser, and when you attempt watch for a message to pop up somewhere in the browser asking if its okay to run the java thing on minecraft's website. Not too long from then (though this might take a minute or 2) you'll get another prompt from the java instead of the browser asking if its okay to run the program. Wait a bit longer (java stuff can take a while to open up in a browser) and the game should work.

---

### Post by Tucker1 on 2013-03-30
Thanks
I have the Icedtea java plugin installed. When I loads the game in the browser it looks like it's going to load up asks for permission to run on this website, but then it just turns to a grey screen and that's it. It doesn't do anything else.

---

### Post by Perfect Storm on 2013-03-30
May be try with oracle java instead?
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)
Though open java is nice, it stills have some problems.

---

### Post by Tucker1 on 2013-03-30
Thanks
I just installed the oracle java and whilst it went beyond the grey screen it didn't load the game in the browser and freezes on the loading screen. Also the downloaded version no longer worked with that version of Java. 

I have just un-installed it and I am back to a grey screen on the browser version and the downloaded game works OK again!!

It's looking like I am going to have to stick to loading the windows dual boot unless there's something else I can try! It's a bit frustrating as I really don't like bothering with windows.

---

### Post by efflandt on 2013-03-30
I have never had luck running minecraft in a browser in Linux. But the **minecraft.jar** should run fine if you have openjdk-6-jre or openjdk-7-jre installed and proper video drivers. If you have old Intel integrated video it may be a bit sluggish.

It is best to download the **minecraft.jar** launcher in Linux, or at least with Firefox or something if you download it from Windows, because Internet Explorer would likely misname the file minecraft.zip. The minecraft.jar is downloaded from [http://minecraft.net/download](http://minecraft.net/download)

In a terminal in X, **cd** to the directory containing the downloaded file and launch it with:```
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```You can give it more RAM if you want to, it will start out with the amount specified by -Xms and use more if it needs it up to -Xmx. The first time you run it, it will download and create other files in ~/.minecraft/

But you always launch it from the minecraft.jar you downloaded, NOT the one that ends up as ~/.minecraft/bin/minecraft.jar (which does not contain the launcher). You can make a shell script to launch it. And if you occasionally get stuck movement keys, just hit the same key again in direction you are moving (lwjgl files can be updated from what is in minecraft to resolve that). But you can look into that once it is working.

---

### Post by Horbo on 2013-04-02
Full guide here: [https://help.ubuntu.com/community/InstallMinecraft147](https://help.ubuntu.com/community/InstallMinecraft147)

---

### Post by Dawit Tilahun on 2013-04-04
In my experience (witch is not much) everything on minecraft(including the online game) works fine once I installed openjdk-6. But openjdk-7 just messes things up on the new ubuntu.
Look at this site it helps I promise

[http://m.wikihow.com/Play-Minecraft-in-Ubuntu](http://m.wikihow.com/Play-Minecraft-in-Ubuntu)

Hope this helps.

---

