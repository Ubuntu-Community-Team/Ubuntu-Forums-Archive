---
title: "How can I throw gij to hell ?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by ichiban on 2005-10-13
gij has been giving me nothing but trouble. :mad: 
I have installed the original Sun JDK. But Eclipse still uses gij. I have tried -vm /usr/lib/j2sdk1.5-sun/ to no avail. If I try to uninstall gij, Synaptic wants to uninstall OO and Eclipse. I don't want to do that. I just want to get rid of gij.

How ???

I have also tryed sudo update-alternatives --config java and change to Suns JDK. But the problem is still there....

---

### Post by mojo on 2005-10-13
[QUOTE=ichiban]gij has been giving me nothing but trouble. :mad: 
I have installed the original Sun JDK. But Eclipse still uses gij. I have tried -vm /usr/lib/j2sdk1.5-sun/ to no avail. If I try to uninstall gij, Synaptic wants to uninstall OO and Eclipse. I don't want to do that. I just want to get rid of gij.

How ???

I have also tryed sudo update-alternatives --config java and change to Suns JDK. But the problem is still there....[/QUOTE]

Dude, use Synaptic and find all 'libgcj' or 'gcj' and remove all of them.

---

### Post by ichiban on 2005-10-13
Thanks I know.  :) 
But if I try that it wants to uninstall Eclipse, OO and a lot of other programs that I do not want to lose. I want those programs to use Suns java instead.

But I have narrowed the problem down to this. Eclipse uses Sun Java, but ant does not. So I'm trying to change that in ant.

---

### Post by chadwick359 on 2005-10-13
If you get this figured out, please send me  a PM, i have been trying to get eclipse to use sun jre1.5 for two weeks now.

---

### Post by rumli on 2005-10-13
Check out [http://ubuntuforums.org/showpost.php?p=351937&postcount=2]("http://ubuntuforums.org/showpost.php?p=351937&postcount=2").

Essentially, try doing a "sudo update-alternatives --config java", and selecting the appropriate choice of java.

---

### Post by chadwick359 on 2005-10-14
Wow, that worked very well, thx.

---

### Post by ichiban on 2005-10-14
Should anyone else have problems with eclipse and Java, then I have found a solution:D 

go to window->Preferences->Java->installed JREs

add /usr/lib/j2sdk1.5-sun and give it a name.

Then Eclipse will run with whatever Java verison you have chosen with
```
sudo update-alternatives --config java
```

But all projects will be buildt with Suns JDK. Ant will also use Suns JDK, but you
can't run ant form the command line, you will have to run it from Eclipse. 
I will write back if I found a solution to that problem.

---

### Post by ivar on 2005-10-14
[QUOTE=rumli]Check out [http://ubuntuforums.org/showpost.php?p=351937&postcount=2]("http://ubuntuforums.org/showpost.php?p=351937&postcount=2").

Essentially, try doing a "sudo update-alternatives --config java", and selecting the appropriate choice of java.[/QUOTE]

thank you - thank you - thank you !!!
that's exactly what I was looking for !

---

### Post by riggsd on 2005-10-14
FYI, you can remove the executable (which is giving everyone fits) while keeping the libs that other programs depend on.

```
$> apt-get remove --purge java-gcj-compat
```

---

### Post by BLTicklemonster on 2005-10-15
What The Firefox?

I just installed /home/bill/jre-1_5_0_05-linux-i586.bin and I can't install anything that uses Java:

```
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.
root@ubuntumonster:/home/bill# sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

Press enter to keep the default[*], or type selection number:
root@ubuntumonster:/home/bill# sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

```

and in preferences, there's no java.


restarted, too.

...but my mousey buttons work.

---

### Post by dmegg on 2005-11-30
[QUOTE=riggsd]FYI, you can remove the executable (which is giving everyone fits) while keeping the libs that other programs depend on.

```
$> apt-get remove --purge java-gcj-compat
```[/QUOTE]

That's pretty critical -- even if you set Eclipse to use the Sun JDK for compiling, Eclipse itself will run sloooooowly under gcj unless you remove this package.

---

