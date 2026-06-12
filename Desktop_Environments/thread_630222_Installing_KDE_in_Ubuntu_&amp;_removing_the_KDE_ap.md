---
title: "Installing KDE in Ubuntu &amp; removing the KDE apps from Ubuntu/GNOME apps from Kubuntu"
date: 2007-12-03
forum: Desktop Environments
---

### Post by lewisskinner on 2007-12-03
Hi everyone.  I installed Ubuntu 64-bit on my machine.  

I have a 50GB NTFS windows partition, a 3GB swap, 10GB ext3 Ubuntu, 1GB /home and a 400GB FAT32 shared partition.  

I downloaded the Kubuntu-desktop environment for Ubuntu.  I found a way to clean the KDE apps from Ubuntu and the GNOME apps from Kubuntu [here](http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/), but I got an error message after the very first command ("$ sudo -s -H") which said "bash: $: command not found".

Does anyone know how I can remove the KDE from Ubuntu/GNOME from Kubuntu in a way that actually works?  Or am I just being daft and can't use the console properly?

---

### Post by logos34 on 2007-12-03
If you were in kubuntu when you tried to run 'sudo -s -H' I think maybe you need to do 'kdesu -s -H' instead. But that may not be the problem

---

### Post by eldepeche on 2007-12-03
If a command in a guide begins with $ or #, that means to run that command as a normal user ($) or as root (#). It's the last character in the shell prompt.

---

### Post by lewisskinner on 2007-12-03
So do I need to include the *$* or *#* in the command then?

And can I paste the whole paragraph together, or do I need to enter the command line-by-line?

---

### Post by lewisskinner on 2007-12-07
> **eldepeche said:**
> If a command in a guide begins with $ or #, that means to run that command as a normal user ($) or as root (#). It's the last character in the shell prompt.

Right, so do I just type in:
what was shown on the page
line-by-line
hit enter after each line
and omit the *$* or *#*

Correct?

---

### Post by eldepeche on 2007-12-07
That's right. Typing "sudo -s -H" at your user prompt will give you a root shell (the -s switch means execute the shell, and -H sets the variable for the home directory to the root user's home). The shell prompt will change to something ending in #, so your screen will look like "# command" when you type "command".

---

### Post by lewisskinner on 2007-12-07
yeah, tried this but without luck.  I just got a whole load of errors coming up!

---

