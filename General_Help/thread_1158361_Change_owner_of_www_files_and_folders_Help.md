---
title: "Change owner of www files and folders Help"
date: 2009-05-13
forum: General Help
---

### Post by shnippy on 2009-05-13
Hi,

I am sorry if this is a nivice question, but I dont want to get it wrong.

I have a server, that is running a website. 

Some of the files and folders in the www directory are owned by root (not intentionally), and my ftp user cannot upload or edit these files or directories, wich i need them to ba able to.

can someone plese help me learn how to change ownership all files and directories contained "within" the www directory, from root to my ftp user i will call "flipper" (so i dont make any mistakes on naming, but is not real user).

i can login to ftp with my "flipper" account, and have access to about 20% of the files and folders in the www directory, but i need access to 100% of them, with full permissions.

i also have root access to the machine, if needed.


Thank you in advance.

shnippy

P.S. I have access to webmin also, if that would be easier. Although I am not real familiar with it.

---

### Post by Cheesemill on 2009-05-13
I'm assuming your web root is located at /var/www
If this is the case then you just need to do a
```
sudo chown -R flipper:flipper /var/www
```
from a terminal.

Cheesemill

PS - See man chown for more details

---

### Post by Lampi on 2009-05-13
can't you open a ssh session with the server?

---

### Post by apmcd47 on 2009-05-13
As root:```
chown -R flipper /path/to/www
```
Not as root:```
sudo chown -R flipper /path/to/www
```

If you wish to change the group, add the group to the user with a dot: *flipper.webmin*

Andrew

---

### Post by shnippy on 2009-05-13
hi,

wow, thank you all for the fast response.

do i need to change the group also? group is owned by root, but "flipper" is a member of that group.

I am very impressed with you speed of your replies!

Thank you very much.
shnippy

---

### Post by shnippy on 2009-05-13
this is a silly question, but again, i sure cant afford to make any mistakes.

if i use:
sudo chown -R flipper:flipper /var/www www, and all programs in there, will still work properly (served over http)?


sorry, that is a funny question, but just making sure.

thank you,
shnippy

---

### Post by ktritty on 2009-05-13
I am trying to learn about security as well.  It seems that the premise of safely hosting a webpage includes safely jailing the web server daemon.  I use apache2, and the name of the daemon is www-data.

Would it make sense to change the owner of my website files to be www-data using a very similar command?

[FONT=Courier New]# chown -R www-data:www-data /var/www


[FONT=Arial]Or would this actually be a bad thing to do?  Or, would it have no security effect at all?[/FONT]

[FONT=Arial]Thanks
    - Ken
[/FONT][/FONT]

---

