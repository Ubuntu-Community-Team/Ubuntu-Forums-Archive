---
title: "Nvidia Geforce 6600 problems"
date: 2009-01-16
forum: General Help
---

### Post by niwatori1 on 2009-01-16
ok i had the graphics card alredy configured with a rather outdated guide and got it to work.
however when i installed a linux header update it failed to start xserver
so i recovered it in recovery mode and tried the guide again, it still failed.
after that i just installed the raw driver from nvidia that failed.
next i enabled the restricted drivers manager,that failed to start as well.
then as a last ditch effort i tried envy i uninstalled all other nvidia using it and reinstalled them that also failed.
it worked before a linux headers update but not after,is there a guide that isnt outdated to install this card?
Also i decided to boot from 2 hard drives 1 is the linux box with the bad driver the 2nd one it a windows one with a standard install(drivers ,antivirous ,ect)
the resolution and features avalable on windows far outclass linux for some resone for instance the resolutuon on linux maxed out was 1024x768 on windows its like 1268x1064or something like that. is there any fix?:confused::popcorn:

---

### Post by tilerwen on 2009-01-16
Sometimes Nvidia drivers have problems determining your monitor settings. Can you post your Xorg.0.log?

---

### Post by JSorrell on 2009-01-16
> **niwatori1 said:**
> ok i had the graphics card alredy configured with a rather outdated guide and got it to work.
however when i installed a linux header update it failed to start xserver
so i recovered it in recovery mode and tried the guide again, it still failed.
after that i just installed the raw driver from nvidia that failed.
next i enabled the restricted drivers manager,that failed to start as well.
then as a last ditch effort i tried envy i uninstalled all other nvidia using it and reinstalled them that also failed.
it worked before a linux headers update but not after,is there a guide that isnt outdated to install this card?
Also i decided to boot from 2 hard drives 1 is the linux box with the bad driver the 2nd one it a windows one with a standard install(drivers ,antivirous ,ect)
the resolution and features avalable on windows far outclass linux for some resone for instance the resolutuon on linux maxed out was 1024x768 on windows its like 1268x1064or something like that. is there any fix?:confused::popcorn:

I had similar problems when I went to upgrade to the new 180.XX drivers. What fixed it for me was:

Download the drivers you want from nvidia,

```
sudo apt-get purge nvidia
```

- switch to TTY1 via ctrl+alt+F1 -

```
sudo /etc/init.d/gdm stop
sudo run [path-of-nvidia-drivers.sh]
(work through the nvidia script)
sudo /etc/init.d/gdm start
```

For some reason, my drivers got xorg.conf got completely messed up when I started mixing installation methods of the drivers. This isn't completely uncommon with nvidia drivers, it seems. Purging the drivers completely then reinstalling them with the official script worked beautifully for me.

---

