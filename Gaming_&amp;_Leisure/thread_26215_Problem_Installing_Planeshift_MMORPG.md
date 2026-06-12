---
title: "Problem Installing Planeshift MMORPG"
date: 2005-04-12
forum: Gaming &amp; Leisure
---

### Post by geo926 on 2005-04-12
When trying to install Planeshift after it verifies the archive integrity I get this message

```
libgtk-1.2.so.0: cannot open shared object file: No such file or directory
``` 

What Should I do?

---

### Post by Giawa on 2005-04-12
I'm not sure if this will help, but this is what I would try first.

Add extra repositories using these instructions:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Then go under System>Administrations>Synaptic Package Manager

Then click reload. Then search for libgtk and make sure you have the updated releases. If not, mark them for installation. If that doesn't fix it then I'm not sure what to do next as I'm pretty new to Linux.

---

### Post by Perfect Storm on 2005-04-12
Some games have troubles launching if they aren't launched from their directories.
So if the solution descripted in the post above doesn't help try

cd /where/the game/is/installed
and start the game from there or making a script so yo can launch it from anywhere.



.:=The AI Dude=:.

---

### Post by rathel on 2005-07-07
I To am having a Installation Problem. But my error message is this:
```

Creating directory ps.cb.03.010
Verifying archive integrity... All good.
Uncompressing Planeshift Crystal Blue Version 3.010..
./setup.sh: line 57: dialog: command not found
./setup.sh: line 59: dialog: command not found
./setup.sh: line 113: dialog: command not found

Removing tmp files...

```
How would I resolve this proble? try downloading it agian?

EDIT: nevermind i got it.

---

### Post by skoenig on 2005-07-08
just install the dialog package :)


```
sudo apt-get install dialog
```

or use synaptic

---

### Post by gat on 2005-07-30
for whatever help it gives:

I downloaded the Planeshift...run file from [http://www.planeshift.it/download.html](http://www.planeshift.it/download.html)

then opened a console:

cd [the download directory i chose]
chmod 700 Plane*.run
./Plane*.run

[then I got the error messages about setup.sh, etc.  I installed the dialog tool as mentioned above, and then it worked]
[the runfile then prompted me (via dialog) to choose an install path, etc.  I chose my home directory, $HOME]

cd $HOME/planeshift

[after some trial and error, I ran the game with...]

./psclient

Sorry if this post is redundant, but I wasn't able to find these few instructions on the same page.  The tip about the dialog tool was a very big help to me.  Thanks and good luck.

---

