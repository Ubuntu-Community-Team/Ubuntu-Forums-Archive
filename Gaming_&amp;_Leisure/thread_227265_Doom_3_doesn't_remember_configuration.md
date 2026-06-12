---
title: "Doom 3 doesn't remember configuration"
date: 2006-08-01
forum: Gaming &amp; Leisure
---

### Post by Icon41 on 2006-08-01
Ok doom3 works fine but I got to setup everything all over again everytime I restart doom3, what should I do?!

edit: I have to run it with the shell script icon thingy, if I type doom3 with terminal it shows alot of things and then this Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg


im thinkin thats the problem. 

Help!

---

### Post by daller on 2006-08-01
What happens if you run it as root?

---

### Post by Icon41 on 2006-08-01
same thing.

---

### Post by FindWaldo on 2006-08-01
I dont have Doom3 installed but I have Quake4 (which is similar)installed and Q3 (which I had the same problem with). Try going into your home folder
>View (enable -show hidden files)
>look for a .doom3 file or something (mine was .quake4)
>go into doom3base folder (mines q4base, im guessing here)
>You should see a "doom3.cfg" file or something of the likes. Right click and save a copy to your home folder (so you can replace it with your original setting (a back-up) or just delete your copy if it works) 
>Double click it and it should open with gedit (if it doesnt, mine didnt, use custom command "gedit"
>Then top line should be "unbindall" just put "//" in front of it save it and close it. Then your config should stay as you config it in the game (or in the file)
(ex: "//unbindall")
Hope that works for ya

Also just saw this in my .cfg file, I dont know if Doom3 is like this but in Q4 to open console you have to press "Ctrl+Alt+`". There is a line in .cfg called "seta com_allowconsole "0"" just replace the 0 with 1 and now the console opens with just `, like every other game.

---

### Post by Icon41 on 2006-08-01
now it doesnt even start up at all

---

### Post by Icon41 on 2006-08-02
hellp!

---

### Post by Icon41 on 2006-08-02
hellp!

---

### Post by FindWaldo on 2006-08-02
Did you replace it with your back-up or delete the "//", should go back to how it was. If I were you I would just copy your save files from SP, if you have those, and reinstall the game with the latest update. Pop your saved files back in place and should be good to go. I really dont know what to tell you, it shouldn't have messed up like that.? Its sounds bad since it couldnt load default.cfg.

---

