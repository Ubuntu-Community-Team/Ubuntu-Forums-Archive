---
title: "Lost /home folder after upgrade to ext4"
date: 2009-05-18
forum: General Help
---

### Post by JonasObrist on 2009-05-18
I seem to have messed up my upgrade to ext4 pretty badly. I followed the guide on [kernelnewbies.org]("http://kernelnewbies.org/Ext4") to upgrade my root partition from ext3 to ext4. However after doing so i couldn't boot anymore. So I booted up from the live CD, ran gParted's partition fixing function on the broken partition. Now I was able to boot again but only until the login screen, then it fails because there is no home folder.

I was silly enough not to do a backup of my home (a mistake I'll certainly not do again) but I have a tiny hope I might still be able to recover it because of nautilus and gparted contradicting each other:

gParted sees the partition as a 59.53GB with 8.17GB unused, nautilus shows it as 63.9GB partition with 5.2GB free. (see attached screenshots).

Now if nautilus is right how/where could i retrieve the lost data?

---

### Post by JonasObrist on 2009-05-19
i know bumps aren't good practice but i really need help with this!

---

### Post by JonasObrist on 2009-05-20
anyone? please help!

---

### Post by urosg3 on 2009-05-20
I think its possible to reinstall Ubuntu, without formating this partition. Just mark this partition as a /home, without checking format and ext3, as in previous system.
Good luck

---

### Post by JonasObrist on 2009-05-20
> **urosg3 said:**
> I think its possible to reinstall Ubuntu, without formating this partition. Just mark this partition as a /home, without checking format and ext3, as in previous system.
Good luck

the problem is i want the content of that lost home folder if anyhow possible!

However should I choose to reinstall ubuntu on that partition, will i still have the apps i installed?

---

### Post by bacardiandwatermelon on 2009-05-20
I think you may have to go down the test disk route and use photorec to recover the files. I'm pretty sure it works on ext4.

[http://ubuntuforums.org/showpost.php?p=6780152&postcount=7](http://ubuntuforums.org/showpost.php?p=6780152&postcount=7)

---

### Post by urosg3 on 2009-05-20
> **JonasObrist said:**
> the problem is i want the content of that lost home folder if anyhow possible!

However should I choose to reinstall ubuntu on that partition, will i still have the apps i installed?

You cannot install Ubuntu on this partition. You must leave this partition unformatted, just marked as a /Home Ext3. For root choose another partition in system.

---

### Post by alphacrucis2 on 2009-05-20
> **JonasObrist said:**
> I seem to have messed up my upgrade to ext4 pretty badly. I followed the guide on [kernelnewbies.org]("http://kernelnewbies.org/Ext4") to upgrade my root partition from ext3 to ext4. However after doing so i couldn't boot anymore. So I booted up from the live CD, ran gParted's partition fixing function on the broken partition. Now I was able to boot again but only until the login screen, then it fails because there is no home folder.

I was silly enough not to do a backup of my home (a mistake I'll certainly not do again) but I have a tiny hope I might still be able to recover it because of nautilus and gparted contradicting each other:

gParted sees the partition as a 59.53GB with 8.17GB unused, nautilus shows it as 63.9GB partition with 5.2GB free. (see attached screenshots).

Now if nautilus is right how/where could i retrieve the lost data?

As a matter of interest did you upgrade to Jaunty before running tune2fs to migrate to ext4? If you did it the other way around then that would definitely cause grub to fail as you would have been booting using the version of grub you had with Intrepid which doesn't understand ext4. If you did it the right way around did you remember to run efsck on the partition immediately after tunde2fs? You must also let efsck run to completetion. A bit late now but I wonder if you can pin down what actually caused the problem. As another poster said you may have to resort to testdisk/photorec to recover the data.

---

### Post by JonasObrist on 2009-05-20
> **alphacrucis2 said:**
> As a matter of interest did you upgrade to Jaunty before running tune2fs to migrate to ext4? If you did it the other way around then that would definitely cause grub to fail as you would have been booting using the version of grub you had with Intrepid which doesn't understand ext4. If you did it the right way around did you remember to run efsck on the partition immediately after tunde2fs? You must also let efsck run to completetion. A bit late now but I wonder if you can pin down what actually caused the problem. As another poster said you may have to resort to testdisk/photorec to recover the data.


I upgraded with jaunty installed. I guess the problem occured because i might not have (correctly) unmounted the partition. Also it's not a GRUB problem.

I did run efsck after the upgrade but that one failed...

Gonna try the recovery suggestions above

---

### Post by MichaelDance on 2009-05-20
> **JonasObrist said:**
> I seem to have messed up my upgrade to ext4 pretty badly. I followed the guide on [kernelnewbies.org]("http://kernelnewbies.org/Ext4") to upgrade my root partition from ext3 to ext4. However after doing so i couldn't boot anymore. So I booted up from the live CD, ran gParted's partition fixing function on the broken partition. Now I was able to boot again but only until the login screen, then it fails because there is no home folder.
 
I was silly enough not to do a backup of my home (a mistake I'll certainly not do again) but I have a tiny hope I might still be able to recover it because of nautilus and gparted contradicting each other:
 
gParted sees the partition as a 59.53GB with 8.17GB unused, nautilus shows it as 63.9GB partition with 5.2GB free. (see attached screenshots).
 
Now if nautilus is right how/where could i retrieve the lost data?
 
Ok, Computeractive had said something about firefox using to much of the cashe, the best thing to try first is load firefox then options then pref or clean cashe im at the library without firefox soz. but i did it on my laptop and it saved be much space.

---

### Post by JonasObrist on 2009-05-20
I managed to recover loads of files with PhotoRec, BUT they all seem to be partial, the folder names are gone and the filenames as well. Does that sound like I did something wrong? It looks like a lot of stuff from my home folder is still there but somehow i can't get really get it all in a usable way...

---

