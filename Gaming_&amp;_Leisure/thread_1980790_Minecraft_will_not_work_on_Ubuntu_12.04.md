---
title: "Minecraft will not work on Ubuntu 12.04"
date: 2012-05-15
forum: Gaming &amp; Leisure
---

### Post by johnboy601 on 2012-05-15
I upgraded to 12.04 yesterday. I was on 11.10 and Minecraft was working fine. I upgraded, and the page to chose "Single Player" MultiPlayer" and "Texture Packs" Doesnt work. The picture shows up, but no background animation, no yellow moving text (The text changes every time I reopen but doesn’t move around) and I can't click anything. I really enjoy playing Minecraft and can't afford a computer that will actually work. I'm starting to get mad that I upgraded to 12.04 (If you know of a way to get back to 11.10, please tell me)

---

### Post by regor210 on 2012-05-15
Sometimes Ubuntu&#8217;s 3D desktop effects has issues with Minecraft. You could try logging out of your Desktop, select Unity 2D then log back in.

And check that you did these things when installing Minecraft in Ubuntu 12.04.    

Ubuntu 12.04

Download minecraft.jar from here.
[http://www.minecraft.net/download](http://www.minecraft.net/download)

Download the Lightweight Java Game Library or lwjgl from here
[http://sourceforge.net/projects/java-game-lib/files/latest/download?source=files](http://sourceforge.net/projects/java-game-lib/files/latest/download?source=files)

If you haven&#8217;t yet run Minecraft do so to automatically to create the folder .minecraft in your home folder. Note. You will get a black screen.

Open a terminal then press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window one line at a time minus the $.
------------------------------------------------
#make sure you have Openjdk-7 and all the Openjdk-7 extentions.

$ sudo apt-get update

$ sudo apt-get upgrade

$ sudo apt-get install ca-certificates-java icedtea-7-jre-cacao icedtea-7-jre-jamvm java-common libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgnome2-0 libgnomevfs2-0 libgnomevfs2-common openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib ttf-dejavu-extra tzdata-java
-------------------------------------------------------------------------

$ cd ~/Downloads

$ sudo chmod a+x minecraft.jar

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame
-------------------------------------------------
Close Minecraft

In Ubuntu 12.04 you have to update lwjgl by hand due to Java 7 or Openjdk-7. You can go here or read down and use the command line.

Lightweight Java Game Library download
lwjgl-2.8.3
[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)


The command line.

Then open a terminal ctrl+alt+t cut and paste the following commands into the terminal window one line at a time minus the $.
------------------------------------------------------------------------------
#update LWJGL
# Note. lwjgl-2.8.3.zip will change over time as updates become available. so you will have to change the names as needed.
# 4-29-2012 the Minecraft version is 1.2.5. When version 1.2.6 comes out its likely you will have to update lwjgl by hand again. Word is, when Minecraft hits version 2.0 they will switch to Java 7 and you will not need to update lwjgl by hand any more.

# update lwjgl by replacing these 9 files

$ cd ~/Downloads

$ unzip lwjgl-2.8.3.zip

# type A for all

$ sudo cp -f ~/Downloads/lwjgl-2.8.3/jar/jinput.jar ~/.minecraft/bin/jinput.jar
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/jar/lwjgl_util.jar ~/.minecraft/bin/lwjgl_util.jar
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/jar/lwjgl.jar ~/.minecraft/bin/lwjgl.jar


$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/libjinput-linux.so ~/.minecraft/bin/natives/libjinput-linux.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/libjinput-linux64.so ~/.minecraft/bin/natives/libjinput-linux64.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/liblwjgl.so ~/.minecraft/bin/natives/liblwjgl.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/liblwjgl64.so ~/.minecraft/bin/natives/liblwjgl64.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/libopenal.so ~/.minecraft/bin/natives/libopenal.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/libopenal64.so ~/.minecraft/bin/natives/libopenal64.so

# close the terminal.
# Open a new terminal ctrl+alt+t

------------------------------------------------------------------------------------
#make sure everything has permission for you to run it.

$ sudo chmod -R 777 .minecraft

$ cd ~/Downloads

$ sudo chmod a+x minecraft.jar

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame

Note. if you have 2GB or more ram on your mother board you may get better performance by alocating more ram to Minecraft. $ java -Xmx1048M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame



------------------------------------------------------------------------------------

---

### Post by skeetlez on 2012-05-16
you have to start minecraft and force update so it download the natives for linux

---

### Post by johnboy601 on 2012-05-16
> **regor210 said:**
> Sometimes Ubuntu’s 3D desktop effects has issues with Minecraft. You could try logging out of your Desktop, select Unity 2D then log back in.

And check that you did these things when installing Minecraft in Ubuntu 12.04.    
------------------------------------------------------------------------------------

I am using Ubuntu 2D and it wont work. I was using 2D in 11.10 when it was working. Now all I want to do is go back to 11.10

---

### Post by mode7 on 2012-05-17
The only way you're getting back to 11.10 is by completely reinstalling Ubuntu 11.10.
You can of course still save your worlds and texture packs from "~/.minecraft/" before reinstalling.
I think that's excessive, though. You should try using the latest stable version of Ubuntu unless you absolutely must go back.

What version of Java are you running? I.e. Openjdk or Sun/Oracle Java, 6 or 7, etc..
Open a terminal and get the output of "java -version".

Also, what are your system specs? Most importantly, your video card and drivers. (Open source or proprietary drivers?)

FWIW, I can run Minecraft under Ubuntu 12.04 using OpenJDK 6, with nothing else changed. I think I tried Java 7 and got the "black screen", with updated LWJGL too. It varies for every computer.

---

### Post by kce007 on 2012-05-17
No problems with minecraft on newest ubuntu :) installed like normal programs

---

### Post by fallenshadow on 2012-05-18
I got it working by doing the following:

Install openJDK 7.

Download the Lightweight Java Game Library or lwjgl from here
[http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip/download](http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip/download)

Extract this folder.

Replace the files inside ~/.minecraft with the ones (with the same filename) in the folder you just extracted.

Right click your minecraft.jar click run with OpenJDK 7.

Success! :)

