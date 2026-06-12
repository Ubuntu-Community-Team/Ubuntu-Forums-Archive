---
title: "Backing up Evolution"
date: 2007-07-13
forum: Desktop Environments
---

### Post by chichibabin on 2007-07-13
Dear All,
I have just migrated over to Ubuntu after one headache too many with Gentoo. I was running Evolution as my email client and had numerous contacts, calender entries and emails. The only files I backed up was everything in my previous home directory so I have my old .evolution directory. When I copy over the backed up .evolution directory I only recover emails up to February 2006 and none of my contact and calendar entries are restored.



Is there somewhere else the emails could be stored within my old home directory?? Have I lost all of this information?


EDIT:  When I untarred the backed up home directory I got an error at the end so it's possible the archiving process failed near the end and the contacts info was not stored. The only directory in the backed up .evolution directory is "mail".
Thanks,
Sat

---

### Post by fdimmling on 2007-07-13
> **chichibabin said:**
>  Have I lost all of this information?

EDIT:  When I untarred the backed up home directory I got an error at the end so it's possible the archiving process failed near the end and the contacts info was not stored. The only directory in the backed up .evolution directory is "mail".


If "mail" is the only saved directory you may have lost the rest. 

There is a backup plugin for Evolution to download from the Ubuntu repos which saves the .evolution directory after shutting down Evolution. It containes a lot of dirs and files, calendar and addressbook are two of them. 

Friedrich

---

### Post by chichibabin on 2007-07-13
Thanks, yes it seems as though I am missing directories within .evolution and the failed unpacking is likely to be responsible. Funnily I did not get any errors when packing so I will try and unpack again and see if I still get that error and missing directories.
Cheers,
Sat

---

### Post by Barry Smalley on 2007-07-13
Here's what I use

Shutdown Evolution

gconftool-2 --shutdown
evolution --force-shutdown

Backup Evolution

cd

tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution

Restore Evolution

gconftool-2 --shutdown
evolution --force-shutdown
tar xzf evolution-backup.tar.gz
gconftool-2 --unload evolution_setting.xml
gconftool-2 --load evolution_setting.xml

Running as a script is better.

---

### Post by chichibabin on 2007-07-16
I unpacked again and the tar file corrupted during the archiving of .evolution. Don't know why, got no errors on packing :(

---

### Post by oomingmak on 2007-07-16
> **chichibabin said:**
> I unpacked again and the tar file corrupted during the archiving of .evolution. Don't know why, got no errors on packing :(
I've had the same thing, using both Sbackup (Simple Backup) and Acronis True Image (restoring from Boot CD).

Both times there were files that could not be restored and caused error messages.

When I restarted Evolution (having restored what I could) many settings were missing and none of my POP account details were present. I had to recreate all my accounts again from scratch.

This has happened across more than one Ubuntu install.

---

### Post by ayoli on 2007-07-16
> **Barry Smalley said:**
> Here's what I use

Shutdown Evolution

gconftool-2 --shutdown
evolution --force-shutdown

Backup Evolution

cd

tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution

Restore Evolution

gconftool-2 --shutdown
evolution --force-shutdown
tar xzf evolution-backup.tar.gz
gconftool-2 --unload evolution_setting.xml
gconftool-2 --load evolution_setting.xml

Running as a script is better.

interesting, i think i'll give that a try one day, i'll just add you need to do that in your home dir (cd ~)

---

### Post by Astrikor on 2007-07-17
> **fdimmling said:**
> 
There is a backup plugin for Evolution to download from the Ubuntu repos which saves the .evolution directory after shutting down Evolution. It containes a lot of dirs and files, calendar and addressbook are two of them. 

Friedrich

Sounds great, so what is the plug-in & where do I find it?

---

### Post by chichibabin on 2007-07-20
> **Barry Smalley said:**
> Here's what I use

Shutdown Evolution



Of course. I backed up from the console on a borked gentoo installation which would not start properly. It seems as though the evolution data server had started though and was actively making changes to the .evolution files. These changes messed up the back up. This is something to look out for because you get no error on packing and you don't always want to unpack 7 gigs of stuff just to check everything went smoothly. Next time I'll make sure I kill that sucker first.
Cheers,
Sat

---

### Post by fdimmling on 2007-07-20
> **Astrikor said:**
> Sounds great, so what is the plug-in & where do I find it?

It is in evolution-plugins-experimental.

Friedrich

---

