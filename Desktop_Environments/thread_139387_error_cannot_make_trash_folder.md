---
title: "error: cannot make trash folder"
date: 2006-03-03
forum: Desktop Environments
---

### Post by 7018 on 2006-03-03
I installed kubuntu over ubuntu after trying various flavours of desktops. 

however now I'm getting an error when I start up.

Error: Cannot make folder /home/gee/.local/share/Trash.

I cannot delete files or move files to my trash icon.. .

Also seems Kubuntu seems to come bundled with alot of drinkers cause there is alot of glass smashing going on in my machine which wasn't there before.... :)

Please help

---

### Post by pestilence4hr on 2006-03-03
Sounds like the permissions on your home folder are set incorrectly.  Try "sudo chown -R gee:gee /home/gee", see if that helps.  You might also try after that "chmod -R u+rw /home/gee/.local"

---

### Post by 7018 on 2006-03-04
pestilence4hr,

Thank you my friend, your suggestion worked like a charm.

My spirits have been lifted :)

---

