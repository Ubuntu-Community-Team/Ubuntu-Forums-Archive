---
title: "Remote ssh command with sudo and echo"
date: 2009-04-06
forum: General Help
---

### Post by ecrossahoo on 2009-04-06
I'm attempting to append a line to /etc/fstab to numerous hosts.  I'm running script that ssh's to a list of hosts and will then echo an NFS mount point into /etc/fstab.  I have attempted several methods, but I'm not successfully appending to the file.

These methods fail:  

ssh $host sudo echo "fileserver.domain.com:/vol/vol1/data /mnt/data rw,-r32768,-w32768,-3  0       0"  >> /etc/fstab

ssh $host sh -c sudo "fileserver.domain.com:/vol/vol1/data /mnt/data rw,-r32768,-w32768,-3  0       0"  >> /etc/fstab

Can anyone provide insight on how I can accomplish this task?

Thanks.

---

### Post by b0b138 on 2009-04-06
Maybe try ssh user@hostname sudo echo.... Have you setup a public key to avoid having to enter a password, as the command might be failing because its looking for one. 

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by kryptikos on 2009-04-06
> **ecrossahoo said:**
> 

ssh $host sh -c sudo "fileserver.domain.com:/vol/vol1/data /mnt/data rw,-r32768,-w32768,-3  0       0"  >> /etc/fstab



Remember, even though you are running sudo the first time a user pushes the sudo command the box will want to authenticate you against its /etc/sudoers. Meaning you will still have to send a password over as the remote box will ask for it. You should be able to see this by running ssh in debug mode:

**ssh -vvv $host <rest of your command>**

You'll need to use something like **'expect'** to send the password. Here is a link that shows how to use it with a ssh login:

[http://bash.cyberciti.biz/security/expect-ssh-login-script/]("http://bash.cyberciti.biz/security/expect-ssh-login-script/")

Hopefully that might help you out. :)

---

