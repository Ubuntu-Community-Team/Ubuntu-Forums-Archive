---
title: "Wubi Xp? Boot to windows as normal, no option."
date: 2008-12-06
forum: General Help
---

### Post by mrbfrog on 2008-12-06
I loaded wubi and it then told me that it needed to restart my computer, I let it.  I have restarted a few times and I do not see the unbunu option.  There is a partition on my hard drive.  I didn't know if it made a difference what partition it was loaded to so I uninstalled and loaded to the other partition.  Same thing.  I am sorry if this has been asked before, I tried searching and could find nothing that really made sense to me.  Please respond as though to a child.  I really have almost no clue.

---

### Post by Jammanuser on 2008-12-06
> **mrbfrog said:**
> I loaded wubi and it then told me that it needed to restart my computer, I let it.  I have restarted a few times and I do not see the unbunu option.  There is a partition on my hard drive.  I didn't know if it made a difference what partition it was loaded to so I uninstalled and loaded to the other partition.  Same thing.  I am sorry if this has been asked before, I tried searching and could find nothing that really made sense to me.  Please respond as though to a child.  I really have almost no clue.

hmm...it sounds like u might be missing a few files! try looking in the C:/ drive, in "My Computer", and checking ur "Ubuntu" folder,  and check to make sure that the folder called "Disks" is there...

And then we can go from there if u want! ;)

Cheers! :)

-jammanuser

:D

---

### Post by mrbfrog on 2008-12-06
yes the folder "disks" is there.
inside that is a "boot" folder and a "shared" folder.  There is also a "root.disk" and "swap.disk" disk file in the main "disks" folder.

in the boot file there is a "grub" folder but that appears to be empty.
and the "shared" folder is also empty.

thanks

---

### Post by Jammanuser on 2008-12-06
> **mrbfrog said:**
> yes the folder "disks" is there.
inside that is a "boot" folder and a "shared" folder.  There is also a "root.disk" and "swap.disk" disk file in the main "disks" folder.

in the boot file there is a "grub" folder but that appears to be empty.
and the "shared" folder is also empty.

thanks

well...there u have ur problem! the "grub" folder is not supposed to be empty...its ok if the "shared" folder is empty though! you should have FOUR different files in ur "Grub" folder...if they're not in there, than that's a serious problem! ;)

Sorry, but i have to go now...will come back later, and try to help u more! ):P

Cheers! :)

-jammanuser

:D

EDIT: ok...i'm back! so like i was saying before...an empty "Grub" folder is the root of ur problem...there should be at least 4 files in it! if there is not, then i would suggest maybe uninstalling and then reinstalling Wubi? Also...how did u install Wubi? was it from [HERE]("http://www.wubi-installer.org/"), or did u try to install it using the LiveCD? if it was the latter, than u might want to download it from that link, first, and THEN install Wubi, because ur CD might be missing some files! Cheers! :D

---

### Post by mrbfrog on 2008-12-07
thank you very much,  I uninstalled and re downloaded from your link and it seems to be working perfectly right now.  again, thank you.

---

### Post by Jammanuser on 2008-12-07
> **mrbfrog said:**
> thank you very much,  I uninstalled and re downloaded from your link and it seems to be working perfectly right now.  again, thank you.

Cool...i'm glad i could be of assistance! :D

Cheers! :)

-jammanuser

):P

---

