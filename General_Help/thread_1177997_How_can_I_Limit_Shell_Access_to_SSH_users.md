---
title: "How can I Limit Shell Access to SSH users"
date: 2009-06-04
forum: General Help
---

### Post by AlexsAntidote on 2009-06-04
I have a small file server I have setup for a web development project for a class and need to allow SSH access to my teammates.

I want to limit their SSH access so that they may only access and make changes to their respective share directories. Something like this:

/var/www/projectX/username

I was able to limit the FTP access, but have no clue how to limit the SSH access. Most of what I've found in searching have more to do with preventing one or the other (ftp or ssh) altogether, but I want to allow both FTP and SSH but just restricted to a specific directory.

Any help would be appreciated!

---

### Post by akakingess on 2009-06-04
> **AlexsAntidote said:**
> I have a small file server I have setup for a web development project for a class and need to allow SSH access to my teammates.

I want to limit their SSH access so that they may only access and make changes to their respective share directories. Something like this:

/var/www/projectX/username

I was able to limit the FTP access, but have no clue how to limit the SSH access. Most of what I've found in searching have more to do with preventing one or the other (ftp or ssh) altogether, but I want to allow both FTP and SSH but just restricted to a specific directory.

Any help would be appreciated!
This may be a stupid question, but would it not work to just right-click on said directory, go to permissions and set it up that way, you could do it per user, group, or owner.  That's the way i would try it, but then again i am a noobie so just learning here.

akakingess

As an afterthought it just occured to me that I was assuming that you had your classmates setup with a user account on your system. If not, then obviously that wouldn't work at all, so sorry to waste your time.

---

### Post by AlexsAntidote on 2009-06-04
> **akakingess said:**
> This may be a stupid question, but would it not work to just right-click on said directory, go to permissions and set it up that way, you could do it per user, group, or owner.  That's the way i would try it, but then again i am a noobie so just learning here.

akakingess

As an afterthought it just occured to me that I was assuming that you had your classmates setup with a user account on your system. If not, then obviously that wouldn't work at all, so sorry to waste your time.

I suppose I could chown, chgrp, and chmod all the files on the system to try to get it the way I want, but I don't think that would be a very good idea.

I tested it out just to be sure I wasn't out of my mind. I created a user and unchecked all privileges in the users and groups (under system->administration) and logged in via ssh. I can still see just about everything on the system. I haven't tried executing anything yet, but I would really like to set it up so that when they SSH in they can only see and access a specified directory.

Perhaps that is simply not possible?

---

### Post by listener on 2009-06-04
I have not done this, so don't know that much about it.  But you 
may want to do a bit of research on 'chroot jail' etc.  It 
does pretty much what you want:  it makes a (sub) directory
the root directory for the remote user.

---

### Post by akakingess on 2009-06-04
Also, is there not a way to limit what a user can see based on what port they are coming in on? Couldn't you just say user A logs in through 192.168.1.23:54321 and then set limits on that port?  Again this may be over my head, just trying to help brainstorm is all.

akakingess

---

### Post by AlexsAntidote on 2009-06-04
> **listener said:**
> I have not done this, so don't know that much about it.  But you 
may want to do a bit of research on 'chroot jail' etc.  It 
does pretty much what you want:  it makes a (sub) directory
the root directory for the remote user.

Hmmm... My understanding of chroot is that it works on processes (and their subprocesses) to limit access to specific directories. But I have no knowledge of chrooting users specifically. If this is possible, then that very well could solve my problem.

Can anyone comment on this?

---

### Post by AlexsAntidote on 2009-06-04
> **akakingess said:**
> Also, is there not a way to limit what a user can see based on what port they are coming in on? Couldn't you just say user A logs in through 192.168.1.23:54321 and then set limits on that port?  Again this may be over my head, just trying to help brainstorm is all.

akakingess

I don't know very much about ports, to be perfectly honest, so you may very well know more than me in that area. I suppose it may be possible to do as you say, but I don't know.

I believe SSH defaults to port 22. I'm not sure if anything else uses that port, or if there is another open port I could switch to and do some type of sandboxing for that port... but as I said, I don't really know much about ports. I'd be willing to give it a try if you have a suggestion of how to go about it...

---

### Post by akakingess on 2009-06-04
> **AlexsAntidote said:**
> I don't know very much about ports, to be perfectly honest, so you may very well know more than me in that area. I suppose it may be possible to do as you say, but I don't know.

I believe SSH defaults to port 22. I'm not sure if anything else uses that port, or if there is another open port I could switch to and do some type of sandboxing for that port... but as I said, I don't really know much about ports. I'd be willing to give it a try if you have a suggestion of how to go about it...
Yes, SSH will default to port 22 and Telnet to 23, etc. but that doesn't keep you from turning creating your own port 54321 (make it as large as you wish within reason) and set it as an SSH port, then let the users access via SSH through only that port and see if you can limit that ports visibility, again, i haven't gone that far with it, but i am sure someone on this forum has an answer for ya. hang in there.

akakingess

---

### Post by AlexsAntidote on 2009-06-04
I came across a few things when searching for chroot users and chroot shell..

I'm way too tired to try anything tonight, but I though I'd post them here for others who may be reading this thread who may be looking for a similar solution or perhaps to comment on if they have done something similar...

[http://ubuntuforums.org/showthread.php?t=248724](http://ubuntuforums.org/showthread.php?t=248724)
[http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/](http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/)
[http://www.cyberciti.biz/tips/howto-linux-unix-rssh-chroot-jail-setup.html](http://www.cyberciti.biz/tips/howto-linux-unix-rssh-chroot-jail-setup.html)

---

### Post by akakingess on 2009-06-05
> **AlexsAntidote said:**
> I came across a few things when searching for chroot users and chroot shell..

I'm way too tired to try anything tonight, but I though I'd post them here for others who may be reading this thread who may be looking for a similar solution or perhaps to comment on if they have done something similar...

[http://ubuntuforums.org/showthread.php?t=248724](http://ubuntuforums.org/showthread.php?t=248724)
[http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/](http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/)
[http://www.cyberciti.biz/tips/howto-linux-unix-rssh-chroot-jail-setup.html](http://www.cyberciti.biz/tips/howto-linux-unix-rssh-chroot-jail-setup.html)
Did you end up using the 'jailkit' option, or have you had any luck, i only ask because I am going to need to do something very similar this summer.

akakingess

---

