---
title: "Minecraft magic launcher problem"
date: 2012-07-10
forum: Gaming &amp; Leisure
---

### Post by cannon_dt on 2012-07-10
Hello to everyone!

I am very new to the world of minecraft and I am slowly getting to be good at it thanks to a lot of help from forums like these and of course other nooks and crannies of the internet. I play minecraft on Ubuntu 11.10 and I have a fairly decent system and the game runs without any serious issues.

So I stumbled upon this launcher and it looks like it would be ideal for me to take my minecraft experience to the next level in terms of mods etc. So I tried to do that but I got stuck - this problem might be more Ubuntu related than the launcher itself but I still need some expertise.

I run the minecraft game using the standard script:
export LD_LIBRARY_PATH="/usr/lib/jvm/java-7-oracle/jre/lib/amd64"
padsp java -Xmx512M -Xms256M -cp Minecraft.jar net.minecraft.LauncherFrame

This works fine. Now when I run the magic launcher it comes up fine but while doing set up, in the advanced tab I dont know what to give for JAVA.
If I leave the default, /usr/lib/jvm/java-7-oracle/jre/bin/java, then while hitting TEST I get the error:
/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
If I try and change it to match the LD_LIBRARY_PATH, I dont have an executable I can point to in the amd64 directory - so I am unable to set it as it does not accept a directory.

I think the problem revolves around setting up java correctly, I am wondering if I should have got a 32 bit java installed. 

I know that to run Minecraft the export statement is mandatory (especially so for java 7), so I am running around
in circles trying to get the launcher working, I am eager to try some mods etc, so I was hoping someone out here can help me out.

Thanks,
Ananth

---

### Post by regor210 on 2012-07-10
Magic launcher

On the  Magic launcher's setup page ModLoader.zip has to be at the top of the top window, so it loads first, that is with mods that require the  ModLoader to run. The same is true of mods that require special sound files & etc... Now OptiFine C Light will not work with with  ModLoader.zip and  OptiFine  C Light will not work with 64 bit Java. I would bet there are other mods that would not work with 64 bit Java. As for me I wont down grade to a 32 bit Java.  I'm concerned that ok, I fixed this Minecraft mod but now I broke something else that needs a  the 64 bit version of Java on my Ubuntu 12.04 64 bit operating system. I would be more inclined to install Ubuntu 12.04 32bit in the first place to keep from having the headaches that would likely come from overly modifying my Ubuntu 64 bit operating system.
 
Right now the kids are using 
MagicLauncher_0.9.8.jar
Openjdk-7

to run 
TooManyItems2012_04_13_1.2.5.zip
1.2.5 carmod v2.2.zip

There are a lot of other Mods they have run in the past but this is what there using right now.


