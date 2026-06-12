---
title: "Lightdm/AccountService config"
date: 2015-11-18
forum: Desktop Environments
---

### Post by panda_adnap on 2015-11-18
Hi

I am installing a media center running on Ubuntu 15.10 and I have some difficulties configuring the login page.

I have two users: kodiuser and user
I have two desktop environment: kodi and unity.

My goal is to autologin kodiuser in kodi after 10 seconds if no user action is done, independently of the previous session.

But I have two problems:
- timer does not stop if I start typing
- user kodiuser logs in unity if previous session was unity (event if there is a "kodi (default)" entry in the menu).

I tried to edit  /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf, /var/lib/AccountsService/users/kodiuser, /etc/lightdm/lightdm.conf but could not find the correct way to do it.

Am I missing something ?

Thanks

---

### Post by oldos2er on 2015-11-19
First, please make a backup copy of any system files before you modify them, if you haven't already done so. Something like ```
sudo cp  /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf  /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf.backup
``` 

You need admin privileges to edit system files, so use ```
sudo nano /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
``` or ```
gksu gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
``` depending on your editor preference.

---

### Post by deadflowr on 2015-11-19
You should avoid editing  the /usr/share/lightdm directories, and instead only create files for lightdm in the /etc/lightdm folder.

Preferably you'd create a folder called lightdm.conf.d in the /etc/lightdm folder.
```
sudo mkdir /etc/lightdm/lightdm.conf.d
```
then make your customized file: usually something like 10-my-config.conf

The reason to do it this way is because when you edit the /usr/share/lightdm files, any updates to lightdm will overwrite your changes without notifying you.
Most updates will avoid the /etc directories settings, and any updates that might have new files for the /etc directory will always ask if you want to keep your old files or install the new ones.
That way you will at least have a chance to avoid loss.

Aside from that, post the output of your config setup, so we can see what it looks like.

---

