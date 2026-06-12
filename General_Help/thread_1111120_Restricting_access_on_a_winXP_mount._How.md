---
title: "Restricting access on a winXP mount. How?"
date: 2009-03-30
forum: General Help
---

### Post by PaganImmolator on 2009-03-30
First let me thank all that inhabit these forums and IRC chans to support this great OS. 

Now, this is what I am trying to accomplish:

I am trying to give access to my wife's and daughter's windows "My Documents" folders while under Ubuntu 8.10. For the sake of safety and convenience, I don't want to give access to the whole windows partition. Last thing I want is my 9yo accidentally deleting something on the XP partition that would cause it to crash. 

Well I know how to mount the **whole** partition through the GUI, manually or in fstab. But is there a way to mount just a given folder for **each** user? 

Ideally, this is what would happen:

User2 would login and see a link or icon on their desktop. Click on it and they would get have r/w access to user2's "My Documents" folder under windows. 


I should also mention that only I have admin rights. I couldn't find any specific post that addressed this issue directly but then again maybe I am not using the correct search terms.

---

### Post by chriskin on 2009-03-30
i have to say that you have a strange name for a family man
that aside (since it is none of my business:) ), i think that the following might help you

being the owner of the disk, all you have to do is to give read-only permission for the whole drive (for example - right click, properties, permissions) and read/write permission for the folder you want(same way while in the folder). 

i think that the terminal can be avoided, or at least i have to say that the previous way worked for me for the same work.

now , having the whole partition mounted will not let your wife/kid delete anything, so there is no risk :)

---

### Post by PaganImmolator on 2009-03-30
Thanks for the reply. I thought about doing what you said but wouldn't that give my daughter r/w privileges for her mothers folders too and vice versa?  

I don't necessary want to give every user read privileges to **every** folder on that drive. For the sake of argument, lets say there were some photos that we didn't want our daughter to see on that drive. Not that we would ever keep anything like that on our computer. I am sure you can appreciate the need to keep the same level security as was previously used by Windows. 

This is complicated because I want to keep the file structure intact on the Windows partition since my wife and daughter still use windows for some things. 

I guess what I am asking for is a unique mount profile for each user and the ability to mount just a folder in that profile instead of the entire drive. 

Oh and the screen name is holdover from my Xbox Gaming days.

---

### Post by chriskin on 2009-03-30
i get the idea and i must say it is a good one

while searching on google i got this [http://forums.whirlpool.net.au/forum-replies-archive.cfm/1013974.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1013974.html) which says that what you are asking is not possible :S, or at least noone there knew.

sorry for not being able to help

---

### Post by DigitalNoise on 2009-03-30
> **PaganImmolator said:**
> Thanks for the reply. I thought about doing what you said but wouldn't that give my daughter r/w privileges for her mothers folders too and vice versa?  

I don't necessary want to give every user read privileges to **every** folder on that drive. For the sake of argument, lets say there were some photos that we didn't want our daughter to see on that drive. Not that we would ever keep anything like that on our computer. I am sure you can appreciate the need to keep the same level security as was previously used by Windows. 

This is complicated because I want to keep the file structure intact on the Windows partition since my wife and daughter still use windows for some things. 

I guess what I am asking for is a unique mount profile for each user and the ability to mount just a folder in that profile instead of the entire drive. 

Oh and the screen name is holdover from my Xbox Gaming days.
Unfortunately I don't think this is possible strictly by mounting a disk, because of the way Windows handles user permissions.  From what I can tell, by default NTFS partitions and disks are mounted with "root" permissions - which I believe translates to "Administrator" permissions in Windows.

The only way I can see to make this work, is to put that disk in another machine, and setup Samba - which does allow for mapping of Linux Users to Windows Users.  I've not done this in a long time, so it's probably easier than it was.

---

### Post by PaganImmolator on 2009-03-30
Hmm, this is disappointing. I can't imagine that I am the only one who wants this. 

I understand the samba idea but I think it might just be easier at this point to mount the whole drive at startup and then chown the individual folders. I guess we will just have to chance that my 9yo won't delete files in my wifes folders. 

Up until this point, I have been the **only** Linux user in this household so its not been an issue. Now my family sees the light and wants to start using Linux more due to the increase in security and stability. 

I will keep searching. Maybe there is a more elegant solution.

---

### Post by PaganImmolator on 2009-03-30
[SIZE="5"]Hey I found this on another website. Will something like this work for my situation?[/SIZE]

> 
I do what you are asking about.

First I create a mount point located in another folder I call "restricted". The mount point in my ubuntu machine will be like this:

/media/restricted/vista

Then I set the permission for the restricted folder so that only root can access it.

In fstab I mount the ntfs partition with this line:

/dev/sda2 /media/restricted/vista ntfs-3g users,locale=en_US.UTF-8,uid=1000,gid=1000,umask=0002 0 0

Then I make a mount point in my home folder for the desktop and user folder in my windows account. The mount points will be like this:

/home/user/Vistadocs/Desktop
/home/user/Vistadocs/Documents

And finally i make two binds in fstab that will enable these specific parts of the mounted ntfs file system from /media/restricted/vista in my home folder. The two lines in fstab will be like this:

/media/restricted/vista/Users/user/Documents /home/user/Vistadocs/Documents none bind 0 0

/media/restricted/vista/Users/user/Desktop /home/user/Vistadocs/Desktop none bind 0 0

Thats it, now when i log in as the linux-user "user" i will have access to the windows-user "user" Desktop and Documents folder from my linux home folder, but I will not be able to reach any other files on the vista file system. 

---

### Post by chriskin on 2009-03-31
seems good but i have not seen it working.
if you make it work though, give us feedback please 

good luck

---

### Post by prophat on 2009-03-31
Can one of you patient types help me?

I don't have any problem restricting access...I am restricted from write access.  I am a Windows user with Ubuntu running from CD and I can see my HDD C: (aka HDA1) and I'm trying to rename one cotton-pickin file.  How can I do this?  Whenever I do try a rename, I am told the file can't be deleted.

I am a Linux-newbie.  Any help would be greatly appreciated.  Thanks.  

:? soon to be \\:D/ hopefully.

---

### Post by TyrantWave on 2009-03-31
This way requires the least terminal use, but is slightly risky. Make sure you know exactly which file you're editing, and don't change anything else.

Open a terminal, and type:

```
sudo nautilus
```

(I presume you're on Ubuntu)

Then in the file browser that opens you should be able to browse to the file and edit it.

Make sure to close that window as soon as you're done, as it has root privelages.

---

### Post by chriskin on 2009-04-01
and while on sudo nautilus, it might be a good idea to click on the folder you have permission problems with, and edit the permissions to read/write for your user. so that you can keep editing files even without sudo nautilus

---

