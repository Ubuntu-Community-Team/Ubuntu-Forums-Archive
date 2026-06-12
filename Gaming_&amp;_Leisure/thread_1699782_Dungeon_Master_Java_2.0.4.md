---
title: "Dungeon Master Java 2.0.4"
date: 2011-03-04
forum: Gaming &amp; Leisure
---

### Post by Nutbun on 2011-03-04
Has anyone managed to get dungeon master version 2.0.4 to work in Ubuntu?  According to the description you are suppose to be able to get it to work.

[http://homepage.mac.com/aberfield/dmj/download.html](http://homepage.mac.com/aberfield/dmj/download.html)

I want this version because you are able to scale the window (make it bigger)

---

### Post by JDShu on 2011-03-04
Copy the the file "./Dungeon Master Java/Dungeon Master Java.app/Contents/Resources/Java/Dungeon Master Java.jar" into "./Dungeon Master Java" and then in the terminal cd into "Dungeon Master Java" and run :

```
java -jar Dungeon\ Master\ Java.jar
```

---

### Post by Nutbun on 2011-03-04
Thanks JDShu, that got it working, it's a shame there is no sound, it looks to be a good game.  I have found a manual of sorts, so I can learn how things work.

---

### Post by Nytram on 2011-03-04
Sounds works fine for me, note that it only kicks in after you've chosen a character.

---

### Post by Nutbun on 2011-03-04
> **Nytram said:**
> Sounds works fine for me, note that it only kicks in after you've chosen a character.

Great, it was a bit bland without sound. :)
Is there no easier way to start the game than having to go through the terminal each time?

Up to now, it seems a really good game.

---

### Post by lykeion on 2011-03-05
> **Nutbun said:**
> Is there no easier way to start the game than having to go through the terminal each time?

[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

---

### Post by Nutbun on 2011-03-05
> **lykeion said:**
> [https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

Haha, I can't understand any of those community documents, they may as well be written in Swahili, shame they don't translate them into plain English. :)

---

### Post by Nytram on 2011-03-05
is that a dog in your avatar pic, what's wrong with its eyes, looks like it's had the **** beaten out of it

---

### Post by Nutbun on 2011-03-05
> **Nytram said:**
> is that a dog in your avatar pic, what's wrong with its eyes, looks like it's had the **** beaten out of it

It was when he was a wittle tubby puppy, he now looks like this.:)

---

### Post by Nytram on 2011-03-05
he's improved some, fine looking dog

---

### Post by Nutbun on 2011-03-05
Well I am into the dungeons with a full group of adventurers and I still have no sound. :(

But I did manage to make a short-cut.

---

### Post by Perfect Storm on 2011-03-05
Try see if running it with **padsp** will solve your sound problem.

---

### Post by Nutbun on 2011-03-05
> **Artificial Intelligence said:**
> Try see if running it with **padsp** will solve your sound problem.

You are going to think me really stupid, but whats padsp? :oops:

---

### Post by Perfect Storm on 2011-03-05
The game may be use an old audio engine, that's not compiled into the kernel anymore. In some cases padsp can workaround the problem.

You can use it when launching eg. a game.

padsp <path>/<binary>

---

### Post by Nutbun on 2011-03-05
I put it into my short cut like so..

```
padsp java -jar Dungeon\ Master\ Java.jar
```

But still no sound.

If I go into the game folder and click on the sounds they all work, yet they won't play while in the game.

---

### Post by Nutbun on 2011-03-06
> **JDShu said:**
> Copy the the file "./Dungeon Master Java/Dungeon Master Java.app/Contents/Resources/Java/Dungeon Master Java.jar" into "./Dungeon Master Java" and then in the terminal cd into "Dungeon Master Java" and run :

```
java -jar Dungeon\ Master\ Java.jar
```

Still trying to fix my sound issue I notice that your path for DMJ starts ./ 
Does this mean that I need to install the game in some way, as at the moment I am just running it from my desktop?

---

### Post by TheGrep on 2011-03-08
> **Nutbun said:**
> Still trying to fix my sound issue I notice that your path for DMJ starts ./ 
Does this mean that I need to install the game in some way, as at the moment I am just running it from my desktop?
No real installation necessary.  As long as you're running the program from the 'Dungeon Master Java' directory, wherever you put it, you should be fine.

Did you follow "The Hard Way" in the instructions you were shown for adding a launcher?  As they say: "Java programs need to be started from within the directory in which their files exist."

If the game runs otherwise fine, I'll guess you did it properly.

Anyways, you're not alone in not getting sound out of this program.  Hopefully someone knows of a solution.  I'd love to get it running with sound.  Using padsp doesn't help me either.

Ah, Dungeon Master... so many great memories.  At least I can still play it in dosbox.

---

### Post by Nytram on 2011-03-08
Maybe it's a problem with the version of Java you have, I'm using Sun's on Arch Linux, I think Ubuntu comes with OpenJava. If the Java version doesn't work there's always alternatives such as running an Amiga version with an emulator, or the MSDOS version.

---

### Post by TheGrep on 2011-03-08
> **Nytram said:**
> Maybe it's a problem with the version of Java you have, I'm using Sun's on Arch Linux, I think Ubuntu comes with OpenJava. If the Java version doesn't work there's always alternatives such as running an Amiga version with an emulator, or the MSDOS version.
Thank you, that did it!

I had both VMs installed, and openjdk was the default.  I uninstalled openjdk completely.  At that point, I got it to play a sound, but only once.  Then it went silent.

However, launching it through padsp solved that problem.  Now I have sound!

So in brief, to get sound from Dungeon Master Java, you must use Sun's jdk and use padsp.

---

### Post by Nutbun on 2011-03-09
> **TheGrep said:**
> Thank you, that did it!

I had both VMs installed, and openjdk was the default.  I uninstalled openjdk completely.  At that point, I got it to play a sound, but only once.  Then it went silent.

However, launching it through padsp solved that problem.  Now I have sound!

So in brief, to get sound from Dungeon Master Java, you must use Sun's jdk and use padsp.

Great stuff, but can you tell me which java file, or file name this is in synaptic?  I can't seem to find it, that is... the one you removed and the one you installed.

Can't believe you actually found a way to get it working with sound, really good news. :D

---

### Post by Perfect Storm on 2011-03-09
Remove OpenJava:
```
sudo apt-get remove --purge icedtea6-plugin openjdk-6-jdk openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openjdk-6-jdk
```

Install Sun Java
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts sun-java6-bin sun-java6-jdk
```

---

### Post by Nutbun on 2011-03-09
Thanks AI,

I managed to un-install  the old java but when it came to installing the sun java my terminal says stuff like.... 

Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

and


This may mean that the package is missing, has been obsoleted, or
is only available from another source

I guess I will have to get it directly from their site.

---

### Post by Perfect Storm on 2011-03-09
You have to enable "partner" repositories in Synaptic Package Manager" or "Ubuntu Software Center" first.

---

### Post by Nutbun on 2011-03-09
> **Artificial Intelligence said:**
> You have to enable "partner" repositories in Synaptic Package Manager" or "Ubuntu Software Center" first.

Yesss, it now works, sound and everything.  It was worth pursuing. :)

Thank you.

---

