---
title: "Xubuntu Programs start at login.."
date: 2012-04-05
forum: Desktop Environments
---

### Post by johnandrews2332 on 2012-04-05
I'm currently running Xubunto 11.10.. When I boot the pc, and login, it starts some applications automatically. I can't seem to find anything in the autostart directories. So I'm a bit confused as to why these apps are loading.. I think It's trying to load the apps I had running the last time I shut down, but I don't want this happening...
Thanks.

---

### Post by 2F4U on 2012-04-05
I am currently not running Xubuntu, so this is from memory. The shutdown dialogue has a setting to save the session settings. This also saves what programs were running when the session is ended and these programs will be started in the new session.

---

### Post by LewisTM on 2012-04-05
In the Settings Manager, pick 'Session and Startup' and uncheck 'Automatically save session on logout'
Then delete the saved session
```
rm -rf ~/.cache/sessions
```
Cheers!

---

### Post by Lemuriano on 2012-04-05
That work for me thanks.

---

