---
title: "PATH driving me crazy!"
date: 2006-10-17
forum: Desktop Environments
---

### Post by IceColdBD on 2006-10-17
Ok, I am trying to get Jedit to work, and it needs the latest Java runtime. I got all that installed, but I want to add the new java to the $PATH, but Ubuntu is not being cooperative.

If I go into a terminal shell and just say

```
 export PATH=/usr/java/jre1.5.0_06/bin:$PATH 
```

It works fine. However, if I edit ~/.bash_profile and add the same line of code to the end of the file I get 

```
josh@ubuntu:~$ echo $PATH
/usr/java/jre1.5.0_06:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
josh@ubuntu:~$

```

Why is the /bin not on the end of the java directory? It is there if I do the export in the shell itself, but not if I add the same line to .bash_profile. This is driving me nuts, because if it doesn't say /usr/java/jre1.5.0_06/bin the right version of java will not be found and I have to export the PATH each time. What is going on?

---

### Post by neumeka on 2006-10-17
Don't know why that is happening.  If you installed java from a package (using synaptic or aptitude) you can try this:

```
sudo update-alternatives --config java 
```

Then select the correct version of java that you need.

-Kyle

---

