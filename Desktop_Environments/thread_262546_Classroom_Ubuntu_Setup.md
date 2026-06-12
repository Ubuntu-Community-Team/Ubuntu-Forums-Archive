---
title: "Classroom Ubuntu Setup"
date: 2006-09-21
forum: Desktop Environments
---

### Post by Prospero2006 on 2006-09-21
Hello All-

I'm a public school teacher in San Antonio, and I teach a journalism class with a media applications middle school magnet. I have a computer lab with about 30 computers and I'm starting to integrate Ubuntu into the classroom. (The network guys with my district have no idea!)  

Anyway, I'm running up a against a few snags and I could use some advice:

     -Group Permissions:
           -I want to customize groups so that I can add kids to groups 
            that have specific access rights on the machine. For example:
            Right now, only root can 
```

mount /dev/sda1 /mnt/sda1.

```
            How can I get a regular user account permission to mount
            the usb drive. (Right now, I'm giving the kids the root 
            password and showing them the command line method. This 
            is not good as a long term solution.) 

           -Usb drives aren't mounting with writable permissions. 
            
           -I want certain kids to be in an 'installer' group. 
            These kids basically get 'adept' privileges and 'apt-get'
            privileges. Right now, the sudo password prompt doesn't 
            work at all from regular user accounts. (Besides, I eventually
            want to lock down sudo, and assign permissions on a group
            by group basis. Just not exactly sure what the standard
            practice is for that. I've always just used the root account
            on my personal machines.) 

           -Is there a stand-in for Microsoft Publisher.


Cheers! Any advice is appreciated. 
(BTW: The kids love it!)


Pros

---

### Post by bbarrons on 2006-09-23
for a stand in for publisher try scribus. Not as pretty but gets the job done.
 As far as the groups go. what are you using in the lab for a server?  I spent alot of time with win 2000 server and was able to setup logins and pass out permissions from there. I have had no need to setup a linux server since those days ( no longer in it) but I am sure one box dedicated to users and authentication will be what you need. 
Bill

---

### Post by Prospero2006 on 2006-09-23
My district uses novel. 
I have all of the machines configured correctly so that the students
are able to access all of their novel resources, which is the first argument I made when my boss stopped in on Friday to see what was up with this 'new' operating system I installed. (The subsequent arguments I made were equally convincing, and he left impressed.) 

The big question is USB access. Root automounts the usb drives flawlessly, but regular users can't. 

Try this: create a user account on your ubuntu machine. Plug in a usb drive.
It appears that root access, by default, is required for that kind of access.

Thanks for the scribus tip.

Pros

---

### Post by bbarrons on 2006-09-24
I am not familiar with novel at all but I am sure it offers the same features. 
 I just created an account and logged into it, put in a usb drive and opened it. I did not try to paste to it though. I can view contents without a problem. Was it write capabilities that was a problem?
Sounds like you have a good handle on it as far as the classroom goes. more kids need to be exposed to alternatives. Makes them grow up ans ask "what else is out there".
 We have a private school at out parish that has a computer lab that is not administered very well. I have often thought that a few linux boxes in that lab would inspire some of the students to dig deeper and look for alternatives..... I admire what you are doing....
keep it up.
 Bill

---

### Post by sabelsen on 2006-09-24
In order to allow normal users to mount /dev/sda1 you need to look at and edit you /etc/fstab file. Somewhere inside that file you should have a line that lists your device /dev/sda1. For example, mine looks like this (somewhat simplified):

/dev/sda1       /media/usb      vfat    defaults    0    1

The first column is the device, second columns is the mount point, third is the filesystem and the fourth describes mount options. Don't care about the last two columns (dump & fsck). What I 'believe' will solve your problem is to modify the line to:

/dev/sda1       /media/usb      vfat    defaults,user    0    1

Hopefully, that will allow your students to automount their usb devices. If not, you can manually add a new group to your system through System->Administration->Users & Groups. Once inside click the Groups tab and create a new group, and then go ahead and add users to the group through the lists below. Write down or remember the Group ID number. Once this is done you need to edit your /etc/group file. This file lists the privileges per group and you need to edit it accordingly for your newly created group. I'm unfortunately not very familiar with grouping and which groups you need or not to set, but you can Google them if you need more information. I believe creating a new group gives that group privileges in a default set-up of services. In any case, after editing the group file (or not) edit /etc/fstab. Edit the line to:


/dev/sda1       /media/usb      vfat    defaults,gid=GROUPID    0    1

Now, replace GROUPID with the number shown when you created the group through the GUI.

Hope this helps.

---

