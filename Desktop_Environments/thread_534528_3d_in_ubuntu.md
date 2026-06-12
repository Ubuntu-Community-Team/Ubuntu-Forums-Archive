---
title: "3d in ubuntu"
date: 2007-08-25
forum: Desktop Environments
---

### Post by joeabiraad on 2007-08-25
Hi 

I am a newbie and i have just installed ubuntu on my HP laptop .
I just want to add some 3d effects and to make it fun to use 

Is there any librairy / plugin  i should install ? and how ? 

Thank you

---

### Post by ArtF10 on 2007-08-25
It's called Compiz Fusion..look in the desktop effects and customization Section, there are plenty of How-Tos there.  BUT, you will need to ensure that you either have an NVIDIA graphics card OR (if you have an ATI card) are relatively comfortable with Ubuntu.

Here's a good link:  [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

ANY MODIFICATIONS MUST BE MADE AT YOUR OWN RISK.  I would HIGHLY recommend backing up any important data BEFORE trying anything UNOFFICIAL and this plugin is UNOFFICIAL.

All the best.

---

### Post by dreadlord_chris on 2007-08-25
> **joeabiraad said:**
> Hi 

I am a newbie and i have just installed ubuntu on my HP laptop .
I just want to add some 3d effects and to make it fun to use 

Is there any librairy / plugin  i should install ? and how ? 

Thank you


What you're probably wanting is [Compiz Fusion]("http://compiz.org/"), but before you go diving in - what kind of graphics chip is you HP using, and how much memory do you have?

---

### Post by dreadlord_chris on 2007-08-25
> **ArtF10 said:**
> It's called Compiz Fusion..look in the desktop effects and customization Section, there are plenty of How-Tos there.  BUT, you will need to ensure that you either have an NVIDIA graphics card OR (if you have an ATI card) are relatively comfortable with Ubuntu.

Here's a good link:  [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

ANY MODIFICATIONS MUST BE MADE AT YOUR OWN RISK.  I would HIGHLY recommend backing up any important data BEFORE trying anything UNOFFICIAL and this plugin is UNOFFICIAL.

All the best.

Intel GPU's seem to be working well too....

---

### Post by ArtF10 on 2007-08-25
Well that's good to know.  I hope that the plugin with Gutsy does not compromise system performance as much as this unofficial one does (although it won't do much on faster computers).

---

### Post by joeabiraad on 2007-08-26
thank you all for your response,

I have an INTEL graphic card with 768 MB of RAM ....

that should do it ?

---

### Post by Dark Star on 2007-08-26
SUre it will : )am on Intel onboard GPU with 256 Mb ram and Cf runs like charm :D

---

### Post by joeabiraad on 2007-08-26
thank you

i will keep u posted :popcorn:

---

### Post by joeabiraad on 2007-08-26
Hi again

I cant seem to install beryl properly,
Can you guide me to a thread where install instructions are available for INTEL graphic card ?

here is the error messages:


```

Err http://www.getautomatix.com edgy/restricted Packages                       
  404 Not Found
Ign http://media.blutkind.org dapper/main Packages                             
Ign http://packages.freecontrib.org edgy-plf/non-free Sources                  
Err http://packages.freecontrib.org edgy/free Packages                         
  404 Not Found
Err http://www.getautomatix.com edgy/universe Packages                         
  404 Not Found
Err http://packages.freecontrib.org edgy/non-free Packages                     
  404 Not Found
Ign http://media.blutkind.org dapper/aiglx Packages                            
Err http://packages.freecontrib.org edgy-plf/free Packages                     
  404 Not Found
Err http://www.getautomatix.com edgy/multiverse Packages                       
  404 Not Found
Ign http://www.beerorkid.com dapper/aiglx Translation-en_US                    
Err http://packages.freecontrib.org edgy-plf/free Sources                      
  404 Not Found
Err http://media.blutkind.org dapper/main Packages                             
  404 Not Found
Err http://packages.freecontrib.org edgy-plf/non-free Packages                 
  404 Not Found
Err http://media.blutkind.org dapper/aiglx Packages                            
  404 Not Found
Err http://packages.freecontrib.org edgy-plf/non-free Sources                  
  404 Not Found
Ign http://www.beerorkid.com dapper Release                                    
Ign http://www.beerorkid.com dapper/main Packages
Ign http://www.beerorkid.com dapper/aiglx Packages
Err http://www.beerorkid.com dapper/main Packages
  404 Not Found
Err http://www.beerorkid.com dapper/aiglx Packages
  404 Not Found
Fetched 6927B in 28s (247B/s)
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/source/Sources.gz  404 Not Found
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://media.blutkind.org/xgl/dists/dapper/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/source/Sources.gz  404 Not Found
Failed to fetch http://media.blutkind.org/xgl/dists/dapper/aiglx/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://www.beerorkid.com/compiz/dists/dapper/aiglx/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: GPG error: http://www.getautomatix.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


```



Thank you

---

### Post by joeabiraad on 2007-08-26
Anyone  ?

---

### Post by Dark Star on 2007-08-26
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104) Check out this thread for guides related to Ubuntu 3d Managers.. btw  I would suggest you Cf :D

---

