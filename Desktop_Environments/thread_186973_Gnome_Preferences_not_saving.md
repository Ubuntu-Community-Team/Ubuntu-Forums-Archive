---
title: "Gnome Preferences not saving"
date: 2006-06-02
forum: Desktop Environments
---

### Post by mistab1034 on 2006-06-02
I just did a fresh install of dapper this morning, and now whenever I try and change a setting, like removing/adding something to panels, making keyboard shortcuts, changing the Theme, anything at all, they won't stay after I log out and log back in. Everything reverts to the default first boot look of dapper. Little help?

---

### Post by wjoe2003 on 2006-07-18
edit: while playing around I found under system-preferences-session, there is a box to click to save your session settings. create a session name and save what you want your session to load up to. hopefully this works!!!

joe

---

### Post by aysiu on 2006-07-18
I would do what wjoe2003 suggested, but it also sounds as if you're having permissions issues for some reason.

Make sure you own everything in your home directory: ```
sudo chown -R mistab:mistab /home/mistab
``` Assumes your username is *mistab*--substitute your real username as appropriate.

**Warning**: It's okay and even advisable to *chown* your home directory, but you should _never_ *chmod* your entire home directory.

---

