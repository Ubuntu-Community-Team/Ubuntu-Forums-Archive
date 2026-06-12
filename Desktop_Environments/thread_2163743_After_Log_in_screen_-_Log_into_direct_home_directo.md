---
title: "After Log in screen - Log into direct home directory in GUI"
date: 2013-07-19
forum: Desktop Environments
---

### Post by pavi_elex on 2013-07-19
I am using ubuntu 12.10.
Is there any settings that if a user logs into his account using log in screen, he should be inside the home directory instead of on the Desktop?
Just like it happens on terminal.

In terminal , If a user logs into his account, he enters in his home directory.

can we do it for GUI too. After log in screen, can a home directory be appeared instead of Desktop?

please help.

Thanks.

---

### Post by dino99 on 2013-07-19
As i does not know if each of your users have their own home folder, or if they share a unique /home partition; thats hard to answer.

- case 1 : each user have its own home folder; meaning it only can reach its own data/settings (as that user have no rights set by the admin to log elsewhere)
- case 2 : a unique /home is shared by many users (quite scary); the admin needs to allow/refuse rights for each users (users & groups settings)

About the desktop, you can (admin) change the rights to refuse it for the users

---

### Post by grahammechanical on 2013-07-19
When you are at the desktop you are in your home folder. Open the file manager and click on Home and you will see the desktop listed there along with the other folders in home.

Also click on file system or computer (in 13.04) and you will see a home folder along with the system folders. Click on that home folder and you will see your user name and anyone else's user name as a folder. Click on your user name folder and it will open showing the folders in your home folder including Desktop.

The terminal only logs us into our home folder because it is being run from the desktop which is in the home folder.

Regards

---

### Post by steeldriver on 2013-07-19
If you mean "can you display the contents of the user's home directory on the desktop, instead of the contents of the user's Desktop directory?"  then the answer is yes - you can edit the ~/.config/user-dirs.dirs file and set

```
XDG_DESKTOP_DIR="$HOME"
```

instead of

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

---

