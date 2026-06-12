---
title: "Mounting Software RAID 0"
date: 2009-05-23
forum: General Help
---

### Post by DarkStarZN on 2009-05-23
Heya people.

Need some help.


I have a software RAID0 created in Vista (stupid idea, I know) and I'm having no short of a lot of trouble mounting it in Ubuntu. (FYI, it's a dynamic disk setup)

I've tried using mdadm (followed instructions in this thread: [http://ubuntuforums.org/showthread.php?t=833653](http://ubuntuforums.org/showthread.php?t=833653)) but have had no luck, as when it comes to mounting the 'drive' is tells me there's no NTFS Handle.

Is there anyone else here who could offer some help, please?

Oh, right, I'm using 9.04

---

### Post by ronparent on 2009-05-23
Presuming you have a MB raid controller you would be using a 'fakeraid'. Don't let the term throw you. To see it in ubuntu you need dmraid. Open a terminal and run:

**sudo apt-get install dmraid -y**

then if the install was successful continue with

**sudo dmraid -ay**

At this point you will see the results in /dev/mapper. I myself am stuck with the next step to mount the raid partitions automatically in ubuntu 9.04. In 8.10 I merely edited the /dev/fstab as sudo to link the symbolic links you see in /dev/mapper automatically to mount points created for that purpose. I am still trying to figure out how to mount automatically in 9.04! At this point you can do it manually with a mount command:

**mount /dev/mapper/<your raid partition entry> /media/<whatever you want to call it>**

It can do no harm to try it and see if it works. Then we both may need help to get to the next step.

---

