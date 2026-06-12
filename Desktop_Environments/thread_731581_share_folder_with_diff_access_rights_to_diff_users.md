---
title: "share folder with diff access rights to diff users"
date: 2008-03-22
forum: Desktop Environments
---

### Post by thyscorpion on 2008-03-22
Hi i am using the latest stable release of ubuntu.

I am a novice user of ubuntu for sometime now. 

i have forgotten how to give different access rights to different users on the same folder. 
my situation is that my ubuntu machine is accessed by my parents me and my friends.
my parents have a folder that they would only want them to access
and similarly i also have a folder dump that only i should be able to access.
and then there are free for all folders that all of us including my friends can access
[All via shared folders][windows network]
except this ubuntu machine all others use windows XP. i have installed samba
i shared a few folders and gave a universal pass by (sudo smbpasswd -a "myusername")
now everyone can access every folder i have shared...

Please advise me how to set restrictions depending on the user that tries to access the shared folder.

Thanks a ton..

---

### Post by prefec2 on 2008-03-24
If I understand you correctly then this is a classic situation. 

You want to have:
- A volume with read write permissions for everyone
- Volume on a user basis, where only the designated user can access the volume

The first can be done in different ways, however I would propose the following definition in smb.conf

[everyone]
path = /data/everyone
browseable = yes
public = yes
writable = yes
guest ok = yes
force user = SOME-USER
force group = users

SOME-USER have to be replaced by a user name. You should create a new user for this purpose or if you want you could be as lazy as I am and use www-data.

The Directory /data/everyone on the server machine must then be owned by www-data
This can be done with chown www-data /data/everyone

The per user directories can be defined with:
[homes]
   comment = Home Directories
   browseable = no

Or you can do it in separate shares like this:
[mom]
  path = /data/mom
  valid users = mom
  browseable = yes

Other options may be needed also, depends on the usage.

Hope that helps
  Reiner

---

