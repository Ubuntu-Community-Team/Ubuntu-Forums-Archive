---
title: "how to run starcraft with cedega 4.3"
date: 2005-05-07
forum: Gaming &amp; Leisure
---

### Post by pdk001 on 2005-05-07
hi buddy
i've installed cedega 4.3 last day, i was trying to figure out HOWTO cedega text file or link(im sorry to google doesnt help me out about this)
i tried to do like above that
pdk001@ubuntu:~$ cedega starcraft.exe?
its says /usr/lib/transgaming_cedega//winex/bin/wine: cannot find 'starcraft.exe'
i have to re install starcraft in linux machine?(i've already been installed sc:bw and copyed broodwar.LCD in windows folder, i dont use cd rom when i run this game)
thanks in advace, regards

---

### Post by Amarack on 2005-05-11
Hey man, I think it might be a problem with the filename. Its been a while since I played starcraft, but I think the actual executable might have been named something like StarCraft.exe. I could be wrong on this, but I would recommend the following:

open a terminal
navigate through your folders to find the location where you installed starcraft to
look at the files in the directory and check to see that you know the right file name (.exe one..) 
Now, while you are still in that directory run the cedega on the file you found. I really hope you get this working. Please reply back whether or not this helps. Good luck!

---

### Post by gil-galad on 2005-05-11
The problem is that you are trying to run starcraft.exe in your home folder.  starcraft.exe probably isn't in your home folder.  You need to go to where the program is and run it there.

---

