---
title: "file perimissions problem"
date: 2008-05-01
forum: Desktop Environments
---

### Post by jubej on 2008-05-01
Hello!

Im having a huge problem here, in my home folder and my other partitions i set the permissions to:

user: myusername read write execute
group: plugdev   read write execute
others           read

with the command : 
                        chown -vR myusername:plugdev /home/myusername
                        chmod -vR 775 /home/myusername
                        sudo chown -vR myusername:plugdev /media/backup
and for the partitions: chmod -vR 775 /media/backup
                        sudo chown -vR myusername:plugdev /media/media
                        chmod -vR 775 /media/media

and they stay that way, but when i download a file to any of this folders

the file get the permissions:

user: read write
group: read only
other read


I want that even my new files will have the permissions i set.

i dont know why that is, please help.

So to make this more clear: when i download a file or movie or mp3 or whatever from the internet, and save it in any of this folders, it get the permissions:

user:myusername   read write
group:myusername  read only
others: read only

I have to run chmod again everytime to set the new permissions.  HOW can I make that even the new files/folders will have the same permitions. im really frustrated please help.
thnx

---

### Post by Oldsoldier2003 on 2008-05-02
Do some reading on umask and that should pretty much solve your issue. Be aware that you should think really carefully about umask because it may produce some permissions effects you hadn't forseen.

[http://www.tech-faq.com/umask.shtml](http://www.tech-faq.com/umask.shtml) is a good start, and googling can fill in the blanks or answer any particular concerns that may arise.

---

