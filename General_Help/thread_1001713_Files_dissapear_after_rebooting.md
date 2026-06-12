---
title: "Files dissapear after rebooting"
date: 2008-12-04
forum: General Help
---

### Post by t3jem on 2008-12-04
Ok, so I've been using ubuntu for some time, but still quite new, recently I had to reinstall after corrupting my installation (real stupid mistake), anyways, now that I have ubuntu 8.10 installed I've been installing the apps and stuff I need such as my todo list, setting up my desktop settings, stuff like that, and I've realized, it seems to take a couple reboots and settings everything back up a couple times to get the setting to stick, that's not the only issue either, the biggest one is that my files keep disapearing on reboot.  just yesterday I was working on an assignment for class today, well, I rebooted, sure enough the file is no where to be found, it's finals week too, but for now I'm going to save to a different harddrive to prevent vital data being lost, but a fix is needed.

I have an inspiron 1720 from dell, two 320 GB harddrives, ubuntu is on a 31 GB partition on my second harddrive, I use windows to do a partition image to a replica 31GB partition on my second harddrive as well and I think this may be the issue, but I'm not sure.  My next step is to try and make an image to a zip archive instead of a disk copy, but if you have any other suggestions please let me know.

thank you in advance for your help!

---

### Post by linux_tech on 2008-12-04
I'm not sure what type of file your working with or where you have tried to save the files to.
Try saving the files to /home/username/Desktop
and home/username/Documents.

The files saved there should be there after a reboot.
Saving the file to a usb flash disk as a backup is also a good idea.
when you insert a flash disk into a usb, it normally appears as a icon on the desktop.  You should be able to save as and browse to that location to save the file as well.

---

### Post by t3jem on 2008-12-04
Sorry, I guess I wasn't too clear, I was mainly using the file as an example, rather, ubuntu is acting as if it was on live CD; however, after a few reboots of doing the same thing (e.g. setting the visual settings to the same values a few times) then the changes stick, otherwise they are wiped clean.  This doesn't just affect the files on my desktop or in my documents, but packages I install and scripts I've installed.  It's pretty annoying, just an hour ago I installed a nautilus script to mount ISO's, just restarted and they are gone, I have decided to back all my important stuff to my other HDD I use for windows for now though.

---