[http://www.minecraftforum.net/topic/249637-125-optifine-hd-c3-fps-boost-hd-textures-aa-af-and-much-more/](http://www.minecraftforum.net/topic/249637-125-optifine-hd-c3-fps-boost-hd-textures-aa-af-and-much-more/)

[http://www.minecraftmine.org/magic-launcher-minecraft/](http://www.minecraftmine.org/magic-launcher-minecraft/)

---

### Post by cannon_dt on 2012-07-11
Regor,
I dont get it, are you telling me that there is no solution to this? I want to be able to use 64 bit Ubuntu only and from what you are suggesting downgrading the Java alone is not a sound option. So in effect, I cannot run Magic Launcher right?

I get all the stuff you say about the mods, for me the problem is Java (the setting to give in the advanced tab) for magic launcher to use in order to execute. Can you please clarify?

Also should I shift out of sun java to open jre? Is that what you are suggesting? I am sorry but your post has left me more confused, please clarify :)

Ananth

---

### Post by cannon_dt on 2012-07-11
Also Regor,
I am not even using any mod as of now. I am just trying to use the plain vanilla magic launcher and trying to use "Setup" option to ready the whole thing - that is when I have this Java problem - so what I wanted to say that I am not even close to loading up and using a mod, still some way to go for that.

Ananth

---

### Post by regor210 on 2012-07-11
Sorry I didn't seem to make it clear that yes we are using vanilla. straight out of the box.  Magic launcher with 64bit Java but there are some mode's that don't work. Yes it should work fine like this

Download MagicLauncher for **Windows/Mac/Linux** not the one for Windows/Mac
[http://www.minecraftforum.net/topic/939149-launcher-magic-launcher-098-mods-options-news/](http://www.minecraftforum.net/topic/939149-launcher-magic-launcher-098-mods-options-news/)

Open a terminal ctrl+alt+t cut and paste the following commands into the terminal window one line at a time minus the $.

$ cd ~/Downloads

$ sudo chmod a+x MagicLauncher_0.9.8.jar


$ cd ~/Downloads && java -jar MagicLauncher_0.9.8.jar

Note. that you will have to make sure the mods you use have permission for you to use them. You can right click on them in your download folder then goto > Properties> click on the Permissions tab and make sure the Owner has Read and Write/ Group  Read and Write/ Other Read only is good.

---

### Post by cannon_dt on 2012-07-11
Regor,
I guess I have still not come across clearly to you.
I have already done all that you have said and the magic launcher works. The problem comes AFTER that.
Once I click the setup button and in that the "advanced" tab I am trying to set the right path for Java and then am trying to hit the "test" button.
Hope I have clarified. It is while launching minecraft from the magiv launcher using the "test" button that the java conflict arises - just running magic launcher or just running minecraft directly using the java 7 has no issues.

Please let me know if I have clearly stated my problem.

BTW, I did get the right jar file.

Ananth

---

### Post by regor210 on 2012-07-11
My Advanced Tab shows

Windows s....  854X480
Memory       1024 MB
Java                   **/usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java**
Parameters   
Base folder   /home/regor210/.minecraft

This is the default and is working here

Here's what I get with Oracle Java 7 after  
$ sudo update-alternatives --config java

Its working and all is the same except.

Java                   **/usr/lib/jvm/java-7-oracle/jre/bin/java**

Normal I use  Openjdk-7 with all the extensions 

$ sudo apt-get update

$ sudo apt-get upgrade

$ sudo apt-get install ca-certificates-java icedtea-7-jre-cacao icedtea-7-jre-jamvm java-common libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgnome2-0 libgnomevfs2-0 libgnomevfs2-common openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib ttf-dejavu-extra tzdata-java

I'm on Minecraft version 1.2.5 and using MagicLauncher_0.9.8.jar

---

### Post by cannon_dt on 2012-07-12
Well Regor, that WAS the problem. Somewhere on the internet, I read that java 7 oracle is better than openjdk and I made sure I updated. 
As you said the java path was **/usr/lib/jvm/java-7-oracle/jre/bin/java** and this was what was causing the **architecture word width mismatch** exception.

Looks like open jdk has a better java path that takes into account the amd64 bit. 

But I have more news - today when I opened the magic launcher and tried the same stuff, it worked. Upon hitting test, it did launch my minecraft game though I did note that even though my items were intact my achievements had croaked and I seem to have to start at the very beginning on that. Any idea why is that? I really dont know what I did but up until last night I was getting the "architecture word width mismatch" exception. Wonder what has set itself right?

I have another issue now - if I give an invalid user name password in order to play offline (in the main screen), upon hitting Play Offline, everything just closes and the entire java process quits - including magic launcher. I dont play on a server and this is what is convenient for me, so can you please tell me if there is some setting I am missing that is causing this?

Thanks for all the help.
Ananth

---

### Post by regor210 on 2012-07-12
I had some permissions issues at one time.

When you have  Magic Launcher start Java-7  that starts Minecraft  & mods restarting Java-7, users and groups some times get all mixed up and  permissions issues can become a problem.

$ sudo chmod -R 777 .minecraft

May fix your problems.


[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)
chmod 777 file change the permissions of the file file to read, write, and execute for all.


This would be better but I had problem updating Minecraft when using it. 

$ sudo chmod -R 774 .minecraft

---

### Post by cannon_dt on 2012-07-13
Did not help. In fact after the chmod, the magic launcher itself does not work. I mean it launches but is in a frozen state, none of the buttons work. Guess I will stick to the classic minecraft and not be greedy for mods etc :(

Thanks for all the advice Regor, appreciate your patience with me 

Ananth

---

