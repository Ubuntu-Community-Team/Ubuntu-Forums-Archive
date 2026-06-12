---
title: "ubuntu idiot"
date: 2009-06-15
forum: General Help
---

### Post by stuarab on 2009-06-15
hello

i have made a stupid mistake on my ubuntu box and hope someone here can help me resolve it.

i use the box as an FTP\Web server - i intended to reset the permissions on a specific folder but i typed the wrong command.  in the folder i typed chmod 777 -R /*  thereby resetting the ownership of all files to 777, instead of setting permissions to 777 in the specific folder.  i realised my mistake as the process was under way and i CTRL-C out but now i cannot access the terminal as i dont have permissions.  i am now very nervous that apps will stop.  any ideas how i can change the ownership of these files?   

i inherited the box from a colleague.

any assistance would be much appreciated.

stu

---

### Post by munky99999 on 2009-06-15
777 should be giving full permissions to everyone. which is a bit of a security issue but shouldnt be giving any problems in terms of access for yourself. Unless I'm mistken? 

The easiest method most likely will be to simply restart fresh. If you were to login as root to get full access you may just further damage the security and cause more troubles.

---

### Post by stuarab on 2009-06-15
i changed the ownership to 777, not the permissions...

---

### Post by sanderd17 on 2009-06-15
I think the ownership has to be set with "chown" and not with "chmod", you have set the file permissions.

---

### Post by jonobr on 2009-06-15
Hello

You change ownership by using the chown command,

```

jonobr@munster:~$ touch file
jonobr@munster:~$ ls -l file
-rw-r--r-- 1 jonobr jonobr 112 2009-06-15 12:08 file
jonobr@munster:~$ sudo chown root:root file 
jonobr@munster:~$ ls -l file
-rw-r--r-- 1 root root 112 2009-06-15 12:08 file


```

you change permissions with chmod

```

jonobr@munster:~$ sudo chmod 777 file
jonobr@munster:~$ ls -l file
-rwxrwxrwx 1 root root 112 2009-06-15 12:08 file
jonobr@munster:~$ 

```


I agree with munky99999 that you dont know whats happened, a reinstall may be the best option.

---

### Post by DGortze380 on 2009-06-15
The simplest solution, honestly, is to reinstall. 

You should be able to use the system. What the command essential has done is given the owner, group, and everyone else read, write and execute privileges to every file on the system.

Finding and resetting the permissions for each individual file would likely be more time and energy than it's worth.

---

### Post by synapsys on 2009-06-15
Re-install....

Next time, be more careful with wildcards. Especially when root.

You're not an idiot. We all make mistakes. This is how we learn.

---

### Post by ZackM on 2009-06-15
Yeah... I've done something very similar... I made everything on the system unreadable by accident... I had to reformat... Lol

---

### Post by andersbk on 2009-06-15
> **stuarab said:**
> hello

i have made a stupid mistake on my ubuntu box and hope someone here can help me resolve it.

i use the box as an FTP\Web server - i intended to reset the permissions on a specific folder but i typed the wrong command.  in the folder i typed chmod 777 -R /*  thereby resetting the ownership of all files to 777, instead of setting permissions to 777 in the specific folder.  i realised my mistake as the process was under way and i CTRL-C out but now i cannot access the terminal as i dont have permissions.  i am now very nervous that apps will stop.  any ideas how i can change the ownership of these files?   

i inherited the box from a colleague.

any assistance would be much appreciated.

stu

[SIZE="5"]**unix (not ubuntu) commands wield great power!**[/SIZE]

FWIW, here are the commands I use the change permissions recursively for files and directories.

Oh, and a quick note. Never, ever do any command with recursion on the root, "/" directory.

**To "chmod" on directories only:**
```

cd /path/to/top/directory/needing/permission/changes

find . -type d | xargs chmod 755

# or

find . -type d -exec chmod 755 {} \;

```

**To "chmod" on files only:**
```

cd /path/to/top/directory/needing/permission/changes

find . -type f | xargs chmod 644

# or

find . -type f -exec chmod 644 {} \;

```

Change the mask flags as needed.

So...

Best case scenario, you might be able to use the above command to get everything that's a dir to 755, and everything that's a file to 644. However, when you run a command recursively on root, or "/", you also change the dev files, and try to change stuff in /proc. Not good. However, a reboot might bring the devs back to default perms since most are handled by udev, etc.

Worst case scenario you need to re-install the OS.

good luck!
.

---

### Post by QIII on 2009-06-15
That's not idiotic.

Idiotic is when you put a new drive on your wife's machine, unplug the SATA cable on her windows drive to make sure you don't install Ubuntu over it, don't bother to look at the menu when you press "Use entire disk" and realize later that you had unplugged the disk you intended to put Ubuntu on -- and have just installed Ubuntu on her Windows drive.

Thank <insert deity of choice here> for frequent backups.

---

### Post by stuarab on 2009-06-15
okay i have doublechecked i have definitely changed the ownership of all files to 777.  when i view a file\folder through the GUI i see owner 777, group username, others blank. i am not the owner so i cant change these permissions.  i need to change these back to root or username... this box is my company ftp\web site... a reinstall is going to be problematic, but more than likely i fear there will be no other way...
doh.

---

### Post by DGortze380 on 2009-06-15
> **stuarab said:**
> okay i have doublechecked i have definitely changed the ownership of all files to 777.  when i view a file\folder through the GUI i see owner 777, group username, others blank. i am not the owner so i cant change these permissions.  i need to change these back to root or username... this box is my company ftp\web site... a reinstall is going to be problematic, but more than likely i fear there will be no other way...
doh.

First read this over: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Then decide.

Option 1) Reinstall

Option 2) Google the default permissions for every file and directory. Change them back to what they need to be using the command: sudo chmod xxx /path/to/file

My Recommendation: Option 1.

---

### Post by Wicca on 2009-06-15
Before re-installing:

As I understand you have mistaken chmod with chown.

Now you have set the ownership of some files to '777' which is a non-existing user. You (root?) lost the ownership and therefore you can't make any file permission changes.

Were you root or were you a sudoer using sudo at that point?

You did not change the group permissions so I guess root still has rights.

Try:
```
(sudo) chown -R root /*
``` 

If that doesn't change anything consider adding a user '777' with root rights, then log in as user '777' and change the ownership back to root. If you don't know how: let me know.

---

### Post by synapsys on 2009-06-15
With great power comes great responsibility.

---

### Post by munky99999 on 2009-06-15
> **QIII said:**
> That's not idiotic.

Idiotic is when you put a new drive on your wife's machine, unplug the SATA cable on her windows drive to make sure you don't install Ubuntu over it, don't bother to look at the menu when you press "Use entire disk" and realize later that you had unplugged the disk you intended to put Ubuntu on -- and have just installed Ubuntu on her Windows drive.

Thank <insert deity of choice here> for frequent backups.
Hahahaha


but ya. Dont worry about making syntax errors. They happen. Infact I count about 3 major ones so far today. One good one from today I did.

Ok so basically Im running ubuntu in an active directory. I'm not integrating. So anyway I'm messing around in the commandline and I accidentally sent a command to basically change all files to .bat files as opposed to just the one policy file. Entire comp basically became bat files.

---

