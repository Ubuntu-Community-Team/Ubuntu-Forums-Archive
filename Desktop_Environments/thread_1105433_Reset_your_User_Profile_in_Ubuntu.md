---
title: "Reset your User Profile in Ubuntu"
date: 2009-03-24
forum: Desktop Environments
---

### Post by AntiBodies on 2009-03-24
Hi all this is my first post I think but I thought I would share my trials and eventual success in reseting my profile in Ubuntu 9.04 (but this should work for all variants and editions)

Ok so Ubuntu keeps all user settings and data in each users home folder (/home/username). Most of the settings files for all applications are hidden files and folders (dot files as they start with a . eg .bash). This makes up any user's "user profile". There is the equivalent in the windows world as well but anyway...

I simply wanted to reset my user profile to default as I had upgraded from 8.10 and wanted a clean slate with settings for 9.04 (I would copy most data\documents over etc)

The easiest way would be to just create another user and use that for testing but I wanted to keep the same username. So you would think it would be easy but there are more steps than you think..

target username is **fred**

**1. **create another administrator user (need sudo access etc) under Administration --> Users and Groups (pretty simple).. you could just use sudo\root from a console but I thought this might be the safest just in case I locked myself out
**2. **logon as that user and go to the terminal
**3. **first backup old profile just in case..
```
sudo mv /home/fred /home/fred.old
```
**4. **create new home folder
```
sudo mkdir /home/fred
```
**5. **copy the skeleton (default) profile folder contents into the new folder.. this gives you tab completion for bash and some other default settings etc
```
sudo cp -r /etc/skel/* /home/fred
``` and to copy the hidden dot files\folders
```
sudo cp -r /etc/skel/.??* /home/fred
```
funny about this originally I did "sudo cp -r **/etc/skel/.*** /home/fred" as it made sense to me but laughed when I saw all of /etc in my home folder.. crazy

**6. **you don't need to do this but to move the old profile folder back into the new one for easier browsing etc do the following:
```
sudo mv /home/fred.old /home/fred/
```
**7. **last we need to set the ownership and the group membership for the new folder back to fred so (note the capital R):
```
sudo chown -R fred /home/fred
``` and
```
sudo chgrp -R fred /home/fred
```
**8. **that should do it.. now logoff and on to your old user and everything should be back to defaults and you should be able to browse the fred.old folder in your home (probably delete it after you have moved everything over)

Hope this helps someone out

If anyone can give a more elegant solution or less steps that would be cool

---

