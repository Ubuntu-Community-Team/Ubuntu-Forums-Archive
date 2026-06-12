---
title: "Dosemu help!"
date: 2008-02-14
forum: Gaming &amp; Leisure
---

### Post by jsnelli2 on 2008-02-14
Ok- I've installed the newest version of dosemu and have been able to load games.  I only have two problems so far:  I am not sure how to configure my sound card and I need to figure out a way to lock the mouse into the program being run (i.e. I'm playing a First Person Shooter, but the mouse isn't tied directly into the system so I can't turn without moving out of the screen.)  

Any help would be GREATLY appreciated!

---

### Post by jcwmoore on 2008-02-14
dos games you say... well I use dosbox, it works great for those games and i have never had any trouble with sound or video, BTW I use dos box game loader (DBGL) as a "manager"  works great!

---

### Post by jsnelli2 on 2008-02-14
Thanks--I'll give it a try.  Where can I find the dos box game loader?

---

### Post by jsnelli2 on 2008-02-14
I just tried dosbox- no problem with sound and the mouse reacted like it should have. Thank you very much!  It seemed to run the first person shooter a little slower, but it's playable now that I have sound and correct mouse movement. I'll mess with it!  Thanks a lot! If you could point me out to the game loader I'd be all set!!

---

### Post by grossaffe on 2008-02-14
when downloading dosbox, you should look at its compatilitiy list and find the version that best suits each of your games.

---

### Post by jsnelli2 on 2008-02-14
so far all of the games I have tried have ran fine.   Are you saying that it is sometimes necessary to run multiple versions of it?

---

### Post by grossaffe on 2008-02-14
> **jsnelli2 said:**
> so far all of the games I have tried have ran fine.   Are you saying that it is sometimes necessary to run multiple versions of it?

different versions of dosbox have different compatibility levels with different games.  they have compatibility lists that show you which version is best for which game.  for the most part it shouldn't cause many problems, but every now and then you may find a game that needs an older version of dosbox.

---

### Post by yowshi on 2009-06-09
i have mouse issues with dosbox. my issue is the mouse cursor moves veeeeeery slow in fullscreen mode. every game i try i have to move the mouse 3 times more then i would have to in say dosemu to get the cursor to move any amount of distance on the screen.

---

### Post by CharmyBee on 2009-06-09
This thread is for dos**emu** however, which is a completely different animal. I can't lock the mouse in either (and I do use dosemu to play the more heavier games such as Blood in 1024x768 smoothly)

---

### Post by rCXer on 2009-06-09
> **yowshi said:**
> i have mouse issues with dosbox. my issue is the mouse cursor moves veeeeeery slow in fullscreen mode. every game i try i have to move the mouse 3 times more then i would have to in say dosemu to get the cursor to move any amount of distance on the screen.

Which game are you using? It may have issues with DOSBox.

Changing the mouse sensitivity in the configuration file might help.  If you haven't created a configuration file, run DOSBox and type the following into its prompt.
```
config -writeconf dosbox.conf
```
This will create a configuration file, dosbox.conf, in "/home/YourUserName/". Open dosbox.conf, find the line that says...
```
sensitivity=100 
```

...and increase it to a higher value e.g. 200, save it and restart DOSBox.

Sorry if this post is off topic :p

---

