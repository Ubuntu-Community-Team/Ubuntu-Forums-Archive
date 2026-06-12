---
title: "sharing entire drive"
date: 2009-10-14
forum: Desktop Environments
---

### Post by kylegio on 2009-10-14
ok i have several drives (used for mass storage of media) on my ubuntu desktop, they are configured to auto-mount on startup because several applications which start on boot require them to be mounted. 

now when i want to share a folder on my computer (an actual folder not a mounted disk) i can simply right click on the folder select "properties" then select "share" and check the "share this folder" option, that works great. 

my question is for mounted drives that option does not exist. is there a way (i assume there is) to share these drives? am pretty sure the service for sharing is called samba, is there a well known/good tool for configuring samba/overviewing shares etc?

thanks for your help!
kyle

---

### Post by stinger30au on 2009-10-14
google to the rescue


[http://ubuntuforums.org/showthread.php?t=399832](http://ubuntuforums.org/showthread.php?t=399832)

---

### Post by sahabcse on 2009-10-14
Hi

Normally harddisk drive are mounted in /media/disk folder, For sharing that drive, run the below command 

#sudo nautilus


 browse the /media/disk folder, right click and select sharing option.

---

