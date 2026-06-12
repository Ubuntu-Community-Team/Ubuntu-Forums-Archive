---
title: "Getting rid of installed features"
date: 2012-12-19
forum: Desktop Environments
---

### Post by Enkel on 2012-12-19
I have managed to alter a setting which causes my Username to appear at the right hand end of the menu bar (12.10 Quantal Quetzel).  Since I know my own username, I don't really need it there.  can someone tell me how to get rid of it, please.

Also I installed the Razor desktop some time ago.  I have decided it's not for me, so how do I get rid of that option, please?

Thanks

---

### Post by zombifier25 on 2012-12-20
I assume you want to remove your username from the top right corner. If so, then type this:
```
gsettings set com.canonical.indicator.session show-real-name-on-panel false
```

And to remove Razor-Qt's entry, have you removed Razor-Qt completely? If you have, then check the folder /usr/share/xsessions and see if Razor's entry is still there.

---

### Post by Enkel on 2012-12-22
Thank you Zombifier25 for those hints.  Job done and all seems OK now, thanks.

---

