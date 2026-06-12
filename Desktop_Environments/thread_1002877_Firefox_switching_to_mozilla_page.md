---
title: "Firefox switching to mozilla page"
date: 2008-12-05
forum: Desktop Environments
---

### Post by Grimmwolf on 2008-12-05
Nautilus and Firefox switch to the set homepages (personal folder, about:blank) while I use the programmes. I have no idea why this happens. First I though it was a firefox issue until I noticed it happened in nautilus as well. I suspect that my Logitech G15 keyboard might cause the issue...

(I will look for similar problems now, I could not find anything with the earlier suspicion of firefox being the problem)

---

### Post by aysiu on 2008-12-05
I don't know this for sure, but it's worth exploring: it's possible that you might have accidentally changed ownership of some configuration files in your home directory.

Can you close both Firefox and Nautilus and then paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
sudo chown -R $USER:$USER ~/
``` And then see if the behavior persists in Firefox?

---

### Post by cpeachey on 2009-12-06
I had this problem too and the above terminal command seems to have fixed it.
What exactly does the command do please?
Chris

---

### Post by Shazaam on 2009-12-06
chown =change owner
-R =recursive
$USER:$USER =change from old owner to new owner
~/ =home folder/directory

[http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)

Or...
```
man chown
```
in terminal.

---

### Post by Grimmwolf on 2009-12-06
Cool, that the commands given by "aysiu" helped you. The solution to my problem was to uninstall the G15 packages. After that the problem did not occur anymore. On 9.10 I installed the g15-daemon again and now the problem seems to be fixed.

---

