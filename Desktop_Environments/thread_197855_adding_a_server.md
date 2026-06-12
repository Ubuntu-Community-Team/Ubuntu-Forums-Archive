---
title: "adding a server"
date: 2006-06-16
forum: Desktop Environments
---

### Post by the_guy1 on 2006-06-16
I am look to set up a personal sever mainly so I can remotely listen to my music and so I can retrieve documents and download other programs 
What is the best way to do it and what programs should I use and can you just point me in the direction of a good tutorial.

---

### Post by taurus on 2006-06-16
I think you are talking about ssh server (sshd) and ftp server (vsftpd or proftpd)...  They are all available from repos.

---

### Post by lamego on 2006-06-16
It is safer to use sshd over ftp because the user, pass and data will be encrypted during the transfers.

You will need to install sshd on the server:
  sudo apt-get install sshd

Then to transfer files from/to your server on windows systems you can use a windows an ssh capable client like [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) .

If you need to transfer from other ubuntu boces just use the "Connect to Server" function and put the sftp login info.

---

