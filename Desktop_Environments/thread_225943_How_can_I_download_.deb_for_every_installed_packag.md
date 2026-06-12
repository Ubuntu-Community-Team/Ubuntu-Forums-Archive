---
title: "How can I download .deb for every installed package"
date: 2006-07-30
forum: Desktop Environments
---

### Post by mk1970 on 2006-07-30
I have everything I need installled on my desktop PC and now I want to install an identical system without internet access (by installing from the official installation CD and then copying all debs to the target PC and then install all my stuff).

Now, let's say my /var/cache/apt/archives/ is completely empty (only the partial directory is there). How can I download the installation debs for all my installed packages.

What should "cmd" be in the following code? You can see your installed packages by substituting "cmd" with "echo $i"...

```
dpkg -l | grep ^ii | awk '{print $2}' | while read i
do
  cmd
done
```

---

### Post by guru369 on 2006-07-30
I dont know exactly what you mean..
But have you concidered ghost?

Just copy the system to a ghost image and dump it on the new PC...

dekela

---

### Post by mk1970 on 2006-07-30
> **guru369 said:**
> But have you concidered ghost?


I don't want to create a disk image but just to download all the .deb files which are currently installed on my desktop PC.

---

### Post by ardchoille on 2006-07-30
I have 11 computers and here's what I do to get them all with the same installation set up:

1. Install Ubuntu on one computer
2. Install all updates, patches, etc.
3. Run partimage from a liveCD or from another partition (MEPIS has partimage on it). Usually takes about 15 minutes to create the image on a new install
4. Use the image that partimage created along with partimage and install that image to on all the other computers. Usually takes 10 to 15 minutes to install the image per machine.

When that is done, all the computers will have an identical software setup.

Partimage homepage: [http://partimage.org/Main_Page](http://partimage.org/Main_Page)

System Rescude CD has partimage: [http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

Or, find a livecd that has partimage on it: [http://www.distrowatch.com](http://www.distrowatch.com)

---

### Post by chalex on 2006-07-30
A better way to do it with with 
```
dpkg --get-selections > list.txt
```

Then make a clean or basic install of ubuntu on the other machine, copy over the file with the list of packages and do
```
dpkg --set-selections < list.txt
```

I haven't tried this myself, but this is the easy way to duplicate a Debian machine.  You will then need to modify /etc and other preferences.

---

### Post by mk1970 on 2006-07-31
> **chalex said:**
> A better way to do it with with 
```
dpkg --get-selections > list.txt
```
I haven't tried this myself, but this is the easy way to duplicate a Debian machine.

This still doesn't give me a list of URLs etc. which would let me download the files on my desktop PC.

---

### Post by aysiu on 2006-07-31
> **mk1970 said:**
> I don't want to create a disk image but just to download all the .deb files which are currently installed on my desktop PC.
I don't see why you would want to do that. It seems a lot more trouble than it's worth if you want an *identical* system and don't have internet access.

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by mk1970 on 2006-07-31
> **aysiu said:**
> I don't see why you would want to do that. It seems a lot more trouble than it's worth if you want an *identical*

It's not identical, the kernel is 686-smp vs k7.

---

### Post by RAOF on 2006-07-31
You could **probably** use **sudo aptitude install --download-only $i** as cmd.  

But if the difference is a -686 rather than -k7 kernel, why not just install a -386 kernel and then image the drive?  You get a totally working system, that you don't need to mess with, complete with configuration :)

---

### Post by mk1970 on 2006-07-31
The solution is to use aptitude (instead of apt-get), i.e.

```
dpkg -l | grep ^ii | awk '{print $2}' | while read i
do
  sudo aptitude download $i
done
```

---

### Post by mk1970 on 2006-07-31
> **mk1970 said:**
> 
```
dpkg -l | grep ^ii | awk '{print $2}' | while read i
do
  sudo aptitude download $i
done
```

And if I use this script after disabling these two lines

```
#deb http://archive.ubuntu.com/ubuntu dapper main restricted
#deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
```

in other words, only leave the universe, multiverse, dapper-backports and dapper-security lines I get only the packages which have been updated since the official release (which is on the CD-ROM) or which are not on the installation CD (like w32codecs). It means I can burn just the updated/extra stuff to a DVD-RW disk and copy the files to my fresh installation.

---

### Post by mk1970 on 2006-08-03
First I executed this on my desktop PC:

```
dpkg -l | grep ^ii | awk '{print $2}' | while read i
do
  sudo aptitude download $i
done
```

Then I burned the .deb files found in /var/cache/apt/archives to a CD-RW disk with GnomeBaker (you can of course use other burning application like K3b). Next I inserted the CD-RW into the second host and executed:

```
sudo cp /media/cdrom/*.deb /var/cache/apt/archives/
sudo apt-cache gencaches
```

Next I executed [my installation script](http://www.iki.fi/kuparine/comp/ubuntu/install.html) and everything worked without internet access.

The reason I wanted to do this is because I'm using RAID-1 for everything and I assumed the current cloning systems don't understand filesystems on Linux RAID-1 devices.

---

