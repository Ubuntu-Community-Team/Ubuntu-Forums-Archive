---
title: "Severe Login Errors (/home user)"
date: 2006-09-12
forum: Desktop Environments
---

### Post by wuZheng on 2006-09-12
Hello, I'm new to Linux, and yea, new to this community too, and I've already screwed up my Ubuntu installation, I need help.

Background Information:
- Just finished installing Lexmark Z55 driver via instructions found in a HOWTO thread in this forum...
- Rebooted to see the below messages...
- Can now only log in using root, /home user disabled... (using root to post this)

Problem:
- Can't log in under any settings, default, last session, or failsafes...

Error Boxes from Default Login Session:
> Your session lasted less than 10 Seconds. If you have not logged out yourself this could mean that there is some installation problem or that you may be out of diskspace. Try loggin in with one of the failsafe sessions to see if you can fix this problem.

and under the detailed error explanation of that box...
/etc/gdm/PreSession/Default: registering your ession with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w ./var/log/wtmp -u /var/run/utmp -x "var/lib/gdm/:20, Xservers" -h " -l";20" "james"
/etc/gdm/XSession: Beginning session setup...
mdktemp: private socket dir: Permission denied

...and that was after logging into root and changing the permissions on the /home/usernamehere directory to make sure it was only accessible to that particular user... I changed it once to allow all permissions using root, but that caused some problems so I changed it back, and then back again, both yielding the same result, can't log in to this user's account...

Now, this is trying to use GNOME's failsafe session:
> Failed to create file 'tmp/gconf-test-locking-file-udj90': Permission denied" (ermo = 2)

Common problem I've been noticing throughout though, there seems to be inadequate permissions somewhere.... and yea, I'm new to Linux and played around to my consequence, and now I'm stuck so any help would be GREATLY appreciated...(would like to get back to school work soon...)

---

### Post by wuZheng on 2006-09-12
*bump*

---

### Post by new2lnx on 2006-09-13
i have the same problem.  just lately i tried to log in as a user other than the first user that i created upon installation and i was prompted that /home/nameofuser does not exist even if it does exist.

i thought this might be related to my moving the home directory to a separate partition, and so i deleted the only user aside from the first user then created a new one.  i logged out and then tried to log in using the newly created user but again i was prompted that /home/nameofnewuser does not exist even if verification showed that the directory is there.  what has gone wrong?

i appreciate receiving help on this.

---

### Post by wuZheng on 2006-09-14
*bumpity bump bump*

---

### Post by wuZheng on 2006-09-15
*bumpity bump bump over the hills we go*

Yea, help would be greatly appreciated in response to first post. Or a kind re-direct if something similar was already posted. kthx.

---

### Post by wuZheng on 2006-09-20
*big bump* *impatient bump* *THIRD bump*

---

### Post by frodon on 2006-09-20
This sounds like a bad permission problem.

I would check the rights of the /tmp directory, give him 777 rights : ```
sudo chmod 777 /tmp
```

---

### Post by new2lnx on 2006-09-21
> **frodon said:**
> This sounds like a bad permission problem.

I would check the rights of the /tmp directory, give him 777 rights : ```
sudo chmod 777 /tmp
```

Thanks for the suggestion, but it didn't help.

Hoping pictures might reveal the problem, I attached screenshots of the error messages that appeared when i tried to login (*yes, ok, continue, close* in that order were selected in response to the prompts).

---

### Post by qhaz on 2007-01-31
Hi, I'm getting the same error as yourself and have been unable to find a solution yet.  I was wondering if you were able to ever find a solution?  Wanna share what you learnt?

thanks

---

