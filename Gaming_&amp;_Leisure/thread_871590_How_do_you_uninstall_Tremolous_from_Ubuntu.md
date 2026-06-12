---
title: "How do you uninstall Tremolous from Ubuntu?"
date: 2008-07-27
forum: Gaming &amp; Leisure
---

### Post by Moonfrost on 2008-07-27
I have Ubuntu Hardy Heron 8.0.4.1 and I got tremolous, didn't like it as much as Alien Arena so I want to uninstall it because I'm not going to play it very often otherwise and it's taking space. I found it has an uninstall script file but I tried many things to run it through terminal and nothing, anybody knows how to completely uninstall it? obviously Sypnaptic won't work because this game is not on the repos obviously so if anybody could help it would be awesome, thanks in advance.

---

### Post by Canis familiaris on 2008-07-27
How did you install it exactly?
By Source?
By drag and drop of binary onto terminal?
.DEB file?

---

### Post by Moonfrost on 2008-07-27
> **Anurag_panda said:**
> How did you install it exactly?
By Source?
By drag and drop of binary onto terminal?
.DEB file?

I installed it using a .run file.

---

### Post by Canis familiaris on 2008-07-27
So it is a binary file.
I'm afraid it is very difficult to exactly uninstall binary files installed programs.
You could try manually deleting the folders and icons.

---

### Post by eragon100 on 2008-07-27
Ehhh, not in synaptic? :confused:

Synaptic has the last version, you can install it by going to add/remove applications and searching for it.

Are you sure you have enabled "show all available applications" ? :wink:

---

### Post by Moonfrost on 2008-07-27
> **eragon100 said:**
> Ehhh, not in synaptic? :confused:

Synaptic has the last version, you can install it by going to add/remove applications and searching for it.

Are you sure you have enabled "show all available applications" ? :wink:

I just checked and no it doesn't appear on sypnaptic, I also checked their official website and it seems that they are not hosting the latest version for Linux but only for Windows, the Linux version is slightly older, 1.0.1 or something like that I think while the version that's being hosted on the Ubuntu repos is 1.1.something else. What I want to know if there's a way to activate the uninstall script that comes with it, it's inside the main folder at ```
usr/local/games/tremulous
```

---

### Post by Perfect Storm on 2008-07-27
```
cd /usr/local/games
sudo rm -rf tremulous
cd /usr/local/bin
sudo rm -rf tremulous*
```

should do it. If you want to delete your config files and save games you have to delete .tremulous in your home directory.

---

### Post by Moonfrost on 2008-07-28
> **Artificial Intelligence said:**
> ```
cd /usr/local/games
sudo rm -rf tremulous
cd /usr/local/bin
sudo rm -rf tremulous*
```

should do it. If you want to delete your config files and save games you have to delete .tremulous in your home directory.

Thanks, that seemed to work. I just had to delete the .tremulous folder and then the menu item and everything seems fine, thanks a lot for the help!

---

