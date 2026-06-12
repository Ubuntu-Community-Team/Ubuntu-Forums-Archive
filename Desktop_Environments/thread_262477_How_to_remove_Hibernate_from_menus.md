---
title: "How to remove Hibernate from menus"
date: 2006-09-21
forum: Desktop Environments
---

### Post by ckr on 2006-09-21
Hi,

I have a lab in a Middle School that is using Edubuntu LTSP.  However, students have discovered the joy of hitting hibernate in the gnome menus, which shuts down the whole lab.  Even the regular users have the right to hibernate the system.  The server also does not wake from hibernation very well, so it's a situation that I wish to prevent. [-X 

Does anyone know where I need to go to remove "Hibernate" from the gui shutdown dialog?  I tried looking through the options in the program Pessulus, but it didn't go into this issue.  Maybe the solution is more simple than that, but I haven't figured it out yet.

Thanks,

Ckr

---

### Post by motin on 2006-09-21
I don't know about the GUI, but you can always alter the hibernate script itself:

motin@laptop:~$ whereis hibernate
hibernate: /usr/sbin/hibernate /etc/hibernate /usr/share/hibernate /usr/share/man/man8/hibernate.8.gz
motin@laptop:~$ sudo gedit /usr/sbin/hibernate

I can't say this is a good thing to do, but you can put in "exit 0;" just after the first row if you really want to disable hibernate. Or maybe there can be a way to add a password prompt in there?

---

### Post by ItsManaged on 2008-01-02
> **motin said:**
> I don't know about the GUI, but you can always alter the hibernate script itself:

motin@laptop:~$ whereis hibernate
hibernate: /usr/sbin/hibernate /etc/hibernate /usr/share/hibernate /usr/share/man/man8/hibernate.8.gz
motin@laptop:~$ sudo gedit /usr/sbin/hibernate

I can't say this is a good thing to do, but you can put in "exit 0;" just after the first row if you really want to disable hibernate. Or maybe there can be a way to add a password prompt in there?

Hi Motin,

Thanks for the idea of modifying the script.

I cannot find hibernate script in gutsy gibbon - can you help with gutsy gibbon?

I find the hibernate option useless, and the last thing I want to do is install uswsusp (also known as µswsusp or simply suspend) to get it to go and risk breaking something else, so, I too would like to remove it - my suspend works well - I run an Asus A8Fm notebook.

---

### Post by jhansonxi on 2008-01-19
To disable the hibernate and suspend buttons in Gnome use Gconf-Editor
[http://ubuntuforums.org/showthread.php?t=229665](http://ubuntuforums.org/showthread.php?t=229665)

---

