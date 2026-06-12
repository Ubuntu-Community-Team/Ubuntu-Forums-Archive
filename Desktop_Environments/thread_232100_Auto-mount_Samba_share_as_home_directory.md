---
title: "Auto-mount Samba share as home directory"
date: 2006-08-08
forum: Desktop Environments
---

### Post by el3ktro on 2006-08-08
Hello there,

our company is currently using Win XP clients with roaming profiles, stored on a Samba PDC. We want to test-drive Linux as a client, and we want 4 users to switch to Linux (dual booting with Windows, just in case). The only programs these users need are Firefox, OpenOffice & Outlook (Evolution) (which we both use on Windows anyway). There are just two issues that have to be solved:

- How can I authenticate Linux users against the Samba PDC (for central user management)?

- Could I mount a Samba share (or NFS share) as the user's home directory? I'd need some kind of script that runs whenever a user logs in and that mounts the user's directory on the server as /home/$user on the client.

Is that possible with not too much effort? The central user management is not so much an issue (at least for this test drive) but we really want the user's home directory stored on the server (for backups etc.)

Tom

---

### Post by jonnymccullagh on 2006-08-08
I'm no expert but at home I mount my home folder to another hard drive partition and at work I mount folders within my home folder to the network shares. There are instructions in the unoffical guide: [http://ubuntuguide.org/](http://ubuntuguide.org/) 
The file you need to edit is /etc/fstab 
sudo gedit /etc/fstab (or sudo kwrite /etc/fstab)

but you will need the credentials file(see ubuntuguide). And you would also need to copy over all existing files from the users home folder (including hidden files).

//Server/Share        /home/youruser  smbfs    credentials=/root/.smbcredentials,uid=youruser,gid=youruser       0       0

---

### Post by el3ktro on 2006-08-08
I know about mounting & stuff, my problem is how do I do this user-specific? If user X logs on I need to mount //server/X to /home/X, but if user Y logs on, I need to mount //server/Y to /home/Y. Isn't there a file that gets executed when a user logs in? Wouldn't it be possible to put a specific mount command there? I don't remember the name of this file though ...

Tom

---

### Post by quinnten83 on 2007-11-23
This is an oldie, but I was looking around for the same thing.
Is there a way to achieve this? The questions posed here are exactly like my own.
Has there been a way to do this?
Also if you're a laptop user, is there a way to make sure that at startup and shutdown/ log off the /home/$user file gets synchronised? And of course ubuntu would have to check first if the server is available at startup and if it is not, it would have to automatically switch to use the local /home/$ user folder...
So if anybody has any ideas on this one, It would be AWESOME!!

---

### Post by deltateam2 on 2008-02-13
In theory this should although it would of course add stress to the NAS server that saves the home directories.  Please somebody respond to this or I will conduct my own research in a virtualized instance of ubuntu.

---

### Post by harrysales on 2008-02-14
Am I missing some but could you not smbfs mount a home directory using fstab as described aready and give the users subdirectories. (you would need to install smbfs).

---

### Post by Silby on 2008-02-14
Check out [pam-mount]("http://pam-mount.sourceforge.net/") for per-user mounts.

---

