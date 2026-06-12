---
title: "Chowned All files"
date: 2008-02-09
forum: Desktop Environments
---

### Post by ltkenbo on 2008-02-09
I have been messing around ubuntu working on a webserver thing me and I friend are doing and without really thinking about it I chowned group ownership of everything using the command:
chown -R :admin *

So now I get the  sudo: must be setuid root whenever I try to sudo. Whats the best way to fix this. I heard you can use the recovery CD and change /usr/bin/sudo back to :root group owner ship.

Btw, all the things that have root user ownership still have it its just the group ownership got changed to admin for most files. Whats the best way to fix this?

---

### Post by jimlay on 2008-02-09
/usr/sbin/sudo doesn't actually need to be root:root to work. It needs it's 's' (suid) bit set

(j@albert:~)$ sudo -s
sudo: must be setuid root

You need chmod +s /usr/bin/sudo

When you changed the group it dropped the suid bit.

Since you did your whole system you are going to have problems all over the place. In my /usr/bin directory alone there are 21 suid programs.

(root@albert:bin)# ls -l|egrep '^...s'
-rwsr-xr-x  1 root   root      11048 2007-12-10 10:33 arping
-rwsr-sr-x  1 daemon daemon    38464 2007-02-20 06:41 at
-rwsr-xr-x  1 root   root      28720 2007-11-06 12:16 chfn
-rwsr-xr-x  1 root   root      23984 2007-11-06 12:16 chsh
-rwsr-xr-x  1 root   root      11214 2008-02-08 08:04 fileshareset
-rwsr-xr-x  1 root   root      22348 2006-06-26 03:54 fping
-rwsr-xr-x  1 root   root      23052 2006-06-26 03:54 fping6
-rwsr-xr-x  1 root   root      37360 2007-11-06 12:16 gpasswd
-rwsr-xr-x  1 root   root       5764 2008-02-08 08:43 kgrantpty
-rwsr-xr-x  1 root   root       6316 2008-02-08 08:43 kpac_dhcp_helper
-rwsr-xr-x  1 root   lpadmin    9364 2008-01-29 13:51 lppasswd
-rwsr-xr-x  1 root   root      46052 2007-05-30 00:49 mtr
-rwsr-xr-x  1 root   root      19208 2007-11-06 12:16 newgrp
-rwsr-xr-x  1 root   root      29104 2007-11-06 12:16 passwd
-rwsr-xr-x  1 root   root      47804 2008-01-30 20:54 pulseaudio
-rwsr-xr-x  1 root   root       5768 2008-02-08 08:43 start_kdeinit
-rwsr-sr-x  2 root   admin    107776 2008-01-22 11:54 sudo
-rwsr-sr-x  2 root   admin    107776 2008-01-22 11:54 sudoedit
-rwsr-xr-x  1 root   root      12296 2007-12-10 10:33 traceroute6.iputils
-rwsr-xr-x  1 root   root      12744 2008-01-02 03:41 v4l-conf
-rwsr-sr-x  1 root   root       7460 2008-01-29 04:49 X

They are all over your system though (/bin, /usr/sbin) . And many need to be chgrp specific things to work with hardware and files that are only supposed to be accessed with those specific programs.

I recommend re-installing or you are going to have little issues that are almost impossible to track down. Upgrading to hardy heron or convince apt to some how re-install everything.

If you boot up in recovery mode though, 

chgrp root /usr/bin/sudo  
is not going to fix it. You need
chmod +s /usr/bin/sudo

Josie

---

### Post by ltkenbo on 2008-02-09
Can I reinstall it without erasing all my files? Like some of the programs installed or should I just wipe everything and reinstall?

---

### Post by xeth_delta on 2008-02-09
> **ltkenbo said:**
> I have been messing around ubuntu working on a webserver thing me and I friend are doing and without really thinking about it I chowned group ownership of everything using the command:
chown -R :admin *

So now I get the  sudo: must be setuid root whenever I try to sudo. Whats the best way to fix this. I heard you can use the recovery CD and change /usr/bin/sudo back to :root group owner ship.

Btw, all the things that have root user ownership still have it its just the group ownership got changed to admin for most files. Whats the best way to fix this?

Welcome to the forums! What directories did you change the group ownership to? Did you apply the change to /?

---

### Post by ltkenbo on 2008-02-09
I did it at / to all directories and files recursively I was trying to give admin privaleges to several users but I guess I should have just added the users to the root group.

---

### Post by xeth_delta on 2008-02-09
> **ltkenbo said:**
> I did it at / to all directories and files recursively I was trying to give admin privaleges to several users but I guess I should have just added the users to the root group.

Hmm, that does not sound that good. Let me check some ownerships on my system, let's see if you can avoid reinstalling.

By the way, I think you should better add the users to the admin and/or adm group to give them administratives privileges.

---

### Post by xeth_delta on 2008-02-09
There are certanly differences between our systems, but I will post some of the ownerships some of the directories and files in my file system, hope it helps.