---

### Post by ELD on 2012-05-18
Try deleting the .minecraft folder and then running the minecraft.jar again to re-download if all else fails, it could be a bad download.

---

### Post by mentorious on 2012-05-18
I had the same problem on Ubuntu 12.04 with OpenJDK7. I thought it was something with java (earlier I played on Sun java 6) but errors were only on 64bit in LWJGL.

So, you need download these archive (***[http://lwjgl.org/download.php](http://lwjgl.org/download.php)***) and unzip all files from folder "jar" inside folder ~/.minecraft/bin, also from folder "native/linux" to ~/.minecraft/natives.

After this Minecraft works perfectly.

---

### Post by johnboy601 on 2012-05-19
I have tried all of theses things with none of them working. I have decided to mirror my drive and then install Ubuntu 12.04 from a live CD so it will be like new. Thanks anyways.

---

### Post by Rahbee Kannuhn on 2012-07-16
argh, so much for java "write once, run everywhere". 
I keep a windows partition handy as a gaming platform anyway, will wait for a proper fix for the linux client, after an hour of toying with all the various fixes, still a black screen, ugh.

---

### Post by efflandt on 2012-07-19
Sometimes people make things more complicated than they need to be.  I have been running minecraft since v1.8 beta in 64-bit Ubuntu using openjdk-6-jre, and that works fine in in 12.04 (including snapshots of upcoming 1.3 version).  I have been using lwjgl 2.6 only because movement keys would occasionally stick with lwjgl 2.4.2 that came with minecraft.  Works great at 1080p on desktop in my sig.

However on laptop from 2006 with Intel 1.66x2 GHz 2.5 GB and integrated Intel video it runs noticeably slower than a 1x2 GHz tablet PC w/2 GB and ATI HD video ( both at same 1280x800 screen resolution).  I don't have anything with Intel HD graphics to see if that has issues.

---

### Post by cbennett926 on 2012-07-19
FWIW 

I can run perfectly fine, no lag, and with an HD texture pack

---

### Post by dmaxel on 2012-07-24
Hey everyone,

Sorry to hijack this thread, but I also have an issue. Pretty much, I cannot chat. The chat prompt appears when I hit "T", but after I enter in my message, it does not get sent off when I hit "Enter".

I have no idea what else I could do to fix this. I've used the latest Minecraft as well as updated the lwjgl, but that didn't help. I even tried the latest Minecraft snapshot and a lwjgl nightly, but that didn't help either. Why am I having this issue?

---

### Post by regor210 on 2012-07-24
Maybe your having a permisstions issue?

To open a terminal press ctrl+alt+t all at the same time. Then cut and paste the following command into the terminal window minus the $.


#make sure everything has permission for you to run it. 

$ sudo chmod -R 777 .minecraft 
---------------------------------
If thats no help try running Minecraft in terminal and post what you get after you hit t. That is if theres an error.

---

### Post by dmaxel on 2012-07-25
> **regor210 said:**
> Maybe your having a permisstions issue?

To open a terminal press ctrl+alt+t all at the same time. Then cut and paste the following command into the terminal window minus the $.


#make sure everything has permission for you to run it. 

$ sudo chmod -R 777 .minecraft 
---------------------------------
If thats no help try running Minecraft in terminal and post what you get after you hit t. That is if theres an error.
Tried the permissions tip, but that didn't help.

I launched it in the terminal, and discovered I was using OpenJDK 6 while I had both versions installed. So I removed OpenJDK 6 so I could use OpenJDK 7. It used OpenJDK 7 successfully but it didn't fix the chat problem.

This is really weird...? I have this problem for chat as well as Minecraft commands.

---

### Post by tdawgf on 2012-07-30
I had a similar problem in the past on windows but it was because I was using a 32bit version of java on a 64bit OS. Not sure if that is possible in Ubuntu though.

---

### Post by dmaxel on 2012-08-01
That wasn't my problem, but I finally figured it out! Apparently, my keyboard is special and Ubuntu decided to make it special when it mapped it out. So, for my enter key, it was using the "KP_Enter" function. I had to remap it to use the "Return" function. Now it works just fine.

More info: [http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys](http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys)

---

### Post by KaizerLinux on 2012-08-01
> **efflandt said:**
>  I have been using lwjgl 2.6 only because movement keys would occasionally stick with lwjgl 2.4.2 that came with minecraft. 
 
Ah! My movement keys keep sticking as well. How do I update lwjgl? Synaptic?

---

### Post by efflandt on 2012-08-02
You can get lwjgl at
[http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/](http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/)

You download the lwjgl file with the version number.  I have been using 2.6 since minecraft beta versions, which works with openjdk-6, even for minecraft 1.3.1 in 64-bit 12.04.  If you are using openjdk-7 or Java 7 you could try lwjgl 2.8.4 (since someone else seems to be mentioning that).

If you right click on the zip file the Archive Manager can extract it to a directory.  Then you need to copy and replace following files from lwjgl-(version)/jar/ to .minecraft/bin/

jinput.jar
lwjgl.jar
lwjgl_util.jar

And following from lwjgl-(version)/native/linux/ to .minecraft/bin/natives/

libjinputlinux.so
libjinputlinux64.so
liblwjgl.so
liblwjgl64.so
libopenal.so
libopenal64.so

That should fix the sticky movement keys that occasionally happen with lwjgl 2.4.2 included in minecraft.

---

### Post by zenlakin on 2012-08-04
I am also having problems with running minecraft under ubuntu 12.04. I have a fresh install of Ubuntu 12.04 64 bit. I have installed both open jdk 6, sun java 6 and open jdk 7 and nothing seems to work as I still just get the screen after logging in and selecting "play demo" that says "Updating Minecraft" "Done Loading" and it never goes any further. Any thoughts?

---

### Post by DarkAmbient on 2012-08-04
Try update your lwjgl-files. I don't have Minecraft on this computer so I might be somewhat off.. but start with downloading lwjgl _[http://lwjgl.org/download.php]("http://lwjgl.org/download.php")_

Extract zip, open folder and go to lwjgl-2.8.4/jar. 
Copy or move lwjgl.jar, jinput.jar and lwjgl_util.jar to ~/.minecraft/bin on your computer.

Go down one step in the extracted folder and open natives/linux.
Copy liblwjgl.so to ~/.minecraft/bin/natives

EDIT: _copy all .so files to ~/.minecraft/bin/natives. liblwjgl.so on its own wasnt enough_

**To view hidden files in Nautilus, such as .minecraft in your homefolder. Press control+h.**

Hope this helps someone. :)

---

### Post by Bubbelgum on 2012-08-05
Hi 

i did try to follow regor210, i can start mincraft login and the get a black window. been trying to read all the other post to find what ppl have done to fix it. 

well now iam asking any one have an ide of what to do, ubunto 12.04  whit OpenJDK kava 7. iam new to this i might add, so ppl know. last time i was in a linux inviromet was readhat 6 about 10 years ago. so please be gentle whit me :D

is ububtu running a generik grafik driver for me or is it running an ati driver? does it mather for minecraft? :confused:

Thx for any help

---

### Post by DarkAmbient on 2012-08-06
> **Bubbelgum said:**
> Hi 

i did try to follow regor210, i can start mincraft login and the get a black window. been trying to read all the other post to find what ppl have done to fix it. 

well now iam asking any one have an ide of what to do, ubunto 12.04  whit OpenJDK kava 7. iam new to this i might add, so ppl know. last time i was in a linux inviromet was readhat 6 about 10 years ago. so please be gentle whit me :D

is ububtu running a generik grafik driver for me or is it running an ati driver? does it mather for minecraft? :confused:

Thx for any help

Saw now that others had mentioned the fix i described before me.. no disrespect to them. Just didn't read pre-posts...

Anyway, that fix go me pasted black-screen. And I'm pretty sure that Minecraft will run without Hardwareacceleration, 3D-drivers etc...

---

### Post by DarkAmbient on 2012-08-06
Wrote a installer for Minecraft in bash that works w/o a terminal. It asks if you wanna install OpenJDK7 as well. And fixes the black-screen-issue during installation. Run this even if you only wanna fix the black-screen-issue.

[SIZE="3"]Download the installer [[COLOR="Blue"]HERE[/COLOR]]("http://ubuntuone.com/0viArrNiGfDcTKabKaPDOL")[/SIZE] or find it attached to this post.

[SIZE="3"][COLOR="Blue"]
To run the installer...
[LIST]
[*]Download "minecraftinstaller.sh".
[*]Rightclick on it and choose "properties".
[*]Beneath the "permissions" tab check the "Allow executing file as program" -option.
[*]Close properties and run "minecraftinstaller.sh" by doubleclicking it and choose "run"
[/LIST]

OR

To start it from a terminal.
[LIST]
[*]Download "minecraftinstaller.sh" to your homefolder (easiest)
[*]Open a terminal and type "sh minecraftinstaller.sh" (without the quotes)
[/LIST]
[/COLOR][/SIZE]

Enjoy!

---

### Post by Bubbelgum on 2012-08-06
Nice, it will make this easyer  :popcorn:

---

### Post by cs34026 on 2012-08-08
very nice but will it handle minecraft forge and other mods that have already came out? i had mods n stuff running earlier using a mod pack base as a quick solution but is there any other easier way because it seems once i get modloader or forge (which has modloader ) minecraft loves to black screen and not send error reports but those mods are too tempting for me not to play without them

---

### Post by redbikemaster on 2012-08-10
Thanks, DarkAmbient. That fixed my problem too.

One question though.

How do I get it to have the Minecraft block as an icon?

---

### Post by redbikemaster on 2012-08-12
Whenever I play Minecraft, it will work for a little while, then crash without warning or errors. Is it Java crashing? If so, how do I fix this?

I found what looks to be Java error logs, but they're too big to attach to this post.

---

### Post by sffvba[e0rt on 2012-08-12
> **redbikemaster said:**
> Whenever I play Minecraft, it will work for a little while, then crash without warning or errors. Is it Java crashing? If so, how do I fix this?

It is possible that you need to allocate more memory to the game.  Just edit the launcher you created for it (but don't try and allocate more memory than you have installed :p)


404

---

### Post by redbikemaster on 2012-08-12
It's already got 2GB allocated. I have 8GB total.

UPDATE: The file is now non-executable, so I have to run DarkAmbient's Script.

---

### Post by sffvba[e0rt on 2012-08-12
Hmmm... 2 GB is plenty.  I have never tried any way except the standard method described on the Minecraft website to get it to work and I have never had any issues.


404

---

### Post by redbikemaster on 2012-08-13
Got it to be executable again. Will find out if it still crashes.

---

### Post by redbikemaster on 2012-08-13
Played for 2 hours straight just now, and no crashes!

---

### Post by zenlakin on 2012-08-13
I am still trying to get minecraft to work and allocate more memory but when I try to run the command from the terminal I get the login screen but then I just get a black screen... If I right click on the .jar file and select open with openjdk java 7 runtime it works perfectly.. Below is my output when running from command line...

sudo java -Xmx2048M -Xms1024M -jar /home/mod/Desktop/MinecraftSP.jar
Hello!
URL: file:/root/.minecraft/bin/lwjgl.jar
URL: file:/root/.minecraft/bin/jinput.jar
URL: file:/root/.minecraft/bin/lwjgl_util.jar
URL: file:/root/.minecraft/bin/minecraft.jar
URL: file:/root/.minecraft/bin/linux_natives.jar
Exception in thread "Thread-1" java.lang.UnsatisfiedLinkError: /root/.minecraft/bin/natives/liblwjgl.so: /root/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1924)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1821)
	at java.lang.Runtime.load0(Runtime.java:792)
	at java.lang.System.load(System.java:1059)
	at org.lwjgl.Sys$1.run(Sys.java:69)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
	at org.lwjgl.Sys.loadLibrary(Sys.java:81)
	at org.lwjgl.Sys.<clinit>(Sys.java:98)
	at net.minecraft.client.Minecraft.F(SourceFile:1853)
	at aoe.<init>(SourceFile:20)
	at net.minecraft.client.Minecraft.<init>(SourceFile:77)
	at anv.<init>(SourceFile:36)
	at net.minecraft.client.MinecraftApplet.init(SourceFile:36)
	at net.minecraft.Launcher.replace(Launcher.java:153)
	at net.minecraft.Launcher$1.run(Launcher.java:94)

