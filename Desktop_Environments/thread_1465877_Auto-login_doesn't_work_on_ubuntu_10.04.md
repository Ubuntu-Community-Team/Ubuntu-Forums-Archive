---
title: "Auto-login doesn't work on ubuntu 10.04"
date: 2010-04-29
forum: Desktop Environments
---

### Post by latebeat on 2010-04-29
Hello guys,
I just finished installing ubuntu 10.04 and I'm really impressed!
Anyways, I wanna do some startup benchmarks with various file systems and I'm trying to enable the auto login in gdm. However it doesn't work for me.
I'm attaching a screenshot from the gnome-login settings. When I chose "login-as" there's no drop down list with my username to chose a person to auto logon.
Any ideas?

thanks

---

### Post by gnimsh on 2010-04-30
Bump. Same problem.

---

### Post by latebeat on 2010-05-01
> **gnimsh said:**
> Bump. Same problem.

actually after doing some research I found out that it's a bug. Try googling "no seat-id found" and you will see.
However I still haven't found a workaround 

Try running:

```
gksu /usr/bin/gdmsetup

** (gdmsetup:2181): DEBUG: init delay=30
** (gdmsetup:2181): DEBUG: "/usr/share/xsessions/une-efl-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:2181): DEBUG: "/usr/share/xsessions/une-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:2181): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:2181): DEBUG: Init default session found:'gnome'
** (gdmsetup:2181): DEBUG: Failed to identify the current session: Unable to lookup session information for process '2181'
** (gdmsetup:2181): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:2181): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:2181): DEBUG: adding monitor for '/home/username/.face'
** (gdmsetup:2181): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:2181): DEBUG: Found 1 sessions for user username
** (gdmsetup:2181): DEBUG: GdmUserManager: not adding session on other seat: /org/freedesktop/ConsoleKit/Session2
** (gdmsetup:2181): WARNING **: Unable to find users: no seat-id found
```

---

### Post by gnimsh on 2010-05-01
It's not really a huge issue for me, I also just wanted to test the speed.  A few weeks ago I was racing a coworker to find a song to play. I booted cold and logged in while her XP was still comingout of hibernation, but she had the song on her laptop and I had to get it from youtube. I would've beaten her otherwise!

---

### Post by kalyp on 2010-05-14
Is it really a lucid issue? I had the same problem in karmic too. And find it pretty annoying myself so if someone ever finds a workaround I'm interested :)
Thanks!

---

### Post by rejven on 2010-05-15
doesnt work for me either :( its not a big problem just annoying cos i know it doesnt work :P

---

### Post by rudeboyskunk on 2010-06-05
I'm having the same problem.  Does it have anything to do with the fact that when I installed Ubuntu I made it where I have to login and use pswd to decrypt my home folder, or are people who chose regular login having the same problem?

---

### Post by MrMistr on 2010-06-06
I have the same problem.

When I created a second user, the problem went away. (This might be a work-around, but not a fix).

---

### Post by latebeat on 2010-06-06
> **rudeboyskunk said:**
> I'm having the same problem.  Does it have anything to do with the fact that when I installed Ubuntu I made it where I have to login and use pswd to decrypt my home folder, or are people who chose regular login having the same problem?

well, whenever I installed with an encrypted home folder I'd always get this problem. Normal install didn't have this though

---

### Post by dewsworld on 2010-06-07
Same problem here...

---

### Post by MrMistr on 2010-06-07
That's not a bug, that's a feature. 

The actual bug is, that you are - in some circumstances - able to select a user with encrypted home dir for auto-login... and mayhem ensues.

The whole point of encrypting your home directory is that you - the user - have to know the pass-phrase in order to decrypt it.

The operating system does not know your pass-phrase. It calculates a hash and checks this hash against the hash in its database.  If they match, it lets you in.

The auto-login feature lets you in without asking the password.

Without knowing the password however, all files are still encrypted (including all config files in the dot-subdirectories) and all kind of nasty error messages appear.

If you are in this situation, press Ctrl-Alt-F1 to go to terminal mode, login, and 

```
sudo nano /etc/gdm/custom.conf
```

set

[FONT=Courier New]AutomaticLoginEnable=false[/FONT]

save and 

```
sudo reboot
```

The actual bug:

After a fresh install of 10.04, with encrypted home directory, the auto-login selection box is empty.
After adding a second user also with an encrypted home directory, the selection box is populated with the name of the second user.
You can select the second user. After a reboot, you are in the situation described above.

---

### Post by gabak on 2010-06-07
did anyone report that bug??

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by MrMistr on 2010-06-07
> **gabak said:**
> did anyone report that bug??

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Launchpad is very sluggish at the moment - I'll check later today.

---

### Post by MrMistr on 2010-06-07
A similar bug WAS reported:

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/353446](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/353446)

I've updated the bug report.

---

### Post by latebeat on 2010-06-07
> **MrMistr said:**
> That's not a bug, that's a feature. 

The actual bug is, that you are - in some circumstances - able to select a user with encrypted home dir for auto-login... and mayhem ensues.

The whole point of encrypting your home directory is that you - the user - have to know the pass-phrase in order to decrypt it.

The operating system does not know your pass-phrase. It calculates a hash and checks this hash against the hash in its database.  If they match, it lets you in.

The auto-login feature lets you in without asking the password.

Without knowing the password however, all files are still encrypted (including all config files in the dot-subdirectories) and all kind of nasty error messages appear.

If you are in this situation, press Ctrl-Alt-F1 to go to terminal mode, login, and 

```
sudo nano /etc/gdm/custom.conf
```

set

[FONT=Courier New]AutomaticLoginEnable=false[/FONT]

save and 

```
sudo reboot
```

The actual bug:

After a fresh install of 10.04, with encrypted home directory, the auto-login selection box is empty.
After adding a second user also with an encrypted home directory, the selection box is populated with the name of the second user.
You can select the second user. After a reboot, you are in the situation described above.

wow... thanks for letting us know :) I guess i was lucky then

---

### Post by werzy33 on 2010-11-10
While this prevents a larger problem from occurring, it is still a bug.  The "Log in as" list should indicate that users with encrypted home directories will not be shown; in addition it should show the users who are in this situation.  As an advanced user, I wasted entirely too much time searching to find the answer to why I could not select my user in the drop down list.  Linux as a desktop will never be adopted by the masses if so much effort is required to fix a simple issue.   I am using Ubuntu 10.10, and there should be some disclaimer by now.

---

### Post by kalyp on 2010-11-10
So is there any way to enable auto-login and avoid this bigger bug? I don't care whether my home directory is encrypted or not since I'm the only one using my computer, but I don't know how to change it.
Thanks in advance!

---

### Post by gabak on 2010-11-11
here you can file a bug report

[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

so they will fix it fast.
they answer pretty quick to any bug

---

