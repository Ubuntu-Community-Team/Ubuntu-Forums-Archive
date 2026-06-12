---
title: "How to add jar file to PATH?"
date: 2011-04-27
forum: Desktop Environments
---

### Post by arcull on 2011-04-27
Hi guys. I've build a jar file in java, which I can execute in terminal like this:```
java -jar /path/to/jarfile/test.jar
```Since I plan to use this jar frequently I thought I could maybe add it to path, so that I wouldn't have to type the absolute path to jar every time I want execute it. On ubuntu 10.10 I tried to edit the .profile file in my home directory and tried to add the following lines, one at a time:```
export PATH=$PATH:/path/to/jar/dist
export CLASSPATH=$CLASSPATH:/path/to/jar/dist/test.jar
export PATH=$PATH:/path/to/jar/dist/test.jar
``` I did logout login and tried the following from the terminal, but unfortunately no go, it says it can access the jar file :(```
java -jar test.jar
``` I need some good advice, thanx in advance.

---

### Post by ankspo71 on 2011-04-27
Hi,
You didn't mention ".bashrc" or ".profile", so I think the reason why setting the path didn't work after you logged back in is because PATH has to be exported on every startup (or PATH can be set in the system directories for all users).
Edit: I see you did mention .profile... I missed that part.

To check on your system's currently assigned paths, you can run the following command
```
echo $PATH
```

If you would like to set the path for only you, then you can add the following line to bottom of the hidden .bashrc file inside your home folder. 

```
export PATH=$PATH:/path/to/jar/dist
```

Save the file, then log out then log back in, and then it should be working correctly.

Before:
```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

After:
```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/path/to/jar/dist
```
Note that this may not work if sudo is required to run the application.

-----

Other files:
The hidden ".profile" file located inside your home directory can be modified too.

Path can be set for all users at /etc/environment
```
gksudo gedit /etc/environment
```
((Be extra careful when editing system files))


Hope this helps.

---

### Post by arcull on 2011-04-28
Thanks man, will give it a try and report back :)

---

### Post by arcull on 2011-04-28
Still no luck, but some progress made. As suggested, I added ```
export PATH=$PATH:/path/to/jar/dist
``` in the .bashrc in my home folder. Then I wrote a simple script like this:```
#!/bin/bash
echo "Today is $(date)"
``` and put in the same directory where my jar file sits. Now I can run the sample script from what ever directory I like, which means PATH is now correct set. However it doesn't work with java jar files, if I do```
java -jar test.jar
``` it still says it can't access the jar file. Is there any way of making my jar visible from terminal. Much thanks again for your help.

---

### Post by imigueldiaz on 2011-04-28
> **arcull said:**
> Still no luck, but some progress made. As suggested, I added ```
export PATH=$PATH:/path/to/jar/dist
``` in the .bashrc in my home folder. Then I wrote a simple script like this:```
#!/bin/bash
echo "Today is $(date)"
``` and put in the same directory where my jar file sits. Now I can run the sample script from what ever directory I like, which means PATH is now correct set. However it doesn't work with java jar files, if I do```
java -jar test.jar
``` it still says it can't access the jar file. Is there any way of making my jar visible from terminal. Much thanks again for your help.

I suppose you can export a variable like MYJAR on your .bashrc and then use it on console, e.g

On .bashrc

```

export MYJAR=/path/to/jar/dist

```

open a new terminal (to re-read .bashrc) and test


```
java -jar $MYJAR
```


Yo can even write $M [tab] and bash should autocomplete the variable.

Hope it helps :)
[B]
EDIT[/B]

I suppose you can add execution permission to the jar file ( chmod u+x /path/to/jar/dist ) and if /path/to/jar is on PATH it should appear on autocompletion possibilities

---

### Post by arcull on 2011-04-28
> I suppose you can export a variable like MYJAR on your .bashrc and then use it on console, e.g

On .bashrc

     Code:
     export MYJAR=/path/to/jar/dist 
open a new terminal (to re-read .bashrc) and test


     Code:
     java -jar $MYJAR 

Yo can even write $M [tab] and bash should autocomplete the variable. imigueldiaz thanks for your solution, I am happy now :)

---

### Post by imigueldiaz on 2011-04-28
> **arcull said:**
> imigueldiaz thanks for your solution, I am happy now :)
You are welcome :D

---

