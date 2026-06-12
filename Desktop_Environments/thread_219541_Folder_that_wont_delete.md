---
title: "Folder that wont delete"
date: 2006-07-20
forum: Desktop Environments
---

### Post by trojanlinux on 2006-07-20
I was downloading some files from my ftp site, when one of the folders would not copy. When I right click on the folder and go to "move to trash" it says "error while moving, cannot move ... to the trash because you do not have permission to change it or its parent folder". The folder also appear to have a lock and an x icon. How do i get rid of this folder?

THanks!

---

### Post by rajasekhar.yeruva on 2006-07-20
Its readonly.. Thats y r not able to delete or move.. just type in the following command to change permissions of the files/dirs. 
sudo chmod 777 folder/file name.

---

