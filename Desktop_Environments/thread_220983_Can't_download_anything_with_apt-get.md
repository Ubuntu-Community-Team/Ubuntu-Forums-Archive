---
title: "Can't download anything with apt-get"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Kadishev on 2006-07-22
Hi, I just upgraded to Dapper yesterday but upon restart X failed to start because it couldn't find my NVIDIA drivers.  Usually when this happens I manually install a driver I got from NVIDIA from the terminal (this is why I upgraded, so I can use nvidia-glx-legacy). However, now the kernel is different and I need to kernel source to compile the old drivers.  

So I'm stuck at a shell trying to use apt-get to download nvidia-glx-legacy or the kernel source and every time I try to download anything it gets to around 9% and then hangs until the connection to us.archive.ubuntu.com times out.  Anyone know what is wrong?

---

### Post by kpurcell on 2006-07-22
ubuntu seems to be down right now
I am also trying to download something via synaptic packet manager and it won't

---

### Post by not_yet on 2006-07-22
apt works fine here

have you changed your sources list for dapper?

---

### Post by dfego on 2006-07-22
It seems like everything from [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) doesn't work...

---

### Post by Kadishev on 2006-07-22
Anyone have any idea when us.archive will be back up?  I can't get back to X without it...

---

### Post by Amaranth on 2006-07-22
I gave up on us.archive long ago and editted my sources.list to point directly to archive.ubuntu.com.

---

### Post by Zikona on 2006-07-22
I am unable to connect to us.archive.ubuntu.com also:


Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
99% [Connecting to us.archive.ubuntu.com (146.137.96.15)]

---

### Post by orzechowskid on 2006-07-22
hmm... traceroute shows me getting stuck at

fwzv662.net.anl.gov (130.202.222.65)

not sure how many hops away from us.archive.ubuntu.com that is, but maybe the problem isn't with Ubuntu.

---

### Post by Kadishev on 2006-07-22
I tried replacing all the "us.archive.ubuntu.com"s with "archive.ubuntu.com" and even "ca.archive.ubuntu.com" and every time they broke before even starting the download complaining about missing dependencies, whereas using us.archive it found all the dependencies and asked me if I wanted to install them (before it hangs).  Is there some other way to get around us.archive?

---

### Post by mlind on 2006-07-22
> **Kadishev said:**
> I tried replacing all the "us.archive.ubuntu.com"s with "archive.ubuntu.com" and even "ca.archive.ubuntu.com" and every time they broke before even starting the download complaining about missing dependencies, whereas using us.archive it found all the dependencies and asked me if I wanted to install them (before it hangs).  Is there some other way to get around us.archive?


I reckon your best change is to try alternative mirrors, or wait until archive.ubuntu.com is reachable again from your location.
Some mirrors may be unsynced which causes those dependency errors..

---

### Post by Zikona on 2006-07-22
I was able to get my Repositories working for now. I have backed up my current sources.list and replaced them with the ones from [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) .

---

### Post by Unoone on 2006-07-22
> **Zikona said:**
> I was able to get my Repositories working for now. I have backed up my current sources.list and replaced them with the ones from [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) .

Ever since I stated using Ubuntu I have been looking for a link like this. Thanks for the link. 

Does anyone know of such a link that covers the Ubuntu basics in other areas like graphic drivers?

---

### Post by mlind on 2006-07-22
> **Unoone said:**
> 
Does anyone know of such a link that covers the Ubuntu basics in other areas like graphic drivers?

I've always found community wiki docs very useful
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by Unoone on 2006-07-22
> **mlind said:**
> I've always found community wiki docs very useful
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Thanks! I got Nvidia working in Dapper! In Breezy I installed the Synaptic nvidia drivers without a problem. In Dapper got errors in the glxinfo and no 3d support until now. Must be a bug or something. It works now! 

I had to replace my Dapper Repos with the linked ones in this thread. I got Opera to install without errors. 

I still have yet to get java and flash to work in Dapper.

---

### Post by mlind on 2006-07-22
> **Unoone said:**
> 
I still have yet to get java and flash to work in Dapper.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by beameup on 2006-07-22
So the us repos are down. I was about to throw this box out the window LOL.](*,) 

I tried psychocats list but it still hangs on the US repo.

---

### Post by erikpiper on 2006-07-22
It took me quite a while to figure out- I used this sources generator, and canada repositories (CA country code) Faster than the working US repos......

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by manwe on 2006-07-22
ca.archive.ubuntu.com is currently down as well
-manwe-

---

### Post by penquin on 2006-08-04
although it is a little slow I am using UK instead of US and they are working

---

### Post by kabronkline on 2006-08-04
I'm having problems with archive.ubuntu.com...

I have created a dedicated post for it:
[http://www.ubuntuforums.org/showthread.php?p=1338102#post1338102]("http://www.ubuntuforums.org/showthread.php?p=1338102#post1338102")

Ubuntu seriously needs a reliable place to check network status.

---

