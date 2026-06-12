---
title: "Problems with APT functions"
date: 2009-03-20
forum: General Help
---

### Post by Kealozim on 2009-03-20
I'm current using Feisty and I'm having trouble downloading packages using apt-get. I try in the prompt and type 'sudo apt-get install irssi' and this is the output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package irssi

So I asked around and came to the conclusion the problem was with my sources.list so I tinkered around with that a bit. I tried with the default that came with the distro and then I got a new one to no avail. Here is the output that I get when I run 'apt-get update':

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package irssi
sscott47@sscott47-laptop:~$ sudo apt-get update
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty Release.gpg
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/main Translation-en_US               
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty Release                              
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/main Packages                        
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/main Packages                        
  404 Not Found
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty Release.gpg                                   
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty/main Translation-en_US                        
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty/restricted Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty/universe Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty/multiverse Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates Release.gpg
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/main Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/restricted Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/universe Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/multiverse Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security Release.gpg
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/main Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/restricted Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/universe Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/multiverse Translation-en_US
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty Release
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates Release              
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security Release             
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty/main Packages                
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty/restricted Packages          
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty/universe Packages            
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty/multiverse Packages          
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/main Packages        
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/restricted Packages  
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/universe Packages    
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/multiverse Packages  
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/main Packages       
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/restricted Packages 
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/universe Packages   
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/multiverse Packages 
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty/main Packages                
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty/restricted Packages          
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty/universe Packages            
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty/multiverse Packages          
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/main Packages        
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/restricted Packages  
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/universe Packages    
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/multiverse Packages  
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/main Packages       
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/restricted Packages 
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/universe Packages   
  404 Not Found [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/multiverse Packages 
  404 Not Found [IP: 146.137.96.15 80]
Ign [http://www.davidpashley.com](http://www.davidpashley.com) ./ Release.gpg                
Ign [http://www.davidpashley.com](http://www.davidpashley.com) ./ Translation-en_US
Ign [http://www.davidpashley.com](http://www.davidpashley.com) ./ Release
Ign [http://www.davidpashley.com](http://www.davidpashley.com) ./ Packages
Err [http://www.davidpashley.com](http://www.davidpashley.com) ./ Packages
  404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/dists/feisty/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://mirror.anl.gov/pub/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://mirror.anl.gov/pub/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://www.davidpashley.com/debian/irssi/./Packages.gz](http://www.davidpashley.com/debian/irssi/./Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

My sources.list file looks like this:

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty main restricted
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty universe multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-security main restricted
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-security universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/) feisty main
deb [http://www.davidpashley.com/debian/irssi/](http://www.davidpashley.com/debian/irssi/) ./
#beryl is now added to the feisty repository.
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

The input on the 404 Errors and failure to fetch is the exact same errors it was giving me with the previous sources.list(the one that came with the OS). So what I'm asking is probably apparent, how do I get my apt-get to work and what did I do wrong? By the way, I'm trying to install irssi on this computer which is how I stumbled into this problem. Any help that can be offered would be greatly appreciated. Thanks!

---

### Post by zvacet on 2009-03-21
You have problems because Feisty is no longer supported.You have few options:

1. upgrade to Gutsy but it will get to the end of life in April and you will have same problems again

2. install Hardy if you want long term support (until 2011) or install Intrepid.If you install Intrepid you will be able to upgrade to Jaunty in April.

If you do fresh install make separate home partition if you don´t have one.You can do it following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") or [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.

---

