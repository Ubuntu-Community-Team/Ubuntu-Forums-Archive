---
title: "username is not in the sudoers file.  This incident will be reported."
date: 2009-05-02
forum: General Help
---

### Post by joeabiraad on 2009-05-02
Now i've been running ubuntu for a while and when i turned it on this morning this is what i found out.

I;ve lost privilege to sudo and so i cannot open anything in the menu.
Yesterday all was working fine.

This is what i get when i'm trying to do smthg using sudo
```

jo@jo-desktop:~$ sudo kilall pulseaudio
[sudo] password for jo: 
jo is not in the sudoers file.  This incident will be reported.
jo@jo-desktop:~$ 

```

What did i do wrong ? and how can i fix this ? ? ? ? 

Thanks 
Jo

---

### Post by Peasantoid on 2009-05-02
Add this to /etc/sudoers:
```
you ALL=(ALL) ALL
```
Where "you" is your username.

---

### Post by eentonig on 2009-05-02
is 'jo' the original username you entered while installing ubuntu? Or is it a user you added afterwards?

Have you ever been able to use sudo with this account?

Is there another account on the machine that can use sudo?

---

### Post by joeabiraad on 2009-05-02
> **Peasantoid said:**
> Add this to /etc/sudoers:
```
you ALL=(ALL) ALL
```
Where "you" is your username.

> **eentonig said:**
> is 'jo' the original username you entered while installing ubuntu? Or is it a user you added afterwards?

Have you ever been able to use sudo with this account?

Is there another account on the machine that can use sudo?

Hi Peasantoid, 

I cannot edit /etc/sudoers

i tried 
```
visudo
```
but it tells me that i have no priv

....
eetonig, jo is the only username i used on this machine for the last 8 months and i've always been able to sudo with it. until this morning.

---

### Post by joeabiraad on 2009-05-02
Hey, 
Thank you both for your help. 
I've fixed the problem from another thread.

What i did is restart the PC and chose recovery mode from grub menu.
That made me log in as root. 

Then i wrote 
```
visudo
```

and added this line at the end of the file
```
jo ALL=(ALL) ALL
```

rebooted using
```
shutdown -r now
```

and everything now is OK :)

Thank you again,
Any idea why this could've happened  ? 
Jo

---

### Post by ed-koala on 2009-05-02
Do you by chance happen to know a practical joker who knows Linux?

---

### Post by lisati on 2009-05-02
Is this related to this:????[http://ubuntuforums.org/showthread.php?t=1145828](http://ubuntuforums.org/showthread.php?t=1145828)

---

### Post by barx on 2009-05-10
Thanx  a lot Peasantoid.

I was trying to make my SD/ Micro memory to work, I couldn't, so I look a solution by my self but doing many steps the sudo wasn't working, so I restarted in recovery mode and following that I could resolve my woe.

:guitar:

p.s. I still can't do something to unlock the read only mode of the SD memory, but the sudoer's problem is solved

---

### Post by Yellow Pasque on 2009-05-10
On a fresh install of Ubuntu 9.04, the sudoers file gives sudo permission to 'root' and any users in the 'admin' group. My guess is that you somehow removed your user from the admin group. You can check what groups your user is a member of by running this in the terminal (without sudo/root permissions):
```
groups
```

---

### Post by kurocan on 2009-10-15
help me please i need you > nurul@localhost:~$
nurul@localhost:~$ sudo su
nurul is not in the sudoers file.  This incident will be reported.
nurul@localhost:~$ /etc/
bash: /etc/: is a directory
nurul@localhost:~$ sudo su
nurul is not in the sudoers file.  This incident will be reported.
nurul@localhost:~$


whay...?

---

### Post by Carl Hamlin on 2009-10-15
> **kurocan said:**
> 
nurul@localhost:~$
nurul@localhost:~$ sudo su
nurul is not in the sudoers file. This incident will be reported.


OK, what this is telling you is that your user credentials don't include admin-level privileges. If you're logging on to someone else's computer, or are connected to a public system, this is unsurprising, and should be expected. If this is your own system, and the credentials you're using are the ones you entered when you performed the linux installation, then you've got a problem.

> **kurocan said:**
> 
nurul@localhost:~$ /etc/
bash: /etc/: is a directory


I'm not sure what you were trying to do here, but I'll hazard a guess that you were trying to get to /etc/sudoers to add your name to the list. Changing directories in linux incorporates the following syntax:

```

cd /etc/

```

However, modification of /etc/sudoers requires that you be logged in with user credentials to whom have been granted admin-level privileges. You won't be able to do it with these credentials.

> **kurocan said:**
> 
nurul@localhost:~$ sudo su
nurul is not in the sudoers file. This incident will be reported.
nurul@localhost:~$


Here again, it's telling you that your current user credentials don't have admin privileges. This is only a problem if it's your own system, and you're logged in with the user credentials you entered during installation.

If that's the case, I recommend replicating joeabiraad's solution - it seems to have resolved the  problem.

---

### Post by SagnaB on 2010-02-16
Ok I think I my have just screwed things up...
I wanted the CPU frequency scaling monitor (2.28.0) to not ask for password every single time i changed it from 600MHz to 1.70 GHz. So I googled a bit and found a site that said adding to the sudoers file:
```

$ sudo cpufreq-set -g Performance

```would fix this.

So, I opened a terminal and entered:
```

sudo visudo

```to open the sudoers file. This was successful as it displayed the sudoers files contents in the terminal.
I then proceded to enter ```
$ sudo cpufreq-set -g Performance
```then i typed exit and it prompted me to save the file as sudoers.tmp. I did not save it as that as I believed that would not work. I saved over the existig sudoers file by saving it just as ´sudoers´. Hit return, and it exited.

I then wanted to check to see if the changes did indeed happen and reopened the sudoers file with
```
sudo visudo
```And now it says:
```

>>> /etc/sudoers: syntax error near line 26 <<<
sudo: parse error in /etc/sudoers near line 26
sudo: no valid sudoers sources found, quitting

```If i reboot, will this cause me the gigantic problem I am anticipating? What on Earth can I do now?

---

### Post by litster on 2010-12-22
Just as a side note, I had the same issue.  I fixed it through the graphical interface.  Somehow, I managed to remove my user from the "sudo" group.

To test, I open a terminal and type:
```
sudo bash
[sudo] password for myuser: 
myuser is not in the sudoers file.  This incident will be reported.
```


So, I go to:
System Menu->Administration->Users and Groups

Click "manage groups"
Scroll down to "sudo", click "properties"

Under "Group Members", my username had no checkbox.

So I checked the box to re-add myself to the sudo group, it popped up the "admin privileges needed" box.  For some reason my GUI admin privileges still worked.

Back to the terminal to test:
```
sudo bash
[sudo] password for myuser: 
root@host:~# 
```

That worked a treat!  However, note that I had previously set up a root password for my machine.  If you can't do anything with admin privileges, maybe you should boot your machine in "single user mode" and set the root password.  Google it.

Well, third edit.  Truly a shotgun approach.  I just checked a normal user on a default ubuntu server install and discovered that that user isn't a member of the "sudo" group, but the "admin" group.  Notice that my /etc/sudoers file should work for if a user is added to either the "admin" group OR the "sudo" group as described above.    

BTW Yes, I know the thread is dead.  However, it is ranked highly in Google and the visudo business is "voodoo magic" for normal users that may have nothing to do with the problem.  Min wasn't:

```

sudo visudo
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

