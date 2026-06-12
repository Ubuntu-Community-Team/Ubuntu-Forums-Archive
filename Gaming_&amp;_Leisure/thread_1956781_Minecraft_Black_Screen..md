---
title: "Minecraft Black Screen."
date: 2012-04-11
forum: Gaming &amp; Leisure
---

### Post by Shvesley on 2012-04-11
I have purged my system of all java and have done a complete fresh reinstall of Oracle Java 7. I have deleted .minecraft and minecraft.jar and downloaded a completely new .jar file. I open with Java 7, login, it downloads all the stuff, and then I get a black screen. 

Minecraft used to work fine on my laptop, on windows XP, 7, Ubuntu 10.10, 11.04, 11.10, Xubuntu 11.10, and now I am on 12.04 LTS. 

It stopped working on Xubuntu and that is when I reinstalled my OS to the newest Ubuntu. I have not been able to get it working on 12.04 as well. I run a MC server and having MC on my laptop is really important. I am really stumped on this one.

---

### Post by ergo-proxy on 2012-04-12
Make sure you have exported LD_LIBRARY_PATH like
 
export LD_LIBRARY_PATH=/path/to/java/jre/lib/i386 (or change i386 to amd64 if you have 64bit system)

---

### Post by regor210 on 2012-04-12
Note. if you are using Ubuntu 12.04 you have to update LWJGL by hand or you will get a black screen when loading the game.

