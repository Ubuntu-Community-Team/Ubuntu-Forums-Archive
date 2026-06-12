---
title: "How can I add KDE desktop to Gnome with Kubuntu CD?"
date: 2006-07-14
forum: Desktop Environments
---

### Post by thalliwell on 2006-07-14
I would like to add the KDE desktop to Gnome (Ubuntu 6.06).

I know you can download it but I have dial-up and would like to use the Kububtu 6.06 CD that I also have.

I have tried to add it to my sofware repositories but it stll looks elsewhere,
may be because the versions are aout of date?

Any help would be appreciated.

---

### Post by shawnrgr on 2006-07-14
you need to add the cd to the respritory list using apt-get or apt-cd. im not sure of the command. then you can use somthing like aptitude to install it.

---

### Post by sharperguy on 2006-07-21
Never done this but in System>Administration>Software Properties there an Add CD option. Try adding the kubuntu CD and then using synaptic to install kubuntu-desktop.

---

### Post by fallingleaf on 2006-08-05
I have the same situation.  I don't really want to download 150MB on my dialup connection:-( 

I think thalliwell is right that some of the cd packages are not the newest versions so it looks to the online repositories.  Is there some way to force apt to use the older software versions?

I did add the cd under software properties.

This thread: 

[http://ubuntuforums.org/showthread.php?t=214780](http://ubuntuforums.org/showthread.php?t=214780)

says that it is not possible to do with the live CD, only the alternate install CD.  It seems like there ought to be a way, though.  I mean, the packages are on the CD, right?

---

