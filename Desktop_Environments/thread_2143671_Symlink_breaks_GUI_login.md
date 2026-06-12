---
title: "Symlink breaks GUI login?"
date: 2013-05-09
forum: Desktop Environments
---

### Post by dfresh4130 on 2013-05-09
I'm used to korn shell, not bash.  Don't use the shell enough on my home desktop to change it from bash, but I always want to edit .profile instead of .bashrc.  So the other night I decide to symlink my .bashrc by doing ```
ln -s /home/user/.bashrc /home/user/.profile
```.  Everything seems fine and I'm happy.  I restarted into windows last night to play some games and then when I reboot to go back to ubuntu desktop I find that I just get a black screen after entering my password like the resolution is changing then come back to the login screen.  Happens every time no matter what I tried.  I could login as a guest just fine.  Finally remembered what had changed recently and removed my symlink.  Now it works fine.  Any one have any ideas why symlinking .bashrc to .profile breaks the GUI login?

---

