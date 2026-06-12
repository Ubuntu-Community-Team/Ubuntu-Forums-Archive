---
title: "I installed compiz on my account named daniel. It messed up so i logged out and logge"
date: 2007-07-18
forum: Desktop Environments
---

### Post by sent17inel on 2007-07-18
I installed compiz on my account named daniel. It messed up so i logged out and logged in as root... i deleted the account daniel but not before i copied all my files to the root account... then from there i made an account named sentinel and while still in root i copied all the files into my sentinel account.... WHen i logged in as sentinel i noticed that all the file permissions wouldnt allow me to open any of my files so i opend nautilus as root and changed all the file permissions to delete create blah blah blah... basically i made it so i can open them delete them pretty much wutever i want... but then when i restarted the comp and then log in as root i get this small little pop up immediatley after typing in my password and pressing enter... it goes something like this....

```
User $home/.dmrc file is being ignored. File should be owned by user and have 644 permissions.
```
Your thoughts?

---

### Post by dougfractal on 2007-07-18
When you used nautilus did you view hidden files?

The old commandline way.
[ctl]+[alt]=[f1]
login as user
sudo chown -R username:username /home/username

will change owner for the whole directory tree.

---

### Post by sent17inel on 2007-07-18
Im confused i dont understand what you want me to type... Can u plz write code for me? Im confused and still new to linux... The files used to be owned by daniel. So if the are under sentinel now then what should i type ?

---

### Post by sent17inel on 2007-07-18
And which user should i login as? Im getting the problem when i login as sentinel.. and daniel account has been deleted already...

---

### Post by dougfractal on 2007-07-19
At login screen

press [ctl]+[alt]+[f1] to goto console
login as sentinel
type 
```
sudo chown -R sentinel:sentinel /home/sentinel
```

will change owner for the whole directory tree.


```
ls -la .dmrc 
```
if file not found
```
touch .dmrc 
```

and then do
```
chmod 644 .dmrc 
```


press [ctl]+[alt]+[f7]   to goto graphical

---

### Post by sent17inel on 2007-07-20
It looked like everything was going perfectly but when i went back to the graphical login to login i still got the pop up... I even rebooted just to be sure that the problem wasnt resolved.... If we deleted the file would my computer create a new one? And what exactly does that file do?

---

### Post by sent17inel on 2007-07-20
HAHAHAHAHA wow.... what u told me to do did what it was supposed to do cuz u fixed some permissions problems i was having in Cedega... i was always having to run sudo cedega but now i can just click the link in my applications tab so thanks for that!!!! thats awesome!!! now we just gotta get that pop up gone....

---

### Post by dougfractal on 2007-07-20
Could you show the "ls -la .dmrc"    --- long list of all files.

my .dmrc is set to ```
chmod 600 .dmrc
``` so try that

How did you get to login in as root? ubuntu nomally disallows this as it is too easy to break you system as root.

```
sudo -s
```   to run a root shell.

---

