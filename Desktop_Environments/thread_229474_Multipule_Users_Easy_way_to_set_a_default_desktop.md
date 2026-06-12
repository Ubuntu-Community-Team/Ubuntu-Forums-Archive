---
title: "Multipule Users: Easy way to set a default desktop?"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Danny Boy on 2006-08-04
I'm trying to move my family over to Ubuntu all they really do play simple games which I should be able to configure in wine with out much trouble. 

I have to create two other user accounts. One for my mother and one for my sister. I want to place desktop shortcuts on both their desktops. Basically just icons to games and firefox. Is there an easy way to this? 

In Windows, I'd just navigate to their Desktop directory in Docs & Settings. I know it's a little different in Ubuntu because of the way folder permissions work. Since the desktop folder is in another users home directory which I don't "own" will I even be able to navigate to it?

Thanks in advance, 
Dan

---

### Post by ifokkema on 2006-08-04
If you open nautilus with
```
gksudo nautilus
```
you'll have write privileges on their desktop. Don't forget - files you create are owned by root, but you can change that through the file's properties -> Permissions.

Good luck!

---

### Post by Danny Boy on 2006-08-07
Thanks, I just remember I installed the Natulis scripts through Automatix, I was able to right click ->> Browse a root. :)

---

