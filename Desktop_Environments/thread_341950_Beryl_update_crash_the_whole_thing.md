---
title: "Beryl update crash the whole thing"
date: 2007-01-19
forum: Desktop Environments
---

### Post by Guillaumeb on 2007-01-19
Ok can anyone tell me what's happening with the update i received to day, Beryl wont start at all. I have no windows manager at all, I'm getting an error for two updates 

E: /var/cache/apt/archives/beryl-plugins_0.2.0+svn20070118-r2838+3v1ubuntu0+svn20070118-r2839+3v1ubuntu0_i386.deb: trying to overwrite `/usr/lib/beryl/libdbus.so', which is also in package beryl-dbus
E: /var/cache/apt/archives/beryl-plugins-nonfree_0.2.0+svn20070118-r2838+3v1ubuntu0+svn20070118-r2839+3v1ubuntu0_i386.deb: trying to overwrite `/usr/lib/beryl/libdbus.so', which is also in package beryl-dbus

Also I get an error thru the terminal 


[I]root@laptop:~# apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy/main Translation-en_US    
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy/universe Translation-en_US
Get:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release.gpg [189B]
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Translation-en_US
Get:3 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:4 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release 
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release 
  
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy Release 
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-updates Release
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports Release             
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release [10.6kB]           
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy/main Packages                            
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release                                 
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy/restricted Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy/main Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy/restricted Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy/universe Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy/universe Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 10.8kB in 0s (13.4kB/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
root@laptop:~# 

[/I]

I don't have a key and don't know where to get it or what to do with it.

Could anyone  explain this to me?

In my source.list file I have:


deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

That's what I put to upgrade from Beryl 0.0.1 to the lastest version

Thank you

Also the Beryl manager only have General Options and Extras now....

---

