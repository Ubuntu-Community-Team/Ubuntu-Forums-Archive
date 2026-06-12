---
title: "tvtime i clicked on mirror and it will not load anymore"
date: 2005-11-27
forum: Desktop Environments
---

### Post by manning33 on 2005-11-27
Ok i was just running through the settings on video, and I think the last thing i clicked on was mirror in the settings and then it crashed, shut down etc.  Now when I start it all it does is shows a blue screen for a milli sec and shuts down. I am not a guru on linux so I dont know where to fine some kind of config file and turn that setting off so it loads tvtime back up. I tried removing and reinstalling but same thing happens.  So there must be a setting file that does not get removed when you remove the program.  If anyone can steer me in the direction to go I would be greatly apprieceated, like I always am when someone gives me there time.

Thanks alot, 
Steve

---

### Post by RAOF on 2005-11-27
If you "Select for complete removal" tvtime in synaptic, that should remove all the configuration files for tvtime as well.

Similarly, from the console "sudo apt-get remove --purge tvtime" will do the same thing.

Finaly, tvtime probably keeps its config files in a hidden directory in your home folder, called ".tvtime".  Deleting or moving this directory should make tvtime recreate its default setup.

---

### Post by manning33 on 2005-11-27
I tried that just now and the same thing. I removed the program, I reinstalled it and still wont load cause of me playing with the settings.  How do you show hidden files, cause that config file is not shown in the home folder

---

### Post by RAOF on 2005-11-27
You show hidden files with Ctrl-H (I think), or View -> Show Hidden files in nautilus (the file manager).

Alternatively, "ls -a" at the console will show everything (including hidden files).

---

### Post by manning33 on 2005-11-28
Ha ha, yes the ctr-h worked and there was the tvtime file. I opened with the edit and changed the mirror setting from 1 back to a zero and bamm the program turns back on.  Sweet!!!!!!!!!!!!  Now i just have to get the sound to work.  But thats on it's own thread.  Roaf I thank you for your expertise....

---

