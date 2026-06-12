---
title: "[SOLVED] Cant install themes"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by upthelum on 2007-07-26
I am trying to install themes, colour shemes, boot splash screens etc, but cant download the files to anywhere except my desktop as there seems to be an issue with file permissions. I cant copy/paste them either as the paste option is greyed out. When i download i am told i dont have permission to save in any directory, except Desktop. I cant browse and select the file as it seems the files have to be in a different directory. 
So far im getting there with the permissions issue but i cant seem to be able to install any themes, 
I dont have System > Preferences and dont know how to get it but was told i have to re-install the os on General Help but surely theres an easier way to install a few themes. Tried kdm theme manager and Control Center to no avail. Im not a noob but feel like an absolute beginner sometimes...

---

### Post by Immolatus on 2007-07-26
You could try reinstalling just the ubuntu desktop in a terminal, that would probably restore all the defaults.
Maybe do :

sudo apt-get install ubuntu_desktop  (<---I'm also thinking that there is an option to reinstall that can be added here, maybe look in the man pages under INSTALL)

then 

sudo apt-get update

---

### Post by Immolatus on 2007-07-26
Sorry for posting again. Or you could just install KDE and do all of this from there.

---

### Post by upthelum on 2007-07-26
Thanks ill reboot and see if there's any change.

---

### Post by upthelum on 2007-08-03
I got it, i didn't realise that you browse to and select the .tar .gz file which is working fine so another problem solved... 
Thanks to all.

---

