---
title: "ubuntu lts user profiles"
date: 2010-06-03
forum: Desktop Environments
---

### Post by felixvah on 2010-06-03
Hi everyone, here's my problem:  Could not update ICEauthority file /home/user/... and etc.. the status of the error is 256.

This is how I get the error.  I have multiple users. I create user1 and customize the desktop and then I use rsync -azv /home/user1/ /etc/skel/  this worked great for the first time when all other users haven't create yet.

My problem lie in when I decided to change user1 setting and do a rsync to user2 using the rsync -azv /home/user1/ /home/user2/.  After the rsync log out and log on as user2 that's how I get the above error.

Here's what I've tried so far but it didn't work for me.  
sudo chown user2:user2 /home/user2/.ICEauthority
sudo chmod 644 /home/user2/.ICEauthority
sudo chown -R user2:user2 /home/user2/.*

if you know something else, please help me..

thank you,

---