---

### Post by QsoftStudios on 2012-08-13
Force update your jar file, it might also be you need to update your java or it could be the actual texture pack

---

### Post by zenlakin on 2012-08-13
After doing that now everything is broke...

No I can't right click the .jar file and open with openjdk java 7 or run it from command line without getting a black screen...

---

### Post by zenlakin on 2012-08-16
nobody else is having this problem?

---

### Post by MasterNetra on 2012-08-16
Yea there are issues with Java 7 it works fine with Java 6. So use  openjdk java 6 instead. I had simliar issues with using Java 7 in windows as well but again Java 6 works fine. Using Openjdk 6 you won't need to manuelly install lwjgl, just grab the .jar from minecraft.net and it will do the work for you.

On a somewhat related note I would also recommend using magiclauncher to handle mods and MC in general (after you initially get it "installed" or downloaded rather. It can handle mods by adding them while their in a .zip (most mods) including .jar installs which it does without ever actually adding anything to the main .jar. Just make sure the mod isn't in a subfolder ex. zip archive: CrapMod/ contents" if they are unzip go into folder and zip the contents and use that.

---

### Post by efflandt on 2012-08-16
> **redbikemaster said:**
> How do I get it to have the Minecraft block as an icon?

Use the file manager to open the original **minecraft.jar** launcher (not the one in ~/.minecraft/bin/) with Archive Manager. Go to **net/minecraft/** and copy **favicon.png** to your system somewhere, and rename it minecraft.png or whatever.  I use that for desktop launcher or for Unity bar (install "Main Menu" aka "alacarte" to add launchers to Unity).

For minecraft server icon I put a white "S" on the icon with gimp.

---

### Post by DarkAmbient on 2012-08-17
Updated my Minecraft-installer somewhat today, so after installation an icon for starting Minecraft appear in your application-menu (or Unity Dash). And upon starting the game it reserves exactly half of your computers-memory to Minecraft.

Saw that allocateB wrote a script for installing Minecraft as well, that one seems great so idk if this one is necessary. But as I've been at it for a while since I'm trying to learn Bash, so I'll link it anyway, it's quite an easy and pure graphical few-click installation. :)

Download link: [HERE]("http://ubuntuone.com/4bL0SBoreLlP5HQgFErMDl")

_Download, allow to run it as an application then doubleclick it. Have fun!_

Edit:

Will update script soon so you can "uninstall" Minecraft with it as well... right now to uninstall after you've installed using my installer, run this in a terminal ```
sudo rm /usr/share/applications/minecraft.desktop && rm -R ~/.minecraft
```(Heads up though.. this will wipe out everything with Minecraft, savefiles, settings...) Might add an option asking the user if he/she would like to backup the (offline-) worlds first though.. hmm

---

### Post by redbikemaster on 2012-08-20
So, I've finally gotten Minecraft working, but I can't install any mods. NONE. I've tried the old-school way, which of course is to directly insert the mod's .class files into minecraft.jar then deleting META-INF, and I also tried using [Magic Launcher.](http://www.minecraftforum.net/topic/939149-launcher-magic-launcher-098-mods-options-news/) Either way, I end up with Minecraft's infamous black screen. What am I doing wrong? I used to play it on Windows, and successfully installed mods on there. I also did it on a Mac. Both on the first try!

---

### Post by bitcrow on 2012-08-20
> **zenlakin said:**
> I am also having problems with running minecraft under ubuntu 12.04. I have a fresh install of Ubuntu 12.04 64 bit. I have installed both open jdk 6, sun java 6 and open jdk 7 and nothing seems to work as I still just get the screen after logging in and selecting "play demo" that says "Updating Minecraft" "Done Loading" and it never goes any further. Any thoughts?

I have the same problem. I have 32-bit though. Those lwjgl things work neither and bin-folder is empty anyway so it would be pretty odd to replace anything there. I've also tried to put entire extracted lwjgl-update to the bin-folder without any results.

---

### Post by redbikemaster on 2012-08-22
> **redbikemaster said:**
> So, I've finally gotten Minecraft working, but I can't install any mods. NONE. I've tried the old-school way, which of course is to directly insert the mod's .class files into minecraft.jar then deleting META-INF, and I also tried using [Magic Launcher.](http://www.minecraftforum.net/topic/939149-launcher-magic-launcher-098-mods-options-news/) Either way, I end up with Minecraft's infamous black screen. What am I doing wrong? I used to play it on Windows, and successfully installed mods on there. I also did it on a Mac. Both on the first try!

Nevermind. Had Java 6 & 7 both installed. :P

---

### Post by DarkAmbient on 2012-08-22
> **bitcrow said:**
> I have the same problem. I have 32-bit though. Those lwjgl things work neither and bin-folder is empty anyway so it would be pretty odd to replace anything there. I've also tried to put entire extracted lwjgl-update to the bin-folder without any results.

Have you tried the installation-script that i linked to in my previous post? I would be glad if someone could try and give feedback. As long as you follow the sort of only instruction it will deal with updating lwjgl and other stuff for you.

---

### Post by redbikemaster on 2012-08-22
Would it be beneficial to switch to 64-bit for performance reasons? I'm asking because I am only running 20-40 FPS on Minecraft. This is with OptiFine installed! As you can see by my sig, my computer isn't lousy. Problem is, I'm only using 15% of my CPU, and 20% max of my RAM.

---

### Post by AZ42 on 2012-08-23
Hi,

I installed sun java 7, than had the black screen bug, so I installed lwjgl-2.8.4, now the game runs, but I can't see textures.. I'm using a Thinkpad X60s.

The problem looks like this:
[screenshot]("http://dl.dropbox.com/u/20548851/Screenshot%20from%202012-08-23%2018%3A35%3A38.png")

Please share, if you have any idea to fix this issue.


AZ

---

### Post by bitcrow on 2012-08-23
> **DarkAmbient said:**
> Have you tried the installation-script that i linked to in my previous post? I would be glad if someone could try and give feedback. As long as you follow the sort of only instruction it will deal with updating lwjgl and other stuff for you.
Doesn't seem to work for me. Still stops at "Updating Minecraft Done loading".

---

### Post by So True on 2012-08-24
> **DarkAmbient said:**
> Have you tried the installation-script that i linked to in my previous post? I would be glad if someone could try and give feedback. As long as you follow the sort of only instruction it will deal with updating lwjgl and other stuff for you.

Your .sh script works fine, from my experience (patching LWJGL) although installing Java 7 I'm not sure about, because I already have Java 7 installed.

---

### Post by redbikemaster on 2012-08-25
I have finally gotten Minecraft to work for me! I have Java 7, I use the Magic Launcher for installing the mods, including OptiFine. I also installed the ATi Catalyst driver (fglrx). I now run at 200-300fps on average, on the rig listed in my sig.

---

### Post by DarkAmbient on 2012-08-26
> **So True said:**
> Your .sh script works fine, from my experience (patching LWJGL) although installing Java 7 I'm not sure about, because I already have Java 7 installed.

Are you using Unity, if that's the case did you get a launcher for Minecraft in the Dash? That's the only part I can't check myself.. (My Ubuntu-computer crashed a few weeks ago, and this computer got Arch Linux w/ xfce)

Clicking yes on installing OpenJDK7 does nothing if you already have it installed. What's happening is that it throws up a new instance of the default terminal in Ubuntu and tell that terminal to try install OpenJDK7, which it won't if it's already installed.

---

### Post by asdk on 2012-08-26
> **DarkAmbient said:**
> Are you using Unity, if that's the case did you get a launcher for Minecraft in the Dash? That's the only part I can't check myself.. (My Ubuntu-computer crashed a few weeks ago, and this computer got Arch Linux w/ xfce)

Clicking yes on installing OpenJDK7 does nothing if you already have it installed. What's happening is that it throws up a new instance of the default terminal in Ubuntu and tell that terminal to try install OpenJDK7, which it won't if it's already installed.

Yes I do have a custom launcher in the Unity launcher.

---

### Post by yetipirate on 2012-08-28
So, I've recently moved to Ubuntu, and have run into a problem that seems unsolvable with the simple google searches.

Essentially, when I run minecraft, everything loads, except any type of non-liquid block appears grey. 

I tried installing texture packs, no success. I upgraded my graphics drivers, again, no success.

I'm using openjdk-7.0 

suggestion?

Driver info:


Device:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
SVendor:	Acer Incorporated [ALI]
SDevice:	Device 0090
Rev:	03
Driver:	i915
Module:	intelfb
Module:	i915

---

### Post by DarkAmbient on 2012-08-28
> **asdk]Yes I do have a custom launcher in the Unity launcher.[/QUOTE]

Sweet, thanks for checking. :)

[QUOTE=yetipirate said:**
> So, I've recently moved to Ubuntu, and have run into a problem that seems unsolvable with the simple google searches.

Essentially, when I run minecraft, everything loads, except any type of non-liquid block appears grey. 

I tried installing texture packs, no success. I upgraded my graphics drivers, again, no success.

I'm using openjdk-7.0 

suggestion?

Driver info:


Device:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
SVendor:	Acer Incorporated [ALI]
SDevice:	Device 0090
Rev:	03
Driver:	i915
Module:	intelfb
Module:	i915

If you start Minecraft through a terminal, is there any useful output? Have you tried upgrading (replace with newer version ones) the lwjgl-files for Minecraft?

---

### Post by AZ42 on 2012-08-28
I have absolutely the same problem with "intel Mobile 945GM" video card. Ubuntu 12.04, using Oracle Java 7. I have texture errors in Dominions 3 as well.

[Screenshot]("https://dl.dropbox.com/u/20548851/Screenshot%20from%202012-08-23%2018%3A35%3A38.png")

I couldn't find any solution yet. 

I made a [tread about it in minecraftforum.net]("http://www.minecraftforum.net/topic/1444269-gre/") 

> **yetipirate said:**
> So, I've recently moved to Ubuntu, and have run into a problem that seems unsolvable with the simple google searches.

Essentially, when I run minecraft, everything loads, except any type of non-liquid block appears grey. 

I tried installing texture packs, no success. I upgraded my graphics drivers, again, no success.

I'm using openjdk-7.0 

suggestion?

Driver info:


Device:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
SVendor:	Acer Incorporated [ALI]
SDevice:	Device 0090
Rev:	03
Driver:	i915
Module:	intelfb
Module:	i915

---

### Post by Nanur on 2012-08-30
> **yetipirate said:**
> So, I've recently moved to Ubuntu, and have run into a problem that seems unsolvable with the simple google searches.

Essentially, when I run minecraft, everything loads, except any type of non-liquid block appears grey. 

I tried installing texture packs, no success. I upgraded my graphics drivers, again, no success.

I'm using openjdk-7.0 

suggestion?

Driver info:


Device:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
SVendor:	Acer Incorporated [ALI]
SDevice:	Device 0090
Rev:	03
Driver:	i915
Module:	intelfb
Module:	i915

You can also try installing and using Oracle Java 6, and running with that.

---

### Post by buckeyered80 on 2012-09-05
Nice job on that script, Dark Ambient. My son wanted to play Minecraft, and it did the trick.

---

### Post by DarkAmbient on 2012-09-06
> **buckeyered80 said:**
> Nice job on that script, Dark Ambient. My son wanted to play Minecraft, and it did the trick.

Great, glad to help =)

If you interested in a newer version of the script, find it in this thread [here]("http://ubuntuforums.org/showthread.php?t=2052084").

---

### Post by discrapheap on 2012-09-16
Oh yes, it does work though not through standard install.

First you need to get the latest java to work (oracle 7u7).

In order to get that to work you need manually dpkg -i libxss1 ppa (you can find it on ubuntuupdates.org site). manually because this pkg-add or whatever crap moans about missing candidates or something. It might also be this is to get chromium or google chrome to work, i cant remember exactly wether it had to do with java. kind of sloppy but may be of information to whoever.

with libxss1 added to standard install you should at least be able to run chrome and probably also java. now to get java to work you first need to remove any existing openjdk stuff;

sudo apt-get purge openjdk*

did you install java 7 from another ppa, proceed with following steps;

sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update

now install oracle java 7;

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

you can check the java through 'which java' or dashboard or something.

you can start running the minecraft.jar through the terminal command java -jar minecraft.jar; you can also right click in your filemanager screen onto the jar file and select properties. then allow it to be executed and let it auto open by the RUNTIME java (not the webstart or any like that crap). you can also chmod +x minecraft.jar in terminal and select default handler through 'mimeopen -d ~/Downloads/minecraft.jar' (also, select the RUNTIME version).

then you probably get a black screen with minecraft. cool, next steps to take this away is described here;
[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

minecraft should work now.

again, im kind of sloppy but i hope this is of information to ya'll. and im almost sure the libxss1 had to do with chromium nevertheless i hope it doesnt annoy you.

---

### Post by contributor on 2012-09-19
> **kce007 said:**
> No problems with minecraft on newest ubuntu :) installed like normal programs

Absolutely right. It is not giving any type of problems on newest Ubuntu.

---

### Post by SniperStyle on 2012-09-22
I just installed Ubuntu 12.04.1 Server on my spare computer and im trying to install and get the minecraft server to run. Hoping to have a dedicated server that wont cost an arm and a leg.

Im VERY new to Ubuntu and would greatly appreciate any help i can get. I have Ubuntu Server installed and can access the server through WinSCP and putty.

Thanks for any help in advance.

---

### Post by temporos on 2012-10-21
I'm getting the problem, too.  I just downloaded minecraft.jar from minecraft.net, and I get this...

```
$ java -cp minecraft.jar net.minecraft.LauncherFrame
asdf
java.io.FileNotFoundException: /home/jonathan/.minecraft/lastlogin (No such file or directory)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:138)
	at net.minecraft.LoginForm.readUsername(LoginForm.java:110)
	at net.minecraft.LoginForm.<init>(LoginForm.java:55)
	at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:23)
	at net.minecraft.LauncherFrame.main(LauncherFrame.java:167)
java.lang.ClassNotFoundException: net.minecraft.client.MinecraftApplet
	at java.net.URLClassLoader$1.run(URLClassLoader.java:366)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:355)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:354)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:423)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:356)
	at net.minecraft.GameUpdater.createApplet(GameUpdater.java:373)
	at net.minecraft.Launcher$1.run(Launcher.java:79)
```
All those errors look bad...  I do have the "official" Java release from Oracle, too.

```
$ java -version
java version "1.7.0_09"
Java(TM) SE Runtime Environment (build 1.7.0_09-b05)
Java HotSpot(TM) Client VM (build 23.5-b02, mixed mode)
```

It does one of two things:
[LIST=1]
[*]it finishes loading and stops at a black screen, or
[*]it stops at about 90% of updating and hangs at "Done Loading."
[/LIST]

Any ideas?

---

### Post by mowriter on 2012-11-05
THIS ACTUALLY WORKED!!  ALL THOSE DAMNED LIBLIST JAVA 7 DOWNLOAD LIBRARY COMMENTS WERE SO MUCH CRAP!  THE BELOW ACTUALLY WORKS!  CANNOT THANK YOU ENOUGH -  my ten year old son will flip his lid!  THANK YOU THANK YOU THANK YOU!!

:):P:guitar:> **DarkAmbient said:**
> Wrote a installer for Minecraft in bash that works w/o a terminal. It asks if you wanna install OpenJDK7 as well. And fixes the black-screen-issue during installation. Run this even if you only wanna fix the black-screen-issue.

[SIZE=3]Download the installer [[COLOR=Blue]HERE[/COLOR]]("http://ubuntuone.com/0viArrNiGfDcTKabKaPDOL")[/SIZE] or find it attached to this post.

[SIZE=3][COLOR=Blue]
To run the installer...
[LIST]
[*]Download "minecraftinstaller.sh".
[*]Rightclick on it and choose "properties".
[*]Beneath the "permissions" tab check the "Allow executing file as program" -option.
[*]Close properties and run "minecraftinstaller.sh" by doubleclicking it and choose "run"
[/LIST]

OR

To start it from a terminal.
[LIST]
[*]Download "minecraftinstaller.sh" to your homefolder (easiest)
[*]Open a terminal and type "sh minecraftinstaller.sh" (without the quotes)
[/LIST]
[/COLOR][/SIZE]

Enjoy!

---

### Post by DarkAmbient on 2012-11-07
> **mowriter said:**
> THIS ACTUALLY WORKED!!  ALL THOSE DAMNED LIBLIST JAVA 7 DOWNLOAD LIBRARY COMMENTS WERE SO MUCH CRAP!  THE BELOW ACTUALLY WORKS!  CANNOT THANK YOU ENOUGH -  my ten year old son will flip his lid!  THANK YOU THANK YOU THANK YOU!!

:):P:guitar:

Great stuff that it works for you! =)

Just a headsup, as I can't ignore that the link you quoted is to a "dead version" ;) Latest version will always be in my sig. Working on a newer version too, that will support installing mods, also created a basic online-tool to translate the-ingame glyphs ([link to 0.1 version]("http://ubuntuone.com/3goAZf8vdFXX5TtcijIp4A")(work in progress) that will be linked from inside the next version. It will be called MCTinker instead of Minecraftinstaller too then. ;)

---

### Post by efflandt on 2012-11-08
If anyone is looking for a way to use both forge and other mods and possibly HD texture pack, I found something called **MultiMC** that can get those to all cooperate.

Originally I used **mcpatcher** to add Rei's MiniMap and use Dokucraft HD textures, but mcpatcher did not seem to work to add ShowMonsters or forge to add the newer forge version of that due to conflicts in java class names.  And even singly on a fresh .minecraft/bin/minecraft.jar I could not get either ShowMonsters nor forge to work by itself.

But then I found MultiMC, used that with a unmoded 1.4.2 minecraft.jar to add forge, Rei's MiniMap, and the forge version of ShowMonsters and that all works with Dokucraft HD textures when I launch minecraft using MultiMC. [http://www.minecraftforum.net/topic/1000645-multimc-42-windows-linux-mac/](http://www.minecraftforum.net/topic/1000645-multimc-42-windows-linux-mac/)

Using 64-bit 12.04 on my desktop below with openjdk-7 and lwjgl 2.6.  And for travel use 64-bit 11.10 or 12.04 with openjdk-6 booted from SD card on 1 GHz 2 core 2 GB tablet PC with Radeon HD graphics.  The only problem with the latter, other than being rather slow is that java seems to crash when I exit minecraft and takes a while to finally close.

**temporos**, you have not specified in the command line how much memory java should use, but not sure why it cannot find lastlogin unless you have never successfully run minecraft before.

---

### Post by SirGrey on 2012-11-12
Hi there! I have a really strange problem with Minecraft graphics. No such problems with LWJGL in Netbeans. Here is screenshot:[IMG]http://dl.dropbox.com/u/50058164/owww.png[/IMG]
Also, keyboard and mouse both not working.

---

### Post by rainbatt on 2012-11-14
Anywhere to find instructions on using **MultiMC** in ubuntu?

---

### Post by xicohospi on 2013-02-20
I try all the things,but when i start minecraft,in my ubuntu 12.04 starts with a black screen :(

---

