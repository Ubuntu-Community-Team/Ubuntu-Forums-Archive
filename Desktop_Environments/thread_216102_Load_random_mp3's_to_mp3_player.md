---
title: "Load random mp3's to mp3 player?"
date: 2006-07-14
forum: Desktop Environments
---

### Post by GAZ082 on 2006-07-14
Hi. Is there a program to sync up a random list of files to a USB music device like my iAudio 5?

I thought about programming a little bash script, but no idea about how to start doing it. And if there is a proggie other than Banshee or Amarok, that'd be w00ting ;)

In Win i use Mediamonkey, which actually is the only piece of software i use in that OS besides games.

Thanks!

---

### Post by .tommie on 2006-10-04
I'm looking for a similar solution, but didn't find any... any ideas?

---

### Post by cmost on 2006-10-04
This website has a fairly extensive bash script for manipulating your mp3 library with regards to the Sony PSP.  I reviewed the code for the script and while i'm not a programmer per se, i'm pretty sure it (or excerpts from it) can be adapted to do exactly what you guys want, maybe much more!  Have a look at it and see what you think!  The link is here:

[http://pspnuts.theyard.org/index.php?option=com_content&task=view&id=20](http://pspnuts.theyard.org/index.php?option=com_content&task=view&id=20)

The script is known as "pspcp - An all-purpose PSP utility" and should run on any system that can run Bash scripts (i.e., Linux / UNIX.)

Personally, I use AmaroK for all my mp3 needs.

Good luck!

---

### Post by .tommie on 2006-10-07
That's one solution, but it does look a bit time-consuming for me at the moment. Thanks anyway! :-|

---

### Post by janroald on 2006-10-10
Hi guys.

Fixed up a small script for you to manage your task.
unzip copyrandom.pl
perl copyrandom.pl [source directory] [dest. directory] [MB's]

Edit the file to do the config and to read a small docu.
I'm no expert at this so it might not fullfill all your needs. 
Tell me if u want anything modified.

The script is attatched.

---

### Post by .tommie on 2006-11-05
Great man! I'll give it a try!

---

### Post by hobie on 2006-11-15
I have written a Java Swing application that does exactly this, plus it remembers what you copied so that when you reuse it, it won't pick the same tunes again within a user-defined time interval.  It has many more features as well. 

Since it is written in Java, it works in Win32, Linux and MacOS.

Find out more here: [Mr. Random]("http://mr-random.net")

---

### Post by .tommie on 2007-02-05
[NeroLINUX]("http://www.ubuntuforums.org/showthread.php?t=341142") is a reliable (non-free) alternative. Most people already have a license for it...

---

### Post by ferreol on 2008-03-12
hi guys

this is great but I have all my songs stocked in a apache server and I ve been trying Mr. Random or the copy random script it doesn t work . any ideas to make this working  ?

for the perl script it keeps saying : 

Use of uninitialized value in split at copyrandom.pl line 67.
Use of uninitialized value in hash element at copyrandom.pl line 68

For Mr. Random it worse as I couldn t load the apps it says :


Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at com.simontuffs.onejar.JarClassLoader.defineClass(JarClassLoader.java:626)
        at com.simontuffs.onejar.JarClassLoader.findClass(JarClassLoader.java:532)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at com.simontuffs.onejar.Boot.run(Boot.java:271)
        at com.simontuffs.onejar.Boot.main(Boot.java:123)


Thanks in advance

---

### Post by apuglisi on 2008-03-12
anyway, me posting in a very old thread.

I've been suffering the same problem, until i've found that in Gutsy, my Rhythmbox copies the files and albums to my mp3 player, just fine, in the order they are supposed to play.

I guess we all have been victims of a known Nautilus bug... it just copies files randomly, it doesn't care if the files have alphabetically ordered names.


Regards and scuse my english, spanish ftw :D

---

