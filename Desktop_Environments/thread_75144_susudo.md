---
title: "su/sudo"
date: 2005-10-13
forum: Desktop Environments
---

### Post by MuRRe on 2005-10-13
If i understand right su = SuperUser
The problem is that i cannot do it when i right su it asks for password. So I write my password and it says:
murre@aspire5024:~$ su
Password:
su: Authentication failure

I know it is my password. What is wrong? Can't do much which out root permissions...

---

### Post by karuptdata on 2005-10-13
In the ubuntu distro root is disabled by default, however all you need to type in is sudo and the you login password and you should be good to go!

---

### Post by jalanbuntu on 2005-10-13
If you want to switch to root, just type 
```
sudo su
```
then, type in your password.

---

### Post by KingBahamut on 2005-10-13
Unless you desire to enable the root account. 

This is done via a 

sudo passwd root

---

### Post by ChrisTheGeek on 2005-10-13
Use sudo before a command and enter YOUR password.  By default the root account is disabled for security.  This has been covered in several threads so search the forum for more help.  You can find some more info here:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[https://wiki.ubuntu.com/UsingSudo](https://wiki.ubuntu.com/UsingSudo)

Enjoy!

---

### Post by Emerzen on 2005-10-13
Ubuntu uses the sudo system...not su (caveat below)...the password you set up when you installed Ubuntu is your sudo password.  So, any commands that require "su" priveleges will start w/ sudo, you don't switch to sudo first though, for example:

to apt-get install something ->

Ubuntu -> sudo apt-get install packagename

Other -> su
            enter password
            at root prompt type in apt-get packagename

Caveat-> you can enable a traditional su password system and even enable an entire su GUI session.  This is not done by default for security...when you sudo, only that one command is given root priveleges, when the process is done you are back as a regular user.  However, if you want to enable normal su... look at the how-to at [www.ubuntuguide.org](www.ubuntuguide.org).  You can also get a root prompt in a terminal by using the following command -> sudo su .  There's really no reason to do this though.  I begrudged this idea when I first started w/ Ubuntu, but I use other distro's now and again and find sudo easier and more sensible now.

---

### Post by pizzach on 2005-10-15
True.  But su does come in useful sometimes.  I'm specifically thinking of when mounting hfsplus cds.  Because of a bug in the driver, It appears I only mount the discs as a super user and I can only browse it as such.

---

