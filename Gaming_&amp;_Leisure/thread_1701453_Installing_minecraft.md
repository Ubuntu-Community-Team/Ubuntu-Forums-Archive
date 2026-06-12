---
title: "Installing minecraft"
date: 2011-03-06
forum: Gaming &amp; Leisure
---

### Post by DarbyCrash on 2011-03-06
Okay im a newcomer to Ubuntu, i want too play mine craft do i need any additional soft ware, like java addons etc

---

### Post by mmsmc on 2011-03-06
you can use openjdk, but java is preferable,  [http://ubuntuforums.org/showthread.php?t=366104](http://ubuntuforums.org/showthread.php?t=366104)

---

### Post by DarbyCrash on 2011-03-06
So i installed it. it then says "The file '/home/maklane/Downloads/minecraft (1).jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit" when i tried to open the download file with the java by left clicking

---

### Post by keltic dave on 2011-03-06
> **DarbyCrash said:**
> So i installed it. it then says "The file '/home/maklane/Downloads/minecraft (1).jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit" when i tried to open the download file with the java by left clicking

right click properties permissions tick the box for executable then go to open with change it from archive manager to open java or whatever java you have installed. Click close double click and it will boot up just fine.

---

### Post by DarbyCrash on 2011-03-06
yep that worked thank you

---

### Post by rocker55555 on 2011-04-10
I have a problem.
I installed Sun Java but when i double click minecraft.jar nothing happens(Sun Java is default).

---

### Post by Perfect Storm on 2011-04-10
> **rocker55555 said:**
> I have a problem.
I installed Sun Java but when i double click minecraft.jar nothing happens(Sun Java is default).

Try uninstall open Java packages and icedtea.

---

### Post by rocker55555 on 2011-04-10
Can you give me a code for that?
I'm new to ubuntu...

---

### Post by Perfect Storm on 2011-04-10
```
sudo apt-get remove --purge icedtea-6-jre-cacao icedtea6-plugin openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
```

---

### Post by rocker55555 on 2011-04-10
I can't uninstall it,it can't connect to several sites,example "Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... "

EDIT: i switched my router,now it works.
         So now i reinstall it or?

---

### Post by Perfect Storm on 2011-04-10
Install sun Java jre, plugins, fonts
Uninstall open Java (as shown above).

---

### Post by rocker55555 on 2011-04-10
Will this do it?
sudo add-apt-repository ppa:sun-java-community-team/sun-java6
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin

---

### Post by Perfect Storm on 2011-04-10
Yeah, but there's an easier way. Just enable "Partners" in Ubuntu Software Center and you'll have sun jave at your disposable.

---

### Post by rocker55555 on 2011-04-10
I installed it.
But now when i run it with terminal i see the process in System Monitoring,but nothing on the desktop.
I get this in the terminal: 

Exception in thread "main" java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
    at Loader.load(Loader.java:25)
    at Loader.main(Loader.java:19)

---

### Post by Perfect Storm on 2011-04-10
```
cd /into/the/folder
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```

---

### Post by rocker55555 on 2011-04-10
Now i get a different error(the last line):
Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: net.minecraft.LauncherFrame.  Program will exit.

---

### Post by Perfect Storm on 2011-04-10
Try:

```
java -Xmx1024M -Xms512M -cp **M**inecraft.jar net.minecraft.LauncherFrame
```

I can't remember if mincraft java file is upper or lower case.

---

### Post by rocker55555 on 2011-04-10
Lower case.
I really don't know what's the problem...

---

### Post by Perfect Storm on 2011-04-10
Linux is case sensitive.

---

### Post by rocker55555 on 2011-04-10
I checked,nothing is misspelled.

---

### Post by Perfect Storm on 2011-04-10
Try this:
```
java -jar ~/filepath/minecraft.jar
```

By the way which video do you have?

---

### Post by Perfect Storm on 2011-04-10
Also make sure the .jar file is set to be executable.

---

### Post by sffvba[e0rt on 2011-04-10
I never get any error messages when trying to play minecraft (from the browser, the free version)... in Ubuntu or in Windows 7... it never works either :p  I gave up... it must be a sign ):P


404

---

### Post by rocker55555 on 2011-04-10
> **Artificial Intelligence said:**
> Try this:
```
java -jar ~/filepath/minecraft.jar
```By the way which video do you have?
Still nothing.
Video?
Also,can it be a problem if the folder is hidden?

---

### Post by Perfect Storm on 2011-04-10
> **rocker55555 said:**
> Still nothing.
Video?
Also,can it be a problem if the folder is hidden?

Nope, other than you give it a wrong path, but then it will you.

---

### Post by rocker55555 on 2011-04-10
What did you mean with the video?

---

### Post by Perfect Storm on 2011-04-10
Video card, sorry was a little too fast writing :P

---

### Post by rocker55555 on 2011-04-10
ATI HD3650.
I installed the FGLRX driver from the "Additional Drivers",i don't know if that i enough.

---

### Post by Perfect Storm on 2011-04-10
I'm running out of ideas...
Though one of the critics of Minecraft that they use too much adding features and less on fixing all the bugs.
My guess it's one of the bug(s).

---

### Post by rocker55555 on 2011-04-10
I was thinking about installing Mint.

---

### Post by Perfect Storm on 2011-04-10
> **rocker55555 said:**
> I was thinking about installing Mint.

High chances it will end up as the same as Mint is based on Ubuntu, just with another theme and couple of Mint made applications.

---

### Post by rocker55555 on 2011-04-10
Looks like i'm gonna need to continiue playing mc on windows...
Anyway i appreciate your help.

---

### Post by Perfect Storm on 2011-04-10
No problem. You could try downloading the Windows version and run it through wine/playonLinux.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=23143&iTestingId=62538](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23143&iTestingId=62538)

---

### Post by rocker55555 on 2011-04-11
I  tried that before,it said I don't have java installed.

---

### Post by allocateB on 2011-04-11
If anyone needs help installing minecraft on ubuntu, I just posted a complete installer script in another topic!
This should work very well for people having trouble.

Watch the video to see exactly how to use it!
there's a download link in the description!
[http://www.youtube.com/watch?v=OqIaWSCSJ38](http://www.youtube.com/watch?v=OqIaWSCSJ38)

the thread:
[http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735)

mine on!

---

### Post by mtalexan on 2011-04-11
If anyone's still interested, you should be running minecraft without extracting the jar.  Instead just do the following to run it.  
```
java -jar minecraft.jar
```
That's the only real change if you don't want everything else allocateB's script will do.

---

