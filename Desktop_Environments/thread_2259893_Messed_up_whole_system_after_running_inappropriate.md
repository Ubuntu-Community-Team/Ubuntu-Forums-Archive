---
title: "Messed up whole system after running inappropriate command"
date: 2015-01-07
forum: Desktop Environments
---

### Post by Cristian_Prigoana on 2015-01-07
Hello everybody,
    while I was developing a web application in Ubuntu 14.04, I read a tutorial that told to change the permissions of multiple files under /usr/lib, so I thought of running ```
sudo chmod -R 777 /usr/lib 
``` ... because what could go wrong? Well many things went wrong from that point on (in fact, after a reboot):
[LIST]
[*]the window manager was messed up: fonts in the toolbars, text areas etc. were constantly changing their sizes (toggling between 11 and 13 approximately) and some colors were changing weird. 
[*]the system responded very slowly 
[*]the disk was full 
[/LIST]

I switched to another tty with Ctrl+Alt+F1 and realised that I could run any command as sudo, I was getting ```
[FONT=courier new]sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner[/FONT]
``` and "cups" had filled the disk with an error log (somewhere in /var/log) with the message "/usr/lib/some_file has insecure permissions" repeated to infinity.

However, I couldn't find what exactly went wrong with the window manager and I reinstalled Ubuntu because I didn't have anything important on the system anyway, but I'm sorry that I forgot to take a screen capture.

To what extent are these expected behaviours? Was there any chance that I didn't have to completely reinstall Ubuntu?

Thanks,
    Cristi

---

### Post by QIII on 2015-01-07
Hello! 

Chances of not needing to reinstall after randomly changing the permissions on important system files are slim indeed.

If a user has not kept detailed notes of what files/directories were changed, the previous permissions and the permissions set, it is practically impossible to sort out what to fix among thousands.

The other case would be certain instances of compromised servers.

---

### Post by Cristian_Prigoana on 2015-01-08
I changed the permissions of the files under /usr/lib/sudo to match those on the live stick and sudo did work afterwards, but manually doing that to thousands is impractical. 
What about a script that does that for every file in the filesystem? I think of giving it a try ...

---

### Post by Impavidus on 2015-01-08
The software installed on the live disk is not exactly the same as the software installed on your system. So if you make all permissions on your system the same as on the live disk, the problem may not be solved yet. The only realistic solutions are reinstall or restoring a cloned backup.

---

### Post by phidia on 2015-01-08
I've found that [this]("http://www.finnix.org/") or sysadmin distros like that can be helpful in situations like described by op.

---

