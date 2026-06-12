---
title: "Folder Permissions"
date: 2005-12-22
forum: General Help
---

### Post by thesupremeg33k on 2005-12-22
Been using Ubuntu for a few months now, and everything has been pretty positive.  One little thing thats been bugging me is something weird thats going on with folder permissions.  Right now I have a folder in my root directory (for easier access by all users) for my music.  When I copy some of my backed up stuff from CD to it, the folders and files show up as read-only.  I have to go through as root and change them, which gets sort of old.  Is there any way to easily have the folders copy over as non-read-only?

---

### Post by Denis on 2005-12-23
I don't realy know how to do that. But you could make to proces of changing the ownership easier by doing it with the terminal. I guess that your files are owned by the root user instead of the normal user. Just type: "sudo chown -R username:username /music/*" (change username and /music) Does this help you? It is a lot faster than doing it in the GUI...

---

