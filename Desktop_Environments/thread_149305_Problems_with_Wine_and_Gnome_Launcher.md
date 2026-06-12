---
title: "Problems with Wine and Gnome Launcher"
date: 2006-03-23
forum: Desktop Environments
---

### Post by nu2linux6 on 2006-03-23
Hi,

I've just installed wine and would like to be able to create icons on my desktop so that I can run Windows apps direct from there. If I "cd" into a relevant game directory from a terminal and type, for example, "wine game.exe", it all works fine, no problem. When I try to create a launcher for it, however, the same game starts to load but then just crashes. I'm guessing this is because it needs a path to be set up so it can see the other files in the directory. I've tried adding the directory to the Environment key in wine's regedit, which means I can now type "wine game.exe" from anywhere, but the game itself still crashes. Do I need to add the path in bash as well? If so, is there an easy way of doing that, or am I on the wrong track completely? ](*,) 

Any help would be much appreciated. Thanks!

---

### Post by bluevoodoo1 on 2006-03-23
Does your command look something similar to this??

wine .wine/drive_c/Program\ Files/Finale\ 2003/FINALE.EXE

and the application should work.

I'm going to go into GNOME and see if it works as a desktop launcher...

EDIT: Tried that command with a Desktop launcher and it worked.

---

### Post by nu2linux6 on 2006-03-23
Thanks a lot for the reply. Yes, I've tried that and it still doesn't work. It just crashes out with the same Unhandled page fault errors. Yet go manually into the directory and run it from there and it all works fine, with full 3D graphics.

Actually I've noticed this with some Linux games as well. Try running it from a launcher and it just crashes. Run it by going into the directory from the terminal and it works fine.

It's clearly not with everything, either, as other windows apps, like calculator, work fine using the launcher. It all seems very odd...

Any more ideas?](*,)

---

### Post by bluevoodoo1 on 2006-03-23
What if you try your command in the terminal as one long command as stated above? (instead of changing directories to its folder and running wine game.exe)  Then any errors *should* hopefully be displayed.

---

### Post by nu2linux6 on 2006-03-24
Yes, that's when I see the Unhandled Page Fault errors. I've kind of found a way round it by writing a small bash script that will cd into the directory and then run it. It's a bit fiddly but it works fine. It seems that for some apps Ubuntu insists you must be in the right directory first or else it won't work. (It doesn't seem to be a problem with either launcher or wine as such.) It's just a bit annoying as you don't know what will work directly and what won't!

Thanks anyway for your help.

---

