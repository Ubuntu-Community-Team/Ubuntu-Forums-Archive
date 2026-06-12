---
title: "Regarding hidden files"
date: 2008-10-05
forum: Desktop Environments
---

### Post by shyam_19489 on 2008-10-05
I want to hide the Show Hidden Files option in the View Menu in Nautilus....

I was possible to hide the Folder Options option under the Tools menu in MS Windows by using a simple registry tweak...
 
I now migrated to Ubuntu n would like to secure the hidden stuff on my comp because i use a shared computer with other people less conversant with computers..

Is there a way to do this? so that files starting with a . are not shown with such a simple option. I would also like to remove the Show Hidden Files option in the right click context sensitive menu in ubuntu open/save dialogs...

Somebody plz... plz.. plz.. help.

---

### Post by mcduck on 2008-10-06
Why not just give the other users their own accounts and then change the home permissions so that users can't access others homes?

The dotfiles aren't really supposed to be a way to truly hide things from users.

Also if you, for some reason, don't want to give them own accounts you could use encryptFS to create encrypted directory to keep your stuff.  Cryptkeeper, for example, gices you a nice icon in the Notification area that allows you to mount & unmount the directory (using a password) whenever you need to access it.

---

### Post by alynx on 2008-10-06
if the other users are less conversant with computers I would definetly go with Mcducks answer.  A username for every user with oridinary access so they won't accidently screw anything up.

---

