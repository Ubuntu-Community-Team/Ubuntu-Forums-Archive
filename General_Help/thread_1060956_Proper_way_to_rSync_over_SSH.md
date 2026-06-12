---
title: "Proper way to rSync over SSH??"
date: 2009-02-05
forum: General Help
---

### Post by NetworkGuy on 2009-02-05
I am trying to rSync or even scp a file from one server to another.  Problem is the file/and directory are owned by root and I as a user do not have the ability to write to the destination location.

Is there a way that I can cron the transfer of this file (every hour) without enabling the root account on the destination server?

The file in question:
-rw-r--r-- 1 root root    581 2009-02-02 20:46 bypasslist

---

### Post by Titan8990 on 2009-02-05
You can create a root cron job without enabling the root account. Just do:


sudo -i

---

### Post by NetworkGuy on 2009-02-05
> **Titan8990 said:**
> You can create a root cron job without enabling the root account. Just do:


sudo -i

Tried your suggestion from the command prompt before cron'ing.  I was challenged for root's password on the destination server. :(
> root@172.16.4.6's password: 


---

### Post by whitegourd on 2009-02-05
If you want to set up a cron to rsync to another server as root but don't want to get prompted for the password from the destination server, do the following.

# rsync w/o password authentication
cd /root/.ssh
ssh-keygen -t rsa (on server 1)
ssh-copy-id -i id_rsa.pub root@server2 (on server 1)

You may need to set up a password for both servers first just to make it easier for you.

# setting the password for root
sudo passwd root

You should then be able to ssh/rsync to the destination server w/o having to input a password.

---

### Post by NetworkGuy on 2009-02-05
I have ssh authenticating by keys, not passwords.  However if I enter a password for root, doesn't that enable the account?  Something I don't want to do since they do have a NIC facing the public Internet.

---

### Post by whitegourd on 2009-02-05
I see, could you adjust the permission for that one file so that you're local account has access to it as well?  Are both servers facing the public Internet or just one?

You could set up ssh keys for root on both the servers.  Just disable ssh root login from the Internet in your /etc/ssh/sshd_config

---

