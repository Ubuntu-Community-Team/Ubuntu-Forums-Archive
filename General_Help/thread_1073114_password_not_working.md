---
title: "password not working"
date: 2009-02-18
forum: General Help
---

### Post by sumwonyuno on 2009-02-18
Hello,

This problem started yesterday, and never happened in the many years I've been using Ubuntu or any Linux distro.

Basically sudo or anything asking for my password (except login) doesn't work anymore.  It's not like I've changed my password or forgot it.  Loging into Ubuntu does work.

But, let's say I go into Synaptic, Update Manager, or Users and Groups, where it has a prompt.  Password is invalid.  Using sudo [command], each attempt fails.  Though I did find a sort of work around.

If I enter my password in the opposite case (e.g. uppercase), it doesn't say invalid password w/ sudo, then if I enter the password in the correct case, it works.  This strategy doesn't work with the prompts.  But using this strategy, I've been able to check things like /etc/groups, /etc/sudoers, /etc/passwd/, /etc/shadow, and they seem all fine.

I've tried many of the "fix sudo" guides that come up in Google (e.g. boot into recovery mode, passwd sumwonyuno, password root, adduser sumwonyuno admin, etc), but none of them have solved it.  I don't want to try disabling sudo/passwords, nor am I willing to reinstall Ubuntu and reconfigure everything just for this, unless, of course, it's the only way.

Though, yesterday I do remember that I installed some updates: consolekit, libck-connector0, hal-info and libpam-ck-connector.  Sudo/password failure definitely occured after installing, though it was a few hours after installing the updates did I discover sudo/password failure.

Also, here are some interesting lines from the system log:

```


Feb 17 18:10:01 sumwonyuno-laptop CRON[6897]: PAM (cron) illegal module type: auto
Feb 17 18:10:01 sumwonyuno-laptop CRON[6897]: PAM (other) illegal module type: auto
Feb 17 18:10:01 sumwonyuno-laptop CRON[6897]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 17 18:10:03 sumwonyuno-laptop CRON[6897]: pam_unix(cron:session): session closed for user root
Feb 17 18:10:32 sumwonyuno-laptop polkit-grant-helper-pam[7013]: PAM (polkit) illegal module type: auto
Feb 17 18:10:32 sumwonyuno-laptop polkit-grant-helper-pam[7013]: PAM (other) illegal module type: auto
Feb 17 18:10:36 sumwonyuno-laptop polkit-grant-helper-pam[7017]: PAM (polkit) illegal module type: auto
Feb 17 18:10:36 sumwonyuno-laptop polkit-grant-helper-pam[7017]: PAM (other) illegal module type: auto
Feb 17 18:10:37 sumwonyuno-laptop polkit-grant-helper-pam[7017]: pam_unix(polkit:auth): conversation failed
Feb 17 18:10:37 sumwonyuno-laptop polkit-grant-helper-pam[7017]: pam_unix(polkit:auth): auth could not identify password for [sumwonyuno]
Feb 17 18:10:37 sumwonyuno-laptop polkit-grant-helper-pam[7017]: pam_unix(polkit:auth): conversation failed
Feb 17 18:10:37 sumwonyuno-laptop polkit-grant-helper-pam[7017]: pam_unix(polkit:auth): auth could not identify password for [sumwonyuno]


```

If anyone else has this problem, and/or can help, thanks!

---

### Post by theDaveTheRave on 2009-02-18
My first suggestion was going to be related to a caps lock problem, but you seem to have covered that one!!

[quote]
If I enter my password in the opposite case (e.g. uppercase), it doesn't say invalid password w/ sudo, then if I enter the password in the correct case, it works.
[quote]

does this only occur when you are opening things like synaptic? or does it occur at the command line too?? for example have you tried

```

davem@Dartagnon:~$ sudo su

```

which gives me the root prompt...

```

[sudo] password for davem: 
root@Dartagnon:/home/davem# 

```

David

---

### Post by sumwonyuno on 2009-02-18
Thanks for responding.  Yeah, everything I've tried w/ sudo and with admin passwords just don't work as designed anymore.

Here's me trying sudo su:

```

sumwonyuno@sumwonyuno-laptop:~$ sudo su
[sudo] password for sumwonyuno: 
Sorry, try again.
[sudo] password for sumwonyuno: 
[sudo] password for sumwonyuno: 
root@sumwonyuno-laptop:/home/sumwonyuno# 

```

That first attempt was with the "correct" password.  Second attempt I switched the case, then third attempt with correct password, and I have root.

---

