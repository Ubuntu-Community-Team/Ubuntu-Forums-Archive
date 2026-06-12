---
title: "Multiple configurations issues."
date: 2006-07-10
forum: Desktop Environments
---

### Post by Third Thoughts on 2006-07-10
I have a doozy of a problem. My system is set up so that I have 3 major partitions (not including swap, boot, etc). One is a /home partition with personal files and such. One has Dapper installed on it and the other whatever distro I'm playing around with. I was installing Elive on my extra partition, but due to some unclear instructions and my own stupidity I managed to wipe the home partition. I went to restore it using my backup and found out that the tar archive I had wasn't valid. I managed to restore most of my files, but none my configuration files could be saved. This has led to a couple of strange problems

1. The default terminal setting is white text on white background. I can change the color of the output, but what I'm typing stays white no matter what color I tell it to be. This is true for all terminals except eterm. I can, however, change the background color 
2. I'm getting "perl: warning: Setting locale failed" errors everytime I run a perl script. I've used every variation of sudo dpkg-reconfigure locales, apt-get install localeconf, export LANG=en_US.UTF-8, that I can think of and nothing seems to fix it.

Thats all I've come across for now, but I'm sure there will be other weird quirks that show they're ugly faces

~Andrew S.

---

