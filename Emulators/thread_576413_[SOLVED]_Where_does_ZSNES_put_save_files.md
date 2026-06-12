---
title: "[SOLVED] Where does ZSNES put save files?"
date: 2007-10-15
forum: Emulators
---

### Post by BigSilly on 2007-10-15
I'm wanting to back up my game saves before I do a clean install of Gutsy this weekend, but I can't find them! When I used the Windows versions of ZSNES, I noticed that your saves are put in your games folder as .srm files, but that doesn't seem to be the case with the Linux version. I checked the pathway in the GUI, it's empty, so where is it storing my save points?

Thanks in advance. :)

---

### Post by BigSilly on 2007-10-15
EDIT: I've found it. Sorry for any trouble, and I'm an idiot! 

Please delete if needs be. Thanks.

---

### Post by dfreer on 2007-10-16
BTW, if anyone else wishes to know, they are kept in ~/.zsnes/

---

### Post by BigSilly on 2007-10-17
Yep. 

Home/ ****/ Edit/ Preferences/ Show hidden and backup files.

D'oh! :oops::roll:

---

### Post by Saghaulor on 2008-01-05
I've gotten that far, I even copied my old save files to the .zsnes folder, however, I can't get the game to recognize my save files.

Also, I started a new game, saved the game, then closed zsnes, then I reopened zsnes and loaded the rom to my game, only to discover that it didn't save my game.

Is there some kind of read/write permissions or something that is not working? I'm not sure what is going on. Also, I tried to change the read/write permissions to my .srm, and when I reopened it to double check, the permissions had returned to default.

Please help. I'm trying to load a game that I've put several hours into.

Ps. I don't know  if it matters, but the save file was originated in zsnes windows, and now I'm using zsnes linux.

Thank you in advance,
Stephen

---

### Post by acoustibop on 2008-01-05
One of the problems that can occur with ZSNES is that, I guess from its history as originally a Windows emulator, it tends not to discriminate between upper case and lower case in paths; I think spaces may cause a problem, as well.  Open your configuration file (~/.zsnes/zsnesl.cfg) and check the path is correctly written; if not, edit it.

You can, of course, set your saves location to be anywhere you want (config -> paths).  Because of the above mentioned idiosyncracy and because, for convenience in sharing, I keep my games, saves etc on an NTFS partition, I always make sure the path to them is free from spaces and all lower case.  I go for lower case because Windows doesn't recognise upper or lower case in paths and this prevents Windows potentially messing up the paths.

**Edit:** ROMs and saves are completely shareable between Linux and Windows.  Not sure about save states.

---

### Post by Saghaulor on 2008-01-11
I've edited my config file found in (~/.zsnes/zsnesl.cfg)  to point to a folder where I have .srm files located. Unfortunately, the saves are still not loading.:(

Do the rom's and .srm's need to be in the same folder? Should I just point the save path to ./zsnes and copy the saves there? I thought that by default this is where ZSNES would look for .srm's. So I copied a .srm to ./zsnes and it still did not load my save files. 

Also, I tried to start a new game and save my progress, only to discover that the new save file didn't actually save.

Is there some kind of rights issue preventing me from saving and loading my game data?

Please help.

Thank you in advance.
-Stephen

---

### Post by BigSilly on 2008-01-11
You shouldn't be having any bother with this. You can stick your save files anywhere you like, and as long as you point ZSNES at it you should be fine. When I performed a fresh install of Gutsy after having Feisty, I managed to re-instate my old save files from a backup just fine - well, once I'd figured out where they were! I just popped them back into the hidden .zsnes folder in my Home folder.

It's certainly not a rights issue anyway.

---

### Post by acoustibop on 2008-01-11
No, Saghaulor, you don't have to  have your saves and ROMs in the same folder.  I don't.

---

### Post by Saghaulor on 2008-03-06
After chatting with a friend who also uses linux, I told him that I was using Xubuntu, and he thought that I was crazy. He swore by Gnome. At this point I had royally screwed up quite a bit in the OS and I had no clue on how to fix it. So I decided to load Ubuntu. Things seems a bit easier, and won't you know, I can load my save files to ZSNES. I don't know of it was the XFCE desktop or Thunar, but something was blocking me from loading my save files.

Anyways, I thought I would post this in case someone else is having similar issues.

---

### Post by Bensy on 2008-09-07
I am having a similar problem. Zsnes worked fine with Gutsy, but now in Hardy it won't load saves I've made already in Hardy (I forgot to backup my old saves when I re-installed, silly me). I mean, I play a new Yoshi's Island game, save, close and when I run zsnes again, they are gone! It doesn't happen when I reset the ROM from within the application. Any tips on what I should do or what it could be? Thanks in advance.

---

### Post by FranMichaels on 2008-09-08
I'm having a little trouble understanding the explanation of the problem. Are you saying if you reset the game from within zsnes, then close, the save states are there, and the problem is only when you close with the X in the corner of the zsnes window. 

If so, try pressing escape and close with the X inside the zsnes GUI.

If you mean saves just aren't kept period, there is likely a permission problem with your .zsnes folder, make sure it is writeable by your user (right click -> properties in nautilus, press ctrl + h to view hidden files.)

---

### Post by tepkel on 2012-03-15
Sorry to bump an old thread, but it is the first one I found when troubleshooting this issue, and I have some input that could be useful to someone searching after me. I believe zsnes has issues with following symbolic links. 

I was having this same issue, saves not being written anywhere while the save path was set to a path that zsnes did not recognize. Initially I had the save path set to a symbolic link. It was not a permission issue, I set everything to 777 to make sure. I decided to set the path to the hard link to the same directory instead, and now everything works fine.

Also, as has been said earlier in this thread, entering a path via the GUI will result in entirely lowercase characters. Alter the config file manually to ensure the path is correct.

Again, sorry if this is not the ideal place to put this. It's my first post.

---

### Post by Perfect Storm on 2012-03-15
Necromancing. Thread closed.
Please start a new thread in our emulator forum.

---

