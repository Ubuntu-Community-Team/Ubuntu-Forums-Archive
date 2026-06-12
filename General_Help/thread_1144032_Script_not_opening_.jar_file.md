---
title: "Script not opening .jar file"
date: 2009-04-30
forum: General Help
---

### Post by Musicologynut85 on 2009-04-30
Hello all, I wrote the following script so that I would have a simple way to open up the [gametable]("http://gametable.galactanet.com/") program which runs in java.

```
#!/bin/bash
clear
echo "Running GameTable"w
echo
cd 
cd gametable-2.0.RC2
sudo java -Xmx500m -jar gametable.jar
```

If I go into the terminal and type out each command in order, then it works just fine. When I run the script, it returns:

```
Unable to access jarfile gametable.jar
```

What modifications to the script do I need to make to get it to work?


Thanks!

---

### Post by sedawk on 2009-04-30
You are running gametable as root, I think that is not
needed (unless it needs some ports <1024 for network stuff).

So first remove "sudo" and try again.

Alternative solution
```

#!/bin/bash
set -x
echo "Running GameTable"
cd ~/gametable-2.0.RC2
java -Xmx500m -jar gametable.jar

```

---

### Post by Musicologynut85 on 2009-05-01
I tried both just removing the "sudo" command, and I tried your alternate. On your alternate solution it gave me:

```
+ echo 'Running GameTable'
Running GameTable
+ cd /home/jeff/gametable-2.0.RC2
+ java -Xmx500m -jar $'gametable.jar\r'
Unable to access jarfile gametable.jar

```

---

### Post by Arndt on 2009-05-01
> **Musicologynut85 said:**
> I tried both just removing the "sudo" command, and I tried your alternate. On your alternate solution it gave me:

```
+ echo 'Running GameTable'
Running GameTable
+ cd /home/jeff/gametable-2.0.RC2
+ java -Xmx500m -jar $'gametable.jar\r'
Unable to access jarfile gametable.jar

```

What's that $' thing? Does the script contain something extra on that line? The \r seems to indicate that there is a spurious Carriage Return character somewhere.

---

### Post by Musicologynut85 on 2009-05-04
I am not sure where the "$" came from. I simplified the names of all the files involved and it started working. Thanks for the help with the scripts.

---

### Post by miggyboi on 2011-01-03
Hello! I'm an Ubuntu Gnome beginner and I didn't really understand what was mentioned in the above posts. I was hoping to open gametable.jar too, but couldn't. I hope someone can tell and help me how to open it.

Thanks! :)

---

### Post by theophiles on 2011-05-28
To open it, you need to make it executable. To do that, right click, choose properties, then choose "make file executable as program"

---