### Post by drs305 on 2009-02-18
There was an intrepid update for *sudo* yesterday. Have you tried to reinstall it?
The current version is  1.6.9p17-1ubuntu2  (apt-cache show sudo | grep Version)

---

### Post by sumwonyuno on 2009-02-19
Yeah, I saw that update yesterday too, I installed it, and the problem is still there.

Though there are two packages:
```

sumwonyuno@sumwonyuno-laptop:~$ apt-cache show sudo | grep Version
Version: 1.6.9p17-1ubuntu2.1
Version: 1.6.9p17-1ubuntu2

```

---

### Post by theDaveTheRave on 2009-02-19
have you tried comparing the var/log/syslog and dmesg both before entering the password for the first time, and then after switching case twice??
just too see if there is anything.

Have you been able to try another Kernel? to replicate?? sound like this is one for the Bug Jam on Sunday! ;)

David

---

### Post by Keith Yanachik on 2009-02-19
I'm having the same problem after the sudo update.  Has anyone resolved this issue yet?

---

### Post by sumwonyuno on 2009-02-19
Well, I've gotten into the habit of purging all the old kernels, roughly after two weeks installing a kernel that hasn't caused me any problems by then.  So no, I don't have any other kernels to try at the moment.

_Looking at the logs while trying sudo:_

**dmesg:**
- the control (before trying sudo):
```

[  456.000240] wlan1: no IPv6 routers present

```
- results (after 3 failed password attempts): no new messages

**syslog:**
- control:
```

Feb 19 16:20:01 sumwonyuno-laptop /USR/SBIN/CRON[8470]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

```
- results: no new messages

the only log that had been updated was **auth.log**:
- control:
```

Feb 19 16:20:01 sumwonyuno-laptop CRON[8464]: PAM (cron) illegal module type: auto
Feb 19 16:20:01 sumwonyuno-laptop CRON[8464]: PAM (other) illegal module type: auto
Feb 19 16:20:01 sumwonyuno-laptop CRON[8464]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 19 16:20:02 sumwonyuno-laptop CRON[8464]: pam_unix(cron:session): session closed for user root

```

these 4 lines were repeating for the past hour or so, and I wasn't doing anything w/ sudo or user passwords.

- results:
```

Feb 19 16:20:03 sumwonyuno-laptop sudo: PAM (sudo) illegal module type: auto
Feb 19 16:20:03 sumwonyuno-laptop sudo: PAM (other) illegal module type: auto
Feb 19 16:20:10 sumwonyuno-laptop sudo: pam_unix(sudo:auth): authentication failure; logname=sumwonyuno uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=sumwonyuno
Feb 19 16:20:25 sumwonyuno-laptop sudo: sumwonyuno : 3 incorrect password attempts ; TTY=pts/0 ; PWD=/home/sumwonyuno ; USER=root ; COMMAND=/bin/su
Feb 19 16:20:27 sumwonyuno-laptop sudo: PAM (sudo) illegal module type: auto
Feb 19 16:20:27 sumwonyuno-laptop sudo: PAM (other) illegal module type: auto
Feb 19 16:20:40 sumwonyuno-laptop sudo: sumwonyuno : 3 incorrect password attempts ; TTY=pts/0 ; PWD=/home/sumwonyuno ; USER=root ; COMMAND=/bin/su
Feb 19 16:26:33 sumwonyuno-laptop sudo: PAM (sudo) illegal module type: auto
Feb 19 16:26:33 sumwonyuno-laptop sudo: PAM (other) illegal module type: auto
Feb 19 16:26:47 sumwonyuno-laptop sudo: sumwonyuno : 3 incorrect password attempts ; TTY=pts/0 ; PWD=/home/sumwonyuno ; USER=root ; COMMAND=/usr/bin/nautilus

```

Thanks **Keith Yanachik** for confirming you have the problem too.  I think it's still a fairly new problem (a couple days after their results).  There may be something unique and common to both of our situations, and this may be why there's hasn't been an outpour of complaints yet.

---

### Post by Keith Yanachik on 2009-02-20
I have Likewise Open installed, which lets me authenticate against Active Directory for network access.  My local Ubuntu username and password do not work, but my cached Active Directory username and password do work.  I never added my AD user to sudoers so I can't test if I have local sudo access with this user.

---

### Post by theDaveTheRave on 2009-02-22
Hello again.

Bug jamming today, and I came across this [bug]("https://bugs.edge.launchpad.net/ubuntu/+bug/292161")

This is affecting a "french" style keyboard? do you have "mutliple" keyboard instaled by any chance??

Do you think you could check your settings during this issue to see if maybe it is somehow related. I have put a cross reference there just in case.

