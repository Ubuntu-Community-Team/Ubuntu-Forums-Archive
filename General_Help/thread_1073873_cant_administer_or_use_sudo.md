---
title: "cant administer or use sudo"
date: 2009-02-18
forum: General Help
---

### Post by akrobert on 2009-02-18
[FONT=Arial][FONT=Arial][SIZE=2][COLOR=Black]today for some reason my account suddenly does not have the ability to do any of the admin functions (software sources, packet manager, startup manager, etc) and I cant sudo anything anymore. I also noticed that it no longer asks me for a password anymore when I try to hit any of the admin tools. 

when I try to sudo something it says 

sudo: /etc/sudoers is owned by gid 1003, should be 0

I pulled up etc/group and it says Im part of root, admin, sudo and all the other relivant groups. I havnt made any changes to my permissions or anything but today there was a sudo update that I installed from the update list. 

I have rebooted and gone in as root and added myself to the admin group and sudo group which it said I was already part of. I cant access the /etc/sudoers file to edit it or even do more than look at the readme it comes up as. What I did notice, dont know if it matters, is that the group root is 1003 and when I go in my account is checked..if I try to uncheck it and check it again and hit ok it comes up and says that changing this could make my system unstable. Ive looked through the forums and over the web and I have no idea what to do next..Im wondering if the fact that its not asking for a password anymore has something to do with it. 

any help would be appreciated

Robert[/COLOR][/SIZE][/FONT][/FONT]

---

### Post by akrobert on 2009-02-18
today for some reason my account suddenly does not have the ability to do any of the admin functions (software sources, packet manager, startup manager, etc) and I cant sudo anything anymore. I also noticed that it no longer asks me for a password anymore when I try to hit any of the admin tools.

when I try to sudo something it says

sudo: /etc/sudoers is owned by gid 1003, should be 0

I pulled up etc/group and it says Im part of root, admin, sudo and all the other relivant groups. I havnt made any changes to my permissions or anything but today there was a sudo update that I installed from the update list.

I have rebooted and gone in as root and added myself to the admin group and sudo group which it said I was already part of. I cant access the /etc/sudoers file to edit it or even do more than look at the readme it comes up as. What I did notice, dont know if it matters, is that the group root is 1003 and when I go in my account is checked..if I try to uncheck it and check it again and hit ok it comes up and says that changing this could make my system unstable. Ive looked through the forums and over the web and I have no idea what to do next..Im wondering if the fact that its not asking for a password anymore has something to do with it.

any help would be appreciated

Robert

---

### Post by geirha on 2009-02-18
The root user must have uid 0 and the root group must have gid 0, so change back the gid of the root group to 0.

---

### Post by akrobert on 2009-02-18
Root user user ID is 0

root group ID was 1003. Changed it to 0

Rebooted and it didnt make a difference

Robert

---

### Post by bodhi.zazen on 2009-02-18
looks as if you changed the ownership and / or permissions of some system files.

Most often this means reinstall as unless you know what you did or make a few small changes , manually resetting all your system permissions takes a long time and is fought with problems.

---

### Post by geirha on 2009-02-18
What does this say? ```
ls -l /etc/sudoers
```

I'm thinking that maybe the root group got a new gid, somehow, before the new sudo update, and that the installation of sudo checked the ownership of /etc/sudoers, noticed it was no longer owned by the root group, and changed it to the new gid ... just speculation though. I don't know how to check how a package configures itself.

---

### Post by akrobert on 2009-02-18
the only thing I did that I know of is I went to the update manager and there was a sudo update. I downloaded and installed it...any way to revert? 

Robert

---

### Post by akrobert on 2009-02-18
did like you said and got this

me@dell-desktop:~$ ls -l /etc/sudoers
-r--r----- 1 root rootaccess 546 2009-01-14 19:05 /etc/sudoers

Robert

---

### Post by geirha on 2009-02-18
rootaccess? Is that a group you've made yourself? Changing the group ownership of /etc/sudoers might at least get sudo working again, but it's hard to say if there is anything else that need changing without knowing exactly what has happened. 

Get to a root shell, either by rescue mode or liveCD, and run chgrp on it
```
chgrp 0 /etc/sudoers
```

You can search your entire filesystem to see if any other files have gotten rootaccess group ownership. If it's just that /etc/sudoers, I think you'll be fine.
```
find / -group rootaccess -ls | tee ~/filelist.txt
```
The above will take a while, depending on how many files you have. It will print all files that have rootaccess as group owner both to the terminal and to the file /tmp/filelist (in case there are many and you want to look through them)

---

### Post by akrobert on 2009-02-18
ok

I went to rescue mode...typed 

chgrp 0 /etc/sudoers

and it seemed to do nothing at which point I said well darn...well something like that at least...and then did the other one..quite a list including printer drivers and everything.

so I rebooted and lo and behold...its fixed..I can do all the admin tasks again...I can use sudo again...its even asking for my password again at the appropriate spots..thanks for all the help..

Now do you think that sudo update this morning could have caused this..if so why and any idea how to make sure it doesnt happen again? also would it be a good idea to create another admin user account so that if this happens again I can use it to go in and fix the primary account? kinda new to ubuntu in case that wasnt obvious..Ive been using it for about 2.5 months now..and its actually been fun.

thanks for your help and advice.

Robert

---

### Post by geirha on 2009-02-18
chgrp, chmod and chown works like that. If there's no output, it means the change went by without problems. If there's output, something went wrong.

It wouldn't make any difference if you created another admin user btw. If sudo smells something fishy, it will simply refuse to cooperate; your only option will ever be rescue mode or liveCD. 

Where did this rootaccess group come from? It's not a good sign that many files are owned by that group.

---

### Post by bodhi.zazen on 2009-02-18
> **geirha said:**
> Where did this rootaccess group come from? It's not a good sign that many files are owned by that group.

+1 on that .

If you did not make the group you are in trouble :)

---

### Post by akrobert on 2009-02-18
when it said I couldnt run sudo cause of the 1003 I tried to create a user and group to fill that slot figuring ok Ill just create like a main root user account and work around the sudo problem...so created the group..named it 1003 and then created a user..which didnt work...so right before I did what you suggested I went in and blasted that group back out..then did what you said and everything works like a charm.

thanks for all your help

Robert

---

### Post by MoebusNet on 2009-02-20
For those of us who are a little hesitant to apply the latest sudo update, what would be the correct typical response to

CODE ls -l /etc/sudoers END CODE

for a default Ubuntu Hardy install?

---

### Post by jespdj on 2009-02-20
```
-r--r----- 1 root root 470 2008-04-25 22:37 /etc/sudoers
```
About code tags: there's a # button above the editor where you edit your posts, use that for code tags.

---

### Post by MoebusNet on 2009-02-20
Thank you!

---

