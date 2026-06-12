---
title: "Users &amp; Groups - System Settings"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Nikos_M on 2006-06-21
Well here is the whole story so that someone may understand what is wrong.

I wanted to make an free partition as my home directory (hda1).So these are the steps (more or less) I did 
as root :

cp -RP /home/ /media/hda1 (i know that this was the mistake!I forgot the p)
rm -fr home
mkdir username

After that the whole thing was really bad with the groups so I deleted the user and added him again which made things a little bit worse.#-o Also fixed the wrong owner of the folder /home/username
chown -R username /home/username

At first all the su and gksu links were broken as well as the sound.I fixed these by adding me to sound and fixing the sudo by adding the my group (users for the moment) in the sudoers and making me owner of the folder again.

adduser username sound 

Now the problem.
Under the kdemenu - system settings - user & groups i get right from the start:
The module Users & Groups could not be loaded
Diagnostics is :
Possible reasons:
*An error occured during your last KDE  upgrade leaving an orphaned control module
*you have old third party modules lying around


The other modules are ok.I can get in administration mode also.
Starting from console systemsettings i get 

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---------------------- (Fine until here)-----------------
and when i press users and groups i get :

adding Users & Groups /usr/share/applications/kde/userconfig.desktop


Pythonize constructor -- pid = 27001
Python interpreter initialized!



Pythonize constructor -- pid = 27001
ScimInputContextPlugin()
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_userconfig
  File "/usr/lib/python2.4/site-packages/userconfig.py", line 1687, in create_userconfig
    return UserConfigApp(parent, name)
  File "/usr/lib/python2.4/site-packages/userconfig.py", line 275, in __init__
    self.__updateGroupList()
  File "/usr/lib/python2.4/site-packages/userconfig.py", line 515, in __updateGroupList
    self.__selectGroup(self.selectedgroupid)
  File "/usr/lib/python2.4/site-packages/userconfig.py", line 521, in __selectGroup
    lvi = self.groupidsToListItems[groupid]
KeyError
error: *** runFunction failure
;


Did i forget to put me in a group or something?

---

### Post by Matthew Bartram on 2006-07-07
I don't know, but it looks as if you've copied /home, but haven't actually mounted your new directory as /home. You can do this from fstab, or from the KDE program for mounting disk partitions. But I don't know how to do either :(. Perhaps someone can advise (unless you know already).

---