David

---

### Post by sumwonyuno on 2009-02-23
Nope, I don't have Likewise Open installed.

But, yes, I have selected another keyboard (USA International (AltGr dead keys)).  I haven't thought of that being a possible cause since I had changed from the default US Keyboard months ago.

---

### Post by theDaveTheRave on 2009-02-26
sumwonyuno

I need to test this at some point on my works system, it has 2 keyboards attached to it....

Do you have access to another system that only has a single keyboard ever installed into it?

I know that the install of ubuntu automatically detects the keyboard as the first thing it does - I wonder how it reacts when it has 2 connected at install time!?

I know that mine allways asks me to enter my password with the french keyboard layout.... which has confused me once or twice when I've been in a "rush" :lolflag:


David.

---

### Post by sumwonyuno on 2009-02-27
I do have my laptop (with the sudo problem) and a desktop with a PS-2 Keyboard.  So, no, I can't test out two keyboards at a time.  But there might be threads out there about the precedence of the keyboards (which might be why Ubuntu asks for passwords on the French one).

Anyways, for the past few days I've been trying to fix another issue that has prevented me from working @ the sudo password problem.  I can't get into Ubuntu at all.  As I only have one kernel atm, in either normal or recovery mode, there is a kernel panic after the grub screen.  The verbose in recovery mode freezes after saying something about:
- RAMDISK complaining about an invalid compressed format (err=0), 
- then VFS not able to open up the root partition,
- then it asks for a correct partition w/ no "available partitions" following the message
- finally VFS not able to mount root fs...

From the online searches I've done, this problem only seems to occur with installing or upgrading, neither of which I was doing.  I've checked the appropriate files and everything seems fine (deja vu from the sudo problem).

It just seems to all be converging onto reinstalling Ubuntu.  But, I would prefer to not to, because of the time it would take to install, upgrade, update, then reconfigure.  I have a few more things I'd like to try (some tricks w/ the LiveCD), but I have to see how fixing Ubuntu, along with other priorities, will all balance out this weekend.

---

### Post by sumwonyuno on 2009-02-28
Update:

I've fixed the problem I had with booting into Ubuntu; I was able to reinstall the 2.6.27-11-generic kernel w/ chroot while using a LiveCD.

I have switched keyboard layouts (between default US, and US Intl w/ AltGr dead keys), no effect.

---

### Post by sumwonyuno on 2009-03-05
So, in the past few days I've tried some more things.

I had upgraded to 2.7.27-13-generic, no effect.

While I was upgrading to Jaunty Alpha 5, update-manager asked about replacing /etc/login.defs , which I did, and yes, no effect. :(

---

### Post by theDaveTheRave on 2009-03-10
Hi guys.

sorry for the slow reply, I never got around to testing this fully.

however yesterday I updgraded from Hardy to Intrepid on my works laptop, and something very strange just happened.

I was working on my laptop, and then went back to my desktop, which had dropped to the screen saver, it asked for my password (which is what it should do) but then didn't accept it! I tried everything, using the english or the french keyboard made no difference.

Eventually I hit the "switch user" button, and the system drops back to the "normal" log in screen - this defaults to a french keyboard layout.

I enter my user name and password, and hey presto I'm logged in....

I then sent a couple of commands to the terminal via sudo, and guess what, no functionality - so I now can't perform any updates I guess!

This is going to be a real disaster.

I'm going to report this on the launchpad page for the other bug I linked to previously.

Have you had any luck in finding a solution?
David

---

### Post by sumwonyuno on 2009-03-11
I think I have fixed my problem with my password not being accepted with sudo or gksu.

I've been wondering why there were PAM illegal module type: auto messages every so often in the auth.log file.  So, I looked in /etc/pam.d and looked through all the files for the word "auto".  I found this in the file common-auth:

```

#auth	required			pam_permit.so
auto	optional			pam_smbpass.so migrate missingok

```

The other "auth"'s in the file were uncommented.  So I changed the two lines to the following:

```

auth	required			pam_permit.so
#auto	optional			pam_smbpass.so migrate missingok

```

Since PAM is suppose to update instantly, I went out to find something to test.  I had already typed sudo to do gedit /etc/pam.d/common-auth, so many things wouldn't ask for my password (due to that 5 minute auto-sudo behavior).  I went for Users and Groups > Unlock.  I typed my password and it accepted.  With my problem I had to type sudo [program name] to access anything (e.g. Synaptic) that needed my password, as of now that isn't necessary.

Added:  I've rebooted and password behaviors for sudo and gksu are normal again.

---

