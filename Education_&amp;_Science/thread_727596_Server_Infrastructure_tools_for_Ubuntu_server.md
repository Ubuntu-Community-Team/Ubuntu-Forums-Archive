---
title: "Server Infrastructure tools for Ubuntu server"
date: 2008-03-17
forum: Education &amp; Science
---

### Post by piousp on 2008-03-17
Ok, i'm not really sure where to post this, so move it as you see fit.

The thing is, i'm doing a research in a Networking class for College. The main topic is Server consolidation and SANs.
I was researching the servers infrastructure, and i found out about some areas to consider while designing the infrastructure. This areas are:

  *  Application Deployment and Management
    * (IT) Asset and Inventory Management
    * Backup and Archiving
    * Batch Processing
    * Configuration and Change Management
    * Cluster Management
    * Data Management
    * Desktop Management
    * Disaster Recovery
    * Enterprise System Management
    * File Transfer Management
    * Job Automation and Scheduling
    * License Management
    * Network Management
    * Performance (Load and Stress) Testing
    * Patch and Update Management
    * Print Management
    * Security Management
    * Storage Management
    * User Management
    * Web Systems Management

Ok, the question is, which software and programs can i use to cover these areas in ubuntu server, which, by the way, i'm gonna use as the servers OS.

Here is the info i was reading: [LINK]("http://www.serverwatch.com/tutorials/article.php/3494341") (I know the article is quite old, but serves its purpose)

What i can think of, is that probably, much of those areas are covered by default in Ubuntu Server, but i do need to know which ones are covered, and which ones arent.
Thanks in advance!!
Long live Linux! :)

---

### Post by piousp on 2008-03-17
Ha ha, its gonna be a LOoOOOooOOoong night

---

### Post by PilotJLR on 2008-03-17
If you're talking server consolidation, then talk about virtualization.

In other words, instead of running a boatload of underutilized servers for various apps (windows and linux), virtualize them with Ubuntu Server and Xen. Then your physical hosts can be as highly utilized as possible, which saves upfront cost, as well as power, cooling, and rackspace costs.

This plays into a SAN because it would be a terrible architecture to not house the guests on some form of monolithic storage. In other words, the physical hosts can boot to local disk (or a san lun, whichever), and then your vm's themselves can reside on SAN.
This makes backup a snap (literally... bad pun, i know).

And then there is a BC DR play by replicating the vm lun to a DR site. That's when it gets more than twice as expensive... but this is a requirement for an enterprise.

---

