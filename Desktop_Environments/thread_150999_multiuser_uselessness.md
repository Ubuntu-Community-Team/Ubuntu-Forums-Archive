---
title: "multiuser uselessness"
date: 2006-03-27
forum: Desktop Environments
---

### Post by brallan on 2006-03-27
Ubuntu's login with a single user as root is a wonderful setup. But for anyone else to use it, i need to get them past the login screen. Is there any way to skip the login screen? 

I have a couple of reasons to want to do this. First of all, I live in a collective house, and I don't mind lending out my machine, but I am not so keen on giving out my (root) password. 

I also do not wish the extra hassle of having to maintain some kind of guest account and maintain it. I have done that in the past and have always run into permissions problems and difficulties, simply because its an account i never use and when people ask me "how do I...?" I wind up sending them down a dead end.

thanks,
brian

EDIT: I looked inside /etc/gdm/gdm.conf which led me to run:

sudo gdmsetup

which is a graphical editor of the gdm.conf file. it's also at <System><Administration><Login Screen Setup> Now I can use automatic logon and timed logon... PERFECT! only one acount for everything, but i'm the only one who needs to know the root password. thanks for your help!

---

### Post by Darkriser on 2006-03-27
first - your account is NOT root account. and when logging in, you log as a common user (not a supersuser). read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

second - as for multiuser, the solution is very simple. create accounts for your friends (one account for each of them) and your problem is solved.

and last - sharing passwords is not the best practice, for sure :-)

---

### Post by yota on 2006-03-27
You can set autologin and timed login from the gdm configuration available under settings/logon screen settings (translated from italian! maybe it's not exactly the same).
You can also directly edit /etc/gdm/gdm.conf and search for AutomaticLogin and TimedLogin.

Hope this helps.

---

### Post by Breeegz on 2006-09-14
I am using a similar setup for me

one guest/group account
and my account (so I can set my non standard preferences and the guests don't need to be looking at the files on my desktop)

I don't want to give out a password to my guests (wife, mother-in-law, sister) so they can use the computer with no problems.

however when my screen gets locked, they cannot login (timed doesn't work) instead of porkchop (my guest account) autologging in, "User" is logging in and failing...  am I doing something wrong?

---

### Post by mixmaster on 2006-09-16
When you leave the computer you should log out rather than leaving the screen to lock on a timer.  If you don't want to do this, don't just lock the screen, select "switch user" instead.  This returns you to the login screen and someone else can log in from there.  When you later log in you will be prompted with the option to either start a new session or return to your old one.

Your other users need to do this also.

---

