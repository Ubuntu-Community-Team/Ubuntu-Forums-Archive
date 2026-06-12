---
title: "Extreme hard drive failure with JFS"
date: 2009-06-11
forum: General Help
---

### Post by wobbleyhead on 2009-06-11
I've been running Intrepid with a JFS since it was released, yesterday my hard drive that contained root died :( I didn't see any major problems with it at the time because i have /home mounted on a different hard drive altogether. 

My / hdd is completly beyond repair apparently one of the platters is a wobbley (possibly due to a fall my pc took during a recent house move, i don't really know)

the problem i have now is that my /home drive (in jfs) is fine i can run diags on it from os x (mounted on a hard drive caddy) when i boot back into ubuntu on my mac to try and recover the data all i get is 

mount: wrong fs type, bad option, bad superbock on /dev/sdb1, missing codepage or helper program, or other error in some cases useful info is found in syslog -try dmesg | tail or so

am i missing something to mount this drive or i am completley lost without the former / hard drive :-k?

thanks in advance

wobbleyhead

---

### Post by DGortze380 on 2009-06-11
> **wobbleyhead said:**
> I've been running Intrepid with a JFS since it was released, yesterday my hard drive that contained root died :( I didn't see any major problems with it at the time because i have /home mounted on a different hard drive altogether. 

My / hdd is completly beyond repair apparently one of the platters is a wobbley (possibly due to a fall my pc took during a recent house move, i don't really know)

the problem i have now is that my /home drive (in jfs) is fine i can run diags on it from os x (mounted on a hard drive caddy) when i boot back into ubuntu on my mac to try and recover the data all i get is 

mount: wrong fs type, bad option, bad superbock on /dev/sdb1, missing codepage or helper program, or other error in some cases useful info is found in syslog -try dmesg | tail or so

am i missing something to mount this drive or i am completley lost without the former / hard drive :-k?

thanks in advance

wobbleyhead

Just to clarify.

What is the file system type on the drive you're trying to mount?
What OS are you using to mount the drive, OS X?

---

### Post by wobbleyhead on 2009-06-11
im trying to mount the hard drive with ubuntu, its formatted with jfs. i hadnt tried under os x. is there a way to do this? at the min ihave it attached via a usb cradle to my mac.

---

### Post by DGortze380 on 2009-06-11
> **wobbleyhead said:**
> im trying to mount the hard drive with ubuntu, its formatted with jfs. i hadnt tried under os x. is there a way to do this? at the min ihave it attached via a usb cradle to my mac.

It appears you need to use the default and rw options while mounting JFS.

---

### Post by wobbleyhead on 2009-06-20
That sorted it, much thanks

wobbleyhead

---

