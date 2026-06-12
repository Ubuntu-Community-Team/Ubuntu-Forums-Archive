---
title: "Lamp server w/ upload script need help with permissions"
date: 2006-09-25
forum: Desktop Environments
---

### Post by marcus2004 on 2006-09-25
I am running a lamp server and I downloaded a php script to allow me to upload files to a folder on my computer. 
The folder is outside of var/www and in my home/username/ directory.
 
The file uploads fine but when it writes into the folder it gives it www-data as the owner. 
I have hellanzb monitoring the folder and it doesn't seem to grab the nzb that I am uploading unless it is owned by me. 
Is there a way to set permissions (which I have been messing with for 2 hours) so that when a php script copies a file to a folder it will be owned by a certain group?
I can post the script if someone is a php genius and can tell me where to put  code in to do this automatically. 
Thanks in advance for any help. 
Marc

---

### Post by lamego on 2006-09-25
> Is there a way to set permissions (which I have been messing with for 2 hours) so that when a php script copies a file to a folder it will be owned by a certain group?
Because apache is running with www-data all files managed by PHP (the apache module) will be owned by www-data, I don't believe you can change that.
What about adding www-data to a group common to hellanzb and setting the directory/file mask/owner for group access ?

---

### Post by marcus2004 on 2006-09-25
I am still pretty new to server stuff and permissions, but the folder is 777 that is being written to with chmod 777 -R 
I added my username to the group www-data and added www-data to my group. Which didn't seem to help. 
Whatever file I upload via this script gets copied to the folder with user and group being www-data with just read write access. 
I read something about umask which I didn't really understand. 
Also I can do the chmod 777 -R and that seems to fix the file that is in the folder, but I am not sure if there is something that can continuously do that.

---

