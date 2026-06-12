---
title: "Block Desktop Background Change"
date: 2010-05-10
forum: Desktop Environments
---

### Post by Andy Wilkins on 2010-05-10
How do I stop users from changing their background?

I'm installing ubuntu on some (non-networked) computers at my school, and I don't want the students to change the background on the desktop.

I don't care if they change it during their session, but it must revert to the default when the session is logged-out or shutdown.

Cheers

---

### Post by matchett808 on 2010-05-10
map /home to /tmp/home/ this makes all changes made by the user (including files that are saved there) non persistent, I have done it that way before for 3 internet computers at my old work (for employee personal use) u wld have to think about what the use is......u have to set up a script to give all the default files though (it was ages ago i done this, it was held together with ducktape) I beleive that there is most probably a more "elegent" (mixture of elegant and gentle) soloution but i dont know off hand, maybe permissions? or maybe making all files in the /home directory owned by root, thus not giving the user the power to change thebackground (the config file is somewhere in /home/user)

---

