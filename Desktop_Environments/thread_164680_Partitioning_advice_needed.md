---
title: "Partitioning advice needed"
date: 2006-04-23
forum: Desktop Environments
---

### Post by QwUo173Hy on 2006-04-23
Usually when I install linux, I use a few partitions. I usually keep /home and /music on partitions of their own so if I want to install a different linux, I can keep my music and my home folder.

When I installed Breezy, I didnt do this because I was afraid of the console partitioner :D I have since used GPartedLiveCD to partition off my music folder (/media/music).

I haven't partitioned off /home yet because I'm afraid that the new partition will confuse Ubuntu and ruin my install. Can anyone tell if its safe to do this? I want to have my system partitioned so I can do a clean install of Dapper when it comes out without formatting my /home folder.

Thanks for any advice!

Jarlath

---

### Post by el3ktro on 2006-04-23
As long as you correctly edit /etc/fstab of your Ubuntu install, everything will be fine. Just create your partitions with the LiveCD you mentioned, then mount your Ubuntu root partition and edit /etc/fstab accordingly, so that /home is on a separate partition.

Tom

---

### Post by jazzmuzik on 2006-04-23
It is safe to create a new partition and then move the contents of your previous /home directory to the new one. You will need to create a line in /etc/fstab that mounts your new /home partition.

---

### Post by QwUo173Hy on 2006-04-23
Thanks guys, thats great.
Tom, your avatar is cool! I use the same one for skype as I'm a 2001 fan.

Thanks again!

Jarlath

---

