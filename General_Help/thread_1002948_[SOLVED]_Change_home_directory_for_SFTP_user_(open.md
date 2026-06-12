---
title: "[SOLVED] Change home directory for SFTP user (openssh)"
date: 2008-12-05
forum: General Help
---

### Post by noway on 2008-12-05
I use openssh-server for SFTP. I have a user called sftpuser which belongs to the group sftp and has its home directory in /home/sftpuser. Now I want to move this users home directory to another harddrive so I go into user settings and change the home directory to /media/disk/mystuff and make the folder /home/disk/mystuff belong to root, just like /home/sftpuser did. The problem is that when I change the home directory I can't log in anymore, I get the error message:

Read from remote host localhost: Connection reset by peer
Couldn't read packet: Connection reset by peer

Everything works as long as the home directory is the original home directory, but when I change that it stops working. I'm not changing anything else, sftpuser still belongs to the same group and the new home directory folder has the same permissions as the previous one. 


Here's the relevant entries from  /etc/ssh/sshd_config

AllowGroups sftp
Subsystem sftp internal-sftp
UsePAM yes
Match Group sftp
ChrootDirectory %h
ForceCommand internal-sftp
AllowTcpForwarding no


Now to the questions. Where do you think the problem lies? Could it be that "ChrootDirectory %h" is hardcoded to lead to /home/*username* and it doesn't get the new home directory I've specified in user settings?

Is the best solution when wanting to share a folder via SFTP to make that directory the home folder of that user and create a new user for every other folder you want to share? I can't think of any other way and symbolic links don't work (which makes sense considering ChrootDirectory).

---

### Post by noway on 2008-12-08
bump

---

### Post by noway on 2008-12-11
bump

---

### Post by stovicek on 2008-12-12
Have you made sure to copy all of the files from the old directory to the new one? This looks similar to an error I would get if I didn't copy my RSA key correctly to a remote computer that was RSA Authentication only (passwordless) login. In your case, I would assume that the .ssh/authorized_keys wasn't present in the new directory. Just a guess, though.

---

### Post by noway on 2008-12-12
To clarify, this is what I want:

I want to share a folder through SFTP. I want the user to be locked in that folder so he can't go outside. If it's possible I want several users, like one in /media/disk/mystuff one in /media/disk/otherstuff and so on. So far the only way I've been able to do this is by having the users home directories being /home/sftpuser and /home/sftpuser2 and in sshd_config "ChrootDirectory %h", but I want the folders to be elsewhere and *not* under /home/

I've asked in Freenode #openssh and #ubuntu, googled and asked here and no one has an answer. If *anyone* has *any* suggestions I'd really appreciate it. This seems like a really common thing to want to do, so someone has to know.

How can I share a directory outside of /home with SFTP?!

---

### Post by noway on 2008-12-12
stovicek: The only files in /home/sftpuser is a few songs that I moved there so I could see that I'm in the right folder. Nothing else than those test files.

---

### Post by trwww on 2008-12-13
I think scponly will do what you want:

[http://www.sublimation.org/scponly/wiki/index.php/Main_Page](http://www.sublimation.org/scponly/wiki/index.php/Main_Page)

---

### Post by noway on 2008-12-13
trwww, It should now be possible to do that with ChrootDirectory in /etc/ssh/sshd_config now. Without using any extra programs. I used this (and perhaps another one that I can't find now) guide to set it up.

[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

### Post by noway on 2008-12-13
SOLVED!

The problem was that **every folder** above /media/disk/mystuff has to be owned by root. I only had /media/disk/mystuff owned by root while /media/disk/ wasn't. 

Many thanks to hoxu in #debian

---

### Post by ram.coelho on 2009-06-18
Ok,

  I've got one here. I've been looking all over. Maybe you guys can help:

I did this a half-dozen times, but this one won't work. It is on a VMWare 64 bits running Ubuntu 8.10:

uname -a:
Linux server 2.6.27-7-server #1 SMP Fri Oct 24 07:37:55 UTC 2008 i686 GNU/Linux

This is what I am trying to do.
What follows was done locally, but happens just the same on remote clients:


user@server:/var$ sftp 192.45.2.137
Connecting to 192.45.2.137...
user@192.45.2.137's password: 
Couldn't read packet: Connection reset by peer



/var/log/auth.log:

Jun 18 20:45:57 server sshd[23658]: debug1: Bind to port 22 on ::.
Jun 18 20:45:57 server sshd[23658]: Server listening on :: port 22.
Jun 18 20:45:57 server sshd[23658]: debug1: Bind to port 22 on 0.0.0.0.
Jun 18 20:45:57 server sshd[23658]: Server listening on 0.0.0.0 port 22.
Jun 18 20:46:03 server sshd[23658]: debug1: Forked child 23664.
Jun 18 20:46:03 server sshd[23664]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
Jun 18 20:46:03 server sshd[23664]: debug1: inetd sockets after dupping: 3, 3
Jun 18 20:46:03 server sshd[23664]: Connection from 192.45.2.137 port 42626
Jun 18 20:46:03 server sshd[23664]: debug1: Client protocol version 2.0; client software version OpenSSH_5.1p1 Debian-3ubuntu1
Jun 18 20:46:03 server sshd[23664]: debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
Jun 18 20:46:03 server sshd[23664]: debug1: Enabling compatibility mode for protocol 2.0
Jun 18 20:46:03 server sshd[23664]: debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
Jun 18 20:46:05 server sshd[23664]: debug1: user user matched group list sftp at line 80
Jun 18 20:46:05 server sshd[23664]: debug1: PAM: initializing for "user"
Jun 18 20:46:05 server sshd[23664]: debug1: PAM: setting PAM_RHOST to "192.45.2.137"
Jun 18 20:46:05 server sshd[23664]: debug1: PAM: setting PAM_TTY to "ssh"
Jun 18 20:46:05 server sshd[23664]: Failed none for user from 192.45.2.137 port 42626 ssh2
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: password authentication accepted for user
Jun 18 20:46:06 server sshd[23664]: debug1: do_pam_account: called
Jun 18 20:46:06 server sshd[23664]: Accepted password for user from 192.45.2.137 port 42626 ssh2
Jun 18 20:46:06 server sshd[23664]: debug1: monitor_child_preauth: user has been authenticated by privileged process
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: establishing credentials
Jun 18 20:46:06 server sshd[23664]: pam_unix(sshd:session): session opened for user user by (uid=0)
Jun 18 20:46:06 server sshd[23671]: debug1: SELinux support disabled
Jun 18 20:46:06 server sshd[23671]: debug1: PAM: establishing credentials
Jun 18 20:46:06 server sshd[23664]: User child is on pid 23671
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: cleanup
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: deleting credentials
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: closing session
Jun 18 20:46:06 server sshd[23664]: pam_unix(sshd:session): session closed for user user



/etc/passwd:

user:x:1003:1003:User,,,:/:/usr/sbin/nologin



/etc/group:

sftp:x:1004:user



/etc/ssh/sshd_config:

# Logging
SyslogFacility AUTH
LogLevel DEBUG 
Subsystem sftp internal-sftp
Match group sftp
        ForceCommand internal-sftp 
        ChrootDirectory /var/sshbox



user@server:/var$ ls -l
drwxr-x---  2 root root  4096 2009-06-18 20:05 sshbox



Did I miss something?

---

