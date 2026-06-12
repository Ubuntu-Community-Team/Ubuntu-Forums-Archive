---
title: "SFTP design"
date: 2009-04-08
forum: General Help
---

### Post by ronin2307 on 2009-04-08
I am new to Linux so please bear with me.

I intend to create a DMZ and put a FTP server in it. Obviously FTP is plain text so I would like to actually use either SFTP or FTPS. After actually setting up FTPS using vsftpd on my Ubuntu VM (testing purposes) I realized that I cannot use it in conjuction with my Cisco ASA because the encrypted FTPS packets cannot be used for port forwarding.

So it appears that I have to use SFTP. I have done some reading but a few question remain. One of them being about users. 
vsftpd lets me create virtual users and chroot them to a folder. Can the same be accomplished with SFTP?
Also, how can I disable any other functionality other than the downloading and uploading of files for the SFTP users? I don't want them to be able to run any shells or anything else for that matter, since this SFTP server would be publicly accessible?

thanks

---

### Post by The Cog on 2009-04-08
Here is a site providing a sw that I tried - it works nicely.
[http://mysecureshell.sourceforge.net/fr/index.html](http://mysecureshell.sourceforge.net/fr/index.html)

Or here is a howto on Debian - should work on Ubuntu too:
[http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny)

Other links that may be useful:
[http://www.google.com/search?hl=en&q=sftp+chroot](http://www.google.com/search?hl=en&q=sftp+chroot)

---

### Post by ronin2307 on 2009-04-08
thank you. I will parse through this and see how far I can get. I think I am safe to assume that virtual users do not exist in the SFTP world then

---

### Post by ronin2307 on 2009-04-08
stupid question:

I have installed openssh 5.1 and made the following changes

# Use the following line to *replace* any existing 'Subsystem' line
Subsystem       sftp    internal-sftp

# These lines must appear at the *end* of sshd_config
Match Group sftponly
        ChrootDirectory %h
        ForceCommand internal-sftp
	AllowTcpForwarding no


i have disabled my firehol and tried to connect using filezilla (from XP)
first I used my username "sftp" and automatically added the Ubuntu IP, so it ended up being [email]sftp@xxx.xxx.xxx.xxx[/email] 
that didn't work 
then I set the username to be sftp@myubuntu_machine and this time the authentication failed...
what am I doing wrong?

---

### Post by The Cog on 2009-04-08
Sorry, I forgot to answer you question about SFTP users. As far as I know, it only allows real users who have user logins on the system.

I don't know what your authrntication problem is. I suggest you take it step-by-step, firstly by just installing the standard SSH server using its default settings, and make sure you can log in using SSH, to a command prompt (putty can do this from windows). Then check that filezilla can log in and see the filesystem. Then start fiddling with the chroot settings and disabling the shell login once you know the basics are working.

---

### Post by ronin2307 on 2009-04-09
I did some snooping around and here is what I know:

1. I have a local user called sftp
2. sftp is regular user, not unpriviledged
3. using sftp@myubuntu_machine from filezilla fails with "authentication failed"
4. auth.log in the /var/log/ directory says this:
   Invalid user sftp@myubuntu_machine from xxx.xxx.xxx.xxx
   Failed none for invalid user sftp@...... 
   pam_lwidentity(sshd:auth): failed to get GP info
   pam_lwidentity(sshd:auth): Looking up name sftp@.......
   pam_unix(sshd:auth): check pass; user unknown
   pam_unix(sshd:auth): authentication failure;............
   Failed password for invalid user........


So basically what I understand from this is that sftp is not in the PAM database. Now when I was messing with vsftpd I recall having to manually "load" users into the PAM db, but those were virtual users.

so the question is what did I screw up now :-) ???

---

