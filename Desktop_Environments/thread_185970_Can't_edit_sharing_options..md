---
title: "Can't edit sharing options."
date: 2006-06-01
forum: Desktop Environments
---

### Post by mysn3xs on 2006-06-01
I recently installed kubuntu on my computer and i am trying to share files with users but i do not have access. when i push the administrator mode button it asks for a password which i enter then it goes back to exactly how it was before I cannot login as root as kubuntu does not allow that and i tried putting me in the root group and i still have limited access. i would appreciate any help with this that you can offer. Thanks.

---

### Post by vidak on 2006-06-02
just a workaround - what about setting up an ftp-server?
btw I got the same effect with the admin button...

---

### Post by RudolfMDLT on 2006-06-02
[QUOTE=vidak]just a workaround - what about setting up an ftp-server?
btw I got the same effect with the admin button...[/QUOTE]

Sorry, not a lot of expierence with Ubuntu or Kubuntu, but doesn't Gnome and KDE both use samba to share files on a network? If you want to use samba, then I can help.

---

### Post by vidak on 2006-06-02
[QUOTE=RudolfMDLT]Sorry, not a lot of expierence with Ubuntu or Kubuntu, but doesn't Gnome and KDE both use samba to share files on a network? If you want to use samba, then I can help.[/QUOTE]

Sure, you are right. Installing samba with 
apt-get install samba 
solves the problem.
Full docs:
[http://www.samba.org/samba/docs/using_samba/toc.html](http://www.samba.org/samba/docs/using_samba/toc.html)
but you probably won't need it... :)

---

### Post by RudolfMDLT on 2006-06-02
Okay, just checked it out... If you have samba server installed you should be able to network to any machine, MS or Linux. 

To get around the user rights thing:

Click on the blue K "start button"? What do we call that in Ubuntu?

Piont to system, and Right Click on Shared Folders. Select the option Put Into Run Dialog. Click the options button and tick the Run was a different user. Enter your Root password and that should give you the rights that you need.

If you get stuck, just keep posting and we'll try to find a work around! The ftp server isn't a bad idea! :)

---

### Post by mysn3xs on 2006-06-02
thank you for your help. I don't have access to my linux computer until moday so i wont be sure if it worked or not. if it doesn't ill post back. thanks alot.

---

