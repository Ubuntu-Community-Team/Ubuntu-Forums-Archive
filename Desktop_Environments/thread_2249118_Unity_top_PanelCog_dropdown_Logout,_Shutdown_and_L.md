---
title: "Unity top Panel/Cog dropdown: Logout, Shutdown and Lock/Switch Account not Working"
date: 2014-10-19
forum: Desktop Environments
---

### Post by myacct on 2014-10-19
I believe that I know what caused this but don't know how to fix it.  Any help will be much appreciated!

Here's what happened:

1. Unity search functionality broke on my machine
2. To solve this I set about to uninstall and reinstall unity-scope-home
3. Upon removing unity-scope-home, apt also removed unity-tweak-tool and ubuntu-desktop
4. Next I reinstalled unity-scope-home, unity-tweak-tool and ubuntu-desktop

Doing this did fix the broken unity search, however a side effect seems to be that I've lost shutdown,logout, and lock/switch account functionality from the top right panel from the cog/gear drop down.

Thank you in advance

---

### Post by deadflowr on 2014-10-19
Have you tried a quick logout?
You can logout by pressing ctrl++alt_delete.

Maybe a full compiz reset is in need.
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

Also, you might get the panel functions back with
```
killall unity-panel-service
```
*might* being the keyword here.
The command will kill the panel, which will be automatically reloaded.Whether or not it works as it should is another matter...

---

### Post by myacct on 2014-10-20
Thank you for your advice.  I did both, reset compiz and stop/restart the unity-panel-service but neither solved the problem.  Also to answer your question, ctrl-alt-delete does bring the logout/shutdown prompt.  Thanks again.

---

### Post by myacct on 2014-10-20
Thank you for your advice.  I did both, reset compiz and stop/restart the unity-panel-service but neither solved the problem.  Also to answer your question, ctrl-alt-delete does bring the logout/shutdown prompt.  Thanks again.

---

