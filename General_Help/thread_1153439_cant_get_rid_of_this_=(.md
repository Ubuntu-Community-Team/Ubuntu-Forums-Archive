---
title: "cant get rid of this =("
date: 2009-05-08
forum: General Help
---

### Post by matt12345 on 2009-05-08
ok so ive been trying to get this thing up and running for a while now, but it has always failed me. So i thought i would take it here.

```
matthew@matthew-desktop:~$ svn co http://rsbot.googlecode.com/svn/trunk
svn: Repository access denied.
matthew@matthew-desktop:~$ 


```

---

### Post by neu2buntu on 2009-05-08
svn needs subversion, so do code in terminal ```
sudo apt-get install subversion
``` then try again

---

### Post by matt12345 on 2009-05-08
thanks anyways D:

```
matthew@matthew-desktop:~$ sudo apt-get install subversion
[sudo] password for matthew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
matthew@matthew-desktop:~$ svn co http://rsbot.googlecode.com/svn/trunk
svn: Repository access denied.
matthew@matthew-desktop:~$ 


```

---

### Post by maheshasolkar on 2009-05-08
I couldn't access that url via a browser too. Do you own this project? It does not seem to be open to all. I get this when I try to reach it via the browser:

```
Forbidden
Your client does not have permission to get URL /p/rsbot/ from this server.
```

There's another rsbot project on Google Code, you might want to try that instead:

  [http://code.google.com/p/rsbotsvn/source/checkout](http://code.google.com/p/rsbotsvn/source/checkout)

Disclaimer: I have not clue what rsbot is, just the name of the project (rsbotsvn) leads me to believe that it may be similar to the one you were looking for.

---

### Post by matt12345 on 2009-05-08
No, i do not own the project. But if it helps, heres the guide that i got it from.

[http://www.rsbot.org/vb/showthread.php?t=1216](http://www.rsbot.org/vb/showthread.php?t=1216)

---

### Post by maheshasolkar on 2009-05-08
> **matt12345 said:**
> No, i do not own the project. But if it helps, heres the guide that i got it from.

[http://www.rsbot.org/vb/showthread.php?t=1216](http://www.rsbot.org/vb/showthread.php?t=1216)

Looking at the logos on that website, it does look like the link I suggested may work.

In the thread you mention, in comment #7 someone also suggested the same link ([http://code.google.com/p/rsbotsvn/source/checkout](http://code.google.com/p/rsbotsvn/source/checkout)).

It may be worth giving a shot. Use the following:
```

  svn checkout http://rsbotsvn.googlecode.com/svn/trunk/ rsbot
```

---

### Post by albinootje on 2009-05-08
> **matt12345 said:**
> i do not own the project.

Looks like it's temp. unusable, or the path is wrong.

---

### Post by neu2buntu on 2009-05-08
> subversion is already the newest version this means you already have subversion installed,so this is not the problem now!!! the problem lays elsewhere,...:popcorn:

---

### Post by matt12345 on 2009-05-09
ok so i got everything pretty much rdy but, i got this in terminal.

```
matthew@matthew-desktop:~/Desktop/rsbot$ ./rsbot free
Exception in thread "main" java.lang.NoClassDefFoundError: com/speljohan/rsbot/Application
Caused by: java.lang.ClassNotFoundException: com.speljohan.rsbot.Application
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: com.speljohan.rsbot.Application.  Program will exit.
matthew@matthew-desktop:~/Desktop/rsbot$ 


```

---

