---
title: "Ubuntu 11.4 - Minecraft runs Very Slow"
date: 2011-09-25
forum: Gaming &amp; Leisure
---

### Post by vincej on 2011-09-25
Hi - I just don;t get it, others seem to have success with Minecraft, so I upgraded to 11.4 in expectation that the problems I had with 10.4 would be solved. There is a small performance improvement, but I am still only getting about 3fps. Java is 100% up to date and I am getting lighting speeds on with browsers. 

My hardware is a Dell Dimension 9150 ( dual Pentium D's ) 2 GB ram.  

I am completely new to Linux and hence have next to no slill in diagnosing problems. 

Are there switches or configs I could check to improve performance or is MineCraft just so processor hungry that there is nothing to do ? 

Many thanks !

---

### Post by mcduck on 2011-09-26
Minecraft indeed is quite demanding on your computer, Java isn't the best platform performance-wise and handling the voxel-based worlds can be quite tasking. Not only for the CPU ad graphics card but things like hard drive speed can have a noticeable effect depending on the fog distance you are using.

Here's a couple of things to pay attention to:

- Java version. Make sure you have installed the latest available Oracle (Sun) Java and that you have set it as default.

- graphics card and drivers, of course.

- the script you use to start Minecraft. That's what defines how much memory the game  has available, and how much it can reserve for itself straight from the start.

There are couple of other tricks that can improve the performance, for example the Optimine mod can have a great effect, and same goes for updating the lwjgl to latest version (Minecraft includes an outdated version). [Minecraft forums]("http://www.minecraftforum.net/") are probably the best place to look for such tweaks.

---

### Post by SlugSlug on 2011-09-26
sudo apt-get install sun-java6-jre

to use Sun's Java

---

### Post by mcduck on 2011-09-26
> **SlugSlug said:**
> sudo apt-get install sun-java6-jre

to use Sun's Java

That only installs it, but doesn't actually make it default so Minecraft would run using the OpenJDK instead. In addition to the above you should run the following command and set the sun-java6-jre as the default:
```
sudo update-alternatives --config java
```

---

### Post by Paqman on 2011-09-26
TBH, although Mojang do suggest using the Sun Java, I've never had any issues (performance or otherwise) running it on OpenJDK.

What are the specs of the machine you're running it on vincej? Try turning the view distance and all other settings down to the minimum. On mimimum settings I'm able to run Minecraft on my netbook, which is far from powerful.

---

### Post by vincej on 2011-09-26
> **mcduck said:**
> 

- the script you use to start Minecraft. That's what defines how much memory the game  has available, and how much it can reserve for itself straight from the start.



Can you give me advice on

a) how to find the script ie what is it called ?

b) what I need to alter within the script ?

I have 4 GB on my system.  

The very curious thing is that Minecraft runs _really fast_ on single user but i get only 2-4 fps on multi ! 

Many thnanks !

---

### Post by SlugSlug on 2011-09-26
> **vincej said:**
> Can you give me advice on

a) how to find the script ie what is it called ?

b) what I need to alter within the script ?

I have 4 GB on my system.  

The very curious thing is that Minecraft runs _really fast_ on single user but i get only 2-4 fps on multi ! 

Many thnanks !


I use

java -jar -Xmx1024M -Xms1024M /path/to/minecraft.jar


Also Minecraft server DrunkenSlug.com ;)

---

### Post by vincej on 2011-09-26
> **SlugSlug said:**
> I use

java -jar -Xmx1024M -Xms1024M /path/to/minecraft.jar


Also Minecraft server DrunkenSlug.com ;)

Thanks for that - however, I am a complete noob to Ubuntu .. can you help me with some more specifics ie what to do  ? 

Many thanks !

---

### Post by SlugSlug on 2011-09-26
create new text file 

save minecraft.jar in your home folder

paste in that java command  and save it as MinecraftLauncer

then right click it properties make it as executable

then double click it to run

---

### Post by SlugSlug on 2011-09-26
save minecraft.jar in your home folder

create new text file 

paste in 
```
 java -jar -Xmx1024M -Xms1024M /home/#YourUserName/minecraft.jar
``` and save it as MinecraftLauncer

then right click it properties make it executable

then double click it to run

---

### Post by ubudog on 2011-09-26
Moved to Gaming and Leisure.

---

### Post by vincej on 2011-09-29
HI Thanks for your help. I ran your script and sadly, it did nothing. I mean, it did not launch Minecraft and when I launched Minecraft through my original launcher, it made no difference. 

- My Java is up to date, version 6

- I updated my video drivers to the most recent Radeon x600

- I have 4 GB Ram, dual pentium D processors. 

- I get 15mbs down load speed. 

- I have 11.4 installed. 

To repeat, single user runs fast, but, multi user gives me only 3 fps. 

I don't get it. If it was to be my computer then, why should multi- user run so slow ?   


Maybe I did not installed your script properly. I did follow your instructions though. 

Any ideas a very gratefully received - my boys are desperate to play Minecraft !

---

### Post by SlugSlug on 2011-09-29
> **vincej said:**
> HI Thanks for your help. I ran your script and sadly, it did nothing. I mean, it did not launch Minecraft and when I launched Minecraft through my original launcher, it made no difference. 

- My Java is up to date, version 6

- I updated my video drivers to the most recent Radeon x600

- I have 4 GB Ram, dual pentium D processors. 

- I get 15mbs down load speed. 

- I have 11.4 installed. 

To repeat, single user runs fast, but, multi user gives me only 3 fps. 

I don't get it. If it was to be my computer then, why should multi- user run so slow ?   


Maybe I did not installed your script properly. I did follow your instructions though. 

Any ideas a very gratefully received - my boys are desperate to play Minecraft !

