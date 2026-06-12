---
title: "gdmsetup problem"
date: 2006-08-26
forum: Desktop Environments
---

### Post by nene on 2006-08-26
hi boys I have a problem when I lunch the command: gdmsetup, the system answers:

 Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

How to resolve it???
th

---

### Post by Crooksey on 2006-08-26
You can acsees the GDM setup menu from the actual GDM window, if its working that is.

---

### Post by Jolly Roger on 2006-09-12
I am having this exact problem. When I start up my computer I don't have the GUI for logging in but I can login with the terminal. I'm guessing this came about because yesterday I installed xubuntu and kubuntu desktops to try them out. They were working fine last night and GDM worked fine last night but now it is not working. I get the same error as the first poster in this thread:

Failed to connect to socket, sleep 1 second and retry
Trying failed command again. Try 2 of 5.
Failed to connect to socket, sleep 1 second and retry
Trying failed command again. Try 3 of 5.
Failed to connect to socket, sleep 1 second and retry
Trying failed command again. Try 4 of 5.
Failed to connect to socket, sleep 1 second and retry
Trying failed command again. Try 5 of 5.
Command failed 5 times, aborting.
Could not access GDM configuration file.

I cannot open the login window app from the system>administration menu and I get that error message when I type sudo gdmsetup. 

Anyone know a solution for this?

---

### Post by taliskar on 2006-10-18
Anyone come up with a solution for this?  I've been using Ubuntu 6.06 until today when I installed the kubuntu-desktop package to try out the KDE interface.  Now I have to log in using the command line interface and manually start X-windows instead of using the X login interface as expected.  Tried to back out kubuntu-desktop to no avail.

What's the story on this one?

---

### Post by Mancman on 2006-10-18
I had the exact same problem, and after plenty of this ](*,)  I just removed gdm completely, and re-installed. Problem solved :D

---

### Post by raul_ on 2006-12-27
-bump-

---

### Post by d3v1ant_0n3 on 2006-12-27
what happens if you run ```
sudo dpkg-reconfigure gdm
``` in terminal?

---

### Post by raul_ on 2006-12-27
I solved it. I went to /etc/rc2.d/ and renamed S13gdm to S21gdm . Seems that it needs to run something before it loads gdm

---

