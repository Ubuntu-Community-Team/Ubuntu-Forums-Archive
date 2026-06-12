---
title: "Suddenly, I can't log in to Kubuntu"
date: 2007-06-07
forum: Desktop Environments
---

### Post by Drenhead on 2007-06-07
I have had Kubuntu installed for a few months with no problems, but now all of a sudden, it won't let me log in.  I haven't installed anything or change any files that I know of that would keep it from being able to log in.

The Kubuntu login screen comes up with my userid already populated.  When I type in my password, it goes to a blank screen, then after a few seconds, it goes back to the login screen.

Does anyone have any suggestions on how to login to my system?

Thanks in advance.

---

### Post by reckless2k2 on 2007-06-07
I had something similar happen to me not too long ago. Boot into recovery mode and the chown your home directory to whatever your username is. make sure to make it recusive throughout everything in your home directoy. "YOUR" HOME DIRECTORY. then try to reboot and login. see if that helps.

---

### Post by scrooge_74 on 2007-06-07
You could have run out of space in the disk also and need to clean up

---

### Post by taurus on 2007-06-07
Press <Ctrl><Alt>F2 and log in with your name and password.  Then, post the output of these two commands here.

```
df -h
ls -la /home
```

---

### Post by Drenhead on 2007-06-07
I ran df -h and it looks like my / directory is full.  I deleted a few files, and was able to log back in.  Now, I have to figure out what to delete!!

Thanks for all your help.

---

### Post by taurus on 2007-06-07
You can clean out the archives with

```
sudo aptitude clean
```

---

### Post by sheepscrossing@yahoo.com on 2008-04-02
I just upgraded to Kubuntu and I'm having the same issue.  I have plenty of disk space, I have chowned my home directory and ran the "sudo aptitude clean (which decreased my % used to 6%)" all to no avail. What can I do to get logged in? I also noticed that I have a strange user listed now and I haven't a clue what the password is for it.  The user is Sabayon-Admin.  Any help would be greatly appreciated.

---

