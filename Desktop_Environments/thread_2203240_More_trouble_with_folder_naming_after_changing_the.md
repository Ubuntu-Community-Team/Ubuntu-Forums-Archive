---
title: "More trouble with folder naming after changing the locale"
date: 2014-02-02
forum: Desktop Environments
---

### Post by ShukatsuRonin on 2014-02-02
Today I tried to create a new user on my 12.04 Xubuntu machine. My base system is in French but I wanted the locale to be English for that person. I added an unprivileged user using the gui interface (no question asked about language, of course).

 First time I loged in, it was in French so I went to language support and bumped up English. Logged out and in again and everything seemed fine. Except for the fact that the default folders in the home directory had kept their French names: Musique, Images, etc. Because it's Xfce (?) I wasn't asked if I wanted to change the folders' name the first time I logged in as in Ubuntu.

 I guess that's when I should have asked for help because I “messed up” the session further. Can't remember what I did exactly but I tried to edit manually .config/user-dirs.dirs. First there was no changes, it reverted. Then I removed the file along with “.config/usr-dirs.locale” and ran  
 ```
xdg-user-dirs-update
```

I got the right names but the icon folders were plain icons folders, no difference between desktop or music or pictures. Furthermore, they all appeared on the desktop (home, trash can, devices and then the whole set of folders within the home folder). I couldn't hide them when clicking properties, I couldn't put them back inside the home folder on the desktop all I could do was send them to the trash. It would make the home folder empty as well.  
 
Any ideas?

---

