---
title: "Group file security"
date: 2009-05-15
forum: General Help
---

### Post by Woodje on 2009-05-15
I'm having some problems about how best to manage a directory structure of data that is shared by multiple people.

As an example, there is a directory of  "/data/www", which has the permissions www:www ug+rw. It is used to host content for a number of websites. Two users, User1, and User2, along with the user www need to be able to access the data to read / update / delete to some extent.

The problem I have is that When User1 uploads new content (editing is ok), then te user:group permissions become user1:user1. If User2 attempts to edit one of these files they will obviously be denied.

The few ways I've seen to try to get this to work is:


[LIST]
[*] Sticky Group bit - Setting the user permission to 'nobody', and a stickup group bit to 'www', didn't seem to work for new files.
[/LIST]

[LIST]
[*] ACL's - was quite complicated (i.e. could not easily see permissions of files), and some applications did not seem to recognise that they had permissions to the file area if they were granted permissions through ACLs.
[/LIST]

[LIST]
[*] Primary Group - Setting User1, User2, and User3's primary group to 'www'.
[/LIST]
 
The last one seemed simplest / most compatible, but seemed a bit of a hack. Ideally it would be good to I guess only allow the webserver account write permissions on the directories it really needed it on (cache / tmp folder or whatever).

Any ideas?

---

### Post by albinootje on 2009-05-15
> **Woodje said:**
>  The problem I have is that When User1 uploads new content (editing is ok), then te user:group permissions become user1:user1. If User2 attempts to edit one of these files they will obviously be denied.


Those two users seem to be working on the same files and directories.
Do you have objections against giving them the same username + password ?
If you do, you can still give them a different username and password, and after that give them the same UID.
I've just tested this quickly, here's an example of the relevant part of /etc/passwd (using vipw) :

```

guest:x:1004:1004:,,,:/home/guest:/bin/bash
guest2:x:1004:1005:,,,:/home/guest2:/bin/bash

```
Same uids, different gid, both users can work on the same files/directories.

Of course this only makes sense if your users are only working on  
the website files, and have no interest in violating files/directories in each others home directory!

Here's another example about how this works fine so far :
```

# su - guest
$ pwd
/home/guest
$ logout
# su - guest2
$ pwd
/home/guest2

```

And do those files really need www-data or www as owner ?

---

### Post by jpvosloo on 2011-03-19
I'm having the same problem and it is not ok to give the users the same UID.
This is simple to do in NTFS but I don't really want to use NTFS inside my Ubuntu machine.  

I have been searching the web for 6 months in an attempt to find a solution but none have thus far worked so please if anyone know how...

---

