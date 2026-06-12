---
title: "Problem with chmod command and Themes"
date: 2011-03-22
forum: Desktop Environments
---

### Post by Riddermark on 2011-03-22
I am trying to add a themes package to the themes folder.  I wanted to change the permissions for the folder so that all users could access the themes, even though I am the only user at the moment.  I downloaded and extracted the files and issued the following commands.  NEW THEME in caps is the new themes folder.

```
sudo cp -r $HOME/Desktop/NEW THEME /usr/share/themes
```Moved file to themes folder

```
sudo chmod 755 /usr/share/themes/NEW THEME /NEW THEME .jpg
```Should allow access to all users.

After this I can see the file in the themes folder but it is not accessible, access denied.  It requires root access.  I thought that   chmod 755 would allow all users access but it looks like it did just the opposite.  Can anyone tell me what I am doing wrong?

Thanks 

K

---

### Post by ankspo71 on 2011-03-22
Hi,
In a nutshell, all you really needed to do is copy the NEW THEME folder to /usr/share/themes. After that, the theme should already be selectable by all users. You might want to try creating a test user account to see if the theme was installed properly.

I'll try to explain a little bit about the permissions:
Anything that gets placed in the /usr/share/themes directory is automatically supposed to be owned by root and has the permissions of 755, but are still shared with other users. The last "5" in 755 is what allows this, because the third digit in 755 is the permissions for "other" users. In depth info on permissions can be found here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

BUT, since the files will be automatically owned by root, nobody has permissions to delete, rename, or modify those files without knowing the sudo password. This is the way it is supposed to be as a security feature.

Hope this helps.

---

