---
title: "/home lost :("
date: 2006-08-18
forum: Desktop Environments
---

### Post by ososxe on 2006-08-18
well, is not really lost.. I was trying to move /home to it's own partition and i thought i did a copy of the data but i didn't (i blame it on my lack of sleep lately, damm graveyard shift)
So now i have a /home partition on a separate disk, but without any data on it, and when i log in with my user i get errors galore.. but my main concenr is to know if i can recover the 2 GB of data i had on my old /home, i've tried a few tools but they didn't found nothing.
Right now i'm at job and i can't remember the instructions i've followed, i hope to find the website and put here the instructions as soon as i get home.

---

### Post by tonym on 2006-08-18
Not clear without further details on what you did.  If you didn't copy the files are they still there in the old directory?  If you have mounted another partition as /home you would not see anything in the old directory but they could still be there.  Try unmounting /home and then see if they are there.

---

### Post by ososxe on 2006-08-18
I did the following:

 mv /home /home.old

 mkdir /home 

 chown root:staff /home

 chmod g+s /home

 then i edited the /etc/fstab to add the new hardrive where the new /home is, but somewhere along the way i should have screwed it up because there's no home.old and the new home dosn't have any users folders.  
I will try unmounting the new /home..



ps: YES!!!! it worked!! I unmounted /home and the old /home was there with all its glorious files!! I'm moving it to another hard drive, then i will mount the new home and copy the data from the old home to the new, and then i will log in with the users to check that is working. right?

Thanks a lot!!!!!

---

