---
title: "Edubuntu/LTSP: Remove/Ignore local hardware on Thin Client (in Gnome) ?"
date: 2007-09-13
forum: Desktop Environments
---

### Post by sadams on 2007-09-13
Hi All,

I am setting up an LTSP environment for a pilot/trial in a primary school.
I am running:
  Edubuntu: Feisty 7.04
  LTSP: 5.0.7 (According to Synaptic)

I require some help/pointers on a specific issue:

Once a thin client is booted and i login as a user, the Gnome Desktop appears (all as expected).
I want to create a "minimal" desktop without the icons for the local devices appearing:
  i.e. floppy drive & local hard drive

It seems to me i could potentially do something like...:
 
 i) Edit/hack Gnome (somehow????) to ignore the devices... i.e. not create or display the icons on the desktop
  - Is this possible... how do you achieve it?
 ii) Configure the Thin Client to ignore the actual hardware.... so effectively it is "not there" so Gnome won't see it and create icons for it
   - Is this possible... how do you achieve it?

iii) Some other better/smarter/easier method ?
 - Any suggestions?

I have done some looking around (forums, wiki, googling etc) but can't seem to find this.
Any help/pointers would be very gratefully received.

Many thanks,
  Steve.

---

### Post by swisscow on 2007-09-13
Not sure if this will work but try ALT-F2 then running

```
gconf-editor
```

You can set what appears on the desktop there, certainly with a PC, not so sure with thin clients.


Used to work with a place that ran thin clients - possibly options are available depending on the type of client I remember (5 yrs ago, memory not what it used to be). Don't forget to password protect the thin client settings! Good luck, good use of your time.

---

### Post by sadams on 2007-09-14
Hi,
Firstly @swisscow
thanks for the response...
I had looked at gconf-editor - however it is not clear how/where/what to edit to achieve this.
Can you be more specific/give instructions.... or were you just making a general suggestion for something which might help ?

Secondly... 2 solutions which I got via the LTSP IRC forom (thanks guys):

i) LOCALDEV in conf file
      edit /opt/ltsp/i386/etc/lts.conf
      set LOCALDEV=False in there
I have implemented this and confirm it works

ii) remove users from the fuse group
edit /etc/group and remove named user(s) from the end of the line for the group
  ```
e.g. in /etc/group
    fuse:x:117:bart,lisa,maggie
  becomes
    fuse:x:117:bart,lisa
  in order to disable the remote "fuse" mounts.
```

I trust this helps any others here who are interested.

A third thing...
In a conventional desktop env (i.e. not LTSP)... is it possible to tell Gnome not to show icons for local devices?
e.g. if i have a laptop with several partitions,
  sda1 = WindowsXP
  sda2 = NTFS (shared data part)
  sda3 = ubuntu (an older version)
  sda4 = ubuntu (the one boot to)
then i will by default get icons on my desktop for each of these if they are mounted (via fstab).
So.. if I would like them to be mounted and accessible, can i disable the icon on my desktop ?
i..e can i tell gnome to ignore them (without having to unmount them) ?

Cheers,
  Steve.

---

### Post by swisscow on 2007-09-14
Sorry should have been more clear

I believe (and this was true in Dapper, not sure in Feisty and I use Kubuntu so can't check) in the gconf-editor settings, scroll down to nautilus, click the arrow next to that. Click desktop in the expanded section and then the information you need should be there.

Hope it helps

---

