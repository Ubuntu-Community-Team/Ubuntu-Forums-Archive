---
title: "Edgy Eft + Quake 3 + AMD64 = no can do?"
date: 2006-10-26
forum: Gaming &amp; Leisure
---

### Post by tjalve on 2006-10-26
Hi, I installed Ubunty Edgy Eft RC, now apt-get upgraded to the final. I have Nvidia graphics and stuff works great (Beryl/XGL, sound, glxgears etc.). 

I try to follow the guide here [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Quake3]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Quake3") but I get this:

/usr/local/games (29.491Mb) $ sudo sh linuxq3apoint-1.32b-3.x86.run 
Verifying archive integrity... All good.
Uncompressing Quake III Arena Point Release 1.32b.................................................................................................................................................
This installation doesn't support glibc-2.0 on Linux / unknown

So.. first of all, I thought Edgy Eft would come with something higher than glibc-2.0? How can I verify what version of glibc I have?

apt-get -s install glibc don't give me anything..

I need the official version instead of icculus since I need PunkBuster support to play on the Rocket Arena servers I linger on.

If I could only get WoW and Q3A over to Ubuntu I could get rid of windows completely :)

Please help. 

T

---

### Post by dmn_clown on 2006-10-29
This is a known issue on 64-bit systems.

[http://zerowing.idsoftware.com/linux/q3a/#64bits]("http://zerowing.idsoftware.com/linux/q3a/#64bits")

You can also use tar to extract the files.  ```
sh blah-blah.run --tar xvf
```

Need more commands?  ```
sh blah-blah.run --help
``` for a complete list of available options.

---

