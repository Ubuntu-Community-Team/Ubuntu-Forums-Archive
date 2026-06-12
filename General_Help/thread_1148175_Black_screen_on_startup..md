---
title: "Black screen on startup."
date: 2009-05-04
forum: General Help
---

### Post by roberwt on 2009-05-04
Hey guys, I've got a problem starting up my ubuntu machine. I run Ubuntu 8.04. I run it as a fileserver, with 4 1TB discs in a software Raid-5, which results in 2 TB of storage room (NTFS). Also, there is an ubuntu startup disc (/root, /swap, /home, ext3) of 320GB and an external backup disc of 1 TB for the raid setup (NTFS). 

Last week, the backups wouldn't run anymore because the raid exceeded 935 GB. I bought a new 1,5 TB disc, formatted to NTFS and hooked it up. As it wouldn't mount, i tried mounting it with my limited (to say the least) knowledge of linux. As you can imagine, I messed up. 

I somehow got my disc to mount, and ran a backup of the raid drive which completed properly. But I think I somehow mounted the drive on my /home partition, as I couldn't see what data was on there. I have two shortcuts in my workbar, 1 firefox, 1 home, but when I clicked them I would get an error message telling me it couldn't find the place/location of that file. I thought that if I'd reboot, the mount points would reset and that everything would run as smooth as before.

That obviously didn't work. After rebooting, i got several error messages and now I'm stuck with a black screen.

However, all the other computers that are on the network can still access the raid drive as they usually could. When I found that out, i tried to see whether the computer did start up. It somehow does, but I'm still stuck at a black screen. When I move the mouse, (logically) nothing shows up. When I move it rigorously though, I can see it once every 10 frames. 

Can anyone help?

Thanks,

Rob

---

