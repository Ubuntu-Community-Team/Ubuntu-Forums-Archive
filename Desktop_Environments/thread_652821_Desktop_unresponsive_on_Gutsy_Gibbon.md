---
title: "Desktop unresponsive on Gutsy Gibbon"
date: 2007-12-29
forum: Desktop Environments
---

### Post by BeamBlack on 2007-12-29
For some reason I can no longer right-click on the desktop. Not only that, but my background no longer shows up and I get no response clicking any of the folders in the Places menu. I can right-click fine everywhere else. Any suggestions?

---

### Post by Mrs Twaddle on 2007-12-29
I think this is due to an update we had this morning, I can't access any folders or anything either.

and when i try to start nautilus in the terminal i get 
nautilus: error while loading shared libraries: libbeagle.so.0: cannot open shared object file: No such file or directory

---

### Post by squee on 2007-12-29
I still have the same problem. Im glad its not due to something that I did. Any ETA on any fix? I need to access some of my files semi-urgently

---

### Post by Mrs Twaddle on 2007-12-29
[http://ubuntuforums.org/showthread.php?t=652477&highlight=libbeagle](http://ubuntuforums.org/showthread.php?t=652477&highlight=libbeagle)

this fixed it for me

---

### Post by squee on 2007-12-29
^^^ Has not yet fixed it for me. I find the link quiet unclear. Thanks anyway.

---

### Post by squee on 2007-12-29
Ok Iv fixed the problem.

Synaptic > search   schmidtke  (searching under version)

Then find the libeagle0 file. I only had a list of about 10 when the search was complete.

select it > package > force downgrade  and select the most recent one under schmidtke one.

Thats the only file you need to downgrade. Select "apply change" then reboot computer.

When you log in things should be back to normal. They were for me anyway.

~Squee

---

