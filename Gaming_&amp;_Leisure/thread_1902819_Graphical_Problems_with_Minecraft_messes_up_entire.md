---
title: "Graphical Problems with Minecraft messes up entire system"
date: 2011-12-31
forum: Gaming &amp; Leisure
---

### Post by Mars11 on 2011-12-31
So, when I play Minecraft it starts out looking fine, then suddenly everything looks like this.
[IMG]http://dl.dropbox.com/u/16007317/Photos/Screenshots/Broken%20Minecraft.png[/IMG]
I've tried changing every setting, with no luck. After a while it starts messing up my entire system with little graphical glitches. I'm using the computer in my sig.

Edit: I'm using Sun's JVM.

---

### Post by ilikelinuxitisthebest on 2011-12-31
unistall suns jvm then open up terminal and enter in ```
sudo apt-get install defualt-jre
```

---

### Post by Mars11 on 2011-12-31
It's already installed.

---

### Post by ilikelinuxitisthebest on 2012-01-01
but. you said you were using suns?

---

### Post by Mars11 on 2012-01-01
I have both installed, and I tried OpenJDK too, it did the same thing.

---

### Post by whatthefunk on 2012-01-01
That could be your problem.  Having both installed leads to conflicts.  Id uninstall both, then reinstall suns java platform.  You also might want to check that your video card drivers are up-to-date.

---

### Post by Mars11 on 2012-01-01
It's actually worse with OpenJDK. [IMG]http://dl.dropbox.com/u/16007317/Photos/Screenshots/Broken_Minecraft_OpenJDK.png[/IMG]

---

### Post by Mars11 on 2012-01-01
How would I go about updating the drivers for my Intel HD 3000? And, I can't figure out how to uninstall Sun Java 7 and 6...

---

### Post by akebdani on 2012-01-01
hmmm i think maybe and just MAYBE its a texture pack problem try changing it if ur using one

---

### Post by Mars11 on 2012-01-01
I'm using the default texture pack. And a messed up texture pack wouldn't start messing up the rest of my system.

---

### Post by whatthefunk on 2012-01-01
If youre using Ubuntu, theres probably some menu item that searches for new drivers.  Not sure exactly where it is as I use Kubuntu.  That will let you check your drivers.

Did you uninstall openjdk?  Id use the command line to get rid of sun java:
```
sudo apt-get purge sun-java6-jre
```
Etc...

To reinstall, youll have to add the sun-java repos before you try to install if you havent already.

---

### Post by akebdani on 2012-01-01
to uninstall just sudo synaptic in a terminal and searsh "java" and uninstall them

---

### Post by Mars11 on 2012-01-01
Nope, that didn't help. How would I go about updating the drivers for the Intel HD 3000?

---

### Post by Perfect Storm on 2012-01-01
You can try checking for updates driver: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Mars11 on 2012-01-01
I added that repository and used Update Manager. When I rebooted it worked fine for longer than it ever has (~10 seconds), but then did it again. :\

---

### Post by Mars11 on 2012-01-08
I hear that the Linux 3.2 Kernel has some better Intel Graphics Drivers. Is there a way I could upgrade to that?

---

### Post by Mars11 on 2012-01-13
So I upgraded to the 3.2 kernel and everything worked fine. There were a few minor graphical glitches, but nothing near what it used to be.

---

