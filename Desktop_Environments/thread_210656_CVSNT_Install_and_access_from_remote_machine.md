---
title: "CVSNT Install and access from remote machine"
date: 2006-07-07
forum: Desktop Environments
---

### Post by canardo on 2006-07-07
Hi,

I am trying to setup cvnt on my Dapper Drake box, have got it all installed and a repository setup in /home/cvs/

However I would like to be able to access the cvs server from a Windows machine(yes I  know, but its for Java Micro development for which the manufacturers emulators only work under Windows) using tortoise cvs.

My question is how do I setup and run pserver I cant seem to find any documentation on it! must just be being daft but please help

the only command I can find is 

cvs -d /home/cvs passwd -a user

however I get the following error
cvs[passwd aborted]: only administrators can add or change another's password

How do I login as the administartor though haha!

Much appreciated

---

### Post by canardo on 2006-07-08
I have added the following to my inetd.conf file    cvspserver      stream  tcp     nowait  root     /usr/local/bin/cvsnt cvsnt authserver

still no joy though :(

---

### Post by nickleus on 2008-05-27
> **canardo said:**
> 
How do I login as the administartor though haha!

you dont.
create a file called admin in your CVSROOT folder
then add to that file your system user name that you're using to administrate cvsnt with.
then try the passwd command again (maybe you have to restart cvslockd first, i can't remember).
i'm still struggling with permissions errors if anybody wants to help. i can't connect to the cvsnt repository from a remote machine.

---

