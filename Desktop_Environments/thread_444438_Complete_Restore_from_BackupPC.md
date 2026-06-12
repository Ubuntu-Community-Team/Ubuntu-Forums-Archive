---
title: "Complete Restore from BackupPC"
date: 2007-05-15
forum: Desktop Environments
---

### Post by steveM49 on 2007-05-15
My home LAN has an Ubuntu machine serving as the Domain Master in Samba and holding the directories that the family uses and needs: accounting, pictures, music, etc.  I have these directories backed up on an external SATA drive using BackupPC.

I moved the Ubuntu server (on Dapper Drake) to a new box last week so that I could expand the drives attached to a RAID controller.  In the process I hurt some SATA wires and the controller decided that the array was toast.  I thought restoring the family files from backuppc would be easy.

I installed Feisty Fawn; selected to install BackupPC; and tried to restore.  The first problems were that the user numbers had changed, so that all the files on the external SATA drive had to have ownership changed to backuppc:backuppc, then I had to contend with the default install expecting that BackupPC will have hosts on connected machines, not the local host.  I kicked myself that I hadn't saved the /etc files for apache, samba, and bacuppc in a readily available manner on the external drive.  Kicked again when my notes from the last time I did this were not sufficient to do it again.

Now I have trouble getting the web page to backuppc - the message reads "Error: Unable to Connect to BackupPC Server".  I believe that this is because Apache has not created a web for BackupPC.  Apache is running, I get a "It Works!" screen when I navigate to it's index page.  I've installed mod_perl in hopes of being able to use backupPC administrator, but without success yet.

It seems that I am having problems both with the upgrade to Feisty and the restore itself.  Any help would be appreciated.

Steve

---

