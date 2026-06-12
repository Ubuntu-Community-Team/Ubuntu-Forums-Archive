---
title: "Laptop - Virtualisation - Virtual Machines"
date: 2008-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by john pilcher on 2008-05-12
Has anyone tried it on Dell laptops + is there any specific documentation available on this subject.

thanks
John

---

### Post by barichardson5727 on 2008-05-15
I recommend VirtualBox for virtualizaton on linux desktops or laptops. 

As far as non-enterprise level virtualization software goes I have tried VirtualBox, Vmware Workstation, and VMware server on my laptop and I find Virtualbox gives the best overall performance of the three while still offering the same features of the non-free offerings from vmware.

Another cool thing about virtualbox is the ability to load a virtual machine created with vmware.

---

### Post by AcidHawk on 2008-05-15
I have historically used VMware to host virtual machines from other distros to different windows platforms on my Dell Inspiron 9300 laptop.  During my preparation for Ubuntu 8.04 I found some posts about Virtualbox.  

I must say that setting up winxp in virtualbox was simple and I have been VERY impressed at the speed which virtualbox runs this windows machine.

One comment though,  I havent looked at using bridged network from virtualbox yet but have been told that it is not a simple straight forward solution (still need to investigate) however vmware handles bridged networking just perfectly.

HTH

---

### Post by PhrygianCat on 2008-05-15
Best bet would be to use Virtual Box. I have it on mine. Found this to be helpful: [http://ubuntuforums.org/showthread.php?p=4813109](http://ubuntuforums.org/showthread.php?p=4813109). I personally prefer VMware Server, but as I did my research I found 'warning' against it, not that it's impossible.

---

### Post by niteshifter on 2008-05-15
Hi,

Yes, it works on Dells. I use VirtualBox, see my sig.

This forum post has an good guide on host networking (non-NAT) in VBox [here.]("http://ubuntuforums.org/showthread.php?t=346185")

After you install VBox, give the manual a look, it will be at /usr/share/doc/virtualbox/UserManual.pdf
There's a lot of good info on using it in these forums and in [virtualbox.org's]("http://www.virtualbox.org/") [forums]("http://forums.virtualbox.org/").

---

