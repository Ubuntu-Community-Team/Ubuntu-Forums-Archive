---
title: "Gnome menu additions"
date: 2005-02-21
forum: Desktop Environments
---

### Post by malegria on 2005-02-21
For some reason my additions to my GNOME menu do not appear. I access them like this ```
nautilus Applications://///
```
And then add a launcher. This _used_ to work, but not anymore.

Need I change something in the Configuration Editor.?

When I run the above command to the launcher group I want,  I _do_  see the launcher created but not when actually running through the menu.

Any ideas?

---

### Post by kassetra on 2005-02-21
I think I had this same problem at first as well... try doing this command... and then try adding a launcher. If it works, you're set -- (username is your username):
  
   ```
sudo chown -R username /usr/share/applications
```
 
 also, after you have added a launcher, you *may* have to log out and log back in to see it in the menu.

---

### Post by malegria on 2005-02-21
[QUOTE=kassetra]I think I had this same problem at first as well... try doing this command... and then try adding a launcher. If it works, you're set -- (username is your username):
  
   ```
sudo chown -R username /usr/share/applications
```
 
 also, after you have added a launcher, you *may* have to log out and log back in to see it in the menu.[/QUOTE]
 Thanks for the tip first of all. I've just tried that and it didn't work. 

I've logged out twice and still nothing. 

Any other ideas? :-)

---

### Post by malegria on 2005-02-21
And another thing. I was able to add a "submenu" to the "Applications" menu, but the launcher I created in it is nowhere to be seen. Likewise the launchers created under "Internet" are not there.

---

### Post by kassetra on 2005-02-21
[QUOTE=malegria]Any other ideas? :-)[/QUOTE]
  
  yes, because I goofed.
  
  You *also* need to type this command:
   ```
sudo chmod -R 775 /usr/share/applications
```

---

### Post by piedamaro on 2005-02-21
Vfolders have always had problems, thus they were removed from gnome. (actually there is no gui to edit menu entries in hoary).

---

### Post by Wim Sturkenboom on 2005-02-21
[QUOTE=malegria]And another thing. I was able to add a "submenu" to the "Applications" menu, but the launcher I created in it is nowhere to be seen. Likewise the launchers created under "Internet" are not there.[/QUOTE]If a submenu is empty, it will probably not show (depending on its settings).

---

