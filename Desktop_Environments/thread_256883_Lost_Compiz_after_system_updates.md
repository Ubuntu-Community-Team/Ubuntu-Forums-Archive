---
title: "Lost Compiz after system updates"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Gouki on 2006-09-13
Hi everyone,

I left on vacations and left one of my computers turned off. When I got back home, I had ~130 updates do download and install.

After downloading all of them, I had an error on the installation on the last few (don't remember the error nor the update who cause it).

After restarting Compiz never worked again. I have the XGL process running, all the packages of XGL installed, but NADA! Doesn't work.

Any ideas? Thank you.

---

### Post by Dinerty on 2006-09-13
The new updates of xgl/compiz have removed gconf-editor and has been replaced by csm (csm is simplat to naviagte and has a friednly gui)

Try this link:

[http://www.ubuntuforums.org/showthread.php?t=250489](http://www.ubuntuforums.org/showthread.php?t=250489)

---

### Post by Gouki on 2006-09-15
Thanks for the tips. *Almost* there.

When I add '/usr/bin/compiz-start/ to startup, I get an error (which I can't read) and can't get into GUI. When I disable the entrie and manually 'compiz-start' on the Terminal, I get the following:

```
nohup: appending output to `nohup.out'
```

Which is empty, BTW.

Any ideas of what is causing X or Compiz to crash when on the startup programs list?

**EDIT/UPDATE:** Fixed! I had to remove my old startup script.

---

