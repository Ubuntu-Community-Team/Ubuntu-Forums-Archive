---
title: "File permission problem...need some hep"
date: 2010-10-09
forum: Desktop Environments
---

### Post by abedepaul81 on 2010-10-09
I am running ubuntu 10.04 

I installed XAMPP localhost server (in....../opt dircrectory)

I installed Joomla in the localhost dir(/opt/lampp/htdocs/ directory)

now when I install any plugins or templates or modules (files)(in the /opt/lampp/htdocs/ dir)....they are automatically made read only directories and documents....all of them!

I can change the permissions by chmod but... thats not my bigger issue....which is when I install anything in the localhost directory...it automatically is read only

how would I get around this
Thank you in advance!

---

### Post by clrg on 2010-10-09
I guess that's because /opt/lampp/htdocs isn't owned by your user, but by lampp:lampp or apache:apache or whatever. This is the way it ought to be. If you want write permissions for you user, chmod the folders recursively for group write access (sudo chmod -R g+w /path/to/directory), then add your user to the group the directory belongs. If it belongs to apache, then do a "sudo usermod -aG apache YOURUSERNAME".

---

### Post by abedepaul81 on 2010-10-09
> **clrg said:**
> 
(sudo chmod -R g+w /path/to/directory), .

I was doing .......sudo chmod a+w /path/to/direcotry

was that bad to change permissions that way or does it matter?

---

### Post by clrg on 2010-10-10
With "a+w" you gave everyone write access.

Without the "-R" option, the change of permissions is only applied to the directory specified, not the files and folders it contains. Do a "sudo chmod -R g+w /path/to/dir" if you want to give the group write permission on every file and directory recursively.

---

### Post by abedepaul81 on 2010-10-10
> **clrg said:**
>  "sudo chmod -R g+w /path/to/dir" \

I did this but I still see the files and documents locked on the file manager as well as when i ls -l it

also I am stuck on the issue (because I didnt understand what you were trying to show me with the usermod command)....that when I install templates (or anyhting) on my website through my content manager (joomla) (which is located in the /opt/lampp/htdocs directory) they are automaticly locked to read only.

so I am guessing that they are being installed actually not by me (the current user at the current time) but by the owner of the directories of /opt/lampp/htdocs through where I installed the Joomla application

am I right or just dead crazy....if so...just let it out!
Thanks :)

---

### Post by clrg on 2010-10-11
You are perfectly right. That's what I wanted to explain to you in the first place.

The files and folders you'd like to have write access to are owned by some other user, for example, apache.

In order for you to get write access, we first need to give the group of the files and folders write access. We accomplished that with "chmod -R g+w /bla/bla/".

Next, we need to add your user to that group, so you can benefit from the permissions we just set. So, if the group ownership of /opt/lamp/... is apache, do a

```
sudo usermod -aG apache yourusername
```

If the group owner is lamp, do a

```
sudo usermod -aG lamp yourusername
```

If you don't know the group, find out with 
```
ls -l /PATH/TO/FILES | awk '{print $4}'
```

---

### Post by abedepaul81 on 2010-10-12
> **clrg said:**
> 

If you don't know the group, find out with 
```
ls -l /PATH/TO/FILES | awk '{print $4}'
```

Thanks allot I really needed this to grasp the general idea of the whole system and how it works with permissions.

---

### Post by abedepaul81 on 2010-10-12
> **clrg said:**
> 
Without the "-R" option, the change of permissions is only applied to the directory specified, not the files and folders it contains. Do a "sudo chmod -R g+w /path/to/dir" if you want to give the group write permission on every file and directory recursively.

when I did this....non of my documents changed permissions.  Is this possible?  to change all of the documents permissions all at once?

---

