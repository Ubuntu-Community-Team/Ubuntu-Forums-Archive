---
title: "lost permissions!"
date: 2004-12-10
forum: Desktop Environments
---

### Post by k3tan on 2004-12-10
i think i screwed the permissions in my /home/***/ directory. i cant rename anything, and i dont think i can write to it anymore. how can i fix this?
thanks
k3tan

---

### Post by oscarh on 2004-12-10
[QUOTE=k3tan]i think i screwed the permissions in my /home/***/ directory. i cant rename anything, and i dont think i can write to it anymore. how can i fix this?
thanks
k3tan[/QUOTE]
 chown -R USER:users home/*** 
chmod 744 /home/*** (chmod u+rwx /home/***)

you have to have execute in all directories to be able to list the files

---