1. /bin and files within: root:root, except fusermount which has root:fuse.
2. /boot: all root:root
3. /initrd: root:root
4. /lib: all seems to be root:root, too many sub-directories for me to go through all of them
5. /opt root:root
6. /root: root:root
7. /sbin: root:root, with the exception of: unix_chkpwd which has root:shadow
8. /sys: all seem root:root, too many sub-directories for me to go through all of them
9. /tmp is root:root. subdirectories and files depend on the respective owner
10. /var root:root, with the exception of local (root:staff) and mail (root:mail)
11. /usr root:root, with the exception of src (root:src). Too many sub-directories for me to go through all of them.
12. /etc. many different ownerships, too many sub-directories for me to go through all of them. for the moment I can tell you all files and directories in first level are root:root, with the exception of: at.deny (root:daemon), chatscripts (root, dip), cups (root, lp), fuse.conf (root, fuse), gshadow (root:shadow), mtab.fuselock (root, user_name), ppp (root, dip), shadow (root, shadow), wvdial.conf (root, dialout)

You may want to empty /tmp and reboot, so that it is repopulated with files with the correct permissions and ownerships.

Good luck!

---

### Post by ltkenbo on 2008-02-09
I can't even reboot the system because I can't get root privaleges and its up in my friends room (dorm) upstairs and he is away for the weekend so I can't shut it off, I guess I'll probably just reinstall it all.

---

### Post by xeth_delta on 2008-02-09
> **ltkenbo said:**
> I can't even reboot the system because I can't get root privaleges and its up in my friends room (dorm) upstairs and he is away for the weekend so I can't shut it off, I guess I'll probably just reinstall it all.

Far fetched given the circumstances, but try a "sudo su". I am a bit confused, if you don't have physical access to the machine, how will you reinstall? Or you meant when your neighbor comes back?

---

### Post by ltkenbo on 2008-02-09
I'm at a college and my friend lives on the floor above me in our dorm building. We set up a forum a while ago running on my windows desktop for people in the dorms over the residential network (they just type in my computer name and they can join and post). Anyways we're moving it over to linux (computer is in his room) and he went home this weekend but since we set up ssh access I can pretty much do everything, unless of course I don't have root privaleges, lol. Yeah he comes back tomorrow so I'll probably reinstall it then.

---

### Post by golovan on 2008-02-11
> **xeth_delta said:**
> There are certanly differences between our systems, but I will post some of the ownerships some of the directories and files in my file system, hope it helps.

1. /bin and files within: root:root, except fusermount which has root:fuse.
2. /boot: all root:root
3. /initrd: root:root
4. /lib: all seems to be root:root, too many sub-directories for me to go through all of them
5. /opt root:root
6. /root: root:root
7. /sbin: root:root, with the exception of: unix_chkpwd which has root:shadow
8. /sys: all seem root:root, too many sub-directories for me to go through all of them
9. /tmp is root:root. subdirectories and files depend on the respective owner
10. /var root:root, with the exception of local (root:staff) and mail (root:mail)
11. /usr root:root, with the exception of src (root:src). Too many sub-directories for me to go through all of them.
12. /etc. many different ownerships, too many sub-directories for me to go through all of them. for the moment I can tell you all files and directories in first level are root:root, with the exception of: at.deny (root:daemon), chatscripts (root, dip), cups (root, lp), fuse.conf (root, fuse), gshadow (root:shadow), mtab.fuselock (root, user_name), ppp (root, dip), shadow (root, shadow), wvdial.conf (root, dialout)

You may want to empty /tmp and reboot, so that it is repopulated with files with the correct permissions and ownerships.

Good luck!

Hi
I'm having somewhat the same problem as the threadstarter...

Someone (no not me:) ) accidentally wrote 
sudo chown username -R  media / Media

this resulted in recursively wiping out every other user and root ownership:)

I've managed to get sudo to work with recoverymode and chown root:root /usr/bin/sudo/ 
and chown root /etc/sudoers 

But all is not well. I made a search for * which is owned by "username" and also owned by group "root" 
It's a big number I must say..

Then I went into my other box and searched for the same thing. No files found...

My question: is it possible to chown all files and folders where owner is "username" and group is "root", to owner "root" and group "root"?  with a single command? 

Or do I have to reinstall?

---

### Post by golovan on 2008-02-11
oh nevermind, then I still would have problems with root: mail  etc.
Guess the best way to fix this is a reinstall...:(

---

### Post by xeth_delta on 2008-02-11
> **golovan said:**
> Hi
I'm having somewhat the same problem as the threadstarter...

Someone (no not me:) ) accidentally wrote 
sudo chown username -R  media / Media

this resulted in recursively wiping out every other user and root ownership:)

I've managed to get sudo to work with recoverymode and chown root:root /usr/bin/sudo/ 
and chown root /etc/sudoers 

But all is not well. I made a search for * which is owned by "username" and also owned by group "root" 
It's a big number I must say..

Then I went into my other box and searched for the same thing. No files found...

My question: is it possible to chown all files and folders where owner is "username" and group is "root", to owner "root" and group "root"?  with a single command? 

Or do I have to reinstall?

My guess is that it would be possible with a bash script. I don't know how to do what you need, but it would seem to fit. You might want to start a new thread asking for this.

---

### Post by golovan on 2008-02-12
Thanks for the reply!
But I decided to just reinstall. It was faster than fiddling around:)

---

