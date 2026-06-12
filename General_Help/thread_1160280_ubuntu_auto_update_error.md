---
title: "ubuntu auto update error"
date: 2009-05-15
forum: General Help
---

### Post by Zoyberk on 2009-05-15
I get the icon that there are new updates for Ubuntu, when I try download them i get this error:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

```
Method gave invalid 400 URI Failure messageMethod gave invalid 400 URI Failure message
```so, I rely wish to have my ubuntu up-to date and if someone could tell me how to fix that :D

Oh and i first noticed that week ago, i just left it for week if it would fix itself but it didnt =)

---

### Post by dtoronto on 2009-05-15
you can download the updates using the CLI

```
sudo apt-get update
sudo apt-get upgrade
```

I can't help fix your packet manager because I don't have enough information about what is going wrong

---

### Post by Zoyberk on 2009-05-15
well posted what you said in terminal and got this:

```
zoyberk@zoyberkolandija:~$ sudo apt-get update
[sudo] password for zoyberk: 
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Get:1 http://si.archive.ubuntu.com jaunty Release.gpg [189B]
Ign http://si.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Ign http://si.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://si.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://si.archive.ubuntu.com jaunty/multiverse Translation-en_US
Get:2 http://si.archive.ubuntu.com jaunty-updates Release.gpg [189B]
Ign http://si.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://si.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://si.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://si.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
E: Method gave invalid 400 URI Failure message                
zoyberk@zoyberkolandija:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Zoyberk on 2009-05-16
could anyone help):P

---

### Post by vexorian on 2009-06-13
I know this is probably too late for you, but since this is the first result people would find at google when searching for this odd error, I better answer:
I had this problem as well, and after wandering around, I noticed it was the playdeb repository.
If you added/installed playdeb, uncheck it in system/software sources. Then refresh the repos, should finally work correctly...

---

### Post by Zoyberk on 2009-06-13
yeah i did somethink like that, forgoted to post i solved it.... XD
thanks anyway =)

---

