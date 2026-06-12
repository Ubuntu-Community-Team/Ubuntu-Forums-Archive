---
title: "Mounted volume showing on desktop and Encfs"
date: 2009-03-13
forum: General Help
---

### Post by jamesjwilsonsr on 2009-03-13
Here's my situation.

I have a volume on my work laptop where I keep all of my client data.  I did that in case the config got hosed, I'd just reinstall and still have my data.  I then figured, hey, it'd be great to encrypt all of this stuff in case it were lost or stolen.

The volume with client data used to mount to the /media folder as /media/disk (it is /dev/sda4).  I didn't like this because it creates a desktop icon.  Now, I like desktop icons for removable media like flash drives and CDs, so I do not want to use gconf-editor and remove the feature as a whole.  
I read that everything in the /media folder goes to the desktop when mounted, that is where it mounted.  
I decided to mkdir, /mnt/disk.  I then went into /etc/fstab and changed it (/dev/sda4) to mount to /mnt/disk.  Ok, that is great, no worries there now.

However when I do this in terminal:
encfs /mnt/disk ~/Documents/Clients 
...the newly encfs mounted drive shows up on the desktop.  I don't want it there either.  I just want to traverse to the folder and work from file browser.

When I run df through terminal, it shows it is not in /media (it is in ~/Documents/Client, right where I mounted it).  

My question is, how do I get the encfs mounted drive to not show up on the desktop.

Any help would be appreciated...and be kind...I'm a bit of a newb here :D

---

### Post by jamesjwilsonsr on 2009-03-13
I'm thinking the answer is going to be to make a directory in the /mnt folder and link Clients to it, right?  Then when I mount using encfs I will mount /dev/sda4 to /mnt/Clients?  
I am going through a bit of testing on this but it seems to be an option.  Any other thoughts?

---

### Post by jamesjwilsonsr on 2009-03-13
> **jamesjwilsonsr said:**
> I'm thinking the answer is going to be to make a directory in the /mnt folder and link Clients to it, right?  Then when I mount using encfs I will mount /dev/sda4 to /mnt/Clients?  
I am going through a bit of testing on this but it seems to be an option.  Any other thoughts?
That did the trick...so here is the objective/solution front to back in case anyone else has the same issue

*You want to keep flash drives and DVD drives mounting to /media and showing up on your desktop
*You don't want your mounted volumes or encrypted volumes to mount to /media and show up on your desktop

As many of the other articles I've read states:
*Created a directory in /mnt
*Go into /etc/fstab and change the mount point from /media (or wherever else the destination may be) to /mnt/newlycreateddirectory

Now the destination of the encrypted data will not show up on your desktop when mounted

To get the viewable source of the encrypted data to not show up on your desktop:
*Create another directory in /mnt...I called mine clients
*Pick the place you want to access or transfer data from the encrypted volume...in my case it was ~/Documents
*Create a soft link in ~/Documents (or wherever you choose) to the /mnt/clients (or whatever) folder
     *ln -s /mnt/clients ~/Documents

You now have a link between a shortcut folder in your Documents folder, to the /mnt/clients directory.

Now using encfs:
*encfs /mnt/disk /mnt/clients
where /mnt/disk is the mounted location of my crypto endpoint../dev/sda4.


Now, when I go to my home directory, into the Documents folder, if the volume sda4 is mounted to /mnt/disk and encfs has mounted /mnt/disk to the startpoint of /mnt/clients...I can access my info in the traditional end user transparent sense in my home folder.

---

