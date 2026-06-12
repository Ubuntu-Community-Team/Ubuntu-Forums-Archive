---
title: "system does not let me in"
date: 2009-06-17
forum: General Help
---

### Post by ybardagi on 2009-06-17
Hi everybody:
I have a big problem as I can't loggon to ubuntu. System verifies username and passwd but it kicks me out. I just can access in recovery mode, but i don't know what I must check.

Partitions (boot and home) they still have space.

---

### Post by jonobr on 2009-06-17
Hang on, just re read your post and removed my initial comments as they were of now use.

See if you can see anything in dmesg which may give you an idea of whats happening
or maybe cat /var/log/syslog

---

### Post by ybardagi on 2009-06-17
It seems nothing weird to me
just an unknown pam_option "use_first_pass". But i removed this value from /etc/pam.d/common-auth  and the message is gone, but I still cant logon

---

### Post by jonobr on 2009-06-17
hello


Were you making changes to your /etc/pam.d/ files before this happened?

---

### Post by ybardagi on 2009-06-17
I never touched this files before this failure

---

### Post by jonobr on 2009-06-17
mmmm.... then (respectfully) im surprised you would change them now when they should be working.

I hate to say this, but for your own piece of mind and if there is nothing critical on your system, I would try a reinstall.

It sounds as if something occurred, and I think any problems you have in the future may have you thinking it is related to this..........

---

### Post by Iowan on 2009-06-17
[This]("http://www.psychocats.net/ubuntu/resetpassword") probably won't help... but just in case. There are a couple of others there - like "Can't Sudo".  You might also check */etc/passwd* to verify that you have a valid shell (/bin/false won't work).

---

### Post by ybardagi on 2009-06-22
I modified them because there were an message saying that an unknown option was there. and i had never seen this mesage before. 
OK. It seems there no option but reinstall...I've seen all of those Can't sudo and there's no usefull tips to me.

---

### Post by ybardagi on 2009-06-22
I modified them because there were an message saying that an unknown option was there. and i had never seen this mesage before. 
OK. It seems there no option but reinstall...I've seen all of those Can't sudo and there's no usefull tips to me.

---

### Post by jonobr on 2009-06-22
Hello

Before you do that, I would just post one more time.

Start a new thread, and in your opening post, I would recommend putting all you have learned in a succint form as possible.,

Say this is not a new install, probably refer to this thread, and put down what you have done,
I have found that once the number of posts in the thread grow people dont look at those posts as much as a new post.

Normally I would recommend a bump to your thread, however, I am thinking you dont want to loose that data, and someone may open a new thread and have the answers

---

### Post by ybardagi on 2009-06-22
I've tried now to change a passwd in recovery mode and didn't do anything

PS to jonobr: Thanks. It is driving me crazy. I have some important data there and it would be a professional suicide to delete it.

---

### Post by ybardagi on 2009-06-22
now i have tried to change passwd and as if i woul be talking to wall.
i'll try something more.
PS thank you jonobr

---

### Post by jonobr on 2009-06-22
Sure thing....

If you can even get to cli and look at the file system you could start rsync it off.. Im sure you knew that, and you problem is you cant get to that login prompt........

Good luck

---

### Post by ybardagi on 2009-06-22
any other advice
???????

---

### Post by ybardagi on 2009-06-23
problem solved. it seems it was some deprecated variables i pam configuration. i restored configuration files and... voilá.
Thanks

---

