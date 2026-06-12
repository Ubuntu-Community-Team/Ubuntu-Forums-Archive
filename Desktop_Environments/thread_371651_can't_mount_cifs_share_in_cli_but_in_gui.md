---
title: "can't mount cifs share in cli but in gui"
date: 2007-02-27
forum: Desktop Environments
---

### Post by mats.lundqvist on 2007-02-27
At my job we use win2k3 and Active Directory, and I usually keep my "My Documents" folder on my personal network share. And quite often I need to access documents in there. And that's no problem, just browse to the samba shares and find the server, authenticate and open the folder.

The thing is... I want to have that folder mounted when I boot i.e putting it in fstab.

But to do that, I need to know the command line string to use for mounting it.

Running

$ sudo mount.cifs -t cifs //10.1.1.100/users$/mats.lundqvist/Mina\ dokument/ /media/test --verbose -o dom=domain,user=user,pass=password,iocharset=UTF8,file_mode=0777,dir_mode=0777

Gives me:


Mounting the DFS root for domain not implemented yet
No ip address specified and hostname not found

Googled that and found a few references to fedora users that were missing a few modules. But I doubt that it's causing my problems, since my gui mounting of the shares are working perfectly.

I've read this one:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

And googled for a few others, and tried alot of different angles. But I can't seem to get it to work.

I'm running feisty herd 4 btw....

Anyone care to give me any hints?

---

### Post by mats.lundqvist on 2007-03-02
Anybody?

I can even play kickin' rock solo for the one with an answer!: \m/

:guitar: 

Or would you like some popcorn perhaps?:

:popcorn:

---

### Post by mats.lundqvist on 2007-04-02
*BUMP*

Sorry, but had to, I really need help with this. 

Thanks.

---

