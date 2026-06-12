---
title: "Linux Virtualisation?"
date: 2007-05-24
forum: Desktop Environments
---

### Post by transatlant1c on 2007-05-24
Hi all, I was just wondering how I would go about installing Windows XP on a virtual machine on my Ubuntu 7 installation..? I hav used VMware before, and it was good to a point, but is there better out there? If so, how do I install it? Does anybody know how to compile the VMware server code for example? I have downloaded it and now I'm stuck.. Hopefully someone can help me out!! :)

---

### Post by tgm4883 on 2007-05-24
There is virtualbox in the repos.  Or you could use vmplayer which is also in the repos.  For vmplayer you will need a premade virtual machine which you can get from easyvmx.com

---

### Post by transatlant1c on 2007-05-27
How do I retrieve vmplayer or virtualbox if it's in the repos? I kind of know what you mean.. But I'm still very new to Linux, so some help would be good :) Can you tell me how to install it?

---

### Post by blacksadness on 2007-05-27
hey,
i dont' think virtualbox is in the repos, or at least it wasn't when i installed it 3 days ago, you should download the feisty package from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) and just double click it :) if you want vmware player or vmware server (both free but virtualbox is better in my opinion) you can install them using synaptic from your system ->Administration menu if you're using Ubuntu, i'm not sure what's the package manager on Kubuntu though.. you could also open the terminal and type sudo apt-get install vmware-player

---

### Post by tgm4883 on 2007-05-27
> **transatlant1c said:**
> How do I retrieve vmplayer or virtualbox if it's in the repos? I kind of know what you mean.. But I'm still very new to Linux, so some help would be good :) Can you tell me how to install it?

Sudo apt-get install vmware-player

I was wrong, virtualbox isn't in the repo's (Could of swore it was back when I used edgy)

I recommend virtualbox, unless you use 64-bit, in which case I haven't been able to get virtualbox working on 64-bit yet although there is a guide (didn't work for me)

---

### Post by blacksadness on 2007-05-27
> **tgm4883 said:**
> Sudo apt-get install vmware-player
I was wrong, virtualbox isn't in the repo's (Could of swore it was back when I used edgy)


actually it's in the automatix i think, because i had it in my repo before, but i found out it wasn't as i was installing ubuntu on my friend's laptop.

anyway between any vmware and vbox i'd go with vbox..

---

### Post by tgm4883 on 2007-05-27
> **blacksadness said:**
> actually it's in the automatix i think, because i had it in my repo before, but i found out it wasn't as i was installing ubuntu on my friend's laptop.

anyway between any vmware and vbox i'd go with vbox..

I don't use automatix (although that doesn't mean it's not in there).  I use to have the sources.list from ubuntuguide.org so I suppose if I had those activated it would be in there.

---

### Post by RAOF on 2007-05-27
If you've got a modern CPU (Core 2 Duo, **recent** AthlonX2), and are running Feisty, then you can install the "kvm" package, which uses the hardware-virtualisation capabilities of your shiny new processor to make it really fast :)

---

### Post by Twintop on 2007-05-28
> **RAOF said:**
> If you've got a modern CPU (Core 2 Duo, **recent** AthlonX2), and are running Feisty, then you can install the "kvm" package, which uses the hardware-virtualisation capabilities of your shiny new processor to make it really fast :)

I'm having some issues with VMWare-Player on my system and am looking at alternatives. What would you consider a **recent** AthlonX2? I've got a  3800+ Toledo (Socket 939, 2.0GHz, 2x512KB L2 Cache) and 2GB Dual Channel DDR. Do you think that would be enough uoomph to get the job done with KVM, or should I try something like VirtualBox or some other VM software? Thanks!

---

### Post by transatlant1c on 2007-05-28
> **blacksadness said:**
> actually it's in the automatix i think, because i had it in my repo before, but i found out it wasn't as i was installing ubuntu on my friend's laptop.

anyway between any vmware and vbox i'd go with vbox..

Ok, well I don't have a dual core machine, and VM Ware has worked before for me (when I was running Linux in VM mode..), but I want to emulate Windows XP.. What would be the best way/software to get the job done? Could you provide links or something for me?

---

### Post by blacksadness on 2007-05-28
> **transatlant1c said:**
> Ok, well I don't have a dual core machine, and VM Ware has worked before for me (when I was running Linux in VM mode..), but I want to emulate Windows XP.. What would be the best way/software to get the job done? Could you provide links or something for me?

from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) download the [feisty deb]("http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_feisty_i386.deb") and install it for virtual box, for vmware you can use vmware-player with sudo apt-get install vmware-player..
Now about the best software to do the job, i personally have used vmware-server and prefer virtualbox over it.. dont' know about vmware workstation though..

