---
title: "can't get ssh to function"
date: 2009-05-24
forum: General Help
---

### Post by Stolea on 2009-05-24
I am trying to connect between 2 Ubuntu computers via SSH.
I have installed SSH on both computers. When I go to >Places>Connect to Server I fill in all the relevant details of the machine I want to connect to and hit "Connect" I get
> Cannot display location "sftp://peter@192.168.0.3/home"Connection refused by server
I get the same result if I try the connection from the other end. What am I doing wrong here?

---

### Post by alphacrucis2 on 2009-05-24
> **Stolea said:**
> I am trying to connect between 2 Ubuntu computers via SSH.
I have installed SSH on both computers. When I go to >Places>Connect to Server I fill in all the relevant details of the machine I want to connect to and hit "Connect" I get

I get the same result if I try the connection from the other end. What am I doing wrong here?

Is the ssh server actually running on the machine you are connecting to?

---

### Post by Stolea on 2009-05-24
what do you mean? do I have to start ssh somehow every time I want to use it? How???

---

### Post by LinuxRules1 on 2009-05-24
Make sure you installed the openssh-server package.

---

### Post by alphacrucis2 on 2009-05-24
> **Stolea said:**
> what do you mean? do I have to start ssh somehow every time I want to use it? How???

ssh consist of two parts. A client and a server. The client is what you run to connect to the server eg sftp, ssh and putty are all ssh clients (I prefer putty as it is a gui client that I am used to). The machine that is receiving the ssh connection has to have an ssh server running to respond to the request. If you just installed the ssh package from synaptic then it installs the basic ssh client plus the server. To check it if the server part is running, on the machine you want to connect to, have a look in System - Administration - Services. In the list of services you should see one called Remote Shell Server. If you click the unlock button and enter your password and start and stop any of the listed services by ticking or unticking the checkbox.

Edit -- once ticked the service will start automatically when the system starts up,

---

### Post by Stolea on 2009-05-24
The box is ticked on both machines.
I restarted both systems and now can connect from #2 to #1 without any problems. I can access the files, but they all have a white X in their icon???
If I try the connection from #1 to #2 I get 
> Cannot display location "sftp://peter@192.168.0.3/home"
Host key verification failed

---

### Post by Stolea on 2009-05-24
I have since checked and installed the nfs-server on both machines thinking that that might have something to do with it. No luck still only one way traffic and read only access.
So I have 3 questions:
1. how do I get aound the host key verification problem?
2. how do I get read write access to the files?
3. is there a way to mount the SSH connection at startup?

---

### Post by bodhi.zazen on 2009-05-24
First, can you connect to the server with ssh ?

ssh user@server ?

If so, go for scp.  If you want to mount the directory locally, use sshfs. If you want to mount the remote directory in windows with a gui interface use winscp.

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

Second, just be sure to secure your ssh server ;)

[uwiki]AdvancedOpenSSH[/uwiki]

---

### Post by duds2008 on 2009-05-24
Install openssh-server on the computer you want to connect to. Once installed test it from the terminal: $ssh localhost
If it's working you can then connect to the same computer from another one on a LAN. $ssh user@host (or IP address)
Connect to it over the internet the same way. Your external IP address can be found out by googling whatsmyip.
Hope this helps.

---

### Post by Stolea on 2009-05-25
Same as before #1 connects with #2 no problem.
#2 to #1 returns> peter@office:~$ ssh peter@192.168.0.3
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
72:91:7b:a3:7b:9d:d3:99:bb:b4:dd:bd:d9:59:6f:00.
Please contact your system administrator.
Add correct host key in /home/peter/.ssh/known_hosts to get rid of this message.
Offending key in /home/peter/.ssh/known_hosts:1
RSA host key for 192.168.0.3 has changed and you have requested strict checking.
Host key verification failed.


I am not sure that I can understand what I am meant to do about this key.

---

### Post by Stolea on 2009-05-25
Update:
I renamed the key files on both computers to known_hosts.bak. I now can access files from both directions. I'm on a winner here :)
I have read through the document 

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/")

I followed the steps and set up a directory /media/office to mount my relevant directory.
When I try to execute the next step, i.e. the mount command I get:
> peter@shop:~$ sshfs office:/windows /media/office
read: Connection reset by peer

Where am I going wrong?

---

### Post by Francewhoa on 2009-06-26
Same here. I found a solution on this post: [http://ubuntuforums.org/showpost.php?p=7521619&postcount=10](http://ubuntuforums.org/showpost.php?p=7521619&postcount=10)

---

### Post by bodhi.zazen on 2009-06-26
> **Onopoc said:**
> Same here. I found a solution on this post: [http://ubuntuforums.org/showpost.php?p=7521619&postcount=10](http://ubuntuforums.org/showpost.php?p=7521619&postcount=10)

That "works"" but is less then ideal.

The message > @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@  @@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@  @@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
72:91:7b:a3:7b:9d:d3:99:bb:b4:dd:bd:d9:59:6f:00.
Please contact your system administrator.
Add correct host key in /home/peter/.ssh/known_hosts to get rid of this message.
Offending key in /home/peter/.ssh/known_hosts:1
RSA host key for 192.168.0.3 has changed and you have requested strict checking.
Host key verification failed. 			 		

(or similar) is a serious security warning. You need to know why you are getting this warning.

Most often this is because the keys on the server changed.

This error message, however, is critical to preventing "man in teh middle" attacks where somebody on the internet is spoofing your server.

Once you confirm that the ssh key has changed on the server, no need to remove ~/.ssh/known_hosts

Simply remove the offending key.

```
ssh-keygen -R hostname
```

Or change hostname to the actual hostname or ip_address of the server.

This preserves all the known hosts in ~/.ssh/known_hosts and security ;)

---

### Post by bodhi.zazen on 2009-06-26
> **Stolea said:**
> Update:
I renamed the key files on both computers to known_hosts.bak. I now can access files from both directions. I'm on a winner here :)
I have read through the document 

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

I followed the steps and set up a directory /media/office to mount my relevant directory.
When I try to execute the next step, i.e. the mount command I get:

Where am I going wrong?

The error message you get when you sshfs is incomplete.

You need to again connect with ssh, using the -vv option, to see the actual error message.

One possibility, unless the user is the same on the client and server, you need to specify a user with the command.

ex 

ssh user@server -vv # <- this will give you the actual error message.

sshfs user@server:/remote_dir /mnt/local_sshfs_mount_point

In your case :

```
ssh user@office -vv
```

```
sshfs ***user@***office:/windows /media/office
```

---

