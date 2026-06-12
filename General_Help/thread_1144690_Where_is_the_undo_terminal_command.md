---
title: "Where is the undo terminal command?"
date: 2009-05-01
forum: General Help
---

### Post by rreyes1316 on 2009-05-01
Still a newbie level II:)

I have Ubuntu installed on three hard drives. The first is my stable configured OS. The other two are for playing and testing. 

If I enter a command in the terminal and it screws things up, how do I undo it? Is there a revert to original or something?

Here is what happened: I tried to install Emerald with this *compiz --replace +c emerald &*  but it did not work. Compiz stopped working and my appearence preferences were set to none. I selected "Extra" but all I got was a window that said "Desktop effects could not be enabled". I have been toying with Ubuntu for two weeks now and there  has to be a revert or undo command somewhere. Or how about taking a snap shot of my current status before I toy with something? This would be a very handy thing to know for someone that loves to tweak all the time.

---

### Post by kanikilu on 2009-05-01
There's definitely not an "undo" command in the terminal. The best advice I can give is when changing config files, manually make a backup first before changing the original. That way, even if you seriously bork your install, you can always boot into recovery mode, drop to a root shell, and restore the backup.

Also, not sure if this is what you are looking for, but there are a couple "Time Machine"-like projects for linux. I haven't had an opportunity to try either yet, but you might want to look into them...

[http://flyback-project.org/](http://flyback-project.org/)

[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

---

