---
title: "Can't eject CD"
date: 2006-01-02
forum: General Help
---

### Post by rainbowjoshua on 2006-01-02
Okay, so I like to run some KDE apps, like k3b, and it was working just fine.  I've burned a bunch of CDs with it.  I was astonished to see that GnomeBaker didn't seem to have an option to "copy DVD".  

I don't know what changed, but I install lots of stuff  :).  I did just add the backports repositories and upgrade k3b through backports, but now, I'm trying to copy a DVD with only one drive, and when the time comes to remove the disc and put in the blank, I cannot get it out.  When I use the disk mounter to try to eject the disc, I get:

```

Unable to eject media
eject: unable to eject, last error: Invalid argument

```

And when I hit the eject button in k3b, nothing happens.  I feel like this has something to do with having kde on my system while running gnome.  I haven't actually been able to run kde, however.  When I try, for some reason I can't determine, my .ICEauthority file becomes owned by root, and I can't log into kde OR gnome.  I then have to go to a terminal, sudo chown that file back to my user and then I can log in to gnome.  This happened once when I was trying to run k3b.

Any ideas?
Thank you!
Joshua

---

### Post by futz on 2006-01-02
When K3b spits out the source disk and demands a blank, just start a Nautilus (I usually have one running in the background anyway), right-click on the source drive and click eject.

Then put in your blank disk and go back to K3b. The K3b people need to build this into the program, but for now this workaround does the trick.

---

### Post by rainbowjoshua on 2006-01-02
That is exactly when I get the error message described, the same whether I do it through the disk mounter appet, or nautilus.

---

### Post by sargeras on 2006-02-18
I have the same problem, however, if I use "sudo eject" it will eject and allow me to continue the burn process.  I'm wondering if I have a permissions error with k3b.

hope this helps

---

### Post by nalmeth on 2006-02-18
If you want to eject the CD whenever the eject button is pushed (sounds logical right?) automatix can set that up for you..
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

