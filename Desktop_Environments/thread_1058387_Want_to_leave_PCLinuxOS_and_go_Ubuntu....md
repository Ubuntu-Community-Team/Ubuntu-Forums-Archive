---
title: "Want to leave PCLinuxOS and go Ubuntu..."
date: 2009-02-02
forum: Desktop Environments
---

### Post by CGHPaul on 2009-02-02
I currently have a workhorse system that has PCLinuxOS on it, but after seeing the latest release of Ubuntu (8.10)...I want it on my workhorse.

My current system has a "/" partition and a "/home" partition.

What I want to do is install Ubuntu on this system, and basically replace the other flavor of linux.

Is there a way to do that?

I still want an administration or "root" account AND a user account on the end result.

I know next to nothing about Linux drive formatting and such.  So, please, be patient with me.  I really want to get over to Ubuntu, but I don't want to lose all the stuff I have on the drive.

---

### Post by adamlau on 2009-02-02
Install as usual, only mount but_do_not_format /home.

---

### Post by CGHPaul on 2009-02-03
I installed Ubuntu on a laptop, and it didn't look familiar with partitioning options.  Not a whole lot I really understand about the partitioning end of everything.

I learned that I could re-install PCLinuxOS and install the op system in the "/" partition after formatting it.  And it sounds like that's what you're asking me to do.

But, it looks GREEK to me in Ubuntu's partitioner.

Can you dumb it down for me?

I'm operating with a "/" partition that has 21 gigs of room.  Is that too small for an Ubuntu system directory?

---

### Post by damis648 on 2009-02-03
During the setup, select to manually partition. At that stage, select your current / partition and click 'edit'. Select to use as Ext3 and mount point as /, as well as check the format box if it is not already. Click OK, and then select your current /home partition and edit. Choose to use as Ext3 and the mount point to be /home. Click OK, and MAKE SURE FORMAT IS NOT CHECKED ON YOUR /HOME PARTITION! Then proceed with the install. :popcorn:

Also 21GB / is fine.

---

### Post by abn91c on 2009-02-03
I had Mandriva 2009 in another computer, I booted to the ubuntu live cdrom then used the guide partitoning option, I just used the slide bar to give Ubuntu 50% of the 40 gig drive, it was an old computer, then ran the installation and both Mandriva and ubuntu were happy in my old PC( 400mhz celeron, 512MB ram, pC100 motherboard,ISA sound-had to set up manually in ubuntu-Belkin 54g USB wireless and SIS video which worked fine in mandriva and low graphics in Ubuntu. So my point is try dualboot, it asked me during setup to migrate Mandriva settings.

---

