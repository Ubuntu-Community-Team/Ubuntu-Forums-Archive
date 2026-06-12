---
title: "Automount Ubuntu"
date: 2011-01-20
forum: Desktop Environments
---

### Post by gimmy32 on 2011-01-20
Original post: in Hardware section concerning RAID 0 not working on 2x2TB on a asus p5ld2 motherboard:

Seem to have solve the problem by buying a sata controller. Now I can mount it by the controller bios as a raid 0 seeing it a 4000gb. I guess the asus p5ld2 controller cannot mount a 2x2TB Raid 0, or it is broken in some way.

I think it could have been done by ubuntu, since that when I set them as non raid in the new controller, the setup in the disk manager looks exactly the same. 2 drives located on the controller sata, but impossible to mount as RAID 0 via ubuntu, only by the controller bios, prior to boot. 

No that I have the two drives, it seems I cannot partition the Disk under the "disk peripheral" (see attached image...in french, sorry.)

If I understand well, ubuntu does not automount the drive automatically and gives it a name. In this case, it changes from /dev/dm-3 to /dev/dm-2. The who TB drives are always /dev/sdd and /dev/sdc. 

My question is, even if I would understand how to automount( which I dont yet, and I tried graphical software such as storage manager and mount manager) how do you automount when the drive name is changing all the time.

Those two software just do not allow me to automount the /dev/dm-3, it only shows dev/sdd and sdc as available. even more, storage manager drives are all gray. Do I have to create a partition ? 

Ill try to post image if someone can tell me how ;)

Thank you.

---

