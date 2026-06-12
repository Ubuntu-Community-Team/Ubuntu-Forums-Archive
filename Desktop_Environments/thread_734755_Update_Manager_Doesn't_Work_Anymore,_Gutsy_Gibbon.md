---
title: "Update Manager Doesn't Work Anymore, Gutsy Gibbon"
date: 2008-03-25
forum: Desktop Environments
---

### Post by cherylholmes on 2008-03-25
Suddenly the Update Manager has stopped working without giving any warnings or error messages.

It tells me there are 18 updates available, then I "check updates"  then "install" and it just keep going in a loop to check for updates again, never getting beyond the "checking for updates."

Can anyone please help me get this thing going again?

Thank you very much! cheryl

---

### Post by Oldsoldier2003 on 2008-03-25
> **cherylholmes said:**
> Suddenly the Update Manager has stopped working without giving any warnings or error messages.

It tells me there are 18 updates available, then I "check updates"  then "install" and it just keep going in a loop to check for updates again, never getting beyond the "checking for updates."

Can anyone please help me get this thing going again?

Thank you very much! cheryl

have you tried
```
killall update-manager
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by strongsad on 2008-04-05
Yeah I'm having this same problem.  I did the sudo killall and it closed.  I then tried to do the sudo apt-get update but i get W:Not using loking for read only lock file /var/lib/apt/lists/lock
E: Unable to write to /var/cache/apt/
E: the package lists or status file could not be parsed or opened

I tried the other command as well but i get the same error

---

### Post by twist2b on 2008-04-05
I had this error once. sad thing is you cant remove something like this and re-install :P atleast what i know of. I got fed up and re-installed the OS....... never got the error again. Though I think it prob something basic, go to sinaptic and see if messing with some settings wont fix it (after you open it, click on prefrences or edit or something then click on repositories.)

---

### Post by warp99 on 2008-04-05
> **strongsad said:**
> Yeah I'm having this same problem.  I did the sudo killall and it closed.  I then tried to do the sudo apt-get update but i get W:Not using loking for read only lock file /var/lib/apt/lists/lock
E: Unable to write to /var/cache/apt/
E: the package lists or status file could not be parsed or opened

I tried the other command as well but i get the same error

The permissions on the lock file are incorrect. Issue the following command:

```
sudo chmod 650 /var/lib/apt/lists/lock
```

then apt-get update then upgrade. If that does not work something is wrong with sudo since you're not getting privileges elevated to root.

---

### Post by strongsad on 2008-04-06
> sudo chmod 650 /var/lib/apt/lists/lock 
That changed the permissions I was getting but since I'm working in recovery mode now because I can't get the system to boot up the other commands don't work. I will just reinstall it all again for the 5th time and then run those commands. If their is a quicker way post it up because i'm sure I'll run into this problem again probably in like an hour when it finishes install lol.

---

