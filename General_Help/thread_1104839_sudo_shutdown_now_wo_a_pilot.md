---
title: "sudo shutdown now w/o a pilot?"
date: 2009-03-24
forum: General Help
---

### Post by Kain000 on 2009-03-24
hey everyone, 

I've been designing a water cooled q6600 to run BOINC while i'm not using my computer, but it worries me not being at the helm so to speak incase of a leak somewhere or if the pump were to fail and temps would rise uncontrollably.    

I have the program sensors configured to the right temp sensors here and there on the motherboard, and the gnome sensors for viewing the current temps on the gnome panel.    there is the ablity to set a high and low temp and when the temp is reached it can be set to run a command.


Now I want my computer to shutdown if the CPU temp ever reaches 71C, an all time high, and thus the result of a cooling breakdown of some sort.


now how can I enter the command such that it will shutdown the computer without needing sudo, or at least needing me to give it a sudo password?

It oviously does me no good to have it detect a melt down and then be waiting for a password to cut the power before a hardware failure.

any suggestions?

---

### Post by ajmorris on 2009-03-25
hi there,
there are a couple of ways to do this, however, IMHO, the method you want, is to modify your sudoers file, to allow your user to use /sbin/shutdown with sudo, without needing to type a password.
So first of all, run visudo as a super user (it is very important to run visudo, and DO NOT edit /etc/sudoers manually) Then append the following line to the file:

```
Kain000 ALL = NOPASSWD: /sbin/shutdown
```

This will allow user, "Kain000" to run `sudo /sbin/shutdown`, without needing to type a password.

If there are multiple users you would like to be able to use /sbin/shutdown with sudo without the need for a password. You could use a group by appending the following line:

```
%admin ALL = NOPASSWD: /sbin/shutdown
```

Where 'admin' is the admin group, but can be whatever group you would like to use.

Enjoy,
AJ

---

### Post by Kain000 on 2009-03-25
wow thanks alot, this is a solution for alot of other little annoyances.  I had a thread a while back about allowing a modified version of ushare to start at boot.     because the command to start it is sudo ushare it wouldn't start on boot, even tho it was added to the runlevel file.

anyhoo now i can run that aswell.

thanks again

ohh btw, why should I not edit the file manualy?

---

### Post by ajmorris on 2009-03-26
> **Kain000 said:**
> wow thanks alot, this is a solution for alot of other little annoyances.  I had a thread a while back about allowing a modified version of ushare to start at boot.     because the command to start it is sudo ushare it wouldn't start on boot, even tho it was added to the runlevel file.

anyhoo now i can run that aswell.

thanks again

ohh btw, why should I not edit the file manualy?

`visudo` is a *safe* method of editing the sudoers file. visudo locks the sudoers file, so that you can't do multiple edits at the same time. It also provides sanity checks and checks for parse errors.
Also, as the sudoers file is quite an important file, it has permissions 440 so you cant actually write to it without changing the permissions yourself. However, using visudo allows you to write the changes.

AJ

---

