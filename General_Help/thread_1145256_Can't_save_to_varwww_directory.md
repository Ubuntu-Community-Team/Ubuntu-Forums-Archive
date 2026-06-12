---
title: "Can't save to /var/www directory"
date: 2009-05-01
forum: General Help
---

### Post by litlfrog on 2009-05-01
In order to use my browser to view a locally stored php file, I apparently have to install Apache. That seemed to go okay; I have a /var/www directory with a simple index.html file that I can access fine. But I'm not able to save any files to that directory! I've tried sudo chown [my username] /var/www/* (chown means "change ownership," I'm guessing?) and not gotten an error message, but I still can't save there. I'm getting frustrated here--why can't I just save a damn file to a local directory on my computer?

---

### Post by wsonar on 2009-05-01
That directory is owned by root just do sudo

ls -al 

should show the owner of the directory


are you hosting a webpage or just trying to view a php file?

if your hosting a page you don't want to change the directory permission 

just use sudo cp to  copy the files if it's an entire directory use cp -r

if your hosting a site you may want your own  folder with your own site in var/www/mysite

you will need to edit the apache configuration file to point to the new directory

---

