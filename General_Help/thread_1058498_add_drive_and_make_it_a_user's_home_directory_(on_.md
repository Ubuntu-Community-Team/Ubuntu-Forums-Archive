---
title: "add drive and make it a user's /home directory (on a server)"
date: 2009-02-02
forum: General Help
---

### Post by jimmy the saint on 2009-02-02
I have a server running Ubuntu 8.10 that serves various media, files and handles a few other tasks.  When I was setting it up I mistakenly put in the wrong drive (no idea how that got past me) and Now it is filled up.  

I have a 750G drive that I need to add and move the main media share to that drive.  I would like to leave the main user on the first drive as it is plenty big to handle backups and various smaller files.  I just think it would be a waste to use a 200G drive just for the / filesystem!

I can add the drive no problem, but how would I migrate just one home directory to it?  I have webmin running on the server but I just used it to set up the samba shares and that's pretty much all the customization that I have done.  Is there a way to do this in webmin or can someone point me to a good guide (or some instructions)?

Thanks,

JTS

---

### Post by mgol on 2009-02-02
I'm not sure if /home can be separated, but if it is, is it not just the case of editing fstab file and adding an additional entry describing /home/USER?

Of course, You'd have to move manually the whole USER folder to the new disk before rebooting and logging to USER again.

---

### Post by jimmy the saint on 2009-02-04
I realized that I don't need to migrate the home directory at all.  I created a media user and use that users home directory to house the samba shares.  It dawned on me, as I was trying to figure this out, that the samba shares dont HAVE to be in the home directory!  My brain was stuck in that line of thinking for some reason.  I'll just make that drive house the samba shares independent of the user.  

On a side note I LIKE WEBMIN.  I just found an option to format the drive.  I need to spend a little quality time with webmin.  I only used it to manage a few of the server services, but I think it can handle pretty much anything I need to do.

---

