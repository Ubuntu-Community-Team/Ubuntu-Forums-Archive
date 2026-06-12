---
title: "root user directory does not exist, root password not recognised"
date: 2010-10-26
forum: Desktop Environments
---

### Post by luminex on 2010-10-26
Hi all. I no longer have access to my root desktop. On a session I attempted to change the root username but i apparently assigned it a wrong directory that does not exist. When I rebooted with my new root username, i was instead recognised as a simple user (no root privileges). I tried the console to change to "old" root but root password is not accepted and there is no way to access to sudoer files. it seems that inserting a new username requires root privileges and i am back to square one. 

Simply logging with old root username and password after restart gives me a blank screen with nothing on it and cannot even reboot. 

What can i do to regain my root access? Thanks in advance for your help!

---

### Post by wojox on 2010-10-26
[How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by luminex on 2010-10-26
ls /home 

"no such file or directory"

passwd username

"i cannot see or change the password" (console is in Italian but this is the message basically)

When typing:

user@user-laptop:~$ sudo password root
[sudo] password for user: 
user is not in the sudoers file.  This incident will be reported.

User and password are correct.

---

### Post by JoshuaRL on 2010-10-26
This is probably one of those examples why it isn't really a good idea to log in as root.  Sudo really gives you all you need as far as root access, as well as protecting the system from accidents like that.

But you should be able to reboot and at the GRUB menu pick the recovery mode to drop into a root prompt.  From there you should be able to fix whatever problems there are.

---

### Post by luminex on 2010-10-26
O.K. let's say i go to root prompt - what should i type in to replace the wrong (inexistent) directory with the correct one? Should i access the sudoer folder from grub, if so how?

---

### Post by sisco311 on 2010-10-26
Please post the output of:
```
awk -F: '{if ($3 > 999) print}' /etc/passwd
```
and
```
grep admin /etc/group
```

---

### Post by luminex on 2010-10-26
Can't. As I type 

awk -F: '{ 

it starts outputting some code like {.bash{history... and then stops and won't let me type anything else.

---

### Post by wojox on 2010-10-26
> **luminex said:**
> O.K. let's say i go to root prompt - what should i type in to replace the wrong (inexistent) directory with the correct one? Should i access the sudoer folder from grub, if so how?

Log into single user-mode, drop to a root prompt and type

```
passwd
```

You should see something like

```
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

```

Another approach is to edit the /etc/shadow file.

---

### Post by luminex on 2010-10-26
done already! But that won't fix the directory. Password and username exist but username is supposed to be in 

/home/root/username

which does not exist

---

### Post by sisco311 on 2010-10-26
Check /etc/passwd for your username and home directory:
```
less /etc/passwd
```
(press q to quit).

[http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/](http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)

---

### Post by luminex on 2010-10-27
The output is long and i could not take a screenshot. I successfully logged in as root user, typed in the snipped, i could not take the screenshot and post it - i think the last line was

```
gdm:x:105:113:Gnome Display Manager:/var/lib/gdm:/bin/false
```

---

### Post by aysiu on 2010-10-27
> **luminex said:**
> done already! But that won't fix the directory. Password and username exist but username is supposed to be in 

/home/root/username

which does not exist
There is no /home/root/username

If you're logged in as a non-admin or admin user (Ubuntu's default security model), your user folder is /home/username

If you've activated the root account for login (wholly unnecessary and not Ubuntu's default security model), the root user folder is just /root (not /home/root/username)

Forget about root. It's not necessary and just complicates support, since that isn't how Ubuntu is set up. If you're having trouble with *sudo*, you can fix it in recovery mode. More details here:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by luminex on 2010-10-28
I followed all your instructions and the instructions in your link (all cases) and i get the screenshot as in (2) but i do not know how to issue the orders - how to change the /home/root/user to default. I dont know how to re-rewrite the file from the prompt. :-(

---

### Post by aysiu on 2010-10-28
> **luminex said:**
> I followed all your instructions and the instructions in your link (all cases) and i get the screenshot as in (2) but i do not know how to issue the orders - how to change the /home/root/user to default. I dont know how to re-rewrite the file from the prompt. :-(
There is no /home/root/user

If you're logged in as user, it's /home/user

If you're logged in as root, it's just /root

In any case, the path the home directory has nothing to do with fixing *sudo*.

To rewrite the file from the prompt, type in ```
sudo nano -B /etc/sudoers
``` or ```
sudo nano -B /etc/group
``` and use the arrow keys and the backspace key to move around and delete stuff. When you're done, press Control-X to save.

---

### Post by luminex on 2010-11-02
I tried all commands, i went to nano and user is still a member of the admin group. The old directories and folders and users do exist. But here's what happens when i reboot. Before i log in i am presented with the following message:

> 
/root/home/user does not seem to exist. Would you like to login by using root as home directory? It is unlikely that this may work unless you boot into recovery mode

NO           YES



if i click "yes" i get a blank screen and can't reboot, as before. the keyboard is frozen. It seems that the computer boots into something that is not there and ignores the right directory - do you think this a boot problem?

---

### Post by sisco311 on 2010-11-02
Change your user's home to /home/**user**.

Create the directory (if it doesn't exist) and set the owner:
```
mkdir -p /home/**user**
chown **user**:**user** /home/**user**
```

Change the user's home:
```
sudo usermod -d /home/**user** **user**
```

Replace **user** with your login name.

---

### Post by luminex on 2010-11-02
All right. I'm in!! 

Thank you Sisco311, thank you all - terrific job. I checked the sys admin from the desktop, I have full access to the user group.

---

