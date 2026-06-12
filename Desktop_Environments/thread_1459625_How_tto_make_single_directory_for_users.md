---
title: "How tto make single directory for users"
date: 2010-04-21
forum: Desktop Environments
---

### Post by mealstrom on 2010-04-21
Hi, 

How can i manage just one directory of /home/*/Downloads (Music/Video/Pictures) for 
all users with propper rights? 

Just create some directory /var/share/music and link it to every's /home/*/Music ?
Or create directory and make links there from /home/*/Music ?

Maybe some other solution? 

(single PC, just want all users to have same directory/access for video/music (files rwx|r--|r-- ))

---

### Post by Morbius1 on 2010-04-21
BINDFS may be the way to solve your requirement:

[http://ubuntuforums.org/showthread.php?p=8983087#post8983087](http://ubuntuforums.org/showthread.php?p=8983087#post8983087)

---

### Post by ajgreeny on 2010-04-21
Just make a directory which has read and write privileges to all members of the audio and video groups, and add all users you want to be able to access the audio and video files to those two groups.  You can then either make the directory in one user's home and link a directory in the home of all the others to that directory, or if you have a shared partition, put it in there.

---

### Post by sisco311 on 2010-04-21
> **ajgreeny said:**
> Just make a directory which has read and write privileges to all members of the audio and video groups, and add all users you want to be able to access the audio and video files to those two groups.  You can then either make the directory in one user's home and link a directory in the home of all the others to that directory, or if you have a shared partition, put it in there.

The problem with your suggestion is that new files will not inherit the permissions. Changing the umask & primary group of the users may work.

@OP

+1 for bindfs or use ACLs & symbolic links:
[uhelp]community/UbuntuLTSP/ACLSupport[/uhelp]

@Morbius1

That's the worst *howto* I have ever read. :)

On a more serious note, since this is a faq, I will try to write a proper tutorial when I have a little time.

@OP (again)

check out bindfs & ACLs. If you have more questions, please feel free to ask.

---

### Post by Morbius1 on 2010-04-22
> **sisco311 said:**
> 
@Morbius1

That's the worst *howto* I have ever read. :)

On a more serious note, since this is a faq, I will try to write a proper tutorial when I have a little time.

I'd be interested to see what a "proper" howto looks from you. I've been pointing people in this and other forums to your bindfs procedure. It's so simple that even I can follow it. :wink:

---

### Post by mealstrom on 2010-04-22
tnx, 
ACL is what i've been looking for.

---

### Post by sisco311 on 2010-04-25
> **Morbius1 said:**
> I'd be interested to see what a "proper" howto looks from you. I've been pointing people in this and other forums to your bindfs procedure. It's so simple that even I can follow it. :wink:

Something like this:
[thread]1460472[/thread]

---

