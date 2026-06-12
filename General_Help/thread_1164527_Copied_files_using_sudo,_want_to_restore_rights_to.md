---
title: "Copied files using sudo, want to restore rights to all users"
date: 2009-05-19
forum: General Help
---

### Post by urban_ryoga on 2009-05-19
Hi,

I accidentally copied parts of my home directory from this computer using sudo. I wanted to do another backup, but have realized this error. How would I go about setting the rights back of folders and files for every user to have access to it?

---

### Post by anjilslaire on 2009-05-19
You could try
```

sudo chmod -R username:group /path/to/folder

```

Or
```

gksudo nautilus
```
which will open a root-enabled nautilus browser that you can then use the GUI with to set permissions as needed.

Be VERY careful with the file browser as root.

---

### Post by taurus on 2009-05-19
You can use chmod (change permissions) and chown (change owner) to reset those files and directories.  Assuming the parent directory that you want to reset, you would so something like

```
sudo chmod -R 755 directory_name
sudo chown -R username:username directory_name
```
The directory_name and everything under it would be set to 755 with username as the owner/group.

---

