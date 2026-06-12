---
title: "mount works differently in 9beta?"
date: 2009-04-13
forum: General Help
---

### Post by MonsterMaxx on 2009-04-13
Installed mythbuntu 9 beta. Lots of problems, but I'll only ask about this particular one.

I come from Redhat distros so some of my difficulties are just due to being a linux novice and only having exposure to RH flavor distros.


So anyway, I'm trying to mount a windows share in 9beta and it's not working.

sudo mount -t cifs //machine/share /mnt/mountpoint -o username=name,password=pass

fyi: 9beta mounts work for all local devices (two drives in the machine and a bunch of partitions because there's many os's installed.)

Mount cifs doesn't work in 9beta. When I installed 8.1 last night and tried the same command it worked. In fact, when I booted 9beta livecd the mount worked, only after installation to the local drive did the mount not work in 9beta.


Any suggestions would be most appreciated. Thanks in advance.

---

### Post by wolfen69 on 2009-04-13
did you do all updates? there could be a bug somewhere. updates must be done manually by system>administration>update manager. then reboot. if you downloaded the regular beta, there will be over 400 updates at this point.

---

### Post by MonsterMaxx on 2009-04-13
yes, all the updates were done to 9beta

---

### Post by cariboo on 2009-04-13
Have a look at this [thread=288534]howto[/thread]

When referring to a version please refer to the full version number eg: 9.04, 9beta could be confusing.

Jim

---

