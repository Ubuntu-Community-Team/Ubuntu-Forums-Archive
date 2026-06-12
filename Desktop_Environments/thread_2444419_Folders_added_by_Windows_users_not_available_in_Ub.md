---
title: "Folders added by Windows users not available in Ubuntu 20.04"
date: 2020-05-29
forum: Desktop Environments
---

### Post by gourmetsaint on 2020-05-29
Using Ubuntu 20.04, I have shared some folders under /home/user directory for file services for Windows users on the network. Users add folders and files to these areas, however, under Ubuntu, the folders appear with a red padlock and unavailable in the Ubuntu file manager. Looking at the folders, they appear as no owner. How do I set it up that the Ubuntu user (running Plex for example) can access the directories in these shares without manually having to take ownership and chmod 777 each time a folder/file is added?

Thanks in Advance,

Mark

---

### Post by Morbius1 on 2020-05-30
If you look at the owner of the saved files from your network clients it is not "no owner" but "nobody". That is an actual local user name and the samba default user when accessing a guest accessible share. Many ways to correct for this but the easiest is to make "nobody" appear as you.

You didn't specify how you created the share - through Nautilus or in smb.conf - so when it doubt apply it to all shares:

Edit /etc/samba/smb.conf and right under the **workgroup = WORKGROUP** line add this one:
```
force user = your-ubuntu-user-name
```
Then restart smbd:
```
sudo service smbd restart
```
All new files added to the share will save as owner = you.

---

### Post by gourmetsaint on 2020-05-30
Thanks for that but I used Nautilus. When I check smb.conf it's empty apart from headers. How do I make the change?

---

### Post by gourmetsaint on 2020-05-30
Oops. Belay that. Needed to scroll down further. Doh. Thanks heaps

---

