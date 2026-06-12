---
title: "help with ipod and amarok"
date: 2006-07-24
forum: Desktop Environments
---

### Post by dpike619 on 2006-07-24
I've been having trouble using ipod support in amarok 1.4.1(I'm running it in Gnome btw.)  When I try to autodetect the device it doesn't work(I'm assuming this feature doesn't work in gnome based on the error message I get).  So then I try to manually configure it.  When I do this the only option for which plugin to use that comes up is generic audio player.  If I use this one , it detects the ipod, but when I look at it I see the whole directory structure of the ipod instead of the names of all the artists and songs.  If anyone knows how I can fix this let me know.  Thanks.

---

### Post by Thund3rstruck on 2006-07-24
Yea, autodetect never worked for me either (video ipod). Also I noticed on this version of amarok I have had a lot of issues when running it as a regular user vice sudo. 

In any event I ran amarok as root

$sudo amarok

Then I went to Settings > Configure - Amarok > Media Devices > Add Device

In the dialog I seleted the ipod driver and changed the mount point to /media/ipod.

Once I did this, it detected everything perfectly. 

to determine where your ipod is being mounted run:
```

$ sudo mount | grep -i ipod

```

It should be mounting in /mnt/ipod or /media/ipod

---

### Post by dpike619 on 2006-07-24
The problem I'm having is that regardless of if I run it as root or as a regular user, the ipod driver does not show up, just 'generic audio player' and 'do not handle'.  Any ideas on how to get the ipod driver to show up?

---

### Post by dpike619 on 2006-07-24
Ok, nevermind I figured it out on my own.  I guess the version I had was the one from the repository so I just uninstalled and then got the onw from the kubuntu repositories.  If anyone else is having this problem check this thread:

[http://ubuntuforums.org/showthread.php?t=221338]("http://ubuntuforums.org/showthread.php?t=221338")

---