---

### Post by transatlant1c on 2007-05-28
> **blacksadness said:**
> from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) download the [feisty deb]("http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_feisty_i386.deb") and install it for virtual box, for vmware you can use vmware-player with sudo apt-get install vmware-player..
Now about the best software to do the job, i personally have used vmware-server and prefer virtualbox over it.. dont' know about vmware workstation though..

Ok I will stick with Virtualbox then :) I have tried VM Ware, and it was pretty good.. But I'll see if Virtualbox is any better.. :) Thanks again!!

---

### Post by RAOF on 2007-05-28
> **Twintop said:**
> I'm having some issues with VMWare-Player on my system and am looking at alternatives. What would you consider a **recent** AthlonX2? I've got a  3800+ Toledo (Socket 939, 2.0GHz, 2x512KB L2 Cache) and 2GB Dual Channel DDR. Do you think that would be enough uoomph to get the job done with KVM, or should I try something like VirtualBox or some other VM software? Thanks!

I believe that your chip is too old (only very new chips have the virtualisation hardware - it's not a matter of oomph :)).  However, the description of the "kvm" package (aptitude show kvm, or search in synaptic) will give you a terminal command you can run to work out whether or not your CPU has the necessary hardware.

---

### Post by Twintop on 2007-05-28
> **RAOF said:**
> However, the description of the "kvm" package (aptitude show kvm, or search in synaptic) will give you a terminal command you can run to work out whether or not your CPU has the necessary hardware.

Thanks again for the advice, guidance, and help RAOF. The following code would have returned something if my chip has propper hardware support.

```
david@alethea:~$ egrep '^flags.*(vmx|svm)' /proc/cpuinfo
david@alethea:~$ 
```

...but it didn't. ;\ Oh well, I managed to get a 32-bit version of XP working without too many problems with VMWare (except for some full screen resizing issues). Thanks again for the advice! :)

---

### Post by jonlink on 2007-06-16
> **tgm4883 said:**
> Sudo apt-get install vmware-player
I recommend virtualbox, unless you use 64-bit, in which case I haven't been able to get virtualbox working on 64-bit yet although there is a guide (didn't work for me)
Virtualbox works fine on 64-bit now, just installed it today and everything seems to be going smoothly (knock on wood)

---

### Post by tgm4883 on 2007-06-17
> **jonlink said:**
> Virtualbox works fine on 64-bit now, just installed it today and everything seems to be going smoothly (knock on wood)

Yes it does now, although two weeks ago when I wrote that it didn't work so much.  Works pretty good now though.

---

### Post by scrime on 2007-06-17
VMWare Workstation rocks!  Wine emulates Windows programs very well, Cedega plays Windoze games.  VMware needs lots of memory and reasonably fast CPU to get the most out of it though.  I wish I could get a VMWare 6 linux key, got it but no key.  VMWare Workstation 5 works great though.

---

### Post by tgm4883 on 2007-06-17
> **scrime said:**
> VMWare Workstation rocks!  Wine emulates Windows programs very well, Cedega plays Windoze games.  VMware needs lots of memory and reasonably fast CPU to get the most out of it though.  I wish I could get a VMWare 6 linux key, got it but no key.  VMWare Workstation 5 works great though.

You can get a key for it [here]("http://www.vmware.com/request_processor?nextPage=/vmwarestore/newstore/category_wkst.jsp&action=CATALOG.GETGROUPS&application=store&ProductGroupCodes=EXT-STORE-WKST6,EXT-STORE-WKST6-SUP,EXT-STORE-WKST6-MK")

---

### Post by scrime on 2007-06-19
Brilliant!!  ;)  Thanks for the help!

---

### Post by tgm4883 on 2007-06-19
> **scrime said:**
> Brilliant!!  ;)  Thanks for the help!

No problem

---

### Post by fjf on 2007-06-19
The problem with vmware server is sharing folders with the linux host.  You have to setup samba and it is not easy.  I couldn't make it work.  The workstation version does that, but it costs 180$.  Virtualbox is not as stable, but if you get it to work well, it is free and it shares folders with the host with no problems at all.  Make sure you get the new 1.4 version.  The previous one had a bug with the sharing folders feature.

---

### Post by tgm4883 on 2007-06-19
i think 1.4 has a bug in the sharing folders feature too.  When I try to transfer large files through it, The virtual machine crashes.

---

### Post by fjf on 2007-06-20
This 1.4 version is not very stable.  My whole ubuntu freezes now and then when installing or using the windoze xp.  I hope next version fixes that.

---

