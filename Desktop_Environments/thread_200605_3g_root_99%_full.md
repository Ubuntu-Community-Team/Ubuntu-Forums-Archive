---
title: "3g root 99% full"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Scunizi on 2006-06-20
When I reinstalled 6.06 fresh I partitioned a 3g root, 1g swap and the remainder for /home.  I get notifications after running 6.06 since the day of the stable release that root "/" is low on memory.  It started notifing me at 96% and now is at 99%.  

Is there a way to repartition without reinstalling everything to increase the size of root and decrease /home?

I remember reading a while back some log files get huge and need to be purged on occation.  I'm not sure if this just applied to Flight xx or to stable as well.  If that's the case, where do I find the log files to delete? (I've seen them before but just forgot where to look).

I've upgraded to i686 kernal and removed the 386 kernal for space.

What get's put into root that makes it grow past the initial install?  Certain files or drivers for installed programs?

Thanks for your replies and help.  Noob learning fast!

---

### Post by xXx 0wn3d xXx on 2006-06-20
You can use the Ubuntu install disc to resize your home partition and add it to your root partition. A good size for the root (/) parition is 10-15 gb. The rest can be dedicated to /home. I would recommend the Gparted live cd for re-partitioning your drive.

Edit: Alot of things get put in root. Applications, settings, temporary files....

---

### Post by lotheac on 2006-06-20
Anything and everything that doesn't get put on other partitions goes to your root partition. So in your case, anything that's not in /home is using space from your root partition.

Logs are stored in /var/log. Also, downloaded packages get stored to /var/cache/apt/archives - you can remove them by doing 'apt-get clean' (see man apt-get).

---

### Post by ifokkema on 2006-06-20
[QUOTE=xXx 0wn3d xXx]A good size for the root (/) parition is 10-15 gb.
(...)
Alot of things get put in root. Applications, settings, temporary files....[/QUOTE]
I must agree that 3 GB is not a lot of space for Linux. But 10-15 GB?!!?? What do you do with that space? If you don't compile much yourself, and you don't have that much *-dev packages laying around, I don't think you'll ever get near the 10 GB, especially if you run an `apt-get clean` a couple of times a year.

---

### Post by Scunizi on 2006-06-20
Thanks everyone.  I originally partitioned the / with 3g because of a thread I read either wiki or somewhere here that not much more than 3g is needed for root.  Obviously mistaken.  I'll attempt to re-part tonight.  I have Synaptic setup to automatically remove install packages after install so hopefully it's doing it's job and isn't leaving old .deb's lying around and I haven't downloaded any -dev packages that I know of.... at least deliberately.

I take it GParted Live is a downloadable iso.  I'll look and make one.

Thanks!

---

