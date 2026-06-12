---
title: "unity problems maybe?"
date: 2013-05-30
forum: Desktop Environments
---

### Post by mreyna16 on 2013-05-30
so basically whats going on is i turn on my computer, could be restart also, and everything is fine until i open an app and then when i want to minimize it to see the desktop it freezes. im able to unfreeze it most times by pressing the "super" button. then i go back to the same app or another app (doesnt matter) and when i try and minimize it to go to the desktop it freezes again but this time its a 50/50 chance that it stays freezed and have to power cycle it or im able to unfreeze it.

this started to happen when i installed gnome 3.8 and uninstalled it because i didnt like it. i deleted most other stuff it leaves behind when you uninstall it and reinstalled unity again but i think it might be that it didnt install right, OR maybe it can be kernel related but i doubt it because i was running the latest 3.8 and now im running 3.9. can anybody help me fix this problem?

---

### Post by Frogs Hair on 2013-05-30
If it happened after installing Gnome 3.8 that would be a starting point . When I tried 3.8 both times it left a lot of 3.8 packages on my system even though I used the PPA purge. The last time I reinstalled because I was spending too much time getting rid of the 3.8 leftovers which affected the way the Unity desktop was working. Gnome 3.8 is still for testing at the moment and there is risk when installing it. No more Gnome PPAs for me .:o

---

### Post by mreyna16 on 2013-05-31
so whats the process of getting rid of them? i did the ppa purge but still did notice some gnome stuff... so how do i completely remove it and reinstall unity the way its supposed to?

---

### Post by Frogs Hair on 2013-05-31
There will be gnome 3.6 packages  on your system because that is what 13.04 uses. It is the 3.7 + packages that shouldn't be there . I had to force the proper versions with the synaptic package manager the first time which was a major pain . To check versions I had select the package in syntactic, enter properties, go to the version tab, and force the 3.6 version to be installed using the force version option in synaptic.
 
Using the autoremove command had no effect on the 3.7+ packages that were installed. On the second time around I backed up and re-installed  because it was too much work to locate and get the correct versions installed. Reinstalling was also faster and I was sure I didn't miss anything.

---

### Post by mc4man on 2013-05-31
Make sure nautilus is handling the Desktop or minimizing apps will cause a lock up, ect.
```
gsettings  set org.gnome.desktop.background show-desktop-icons true
```

---

### Post by mreyna16 on 2013-05-31
> **mc4man said:**
> Make sure nautilus is handling the Desktop or minimizing apps will cause a lock up, ect.
```
gsettings  set org.gnome.desktop.background show-desktop-icons true
```

nothing happened, if it continues ill just reinstall ubuntu again

---

### Post by mreyna16 on 2013-05-31
i dont know what that was but that seemed to work for now

---

