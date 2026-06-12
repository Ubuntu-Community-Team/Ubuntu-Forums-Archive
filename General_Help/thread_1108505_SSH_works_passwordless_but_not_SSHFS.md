---
title: "SSH works passwordless but not SSHFS"
date: 2009-03-27
forum: General Help
---

### Post by LarsEriksson on 2009-03-27
Ive done a passwordless setup, like this:

```
ssh-keygen -t rsa
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
ssh server
chmod 700 .rss
chmod 600 .rss/authorized_keys
```

And i can connect with: ssh user@server
without a password, but when i try to connect with:
sudo sshfs user@server:/remote_folder /local_mountpoint
the server asks for a password.
How can i troubleshoot/fix this ??

---

### Post by lensman3 on 2009-03-27
Mine sftp does.   My ftp server is "vsftpd".

Once I have the key-gen done I use the following command to copy everything to the remote client.

cat ~/.ssh/id_rsa.pub | ssh user@remotebox "(mkdir .ssh&>/dev/null; chmod 700 .ssh && cat - >> .ssh/authorized_keys )&&chmod 600 .ssh/authorized_keys"


Change the user@remotebox and put everything on the same line.  It will prompt for password as this line is executed. I always set this up as super-user.

I assume that "ssh-keygen" has no password entered.

Hope this helps.

---

### Post by lensman3 on 2009-03-27
I was wrong above.  The ftp client is not vftpd but is the sshd daemon.  I just checked the /var/log/secure logs. 

Unfortunately, this implies that selinux might be the problem.   I'm running Redhat Core 10.  I have turned selinux to "enforcing", but selinux does have a lot of problems.

---

### Post by LarsEriksson on 2009-03-28
Well, as i said, i do it exactly the same way you do, just another method to get the key-file from the client to the server.

I cant really see how it can work with the normal ssh-connection, but not with the SSHFS..

---

### Post by reanjr on 2010-06-10
This threw me for a bit as well.  Remember that when you run something with sudo, you are actually running it as root, not as the user you are logged in as.  So you correctly set up public-key auth for your user account, which works when you do "ssh whoever@wherever", but you still need to set up public-key auth for the root user to get "sudo sshfs ..." to work properly.

---

### Post by bilkay on 2010-10-27
Also, it's necessary to set up ssh for root if you're going to use sshfs with autofs. It can be a little tricky attempting to transfer root's id_rsa file via ssh since root requires a password, and root doesn't have a password. I got around that by copying it to a user directory, changing ownership to the user that can ssh, scp-ing it to the server, and then (sudo) cat-ing it to root's  .ssh/authorized_keys file.

---