[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

---

### Post by ThePinion on 2012-05-11
Once you've ran it once, open up your terminal and try this. It's just a quick way to automatically do what the poster before me suggested

cd ~/Downloads; wget -O lwjgl-2.8.3.zip [http://downloads.sourceforge.net/project/java-game-lib/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.3%2F&ts=1336277720&use_mirror=softlayer;](http://downloads.sourceforge.net/project/java-game-lib/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.3%2F&ts=1336277720&use_mirror=softlayer;) unzip lwjgl-2.8.3.zip; cd lwjgl-2.8.3; cp -r native/linux/* ~/.minecraft/bin/natives/; cp jar/lwjgl.jar ~/.minecraft/bin/;cp jar/jinput.jar ~/.minecraft/bin/;cp jar/lwjgl_util.jar ~/.minecraft/bin/; quit

It worked for me, I've posted it on my site with other Ubuntu 12.04 tips/tricks, hopefully it will help you out more: [http://modifyubuntu.com/12.04/#minecraft](http://modifyubuntu.com/12.04/#minecraft)

---

### Post by Chriselflord on 2012-05-27
I have had this problem this weekend getting minecraft to work under ubuntu 12.04. After trial and error, I just went to the software center and used the older version of java (6 not 7) and presto, it works. There is probably a better method to fixing this problem, such as those mentioned above. But this worked for me on a system set up specifically for minecraft and a few other games. 

Hope this helps and good luck.

---

### Post by sffvba[e0rt on 2012-05-28
> **Chriselflord said:**
> I have had this problem this weekend getting minecraft to work under ubuntu 12.04. After trial and error, I just went to the software center and used the older version of java (6 not 7) and presto, it works. There is probably a better method to fixing this problem, such as those mentioned above. But this worked for me on a system set up specifically for minecraft and a few other games. 

Hope this helps and good luck.

Slightly late but I can echo the above, with OpenJDK 7 I got the black screen, switched back to 6 and no issues in Ubuntu 12.04 LTS 32-bit.


404

---

### Post by tehcavil on 2012-08-09
> **ThePinion said:**
> Once you've ran it once, open up your terminal and try this. It's just a quick way to automatically do what the poster before me suggested

cd ~/Downloads; wget -O lwjgl-2.8.3.zip [http://downloads.sourceforge.net/project/java-game-lib/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.3%2F&ts=1336277720&use_mirror=softlayer;](http://downloads.sourceforge.net/project/java-game-lib/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.3%2F&ts=1336277720&use_mirror=softlayer;) unzip lwjgl-2.8.3.zip; cd lwjgl-2.8.3; cp -r native/linux/* ~/.minecraft/bin/natives/; cp jar/lwjgl.jar ~/.minecraft/bin/;cp jar/jinput.jar ~/.minecraft/bin/;cp jar/lwjgl_util.jar ~/.minecraft/bin/; quit

It worked for me, I've posted it on my site with other Ubuntu 12.04 tips/tricks, hopefully it will help you out more: [http://modifyubuntu.com/12.04/#minecraft](http://modifyubuntu.com/12.04/#minecraft)

holy crap man thanks this worked perfectly! followed the instructions on your site and got minecraft working with java 7~ nice!!

thanks for your help!

---

### Post by HikariKnight on 2012-08-17
Had a similar issue with several java based games so i ended up writing a script wrapper that solved those issues for me.

the source can be found at
[http://dl.dropbox.com/u/11631899/opensource/Perl/java-wrapper/java-wrapper](http://dl.dropbox.com/u/11631899/opensource/Perl/java-wrapper/java-wrapper)

An installation guide can be found here (made this for the linux users in runescape but it works for games like minecraft too, plus it lets you override runtime parameters set by websites which is something i made for the java games that do not have a game client ;) )
[http://www.youtube.com/watch?v=NRhR3o7TFEw](http://www.youtube.com/watch?v=NRhR3o7TFEw)

NOTE: i wrote it to be universal so it works through the web browser too and works with both openjdk and oracle java.


Setting a runtime parameter override is easy, run the wrapper 1 time and it will generate a default one in 
"~/.config/java-wrapper/overrides.pm"

the contents are something like
```
package overrides;

# This is a collection of programmable overrides for the java parameters
# _if_overridename is(=>) "value",
# _set_overridename to(=>) "value",

# NOTE: you can add any if statements if you follow the method above!
$overrides = {
	_if_maxmem => "-Xmx256m",
	_set_maxmem => "-Xmx512m",
	_if_stacksize => "-Xss1m",
	_set_stacksize => "-Xss2m",
};
## END OF OVERRIDES

#
#---------------------------------------- *** ----------------------------------------
#

# Callback, DO NOT TOUCH!
sub get_overrides
{
	return $overrides;
}

```

basically we have _if_overridename is set to "value" then _set_overridename to "value"

overridename can be anything, it is just used as an identifier!

so basically in the default file if  -Xmx256m is passed to java it will override it and use -Xmx512m instead.
Same goes for -Xss1m which will become -Xss2m.

Hope others will find this useful for the java games they play, be it runescape or minecraft :)

---

### Post by cooktastic on 2012-08-26
> **ThePinion said:**
> Once you've ran it once, open up your terminal and try this. It's just a quick way to automatically do what the poster before me suggested

cd ~/Downloads; wget -O lwjgl-2.8.3.zip [http://downloads.sourceforge.net/project/java-game-lib/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.3%2F&ts=1336277720&use_mirror=softlayer;](http://downloads.sourceforge.net/project/java-game-lib/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.3%2F&ts=1336277720&use_mirror=softlayer;) unzip lwjgl-2.8.3.zip; cd lwjgl-2.8.3; cp -r native/linux/* ~/.minecraft/bin/natives/; cp jar/lwjgl.jar ~/.minecraft/bin/;cp jar/jinput.jar ~/.minecraft/bin/;cp jar/lwjgl_util.jar ~/.minecraft/bin/; quit

It worked for me, I've posted it on my site with other Ubuntu 12.04 tips/tricks, hopefully it will help you out more: [http://modifyubuntu.com/12.04/#minecraft](http://modifyubuntu.com/12.04/#minecraft)

This guys is a genius! Helped me a bunch!

---

### Post by asdk on 2012-08-26
> **DarkAmbient said:**
> Updated my Minecraft-installer somewhat today, so after installation an icon for starting Minecraft appear in your application-menu (or Unity Dash). And upon starting the game it reserves exactly half of your computers-memory to Minecraft.

Saw that allocateB wrote a script for installing Minecraft as well, that one seems great so idk if this one is necessary. But as I've been at it for a while since I'm trying to learn Bash, so I'll link it anyway, it's quite an easy and pure graphical few-click installation. :)

Download link: [HERE]("http://ubuntuone.com/4bL0SBoreLlP5HQgFErMDl")

_Download, allow to run it as an application then doubleclick it. Have fun!_

Edit:

Will update script soon so you can "uninstall" Minecraft with it as well... right now to uninstall after you've installed using my installer, run this in a terminal ```
sudo rm /usr/share/applications/minecraft.desktop && rm -R ~/.minecraft
```(Heads up though.. this will wipe out everything with Minecraft, savefiles, settings...) Might add an option asking the user if he/she would like to backup the (offline-) worlds first though.. hmm
here's a great .sh script which updates lwjgl as well as installs OpenJDK Java 7 if you don't have it (credits to Dark Ambient)

---

### Post by prankstar008 on 2013-03-25
Thanks, this worked great.

---

### Post by gbmaizol on 2013-04-06
This worked like a charm for me! I just changed the version number of lwjgl to the latest.

  Thanks!

> **ThePinion said:**
> Once you've ran it once, open up your terminal and try this. It's just a quick way to automatically do what the poster before me suggested

cd ~/Downloads; wget -O lwjgl-2.8.3.zip [http://downloads.sourceforge.net/project/java-game-lib/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.3%2F&ts=1336277720&use_mirror=softlayer;](http://downloads.sourceforge.net/project/java-game-lib/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.3%2F&ts=1336277720&use_mirror=softlayer;) unzip lwjgl-2.8.3.zip; cd lwjgl-2.8.3; cp -r native/linux/* ~/.minecraft/bin/natives/; cp jar/lwjgl.jar ~/.minecraft/bin/;cp jar/jinput.jar ~/.minecraft/bin/;cp jar/lwjgl_util.jar ~/.minecraft/bin/; quit

It worked for me, I've posted it on my site with other Ubuntu 12.04 tips/tricks, hopefully it will help you out more: [http://modifyubuntu.com/12.04/#minecraft](http://modifyubuntu.com/12.04/#minecraft)

---

### Post by Horbo on 2013-04-06
Minecraft doesn't like Oracle Java 7 - you need Java 6.  I don't know which versions of Openjava work.

I haven't had lwjgl problems that stopped mc from working, although I have had to upgrade lwjgl to make sure my mouse buttons worked correctly in mc.

---

