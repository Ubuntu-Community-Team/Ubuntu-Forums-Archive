---
title: "Help, I borked my synaptic package manager"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Handle123 on 2006-06-10
I installed and ran automatix, and one of the options I told it to get was the Java JRE. It starts running, gets the firefox plugins and a few other things and then starts to get Java, which prompts me for my admin password. I enter it, and wait, but it doesn't seem to be installing or doing anything so I kill off the Java thing. Automatix continues running and installing the other packages. 

Now whenever I go into update or synaptic package manager, they won't work. Synaptic tells me there are 2 broken packages that I need to find (and error initialising cache) - but there no are packages listed at all in the package manager, broken or not.

I don't know how to fix this :(

---

### Post by andersonmanly on 2006-06-10
Try this post...

[http://www.ubuntuforums.org/showthread.php?t=186672&highlight=remove+broken+packages](http://www.ubuntuforums.org/showthread.php?t=186672&highlight=remove+broken+packages)

---

### Post by Luke771 on 2006-06-10
Open Synaptic, go to Settings/Repositories, delete anything that's not Ubuntu 6.06, then click on OK 
To apply your changes, select Reload.
Open Repositories again
click Add and then Custom.
Type the line
```

deb http://archive.ubuntu.com/ubuntu/dapper universe main restricted multiverse
```
Click OK 
To apply your changes, select Reload.
Go to
System &#8594; Administration &#8594; Software Properties
Select Add
To enable the Universe repository, check the Community Maintained (Universe) button.
To enable the Multiverse repository, check the Non-free (Multiverse) button.
Click Close to save your changes and exit.
To apply your changes, select Reload.

---

