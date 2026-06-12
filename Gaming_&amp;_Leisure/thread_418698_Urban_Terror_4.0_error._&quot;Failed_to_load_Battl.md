---
title: "Urban Terror 4.0 error. &quot;Failed to load BattlEye server&quot;"
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by wat3r on 2007-04-22
Hello.
When I try to join a server on the internet in Urban Terror 4.0, or make a server, I get an error message that says "Failed to load BattlEye server"
What can that be? I tried to update the BEServer and BEClient files, but it did not help.

---

### Post by berserker on 2007-04-22
This solved it for me.  Put this in a bash script, make it executable and use it to launch UrT:

```
#!/bin/sh
cd /usr/local/games/UrbanTerror
./ioUrbanTerror.i386 $*
exit $?
```

Make the directory in the second line wherever you installed UrT.

---

### Post by wat3r on 2007-04-23
> **berserker said:**
> This solved it for me.  Put this in a bash script, make it executable and use it to launch UrT:

```
#!/bin/sh
cd /usr/local/games/UrbanTerror
./ioUrbanTerror.i386 $*
exit $?
```

Make the directory in the second line wherever you installed UrT.

I am not the best Ubuntu'er ever, so I have to ask some dumb questions:
- What is a bash script?
- How do I make it executable?
- How do I use it to launch Urban Terror?

---

### Post by berserker on 2007-04-23
1.  Open up a terminal and type "gedit" if you use GNOME or "kedit" if you use KDE (without the quotes).

2.  Paste in the code.  Save as (for example) /home/yourusername/urbanterrorlauncher.  Close gedit or kedit.

3.  Type ```
chmod +x /home/yourusername/urbanterrorlauncher
```  This makes it executable.

4.  ```
cd /home/yourusername
./urbanterrorlauncher
```  This will launch the game.  

You can now make a desktop icon that launches that script.  The forum has plenty of examples of how to do that.

HTH

---

### Post by Perfect Storm on 2007-04-23
You can check here for Installation guide of Urban: [http://gaming.gwos.org/e107_plugins/content/content.php?content.68](http://gaming.gwos.org/e107_plugins/content/content.php?content.68)

---

### Post by wat3r on 2007-04-23
> **berserker said:**
> 1.  Open up a terminal and type "gedit" if you use GNOME or "kedit" if you use KDE (without the quotes).

2.  Paste in the code.  Save as (for example) /home/yourusername/urbanterrorlauncher.  Close gedit or kedit.

3.  Type ```
chmod +x /home/yourusername/urbanterrorlauncher
```  This makes it executable.

4.  ```
./urbanterrorlauncher
```  This will launch the game.  

You can now make a desktop icon that launches that script.  The forum has plenty of examples of how to do that.

HTH

Ok. Thank you for your help. I can't try this now, since I don't have my computer here, but I will try this :)

---

### Post by wat3r on 2007-04-23
> **Artificial Intelligence said:**
> You can check here for Installation guide of Urban: [http://gaming.gwos.org/e107_plugins/content/content.php?content.68](http://gaming.gwos.org/e107_plugins/content/content.php?content.68)

I used this guide when I first installed Urban Terror. At least it got the game running into the start menu ;)

---

### Post by wat3r on 2007-04-28
> **wat3r said:**
> Ok. Thank you for your help. I can't try this now, since I don't have my computer here, but I will try this :)

Just wanted to inform that this works ;)

---

