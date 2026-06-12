---
title: "strange error"
date: 2006-05-29
forum: Desktop Environments
---

### Post by raovq on 2006-05-29
for the past week or so, i have been battling samba to get file sharing between two unbuntu computers. i am not using nfs because both machines occasionally dual boot into xp. one box is working perfectly, the other...isn't.

now, i ended up using swat to configure it because it just plain wasn't making sense to me. i ended up with a smb.conf that looks like this.
```
# Samba config file created using SWAT
# from 0.0.0.0 (0.0.0.0)
# Date: 2006/05/29 01:17:31

# Global parameters
[global]
	server string = mum
	security = SHARE

[torrents]
	path = /home/guy/Torrents
	guest ok = Yes

[done]
	path = /home/guy/Torrents/downloaded
	read only = No
	guest ok = Yes

```

that works so far, when i go to network places, i can see the computer, i can see the two folders, but i can't open them. it gives me a generic error, saying something along the lines of that files can't be found, perhaps they have been deleted. i know the address of the directories is correct, so im a bit lost.

i dug into my samba log, and found this-
[2006/05/29 12:05:21, 0] smbd/service.c:make_connection_snum(615)
  '/home/guy/Torrents' does not exist or is not a directory, when connecting to [torrents]

the permissions are either 777 or 755, and it doesn't make a difference.
i'm a little confused by this error, when i know the folders are there are globally viewable.

any ideas?

---

### Post by mjziegle on 2006-05-29
Try setting up your shares like this 

[public]
   comment = Public Folder
   path = /home/public
   public = yes
   writable = yes
   create mask = 0777
   directory mask = 0777
   force user = nobody
   force group = nogroup

-mjziegle

[QUOTE=raovq]for the past week or so, i have been battling samba to get file sharing between two unbuntu computers. i am not using nfs because both machines occasionally dual boot into xp. one box is working perfectly, the other...isn't.

now, i ended up using swat to configure it because it just plain wasn't making sense to me. i ended up with a smb.conf that looks like this.
```
# Samba config file created using SWAT
# from 0.0.0.0 (0.0.0.0)
# Date: 2006/05/29 01:17:31

# Global parameters
[global]
	server string = mum
	security = SHARE

[torrents]
	path = /home/guy/Torrents
	guest ok = Yes

[done]
	path = /home/guy/Torrents/downloaded
	read only = No
	guest ok = Yes

```

that works so far, when i go to network places, i can see the computer, i can see the two folders, but i can't open them. it gives me a generic error, saying something along the lines of that files can't be found, perhaps they have been deleted. i know the address of the directories is correct, so im a bit lost.

i dug into my samba log, and found this-
[2006/05/29 12:05:21, 0] smbd/service.c:make_connection_snum(615)
  '/home/guy/Torrents' does not exist or is not a directory, when connecting to [torrents]

the permissions are either 777 or 755, and it doesn't make a difference.
i'm a little confused by this error, when i know the folders are there are globally viewable.

any ideas?[/QUOTE]

---

### Post by raovq on 2006-05-29
ive tried many configuration setups, and none seem to make a difference. this error keeps appearing, and i think it has something to do with something other than my configuration. what i have there does work, ive used it and tested it many times before, i can't think of a reason why it wouldn't now.

---

### Post by raovq on 2006-05-30
right i solved it!!!!!!!!!!!!!!!!

i found out that you can't just have the directory you want to share with nice permissions, the whole path has to be permissioned at least to read. kinda makes sense now i think about it, but this has been driving me nuts.

ubuntu is now configured on two computers, both running perfectly!

after a trial by fire like that, i feel i can do anything with this now.

thanks community! thanks ubuntu!

i shall now devote my life to helping others on these forums, and gain some karma.

---

### Post by sinaen on 2006-05-30
[QUOTE=raovq]right i solved it!!!!!!!!!!!!!!!!

i found out that you can't just have the directory you want to share with nice permissions, the whole path has to be permissioned at least to read. kinda makes sense now i think about it, but this has been driving me nuts.

ubuntu is now configured on two computers, both running perfectly!

after a trial by fire like that, i feel i can do anything with this now.

thanks community! thanks ubuntu!

i shall now devote my life to helping others on these forums, and gain some karma.[/QUOTE]

I have a problem that i cannot get into a directory under the one i share. it seems like it needs passwd or such. and it is somehow rambling about it dont exist. but i know it is else it wouldnt show up in the share list

can you access your shares from windows machines?

---

### Post by raovq on 2006-05-30
i havent tested it yet, i was just thrilled to get it working at all. i'll give it a crack when i get home from uni today, and post the resutls.

---

