---
title: "Where does the apt-get store the downloaded software package archives?"
date: 2008-12-23
forum: General Help
---

### Post by tee4cute on 2008-12-23
Where does the apt-get store the downloaded software package archives?

Actually, I've just finished reinstalling ubuntu a few hours ago. And I have to download the system update packages all again.

"Can I back up the downloaded software package archives in another drive, copy&paste it in the new installed system and then run the system update with no any packages downloading anymore?"

If yes, where does the apt-get store the archives?

Thanks, this may be helpfully in the next time I have to reinstall the system.

---

### Post by taurus on 2008-12-23
```
ls -la /var/cache/apt/archives
```

---

### Post by lswb on 2008-12-23
Downloaded pcakages are stored /var/cache/apt/archives. I'm not sure if copying package files directly to this directory is a good idea because they may be tracked in some kind of database by the package system. WIth all those apt-something commans there is probably one made for manipulating these files.

---

### Post by tee4cute on 2008-12-23
As "lswb" reply.

It's mean that copy&paste the archives may not help?

Does anyone ever tried to do in this way?

(Thank you ^^)

---

### Post by snova on 2008-12-23
> **tee4cute said:**
> It's mean that copy&paste the archives may not help?

Why would you want to do that?

If you want to install a downloaded .deb you have, right click the package and click the top item, "Open with GDebi Package Installer".

---

