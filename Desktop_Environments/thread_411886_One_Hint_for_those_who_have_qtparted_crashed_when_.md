---
title: "One Hint for those who have qtparted crashed when installing"
date: 2007-04-17
forum: Desktop Environments
---

### Post by maybee on 2007-04-17
I tried to install many times the Kubuntu from live cd. None suceeded. Finally I found out that it is due to qtparted crashing. When I open a terminal and run 
```
sudo qtparted
```
it delivers a message:
```
No Implementation: Support for opening ntfs file systems is not implemented yet.
```

That is ridiculous, because the qtparted is version 0.4.5-cvs, which is acclaimed to be able to resize ntfs system from the homepage of qtparted. No idea what is going on there.

Besides I google "ubuntu qtparted crash" and find out this is so long and common a problem that quite a few people have met and reported it as bugs but simply remains unsolved since Dapper released.

In the end, one quick and working solution is to install gparted( which is used in Ubuntu) using live cd first
```
sudo apt-get updated
sudo apt-get install gparted
```
and then run gparted and do whatever you want to free some empty space on your hardisk.  The Kubuntu installer will automatically select the free space to install.

This works for me quite well, I believe there are quite a few people out there have experienced the same problem as I had. I hope this helps you.:)

---

