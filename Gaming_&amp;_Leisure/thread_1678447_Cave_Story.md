---
title: "Cave Story"
date: 2011-01-30
forum: Gaming &amp; Leisure
---

### Post by Refresh100 on 2011-01-30
So anyone here heard of the nifty little game Cave Story?
If not head on over to [http://en.wikipedia.org/wiki/Cave_Story]("http://en.wikipedia.org/wiki/Cave_Story").

Now that you know about it, I am trying to create a launcher (as it took me like 8 minuets trying to figure out how to start it) and it is somewhat successful, but I would like a better GUI for it.
Now, I need a team to help me with this, I need someone to help with the launcher, someone with packaging knowledge to create a .deb, and someone to help me get it on the Software Center.
The source can be found _[here]("https://docs.google.com/leaf?id=0B9xay8N0yLoRZGRiNmYxM2ItMTIwNy00MzE3LThjZTktMDNjYWUwNzY0N2Nm&hl=en")_.
The folder it has to be installed to is $HOME/.Doukutsu
The current launcher is based off of PanelRestore by PhrankDaChicken. I uploaded a screenshot of the launcher as an attachment. Any help is appreciated.

---

### Post by headcheese3 on 2011-09-13
What did you use to launch Cave story? I seem to be incapable of doing so.

---

### Post by mister_k81 on 2011-09-15
Where did you get your version of Cave Story from? 

If you got it from [HERE]("http://www.cavestory.org/downloads_game.php"), you would need to download the file marked: "Doukutsu Linux Port by Simon Parzer and Peter Mackay" and possibly even the 1.2 update (just drop the 1.2 version of the doukutsu_32bits or doukutsu_64bits executable into the linuxDoukutsu-1.01 directory.) .

Once you have done that, click on the file marked "doukutsu" (It has no extension), and Cave Story should run. 

To use the DoConfig.exe file you need to run it in wine...

 But also, in the link I posted above, there is also a native linux configure file called "DoConfigure for Linux by Sean Baker". To use that instead, you just move all the files in the DoConfigure-r2.zip to the linuxDoukutsu-1.01 directory. 

and if you want to create a shortcut to Cave Story, create a new launcher and put this in the command: 

```
sh -c "cd /your_cave_story_directory_here(linuxDoukutsu-1.01) && ./doukutsu"
```

---

