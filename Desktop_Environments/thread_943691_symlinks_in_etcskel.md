---
title: "symlinks in /etc/skel"
date: 2008-10-10
forum: Desktop Environments
---

### Post by Keymaster on 2008-10-10
Every once in a while I add a new symlink that I want to be in /home/userdir for all the users on the system.  Now I normally put this in /etc/skel so it propogates to all existing users, but there are 7 or so users already here that need 9 new symlinks added to their homedirs.  How can I "reskel" the symlinks to existing users.  Any script source would be really helpful. Thanks

---

### Post by Keymaster on 2008-10-13
Seriously? No one can help me with this?  It's very important I get this figured out.  Thanks

---

### Post by whollycow on 2008-10-31
Don't know if it's exactly what you're looking for but I just ran across this today while trying to solve a similar problem:

[http://www.k12ltsp.org/mediawiki/index.php/Pushing_Folder_Icons_to_Clients](http://www.k12ltsp.org/mediawiki/index.php/Pushing_Folder_Icons_to_Clients)

Note: It looks like the script needs to be updated by hand but the site has instructions for all of that.  Good luck.

---

### Post by Keymaster on 2008-10-31
Thanks.  I could not find the DL link for the script.  Any idea where it is?

---

### Post by Desertship on 2011-02-25
I'm quite new to this. But i've read that the adduser command just copies the skel-folder so you should be able to just write a script that copies all the symlinks in evry dictionary...

---

