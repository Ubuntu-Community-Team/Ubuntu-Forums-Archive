---
title: "Problems networking PC to PC"
date: 2005-08-21
forum: Desktop Environments
---

### Post by stig on 2005-08-21
[I posted this on the Absolute Beginners Forum on Friday but only got one reply (giving the URL for Samba doc pages). Perhaps I posted to the wrong forum, so please forgive me for re- posting here. :razz: ]

As a newbie to Ubuntu/Linux (and not knowing much about software and computers in general) I am having problems getting my PCs networked together, and I would be grateful for help.

I have two PCs using Windows 98SE and networked with cable, router and DHCP. This network has worked for a long time with no problems. I have now added a third PC which uses Ubuntu hoary and is linked to the other two by cable via the router. Also, one of the Windows PCs now has a 2nd hard disk with Ubuntu hoary.

I can still pass files between the two Win PCs but have had no success linking Win to Ubuntu or Ubuntu to Ubuntu (regardless of searching Google, Ubuntu Forums etc). On the Ubuntu systems the eth01 is active when I do System > Admin > Networking.

I followed the Unofficial Ubuntu guide “How to install Samba Server for files/folders sharing service?” and did:

sudo apt-get install samba
sudo apt-get install smbfs

The next step, “ How to add/edit/delete network users?” says to do:

sudo smbpasswd -a system_username
sudo gedit /etc/samba/smbusers

When I did the first line of this with my username (and enter my requested user password) then press return it asked me for “New Samba password”. Whatever I entered it returned a “Failed” - I tried my username, my password, the username of the other Ubuntu disk, new passwords etc, but all failed. I tried the second line from the Guide but got the same results.

After more searching on the Forum I found the following instructions:
*********
sudo apt-get install samba
sudo gedit /etc/samba/smb.conf

look for this (line 76):
Code:

; security = user

change it for
Code:

security = share
(notice that the ; is gone)

sudo /etc/init.d/samba restart
**********

I tried this but the sudo /etc/init.d/samba restart gave me:
* Stopping Samba Daemons....ok
* Starting Samba Daemons.....fail

I again tried sudo smbpasswd -a system_username but now get:
Can’t load /etc/samba/smb.conf - run testparm to debug it

I put testparm into a terminal and got:
Processing section “[homes”]
Processing section “[printers”]
Processing section “[prints$]
params.c:Section() - Empty section name in configuration file.
params.cm_process() - Failed. Error returned from params.carse()
Error loading services.
[N.B. I didn't ask for the smilies!]

I went back to the file and changed it back to the original setting, i.e.
security = share
changed back to
; security = user
but sudo smbpasswd -a system_username still gives me Can’t load /etc/samba/smb.conf - run testparm to debug it.

Unfortunately the testparm output means nothing to me.

I seem to be digging myself into an ever-deeper hole! ](*,)  Can anyone please help?
Thanks

---

### Post by cwaldbieser on 2005-08-21
> **stig][I posted this on the Absolute Beginners Forum on Friday but only got one reply (giving the URL for Samba doc pages). Perhaps I posted to the wrong forum, so please forgive me for re- posting here. :razz: ]

As a newbie to Ubuntu/Linux (and not knowing much about software and computers in general) I am having problems getting my PCs networked together, and I would be grateful for help.

I have two PCs using Windows 98SE and networked with cable, router and DHCP. This network has worked for a long time with no problems. I have now added a third PC which uses Ubuntu hoary and is linked to the other two by cable via the router. Also, one of the Windows PCs now has a 2nd hard disk with Ubuntu hoary.

I can still pass files between the two Win PCs but have had no success linking Win to Ubuntu or Ubuntu to Ubuntu (regardless of searching Google, Ubuntu Forums etc). On the Ubuntu systems the eth01 is active when I do System > Admin > Networking.

I followed the Unofficial Ubuntu guide “How to install Samba Server for files/folders sharing service?” and did:

sudo apt-get install samba
sudo apt-get install smbfs

The next step, “ How to add/edit/delete network users?” says to do:

sudo smbpasswd -a system_username
sudo gedit /etc/samba/smbusers

When I did the first line of this with my username (and enter my requested user password) then press return it asked me for “New Samba password”. Whatever I entered it returned a “Failed” - I tried my username, my password, the username of the other Ubuntu disk, new passwords etc, but all failed. I tried the second line from the Guide but got the same results.

After more searching on the Forum I found the following instructions:
*********
sudo apt-get install samba
sudo gedit /etc/samba/smb.conf

look for this (line 76):
Code:

 said:**
> 
Processing section “[printers”]
Processing section “[prints$]
params.c:Section() - Empty section name in configuration file.
params.cm_process() - Failed. Error returned from params.carse()
Error loading services.
[N.B. I didn't ask for the smilies!]

I went back to the file and changed it back to the original setting, i.e.
security = share
changed back to
; security = user
but sudo smbpasswd -a system_username still gives me Can’t load /etc/samba/smb.conf - run testparm to debug it.

Unfortunately the testparm output means nothing to me.

I seem to be digging myself into an ever-deeper hole! ](*,)  Can anyone please help?
Thanks

OK, basically, if you make a typo in your config file, the computer won't know what you meant.  So it first checks the file for typos and inconsistancies, and it won't run if it finds them.

There is a program called "testparm" you can run from the terminal.  It will diagnose the problems with the config file and tell you what they are.  Then you can correct the file.

At the terminal, type
```
$ testparm -s
``` and post the output here.  Someone will let you know what the problem means.
Thanks.

---

### Post by stig on 2005-08-22
Thanks for the help! I hope someone can explain what is wrong. Background info is in my original message above. (I don't know why smilies appear in the posted message below because I didn't put them there - something to do with HTML code perhaps?)

The output from testparm -s is as follows:

Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
params.c:Section() - Empty section name in configuration file.
params.c:pm_process() - Failed.  Error returned from params.c:parse().
Error loading services.

---

### Post by Wolveen on 2005-08-25
Im getting the same errors as well, I can see the Ubuntu machine over our network and everything from the X-Box to the M$ work fine as always.

...Nevermind just checked I cant see the Ubuntu machine over the network now LOL.

Anyway any more ideas for us noobs?

---

### Post by stig on 2005-08-25
Hi Wolveen,
In my original message I explained how I had posted it in the Absolute Beginners forum but nothing much was happening so I posted a copy here. Since then, I have got responses to the one in the the Beginners Forum!

I think I solved my problem with the smb.conf file and the testparm message. I got "()" twice in the testparm result and I found there was an empty set of brackets at the end of the smb.conf file. Have a look at the other thread for a fuller description if it is any help.
[http://ubuntuforums.org/showthread.php?t=58182](http://ubuntuforums.org/showthread.php?t=58182)

A noob's life is a difficult one when it comes to networks - which is why I also posted a request for some simple answers to very basic network questions. See:
"Help newbie please with really simple network questions"
[http://ubuntuforums.org/showthread.php?t=59557](http://ubuntuforums.org/showthread.php?t=59557)

Good luck with your network! :smile:

---

