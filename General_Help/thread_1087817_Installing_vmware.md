---
title: "Installing vmware"
date: 2009-03-05
forum: General Help
---

### Post by watsgoodg on 2009-03-05
Tried the following website to install vmware but i get the error E:couldn't find package parallels when running "sudo apt-get install parallels".  Anyone know any other ways to install?  Im using ubuntu 8.10.

[http://www.techthrob.com/2009/03/02/virtualization-in-linux-a-review-of-four-software-choices/](http://www.techthrob.com/2009/03/02/virtualization-in-linux-a-review-of-four-software-choices/)

---

### Post by williane on 2009-03-05
parallels is a mac VM. you need to go to vmware.com and download it. i dont believe VMware is in the repository.

actually if this is your first attempt with a VM you might try virtualbox. its really simple to get running.


edit: oh i didnt realize there was a "parallels" for linux. i have no experience with that. sorry =/

---

### Post by watsgoodg on 2009-03-05
I have used virtual box in Linux works ok, easy to install via add/remove.  Still prefer vmware. 


> **williane said:**
> parallels is a mac VM. you need to go to vmware.com and download it. i dont believe VMware is in the repository.

actually if this is your first attempt with a VM you might try virtualbox. its really simple to get running.


edit: oh i didnt realize there was a "parallels" for linux. i have no experience with that. sorry =/

---

### Post by Operan on 2009-03-05
Virtual Box is better than VMWare in Ubuntu 8.10. VMware Workstation usually hungs up and it gets error in keyboard ( you can fix this error)

---

### Post by williane on 2009-03-05
yeah i like vmware myself. i have server 2.0 running on intrepid. when i installed it i just DL'd the .tar from their site (no DEB package) and installed it that way. went really smooth.

---

### Post by watsgoodg on 2009-03-06
> **williane said:**
> yeah i like vmware myself. i have server 2.0 running on intrepid. when i installed it i just DL'd the .tar from their site (no DEB package) and installed it that way. went really smooth.

Ok so I downloaded the .tar file, how do I install?

---

### Post by smurray on 2009-04-10
Has anybody made any headway on this?  I've searches quite a few threads, and I have no clue how to even start getting VMWare Workstation 6.5 up, much alone installed.

I went the route of getting the RPM and then using alien to turn it into a .deb package and dpkg installing it, but I see no difference on my machine.  No added tabs, not even a vmware in the /etc/init.d

I'm getting pretty confused here

---

### Post by fieroboom on 2009-04-10
Just wanted to add another vote for VirtualBox... The [closed source edition](http://www.virtualbox.org/wiki/Linux_Downloads), because it fully supports USB, automatic bridging, and supposedly 3D rendering inside the VM (haven't tested that for myself yet). That's what I'm currently running, and haven't had a single glitch or freeze yet.
:D
-Paul

---

