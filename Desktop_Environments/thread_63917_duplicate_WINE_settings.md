---
title: "duplicate WINE settings"
date: 2005-09-09
forum: Desktop Environments
---

### Post by X5-655 on 2005-09-09
is there a way to duplicate WINE settings I setup for one user, to another?

for example, we have a livingroom computer, it runs Linux...  it has 3 accounts, mine, my fathers, and a guest account..

I setup WINE on my account, but would also like to easily copy the settings to the other two accounts, without running Wine utilities again..

---

### Post by KingBahamut on 2005-09-09
is there a /home/<user>/.wine folder? 

I imagine you could just copy that from one to the other.

---

### Post by X5-655 on 2005-09-09
[QUOTE=KingBahamut]is there a /home/<user>/.wine folder? 

I imagine you could just copy that from one to the other.[/QUOTE]
yes, there is one...

i was just thinking, is it possible to link all the other users to my one folder?  so that way it don't take up alot of hard drive space?

also:  im using Wine Tools, and installation of IE 6 seems to not do anything...

---

### Post by KingBahamut on 2005-09-09
I dont think thats possible, no. 

Ive no experience with Wine and IE use in linux. Firefox all the way for me.

---

### Post by X5-655 on 2005-09-09
[QUOTE=KingBahamut]I dont think thats possible, no. 

Ive no experience with Wine and IE use in linux. Firefox all the way for me.[/QUOTE]
well, WINE Tools states I need to install IE 6 on it, otherwise the main system files won't work..

---

### Post by sbassett on 2005-09-09
You may be able to share this directory between all users. Create a group that all 3 of the users belong first. Then copy the .wine directory to some place everyone will be able to access, like /opt. 

```
sudo mv .wine /opt
``` 
This will be done from your home directory.

Then make sure that this belongs to the group you had created above.

```
sudo chgrp groupname /opt/.wine
``` 

After that, change the perms. May not be needed, but hey.

```
chmod 770 /opt/.wine
``` 

And finally each user should create a soft link to there home directory

```
ln -s /opt/.wine .
``` 
Each user will perform this from their home directory.

This should suffice I believe.  GroupID  may need to be set as well.

---

