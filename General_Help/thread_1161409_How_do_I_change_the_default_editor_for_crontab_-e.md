---
title: "How do I change the default editor for crontab -e ?"
date: 2009-05-16
forum: General Help
---

### Post by macey on 2009-05-16
Hi,
I have migrated to 9.04 and the editor used for crontab -e has changed to VI(M) from gedit. I want to go back to gedit.
I appears from the man pages that it is controlled vis the VISUAL or EDITOR global variables.
How do I change this please?
Thanks.

---

### Post by llamaX on 2009-05-16
This can be set in your ~/.bashrc file.  The line will look like:

export EDITOR=/usr/bin/vim

---

### Post by macey on 2009-05-16
> **llamaX said:**
> This can be set in your ~/.bashrc file.  The line will look like:

export EDITOR=/usr/bin/vim


Thanks but mine doesn't!

---

### Post by PGScooter on 2009-05-16
then you can just add the line. Make sure you open the file with sudo and you should save a copy of it before as a backup.

---

### Post by Locutus_of_Borg on 2009-05-16
in /etc/profile:
export EDITOR="/usr/bin/nano"
export VISUAL="/usr/bin/nano"


thats what i had to do for slackware at least

---

### Post by macey on 2009-05-17
> **Locutus_of_Borg said:**
> in /etc/profile:
export EDITOR="/usr/bin/nano"
export VISUAL="/usr/bin/nano"


thats what i had to do for slackware at least

None of the suggested methods seem to work for me:confused:

---

### Post by kpkeerthi on 2009-05-17
> **macey said:**
> None of the suggested methods seem to work for me:confused:

If you make changes to .bashrc, you should close the terminal and open again for the changes to take effect. Or enter **source ~/.bashrc** at the command prompt.


If you make changes to /etc/profile, you should logout and log back again for the changes to take effect.

---

### Post by macey on 2009-05-17
> **kpkeerthi said:**
> If you make changes to .bashrc, you should close the terminal and open again for the changes to take effect. Or enter **source ~/.bashrc** at the command prompt.


If you make changes to /etc/profile, you should logout and log back again for the changes to take effect.

I re-booted the machine after both edits.

---

### Post by kerry_s on 2009-05-17
in a terminal: **export VISUAL=gedit `crontab -e`**

post any errors you get.

---

### Post by macey on 2009-05-17
> **kerry_s said:**
> in a terminal: **export VISUAL=gedit `crontab -e`**

post any errors you get.

No errors, perhaps I should have explained, I am not trying to edit 'my' crontab, but the *system* one via 'sudo crontab -e'. Thats when the system uses vi(m) instead of gedit.   OOPS!:redface::redface::redface:

---

### Post by TheExplorer on 2009-05-17
> **PGScooter said:**
> Make sure you open the file with sudo...

Are you sure? :) Sudo in your home dir?

---

### Post by kerry_s on 2009-05-17
> **macey said:**
> No errors, perhaps I should have explained, I am not trying to edit 'my' crontab, but the *system* one via 'sudo crontab -e'. Thats when the system uses vi(m) instead of gedit.   OOPS!:redface::redface::redface:

okay then> **sudo export VISUAL=gedit `sudo crontab -e`**

post those errors.

---

### Post by macey on 2009-05-17
> **kerry_s said:**
> okay then> **sudo export VISUAL=gedit `sudo crontab -e`**

post those errors.

Ok Thanks, here it is:-

richard@kagyu-laptop:~$ sudo export VISUAL=gedit `sudo crontab -e`
[sudo] password for richard: 
Vim: Warning: Output is not to a terminal

Terminal does not the respond, Cntl D, C etc......

---

### Post by kerry_s on 2009-05-17
> **macey said:**
> Ok Thanks, here it is:-

richard@kagyu-laptop:~$ sudo export VISUAL=gedit `sudo crontab -e`
[sudo] password for richard: 
Vim: Warning: Output is not to a terminal

Terminal does not the respond, Cntl D, C etc......

ouch, it looks like it don't want you to run console executed gui's as root.

try putting the> **export VISUAL=gedit** < in /etc/environment
logout or reboot, then try the "**sudo crontab -e**"
other than that i don't know, maybe learn vi. ;)

---

### Post by thunderforce on 2010-08-31
> **Locutus_of_Borg said:**
> in /etc/profile:
export EDITOR="/usr/bin/nano"
export VISUAL="/usr/bin/nano"


thats what i had to do for slackware at least

Thanks a bunch for this. Worked for me! (Slackware 13.1 64-bit)

---

### Post by AlexanderDGreat on 2010-09-06
Hi, but mine still doesn't work. I regularly use:

```
sudo crontab -e
```

But my editor is only nano, **how can I change it so I can use _gedit_?**

I'm using Ubuntu Lucid Lynx. Thanks.

---

### Post by MooPi on 2010-09-06
Try this in terminal.
```
export EDITOR=gedit
```

---

### Post by AlexanderDGreat on 2010-09-08
Hi MooPi - thanks but I switch from

```
sudo crontab -e
``` to

```
sudo gedit /etc/crontab
```

They're really the same. Just indicate who's the user that will execute the command.

Problem solved. Thanks. :)

---

