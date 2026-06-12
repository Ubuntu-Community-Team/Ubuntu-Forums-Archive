---
title: "System sluggish during heavy disk access"
date: 2009-11-13
forum: Desktop Environments
---

### Post by locketine on 2009-11-13
I've been having this problem ever since using CIFS for my remote samba shares. If I manage to generate enough disk traffic that the samba server can't keep up, my system starts hard locking. Sometimes it's really brief, sometimes it lasts 5 seconds. Today, something interesting happened. I had this exact same problem while modifying files on my local disk.

I was willing to accept it with the remote shares because those were generally large file transfers that I could walk away from my computer for but getting dead locks accessing files on my local disk? Come on.

I have a theory that this is caused by the linux scheduler giving precedence to i/o processes and freezing normal processes out of the cpu. This is probably not a problem normally because disk i/o is really slow but if the data stream is intermittent enough it might be causing the task scheduler to constantly swap processes. Obviously, networked drives would be more likely to cause this sort of issue due to having a virtual disk io process and a real network io process but if I can do it with my local drive something needs to be fixed.

If someone wants to try to reproduce my local disk problem they can do what I did and run the following command in their console. This command fixes variable bit rate mp3 file headers so that they show correct bit rate and track length in Amarok and possibly other players. Make sure to install vbrfix before running the command.
```
find ~/Music -type f -name "*.mp3" -exec vbrfix {} {} \;
```

---

