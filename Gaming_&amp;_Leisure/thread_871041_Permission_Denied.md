---
title: "Permission Denied"
date: 2008-07-26
forum: Gaming &amp; Leisure
---

### Post by Death Dream on 2008-07-26
I know this has been asked a lot because I did some searching but can't find the exact answer I am looking for.

Is there a way to change the permissions on the Games folder (user/local/games) so that anyone can write to that folder? Right now the only way I can create a folder is with Sudo in terminal.

---

### Post by DoktorSeven on 2008-07-26
Basically, installing things anywhere in /usr does require root permission (via sudo) for a reason (system security).  Installing a game in /usr/local/games would require you use sudo or root user (if you enable it).  

If an unpriviledged user wants to install something, they can put it in their home directory and run it from there.

Is there something specific you want to do here?

---

### Post by Death Dream on 2008-07-26
Well I thought that was just the general location we should install our games. I was going to put UrbanTerror in there and then install UT04 there as well. I was just hoping to change the security permissions on that game folder so I can just drag and drop my UrbanTerror there and do the GUI install for UT04.

---

### Post by kdorf on 2008-07-26
Instead of changing the permissions on the folder, run the installer with sudo and change the path to /usr/local/games.

Easy enough?

If you insist on changing permissions, you can give write permissions to all via chmod or you can change the owner via chown.

Use "man chmod" and "man chown" in the terminal for more information.

---

### Post by Death Dream on 2008-07-26
I just went ahead and installed them under the User's name and created a Games folder and just install the games there lol.

---

### Post by RuleMaker on 2008-07-26
To enable anybody to write in "/usr/local/games" use the following:
```
sudo chmod a+w /usr/local/games
```

---

### Post by DoktorSeven on 2008-07-26
> **RuleMaker said:**
> To enable anybody to write in "/usr/local/games" use the following:
```
sudo chmod a+w /usr/local/games
```

However, please note that this is not a good idea.  Again, system security should be more important, and it's really not that hard to use sudo to install stuff so that you always know when you're changing system directories.

Not judging, really; it's your system and if you want to do this, go ahead.  Just warning that it's generally not a good idea.

---

