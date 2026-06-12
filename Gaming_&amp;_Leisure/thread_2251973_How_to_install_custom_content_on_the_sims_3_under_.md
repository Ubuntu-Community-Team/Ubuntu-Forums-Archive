---
title: "How to install custom content on the sims 3? under wine?"
date: 2014-11-08
forum: Gaming &amp; Leisure
---

### Post by ange3 on 2014-11-08
Hi everyone!
I have ubuntu 14.04LTS  and wine 1.7.27
after installing (under wine, not playonlinux) from cd the game the sims 3, updating it to the latest patch and installing the seasons expansion, now I'd like to install some custom content (clothes, hair, furniture etc...) I haven't been able to find a guide or an how to for this, can anyone tell me how to do it?

(I also created a thread for 'how to install mods' here [http://ubuntuforums.org/showthread.php?t=2250581](http://ubuntuforums.org/showthread.php?t=2250581) but maybe I posted it in the wrong subforum? (and if anyone can help me with that as well it'd be great))

Thanks for reading!

---

### Post by dhruv3 on 2014-11-08
It should work normaly like windows, if there isnt a .exe idk then, maybe enter the windows directory under wine and install the .dll from there?

---

### Post by SirMoo on 2014-11-09
If you download the files from an eternal site... It's a pretty simple process of of placing them in the /Mods/Packages folder. Example: /home/sirmoo/.wine/dosdevices/c:/Program Files/Origin Games/The Sims 3/Mods/Packages (If /Mods/Packages folders are missing... make them). 

That being said, Sims 3 has it's own store that has a tool that adds them to the launcher and installs it for you. From my understanding this does not currently work through wine. 

Files using the official site do not work. Third party tools of actually downloading content does work.

---

### Post by ange3 on 2014-11-09
> **SirMoo said:**
> If you download the files from an eternal site... It's a pretty simple process of of placing them in the /Mods/Packages folder. Example: /home/sirmoo/.wine/dosdevices/c:/Program Files/Origin Games/The Sims 3/Mods/Packages (If /Mods/Packages folders are missing... make them). 

That being said, Sims 3 has it's own store that has a tool that adds them to the launcher and installs it for you. From my understanding this does not currently work through wine. 

Files using the official site do not work. Third party tools of actually downloading content does work.

Thanks for your reply!
I don-t understand one thing though, is the mods or the custom content that I install in /Mods/Packages ?

---

### Post by SirMoo on 2014-11-09
Both. All mods/custom content have a .package file You play that .package in the /Mods/Packages folder. 

You can also organize things by putting folders inside of the Packages folder for things like clothing, hair, or other ways to sort it if need be... But just make sure you do this slow as if a package is broken it will prevent your game from loading. I would start out with just a few packages at a time to make sure they're all compatible. 

In the event that you place the content in the /Mods/Packages folder and it does not load... You might need the following text file. 

It's named resource.cfg
> Priority 500 
PackedFile Mods/DCCache/*.dbc 
PackedFile Mods/Packages/*.package 
PackedFile Mods/Packages/*/*.package 
PackedFile Mods/Packages/*/*/*.package 
PackedFile Mods/Packages/*/*/*/*.package 
PackedFile Mods/Packages/*/*/*/*/*.package

---

### Post by ange3 on 2014-11-09
Thanks again for the explanation!
but that resource.cfg ... what is it? Do I have to create it myself? and put it in which folder?

---

### Post by SirMoo on 2014-11-09
It should go in the main sims3 game folder (if it's not already there). Basically all it does is tell sims3 which folders are acceptable to look for add ons in. That will allow addons to be placed in subfolders within the Packages folder as well as tell the system that is where your mods are.

---

### Post by ange3 on 2014-11-15
> **SirMoo said:**
> It should go in the main sims3 game folder (if it's not already there). Basically all it does is tell sims3 which folders are acceptable to look for add ons in. That will allow addons to be placed in subfolders within the Packages folder as well as tell the system that is where your mods are.

Thank you! everything works and i could finally install cc! thanks!

---

### Post by carrington2 on 2014-11-20
i think .dll file missing. you double check your game file.

---