### Post by piousp on 2008-03-18
Whoah! You got me there ;)
Indeed, i was thinking in virtualization (but i haven't reach that part of my investigation =P)

Your last sentence
> And then there is a BC DR play by replicating the vm lun to a DR site. That's when it gets more than twice as expensive... but this is a requirement for an enterprise. its quite cryptic for me right now. That only can mean one thing: i need to research MORE :lolflag:

THANKS for your help!!!

---

### Post by PilotJLR on 2008-03-18
I was talking about Business Continuity / Disaster Recovery... basically, the idea is to do synchronous replication from primary to the DR site. If the primary site goes down for fire, flood, etc, then you have an exact replica of the big VM lun at the DR site.
You then power up your VM's using the replicated LUN and resume operations.

This may not be relevant to your paper, since it's not really consolidation (the opposite, if anything). But BC DR is a really important planning element to enterprise computing. We have 1 primary and 2 DR sites where I work, since we lose a LOT of money for even a minute of downtime.


If you want a softball, also throw in blade servers to this... it's for physical space and power and cooling consolidation.
Add virtualization on top of that and you're golden!

[http://h18004.www1.hp.com/products/blades/solutions/customers.html](http://h18004.www1.hp.com/products/blades/solutions/customers.html)

---

### Post by piousp on 2008-03-18
Thanks again!
I was thinking in using the blades (haven't read your article, i'm working right now ;) ) and for the san/lun, i read i need to take special considerations for its management. I was thinking in using GFS on the whole SAN. I'm not really sure if that way, the servers can have concurrent acess to it without currupting the FS and without having to having to administrate each luv. Damn, i'm not even sure of what the heck i'm talking about! :lol
Thanks!

---

### Post by PilotJLR on 2008-03-18
GFS is great for when machines need concurrent access to the same LUN, but I wouldn't do that unless you have a reason to. People use cluster filesystems basically when they need to deploy a cluster application (and those require access to a shared lun). For security and safety, it's otherwise best to avoid GFS. So GFS is really good, but only when used at the right time.
If you need something like a file server, then what you can do is present a single LUN from the SAN to a NAS head, like an EMC Celerra. The nas head then exports the LUN via whatever protocol you set it up for.

If you want to get really fancy with virtualization, then explore VMware Infrastructure. It's closed source, and will not have an Ubuntu slant, but it's really cool. You can, for example, live migrate VM's across physical hosts with basically no downtime. It's pretty cool to see that. VI3 does, since it is a type of cluster, use a proprietary VMFS cluster filesystem, which allows nodes to all see the VMFS lun, which is where the VM's live.

---

### Post by piousp on 2008-03-18
Man, you should do the research for me.... :lolflag:
So, since in the case the company dont have any apps that need concurrent access, i'm just going to ignore GFS.
So, if i understand right, i can use virtually any type of FS system on a specific LUN, right? Say, for example, Reiserfs. And, i can have a diferent FS on each LUN, right. If say, i use iSCSI for the SAN, i can assing a LUN to a specific server?

As you can see, i havent read practically anything about SANs so far, mainly 'cuz i'm kinda focused right now on the server side of the case.

Do you know any articles i can read? Thanks for your time and help!

---

### Post by piousp on 2008-03-18
I reading good old wiki

---

### Post by PilotJLR on 2008-03-19
You're on the right track! 
With either iSCSI or Fibre channel, LUN masking (it has several names) is used to control what servers can see the storage.
A lot of iSCSI vendor use IQN to LUN mask. You basically make a LUN on the SAN, then present it to the host you want via the hosts' IQN. All others would then not be able to see that LUN.
Once the iSCSI LUN is connected to a host, the host perceives it a lot like local storage. For example, a linux host will see the lun as something like /dev/sdb, /dev/sdc, etc.
What you do with it then is up to you... Reiser, ext, ntfs, etc etc

Since you are doing iSCSI, one cool thing you can do is get VMware Server (it's free) and make an iSCSI target that you "host" ubuntu can connect to.
For example:
[http://www.vmware.com/appliances/directory/217](http://www.vmware.com/appliances/directory/217)

---

### Post by piousp on 2008-03-25
Woah, thanks a lot.
Just one more question. Whats the diference between XEN and VMWare?
I know both are for virtualization, and i wanna be sure i'm understanding this.

---

### Post by PilotJLR on 2008-03-26
Sure, no problem!

VMware ESX is a "bare metal hypervisor." This means you install ESX much like an operating system (it is, in fact based on RHEL). You then manage it via a Windows client application (or command line on the ESX box, which most people don't do in normal operation).

Xen is a hypervisor that runs in a Xen-enables Linux kernel. In reality, these two things are pretty similar... except that a Xen distribution makes it easy to add X, other applications, etc, which basically turns the machine into a hosted system instead.

The big difference right now is management tools and vendor support. VMware is adopted heavily and well supported. The tools also make it easy to use for CLI-adverse Windows guys. Xen is more like what VMware was several years ago... it's less "point and click" but it gets the job done.

---

### Post by piousp on 2008-03-27
PilotJLR,

thanks for all the information you gave me! :KS
This discussion was amazingly educative! Thanks again for your help, effort and time.
Just to let you know, i got a 95 out of 100 in my investigation!
But the end of it, doesnt mean i gonna stop reading about this stuff.
Thanks again!

---

