---
title: "xampp"
date: 2009-02-03
forum: General Help
---

### Post by nemiux on 2009-02-03
Topic says what kind help I need. I started it at windows, but it bugged, linux is better for it. So now i downloaded it, but i can't install it.
Everything how to do is in this page:
[http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)
But it didn't help. I downloaded, then entered command: 
su
password
then i entered:
tar xvfz xampp-linux-1.7.tar.gz -C /opt
and it wrote this to me:
root@ubuntu:/home/nemiux# sudo tar xvfz xampp-linux-1.7.tar.gz -C /opt
tar: xampp-linux-1.7.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


Tell me what is wrong with this. Ty.

P.S. that file is on desktop, maybe link is bad?


Thanks again

---

### Post by Pablo Pablovski on 2009-02-03
If the file is on your desktop, you'll probably need to run the installer command from there, rather than your HOME directory.

Assuming the path to your desktop is /home/nemiux/Desktop, type:

```
cd /home/nemiux/Desktop
sudo tar xvfz xampp-linux-1.7.tar.gz -C /opt

```
That should work. I installed xampp myself the other day - it's great.

---

### Post by nemiux on 2009-02-04
Thanks, that so helped. Now one more thing, i need to go to htdocs and create files i'm doing php, but i can't access restriced, how do i copy/move items?

I create index.php on desktop, i go cd /home/nemiux/desktop/
Next what

Thanks

---

