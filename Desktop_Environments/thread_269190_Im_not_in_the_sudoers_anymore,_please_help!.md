---
title: "Im not in the sudoers anymore, please help!"
date: 2006-10-01
forum: Desktop Environments
---

### Post by Estrayk on 2006-10-01
I followed something i should'nt do, and now everytime i want to sudo it tells me: ntc is not in the sudoers file.  This incident will be reported.

what i did was : usermod -G ftpuser ntc

How can i redo this, please..

EDIT: "ntc" is my login name, ofcource, and now i cant do nothing, cant listen to music, cant sudo, and so on..

---

### Post by ZipoTe on 2006-10-01
an extract of the usermod man:

"usermod -G group1[,group2,...,[groupN]]]
              A list of supplementary groups which the user is also a member
              of. Each group is separated from the next by a comma, with no
              intervening whitespace. The groups are subject to the same
              restrictions as the group given with the -g option. If the user
              is currently a member of a group which is not listed, the user
              will be removed from the group. This behaviour can be changed
              via -a option, which appends user to the current supplementary
              group list."

I think that means that you have removed the user of all the groups you were in except the ftp. Maybe loggin in as root you can add your user to the groups.

---

### Post by slaging on 2006-10-02
Same thing happend to me over the weekend.
After installing proftpd and adding myself to 'ftpuser' group, I'm unable to use sudo / su commands.
After searching the web, it looks like one must remove there username from ftpuser group to restore sudo privilege. Yet we can not login as root.
Weeks ago I found a post about logging into root by adding something like 'init=/bin/bash' in grub, but I can't remember where I read that.:-? 
If you have any luck please post.

---

### Post by anaconda on 2006-10-02
You can always select "Recovery mode" from grub, and then it boots to text mode with root priviledges.

Then you can add yourself to sudoers group, or create a new user-account with sudo rights...

Just type:
addgroup username admin
to get you back to admin group. Ofcourse change the username to your username first..

---

### Post by tideline on 2006-10-02
Two things:

Make sure the user in question is still listed in the /etc/group file as part of the admin group.

Here is the line in question:
```
admin:x:112:*username*
```

The sudo command looks at the sudoers file to ensure that you are in a specific privledged group.  If your username is not there put it in there.  Hopefully you set the root password earlier.:confused: 

If you didn't set the root password you could probably reboot into single user mode and reset it there.

Mike

---

### Post by aysiu on 2006-10-02
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo) has instructions for getting you back in.

---

### Post by slaging on 2006-10-02
Never thought about recovery mode. I've been using a live cd to fix such problems.
I've booted into the root shell using Recovery Mode;
```
cat /etc/group | grep admin
```
no "admin: x:112:user" listed, so I ran:
```
addgroup username admin
```
Problem Solved.
Thanks Everyone!

---

