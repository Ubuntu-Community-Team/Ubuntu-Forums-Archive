---
title: "moving dir's"
date: 2009-03-27
forum: General Help
---

### Post by jshx87 on 2009-03-27
so im trying to move the folder where wine installs programs to.  im running a little too low of space in my home folder.  what would be the best way to move a hidden dir to another drive and create a symbolic link? 

thanks!

---

### Post by albandy on 2009-03-27
link it, 
first copy all the contents to the new partition, for example:

copy:
cp -R /home/myuser/.wine /mnt/mynewdisk/myfolder/.wine
delete:
rm -rf /home/myuser/.wine
link:
ln -s /mnt/mynewdisk/myfolder/.wine /home/myuser/.wine

---