the only reason that would not work is if your paths are wrong or its not executible

 java -jar -Xmx1024M -Xms1024M /home/#YourUserName/minecraft.jar
minecraft.jar must be in your home folder & you need to rename the '#YourUserName'  bit 

but am not sure why it would run fine on SP and not MP ~ I take it you have tried different servers?

---

### Post by vincej on 2011-09-30
Hi ! Thanks for all your help, 

I must be doing something very wrong, here is the path I am using adjusted to reflect where the jar file is. 


java -jar -Xmx1024M -Xms1024M /home/vincej/.minecraft/minecraft.jar

I have placed this file in a txt file and given it permission to run as an Executable. I run in terminal and nothing happens. Is my path wrong ? 

something else I have done. In order to ensure that my MC install was correct, I re-installed it using the automated script from allocateB on the forum

[http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735)

It all installed fine, but runs just as slow as ever. 

Trust me, I'm really not that stupid when it comes to Microsoft, but this Ubuntu stuff is a real learning curve !



Many thanks Vincej

---

### Post by donkyhotay on 2011-09-30
Post the output you get when attempting to run the script from terminal.

---

### Post by vincej on 2011-09-30
Hi - thanks for  your help ! 


When I run the txt file 'in terminal' I get no response from the terminal at all, just the following:


vincej@Ubuntu-desktop:~$

---

### Post by donkyhotay on 2011-09-30
Sounds like you didn't create the script right, what happens when you type: 
```

java -jar -Xmx1024M -Xms1024M /path/to/minecraft.jar

```

making the necessary changes to the path depending on where you have saved minecraft? If you are uncertain of the path where minecraft is saved try copying and pasting:
```

java -jar -Xmx1024M -Xms1024M ~/.minecraft/minecraft.jar

```
which is the default path for minecraft.

---

### Post by vincej on 2011-09-30
Ok I ran the second script as I was unsure of the path and great it started. I attach the terminal screen shot as requested. After checking ti , I shut it down again.   

Unfortunately it ran just as slowly as ever, about 3 fps.
many thanks Vincej

---

### Post by vincej on 2011-10-01
Some more interesting data: 
I have 3 computers all providing different performance on MC but all using the same network / router. 

1) New Dell XPS 8300 Win7 pro /  with 4 core i7's and Radeon 6770 video card: 75fps

2) Dell Inspiron 1720 laptop & Vista  - 12 fps 

3 ) Dell dimension 9150 / Ubuntu 11.4 AND XP pro dual pentium D 4GB ram Radeon x600 card - 3 fps with Ubuntu and total crash with XP.


Question, assuming that my older Dimension 9150 is just not powerful enough, would there be any value in getting new more powerful video card ? and if so, how powerful ? 

Many thanks  for all the advice !

---

### Post by pwnjangles on 2011-10-03
Wow thanks, didn't know you could use sun java...Also for OpenJDK Minecraft performance is way better for me than on windows but every time you click the mouse it goes through the client and sometimes when you move with w,a,s,d you get stuck in that direction.

---

### Post by SlugSlug on 2011-10-03
> **pwnjangles said:**
> Wow thanks, didn't know you could use sun java...Also for OpenJDK Minecraft performance is way better for me than on windows but every time you click the mouse it goes through the client and sometimes when you move with w,a,s,d you get stuck in that direction.


yer the keys sticking are a bug for me 2 (using Sun)

---

### Post by desktorp on 2011-10-05
I wonder - are you hosting and playing simultaneously, from this Pentium D?

The Pentium D isn't a bad processor, but it's getting old.  For example, my sister's (Windows) machine is nearly identical to yours and for a while, could barely play Minecraft, without having some sort of a crash.  I had her update the Nvidia driver (she has a geforce 7800 or something) and it magically got a little better.. but not much.  It still runs like a pig, but no longer crashes.

That said, I don't know why you'd get *such* a low frame rate in multiplayer and not in single player, unless it's simply a case of your machine becoming overloaded by the simultaneous task of hosting and playing.. something which is doable, but not advisable.  (especially on an older machine)  If you're hosting, check the GUI output to see if it's warning of overloading problems or movement errors.  If you are running the GUI, try just running minecraft_server.jar from the terminal.

One of my Athlon II machines often hosts while playing, but we generally keep it pretty small.  You might want to check in your server properties file, for view distance; make sure it isn't set very high.  (Mine is at 10 by default)

Turn graphics from fancy to fast, turn off screen bobbing, turn frame rate from "Balanced" to "Max FPS" .. it's not advanced opengl mode, but hell.. toggle that anyhow and make doubledog sure it's not causing a problem.  Disable any extraneous desktop effects, like compositing.  If you must use a compositor, make sure you check "unredirect fullscreen" (if you're using fullscreen, that is)

Also.. Close EVERYTHING else.  Left open, in a real-time interface (like Gmail/chat or something) a browser will devour your resources.

Without some sort of error however, it's just hard to say why it's running so badly.

edit: oh oh oh.. and make sure you're allowing the level/chunks to really get a long time to render.  The older the machine, the more time it needs to get the world all ready for you.  I've seen a host take 10 minutes to really get all the fat chewed out, before it stopped running choppily.

---

### Post by meatytaco on 2011-10-05
> **SlugSlug said:**
> yer the keys sticking are a bug for me 2 (using Sun)

yeah that kills me, sometimes literally. O.o

---

### Post by proxy.qtz on 2011-10-06
You probably need to make the launcher script, to allow MC to get a decent amount of resources. Also, you may want to use the Advanced openGL option, and on a side note, MC has a few issues with Lag spikes as of late.

---

### Post by SlugSlug on 2011-10-07
you could also use the spout client - works very well with bukkit servers

---

