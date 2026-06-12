---
title: "Backup over network (long)"
date: 2006-01-04
forum: Desktop Environments
---

### Post by cajunlibra on 2006-01-04
As far as I know I have everything up to date on one machine I'll call "Lilbox".  I have had Ubuntu installed on it for at least 6 months.  I have the most recent updates of the kernel and Breezy.  I have another computer I'll call "Bigbox" that has XP Pro installed.  It was an illegal copy of XP I'll admit.  I tried to change the CD Key and now XP will not load properly.  I have decided to setup Bigbox as a dualboot system for XP and Ubuntu.  I am running Ubuntu Live on Bigbox.  I ahve been trying with no luck to back up one of my HDs on Bigbox onto a CD, however one of teh files is too large for the CD so I need to back it up to lilbox.  The CDRW doesn't seem to be recognized by Ubuntu.  I do not know how to mount a CDRW.  i need help with that so that I can burn a CD.  I also need to set up filesharing so that lilbox can access files on bigbox.  lilbox is already setup with samba and worked fine with XP.  I have tried to install samba onto bigbox but i am unable to create any usernames.  I get the following:  
/home/ubuntu # sudo smbpasswd -a bubba
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user bubba. Does this user exist in the UNIX password database ?
Failed to modify password entry for user bubba

PLease help me.   Real-time help would be best if possible.  I am available on any of the 4 major IM networks or even on IRC.  just PM me for a network screenname.

Thanks
CL

---

### Post by ptmurphy on 2006-01-04
The username you enter into samba has to be a valid user in Linux as well.  You must be able to login as that user, so setup an account and login as "bubba" or whatever you choose to call it, and verify it is a valid account.

Then go back and set the samba password for user "bubba".

---

