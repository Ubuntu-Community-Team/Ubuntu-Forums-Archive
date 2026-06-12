---
title: "Default user settings"
date: 2014-09-25
forum: Desktop Environments
---

### Post by Leonardvb on 2014-09-25
can somebody please explain to me how i copy the user settings (wallpapers, dock items and so on) to the default user settings , meaning that when i create a new user they get the same settings as set for the user that i used to customize te dektop and settings. 

I'm using ubuntu server 12.04 , with the xfce4 desktop installed. 
Docky , and a lot of apps 

(kinda like xubuntu)

tanks

---

### Post by ajgreeny on 2014-09-25
Copy the .config/xfce4 folder from the home of the first user and paste it into the home of the new user, then change ownership of the folder in that new user to his username with ```
sudo chown -R *newusername:newusername* /home/*newusername*/.config/xfce4/
```

You may also need to copy the image used for wallpaper if it is in the first user's home and not in the usual system folder.

Not sure about docky but look for a similar configuration folder somewhere in the first user's home and copy/paste that, and chown it as well.

---

### Post by Leonardvb on 2014-09-25
tanx a lot ! this is gonne help so gonne try that  , is this the same proces with unity ?

---

### Post by ajgreeny on 2014-09-26
> **Leonardvb said:**
> tanx a lot ! this is gonne help so gonne try that  , is this the same proces with unity ?

Yes, it should be the same general procedure whichever DE you use.

---

### Post by ThatBum on 2014-09-26
The contents of the /etc/skel/ directory will be copied to new users' home directories, if that helps.

---

### Post by Leonardvb on 2014-09-26
thanks people for the help , i used the method to set up a user account , create all the mods , and copy the home folder of this user including all hidden files and folders  to /etc/skel this works great , every new user gets all the settings now.

---

