---
title: "How can I change the password for my default keyring in gnome-keyring?"
date: 2007-05-28
forum: Desktop Environments
---

### Post by cdmarcus on 2007-05-28
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/gnome-keyring/+question/7336](https://answers.launchpad.net/gnome-keyring/+question/7336) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				I use pam-keyring, so I need my keyring password to be the same as my account password. I recently changed my account password, but I can't seem to figure out how to change the password for my keyring. Is this possible, or will I have to delete my keyring configuration entirely and put in my passwords from scratch?

---

### Post by newagelink on 2007-07-20
I'm having the same problem. Or, as I had asked in #ubuntu -- and was ignored (or rather, I should say, people were preoccupied),

How do I change my keyring password? I went to [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) and tried the section headed "Automatic Keyring", but it returned the following: [http://paste.ubuntu-nl.org/30658/](http://paste.ubuntu-nl.org/30658/)
```
daniel@daniel-laptop:~$ /usr/lib/libpam-keyring/pam-keyring-tool -c
pam-keyring-tool: only one keyring action my be specified on the commandline
daniel@daniel-laptop:~$ sudo apt-get install libpam-keyring
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpam-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  libmtp5 fftw3 mysql-common python2.4-minimal libmysqlclient15off ruby1.8
  kdebase-kio-plugins ruby libkonq4 kdebase-bin libtunepimp5 libifp4
  libdbus-qt-1-1c2 kdesktop libpq5 libgpgme11 libruby1.8 libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daniel@daniel-laptop:~$ /usr/lib/libpam-keyring/pam-keyring-tool -c
pam-keyring-tool: only one keyring action my be specified on the commandline
daniel@daniel-laptop:~$ 
```

---

### Post by cdrappier on 2007-08-29
bump.. same thing

---

### Post by peddy on 2007-10-21
me too

---

### Post by electralake on 2007-10-30
Back to the Top, I also have a need to sync my keyring password with my new account password.

---

### Post by s3019293 on 2007-11-08
I am also having this problem? has anyone managed to figure it out?

---

### Post by s3019293 on 2007-11-08
I solved the problem. Unless your Ubuntu password is different to your gnome keyring password you don't need to complete this step. If it is you need to go into System>Administration>Keyring manager and delete the keyring.

---

### Post by qwill on 2007-11-12
I just got the same problem and finally figured it out :

within keyring manager; press F9 to see the keyring; then delete it.
Log off and logon;
Open keyring manager again. It will ask to make a new keyring to store the wifi authentification password.
This new keyring is now in sync with your new password

---

### Post by Luke.Hoersten on 2007-11-30
This is, unfortunately, not working for me. I am running gutsy and don't see the check-box asking if I want to enter my password automatically after I login. I've tried deleting the keyring and then it asked me for a new one but that didn't fix the problem either. I'm using the same password for both login and keyring.

Any more suggestions?

---

### Post by Niniel on 2007-12-27
No, but I'm happy to report that logging in without a password - or rather, a fake password that's like the live CD password and doesn't require you to enter anything - will also cause a problem with the keyring.

---

### Post by mexpolk on 2008-02-06
Here is, a solution to change default Keyring Manager password:

[URL="http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html"]
http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html[/URL]

best,
Ivan Torres

---

