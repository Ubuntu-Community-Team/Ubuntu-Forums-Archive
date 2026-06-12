---
title: "HOWTO: Installing and playing Rigs of Rods"
date: 2006-12-08
forum: Gaming &amp; Leisure
---

### Post by patrick295767 on 2006-12-08
Hi,
  
screenshots: [http://repository.rigsofrods.com/files/Screenshots/](http://repository.rigsofrods.com/files/Screenshots/)
video: [http://patrick295767.sitesled.com/video/Challenger.wmv](http://patrick295767.sitesled.com/video/Challenger.wmv)
 
   
check it &  run this script :
(-f -y attention !)
```
cd /tmp
wget http://patrick295767.sitesled.com/lib/libCgGL.so  
wget http://patrick295767.sitesled.com/lib/libCg.so
cp libCg.so  /usr/lib
cp libCgGL.so  /usr/lib
#sudo apt-get -f -y install xarchive
sudo apt-get -f -y install libopenal0 libopenal0a libalut0    xmessage file-roller
sudo apt-get -f -y install ogre-tools ogre-doc  libogre5c2a blender-ogrexml 
###wget http://repository.rigsofrods.com/files2/RoR-0.29b-linux.tgz
wget http://repository.rigsofrods.com/files2/RoR-0.30-linux.tgz
##wget http://repository.rigsofrods.com/files/Official_Releases/RoR-0.29b-linux.tgz
xmessage "extract it where you would like and type ./start to run the game. Enjoy ! " &
##xarchive RoR-0.29b-linux.tgz 
file-roller RoR-0.30-linux.tgz

```
and ./start to play 

Enjoy !
  
---
[http://repository.rigsofrods.com/files/Official_Releases/](http://repository.rigsofrods.com/files/Official_Releases/)
[http://rigsofrods.blogspot.com/2006/11/linux-release-candidate.html](http://rigsofrods.blogspot.com/2006/11/linux-release-candidate.html)
trucks: [http://repository.rigsofrods.com/files/Trucks/](http://repository.rigsofrods.com/files/Trucks/)

---

### Post by patrick295767 on 2006-12-10
I updated the script. I like the game. :-)

---

### Post by frankerooney on 2006-12-11
game looks good, but the 
wget [http://patrick295767.sitesled.com/lib/libCgGL.so](http://patrick295767.sitesled.com/lib/libCgGL.so)
and the other wget from the same site fails. Looks like a file hosting problem?

---

### Post by MaximB on 2007-01-08
Partick
1. the wget link is broken and I don't know were or how can I get those files otherwise
2.please update to the newest version 0.30

thanks.

---

### Post by patrick295767 on 2007-01-08
> **MAXDDARK said:**
> Partick
1. the wget link is broken and I don't know were or how can I get those files otherwise
2.please update to the newest version 0.30

thanks.

Thanks max for the info. 
I updated the wget in the script. ;) 
0.30 ? oh ... I am looking ... [http://repository.rigsofrods.com/files2/RoR-0.30-linux.tgz](http://repository.rigsofrods.com/files2/RoR-0.30-linux.tgz)

---

### Post by MaximB on 2007-01-08
thanks Patrick , now I found out that I had those files already (but not in the game dir) , the problem is that that worthless program - beagle , couldn't find them.

---

### Post by kaffelars on 2007-02-15
A friend told me that the ligcg-files where a part of Nvidias cg toolkit.
I found the files in the Cg Redistributable Binaries-zip on this page:
[http://developer.nvidia.com/object/cg-redistributable-binaries.html]("http://developer.nvidia.com/object/cg-redistributable-binaries.html")

Can't wait to try it when i get home :)

---

### Post by Bmtt on 2008-09-23
I added deb [http://apt.rigsofrods.com](http://apt.rigsofrods.com) to my source list but when I open my synaptic package manager I get this error.


E: Malformed line 57 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


Can anyone HELP!

Thank you

---

### Post by Perfect Storm on 2008-09-24
```
cat /etc/apt/sources.list
```

---

### Post by Bmtt on 2008-09-24
Ok, I've tried everything that I could find on the forums. Maybe somebody could walk me through please.

Thank you

---

### Post by MaximB on 2008-09-25
> **Bmtt said:**
> Ok, I've tried everything that I could find on the forums. Maybe somebody could walk me through please.

Thank you


Please follow AI's suggestion.
Post us your sources.list (if it's still the same problem as before).

---

### Post by MikeDK on 2012-01-05
Anyone got RoR working under newer versions of ubuntu than 10.04?

---

