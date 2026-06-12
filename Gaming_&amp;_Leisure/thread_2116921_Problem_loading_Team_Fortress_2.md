---
title: "Problem loading Team Fortress 2"
date: 2013-02-17
forum: Gaming &amp; Leisure
---

### Post by Edenapple on 2013-02-17
I installed steam on ubuntu but every time it opens a window pops up called "Package Install" and it says:

Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386
[sudo] password for edenapple: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx : Depends: libglapi-mesa (= 8.0.4-0ubuntu0.3)
E: Unable to correct problems, you have held broken packages.
Press return to continue: 

When I press enter steam loads, but when I try to open Team Fortress 2 it says:
"Required OpenGL extension "GL_EXT_texture_compression_s3tc" is not supported. Please install S3TC texture support."

---

### Post by omeomi on 2013-02-17
Which Ubuntu version are you running? 

Have you tried to install the missing dependencies [manually]("http://packages.ubuntu.com/search?keywords=libglapi-mesa")?

---

### Post by Edenapple on 2013-02-17
My ubuntu version is 20.04 LTS and I tried searching for the missing dependencies and installing them but it says "Breaks existing package 'libglapl-mesa-lts-quanta' conflict: libglapl-mesa ()".

---

### Post by rudeboyskunk on 2013-02-17
I assume you mean Ubuntu 12.04, since we're not yet in the year 2020.

Have you tried:  sudo apt-get install -f  ??

---

### Post by efflandt on 2013-02-17
Have you tried:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

That does not upgrade to a different distribution (unless you changed your sources.list) it is just smarter about resolving changing dependencies for your current Ubuntu version.

Or if you are running 64-bit, maybe you need to install **ia32-libs-multiarch**. Steam is 32-bit and I already had that installed when installing Steam beta a couple of weeks ago (since updated to release). Also what video card and driver do you have, because they recommend running most recent (experimental) drivers, at least for my nvidia.

I have been running tf2 in 64-bit 12.04 since late January.

---

### Post by izzydojo on 2013-02-17
hey found this and im having a issue as well ive installed steam on ubuntu 12.04 lts the steam works great ive installed TF2 no problems but when i try to open the game i get a error that states:

Required OpenGL extension "GL_EXT_texture_sRGB_Decode" is not supported. Please Update your OpenGL driver.


my FGLRX driver is up to date and runnning my system is up to date idk what im missing

---

### Post by Edenapple on 2013-02-17
I tried sudo apt-get update && sudo apt-get dist-upgrade, but it says:

Get:1 [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease [836 B]
Get:2 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise InRelease [836 B]                   
Get:3 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates InRelease [836 B]           
Get:4 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports InRelease [836 B]         
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease [836 B]            
Get:6 [http://repo.steampowered.com](http://repo.steampowered.com) precise Release.gpg [836 B]                 
Get:7 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise Release.gpg [836 B]                 
Get:8 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates Release.gpg [836 B]         
Get:9 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease [836 B]                       
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [836 B]         
Get:11 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports Release.gpg [836 B]      
Get:12 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise Release [836 B]                    
Err [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise Release                               
  
Get:13 [http://repo.steampowered.com](http://repo.steampowered.com) precise Release [836 B]                    
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise Release                               
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

E: GPG error: [http://repo.steampowered.com](http://repo.steampowered.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

---

### Post by izzydojo on 2013-02-17
well from what ive looked up and dont quote me but its a error only assiocated with AMD Graphic Cards   this is the url i found 

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

now for me it doesnt seem to work out i get errors with my  amdcccle.exe maybe it will help u idk but amd has the most issues with it from all the forums ive read nvidia seems to have it licked though.

---

### Post by Edenapple on 2013-02-18
I am using NVIDIA GeForce GT 330M, what should I do.

---

### Post by rudeboyskunk on 2013-02-18
> **izzydojo said:**
> hey found this and im having a issue as well ive installed steam on ubuntu 12.04 lts the steam works great ive installed TF2 no problems but when i try to open the game i get a error that states:

Required OpenGL extension "GL_EXT_texture_sRGB_Decode" is not supported. Please Update your OpenGL driver.


my FGLRX driver is up to date and runnning my system is up to date idk what im missing

This is a problem with your graphics card.  I assume you're using an AMD card, because most people getting this error are (including me).  You will have to update to the newest fglrx by downloading the driver from AMD's website and installing it yourself.  Here is a link with instructions:

(Ubuntu 12.04) [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

(Ubuntu 12.10) [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide)

---

### Post by Edenapple on 2013-02-19
I am running ubuntu on parallels. It has VESA: Parallels Video Adapter, does this make it AMD?

---

### Post by izzydojo on 2013-02-20
Ya I did that before posting my issue on here ill reinstall and see If that takes care of it this time

---

### Post by Edenapple on 2013-02-23
Bump.

---

### Post by Edenapple on 2013-02-27
Bump.

---

### Post by Bad Boy Bubby on 2013-02-27
I am no expert but I would suggest installing the latest linux driver direct from nvidia's website.

This link is to the 32 bit version

[http://www.nvidia.co.uk/object/linux-display-ia32-310.32-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-310.32-driver-uk.html)

This is for the video card you mentioned geforce GT330m

I had similar issues with my ATI card until getting the latest driver direct from AMD.

Bubby

---

