---
title: "Easy Ubuntu Clustering"
date: 2009-01-04
forum: Education &amp; Science
---

### Post by ajt on 2009-01-04
Discussions about Ubuntu Clustering seem to be scattered over several forums, and discussion about the Easy Ubuntu Clustering blueprint have been dormant so long that the threads are archived and marked read-only!

I want to re-start discussion about Ubuntu clustering here, where Ubuntu users in Education and Science can contribute: This is related to my proposed blueprint for a "Bioinformatics workstation/server for Ubuntu" [https://blueprints.launchpad.net/ubuntu/+spec/biobuntu]("https://blueprints.launchpad.net/ubuntu/+spec/biobuntu"), which I've marked as obsolete now that NEBC have released Bio-Linux5 based on Ubuntu 8.04 LTS [http://nebc.nox.ac.uk/biolinux.html]("http://nebc.nox.ac.uk/biolinux.html")

The Beowulf 'clustering' and grid aspects of my blueprint overlap with those of the "Easy Ubuntu Clustering" blueprint. In particular, creation of Kerrighed packages for Ubuntu: Some (very) old Debian packages have been removed from the Kerrighed website because they are badly out of date with the upstream sources. I've compiled the latest Kerrighed sources under Ubuntu 8.04, and booted it successfully. I'll post details on the "Easy Ubuntu Clustering" wiki [https://wiki.ubuntu.com/EasyUbuntuClustering]("https://wiki.ubuntu.com/EasyUbuntuClustering")

Tony.

---

### Post by Kellemora on 2009-01-12
Hi ajt

Glad you brought this back to the front again!

I was partly involved in the SETI project, quite a number of years ago now though, not in the computer end, just the CPU sharing end is all.  UC of Berkely would use my shared computers as a part of their Beowulf Cluster.

More recently I have done a little on-line research into connecting a few of my computers here together into a cluster, hopefully to speed up some of the intense graphics work we do.

I've already retrofitted 3 of my computers with gigabyte LAN cards and played around with trying to figure out how to set them up, but I either kept hitting a brick wall or when I did find some instructions, they were so far over my head it was pitiful.

What led to this in the first place was, I wanted to learn more about how servers work, so I downloaded and installed Edubuntu.
Edubuntu works out of the box so to speak, but all the computers become dumb terminals and use the computing power of the computer the workstations are connected to, as well as burn up all the memory available.  Although I liked the idea of a server, I didn't like the fact IT had to provide everything, including the CPU resources.

With so many computers sitting around here, I thought, why not tie them all together.  After all, we have dual and quad core computers now, so how hard could it be anyhow......?

Turns out, it's WAY over my head right now, hi hi..........
Nonetheless, I've learned to do different things on different computers using a KVM then taking all the output and stuff it on a file server.  That way I can keep working on other things while the crunching is being done on other machines.  NOT a Cluster of course, just more efficient use of the machines I do have here.

Since then I've dumbed down to a single Data File Server, which is nothing more than File Sharing, and keep all the working programs on different machines, whichever is best for the project at hand.

But wouldn't it be nice to be able to put all that computing power to use by tying it all together like it was one large computer?

I see it done all over the place.  4, 6, 8, up to 36, 150 and 250 computers all working together.  But they are for specific projects designed to use such a system.

Any any case, I'm going to keep monitoring this thread and hope it goes somewhere positive and progressive!

TTUL
Gary

---

### Post by ajt on 2009-01-12
> **Kellemora said:**
> Hi ajt

Glad you brought this back to the front again!

Hello, Gary.

Thanks for joining this thread about Ubuntu Clustering :-)

I've been running openMosix for quite a while under Ubuntu 6.06 on our Beowulf cluster:

[http://bioinformatics.rri.sari.ac.uk]("http://bioinformatics.rri.sari.ac.uk")

I've posted a few times about openMosix on the Ubuntu Forums, but the threads are very dispersed so I decided to try and focus a discussion here in Education and Science where, I believe, potential Beowulf users might pick up on the thread!

> **Kellemora said:**
> 
I was partly involved in the SETI project, quite a number of years ago now though, not in the computer end, just the CPU sharing end is all.  UC of Berkely would use my shared computers as a part of their Beowulf Cluster.

More recently I have done a little on-line research into connecting a few of my computers here together into a cluster, hopefully to speed up some of the intense graphics work we do.


We ran SETI as a test load when I first built our Beowulf, but I found it increasingly difficult to justify using all that electricity and switched to running Folding@home until we got into the top 1,000 ;-)

> **Kellemora said:**
> 
I've already retrofitted 3 of my computers with gigabyte LAN cards and played around with trying to figure out how to set them up, but I either kept hitting a brick wall or when I did find some instructions, they were so far over my head it was pitiful.


There are good instructions about how to setup DHCP and PXE boot Kerrighed at:

[http://www.kerrighed.org/wiki/index.php/Kerrighed_on_NFSROOT]("http://www.kerrighed.org/wiki/index.php/Kerrighed_on_NFSROOT")

[http://www.kerrighed.org/wiki/index.php/Kerrighed_on_NFSROOT_(contrib)]("http://www.kerrighed.org/wiki/index.php/Kerrighed_on_NFSROOT_(contrib)")

> **Kellemora said:**
> 
[...]
But wouldn't it be nice to be able to put all that computing power to use by tying it all together like it was one large computer?

I see it done all over the place.  4, 6, 8, up to 36, 150 and 250 computers all working together.  But they are for specific projects designed to use such a system.


It's not that complicated if you are motivated enough to experiment. My summer student Kenny Strouts wrote a brief tutorial about his project installing Kerrighed under Debian Etch:

[http://bioinformatics.rri.sari.ac.uk/drupal/?q=wiki/tutorial_kerrighed]("http://bioinformatics.rri.sari.ac.uk/drupal/?q=wiki/tutorial_kerrighed")

> **Kellemora said:**
> 
Any any case, I'm going to keep monitoring this thread and hope it goes somewhere positive and progressive!


Please do, and see if you can interest any of your friends and colleagues in the thread too.

Bye,

    Tony.

---

### Post by kloplop321 on 2009-01-14
I am excited about computer clustering as well, but because of no ubuntu availability I have been trying live CD's, and one of the computers I want to use it on doesn't have support for my LAN card. :( and it doesn't know how to do WiFi either, it thinks it is just an ethernet connection

---

### Post by ajt on 2009-01-14
The kerrighed project have recently announced a Mandriva live CD running the Kerrighed Kernel:

[http://www.kerrighed.org/forum/viewtopic.php?p=607#607]("http://www.kerrighed.org/forum/viewtopic.php?p=607#607")

You can use this to see if your computers would run Kerrighed, but beware that it runs a DHCP server, so don't do it on someone else's LAN ;-)

Bye,

    Tony.

---

### Post by kSt. on 2009-01-14
Good paper (few years old though) -

"OpenMosix, OpenSSI and Kerrighed: A Comparative Study"
[http://hal.inria.fr/docs/00/07/06/04/PDF/RR-5399.pdf](http://hal.inria.fr/docs/00/07/06/04/PDF/RR-5399.pdf)

OpenMosix is no longer maintained.  Supported distributions for openSSI are Fedora Core 3 and Debian Sarge (with work in progress to port to Etch & Lenny) - so I've no idea as to the status of OpenSSI with regards to Ubuntu.  (Maybe someone could shed some light on this?)

Kerrighed is exciting, but still a research project - not yet production ready.  At the moment, node failure under Kerrighed causes the whole cluster to freeze.  Work is being done to solve this problem; see the following; 
[http://article.gmane.org/gmane.linux.cluster.kerrighed.user/69](http://article.gmane.org/gmane.linux.cluster.kerrighed.user/69)

At present the best place to seek information concerning Kerrighed is the mailing list, see [http://news.gmane.org/gmane.linux.cluster.kerrighed.user](http://news.gmane.org/gmane.linux.cluster.kerrighed.user)

---

### Post by ajt on 2009-01-14
I'm still running openMosix (linux-2.4.26-om1), but I'm planning to upgrade to Kerrighed. I tried out openSSI under Ubuntu 6.06 and 8.04, but had a lot of problems just trying to get it to run. There was some discussion about SSI recently on the beowulf list.

Apparently, kerrighed is used in production by Kerlabs:

[http://www.kerlabs.com/-Home-.html]("http://www.kerlabs.com/-Home-.html")

However, I agree Kerrighed is still quite fragile...

My colleague Luca Clivio from the Mario Negri Institute in Milan visited Christine Morin's group and they were extremely helpful. It seems that Kerrighed functionality has been their priority, but the current version is more robust. One thing we could do is help to package Kerrighed for Ubuntu, and get more people interested in using it.

I posted a message to the kerrighed-users list about this dicussion. My objective in starting this thread is to encourage people to try getting Kerrighed running under Ubuntu. It is already quite well supported by Mandriva. However, that is an rpm-based distribution and I want to use Ubuntu because I use bio-Linux (which is based on Ubuntu).

Bye,

    Tony.

---

### Post by djamu on 2009-01-14
Hi all,

I've been using / compiling kerrighed for some years now. ( 3D, non-academic )


My thoughts / experiences  / ideas on kerrighed:


I'll sum up a couple of points that I'll elaborate.

1. It's a bad idea to use the Ubuntu > rather use a stock debian.
Although ubuntu originates from debian, a lot of things changed aside from the kernel version.  It's easier to upgrade a debian kernel then to downgrade an ubuntu one. ( And just forget about compiling it the ubuntu way ... )

2. Someone mentioned OpenSSI which is nearly dead > know that Kerrighed re-used most of the OpenSSI + Mosix source.

3. While it's being the most likely candidate to be used by mere mortals, it lacks some elementary functionality ( aside from the outdated howto's & documentation ).
Despite the info on their site, some advertised functionality will not ( ever ) be available 
[http://www.kerrighed.org/wiki/index.php/Status](http://www.kerrighed.org/wiki/index.php/Status)
Roadmap  >november 2008 > thread migration will NOT be implemented any time soon.
This is very misleading, and leaves me with mixed feeling knowing that it is (was) a EU funded operation, that is now run by Kerlabs.

I made some inquiries via a major german corporation in regard to aforementioned feature ( Just to make sure I got an honest reply).

I cannot fully disclose the document but in short it reads that Kerlabs doesn't see any benefit in developing thread migration any further. This because of the small user base that might actually use it ..... (sic)
It must have been a prank if this wasn't a genuine answer. Nothing wrong with out-of-this-world academics, but really how can a company / management be so ignorant for not seeing the huge benefits to the community..
About everyone I know ( in 3D ) would hook up their computers to create a mini cluster(s) ..

I also got an estimate from Kerlabs > the cost to fully implement / support thread migration....


4. Kerrighed live CD > don't bother trying to run it on vmware machines, kernel doesn't support PCNET32 ( NIC drivers vmware uses ). 
I'll release my own LiveCD soon ( has proper failover head-node with iptables nat / gateway, webinterface, support for most high-end renderers ( LW / RIB / Maya / Houdini etc .. ) + 3rd party plugin support hooks > to control cluster from within an application ( 3D/video ) etc...
Just need to work a bit on an interface.
( volunteers register on my site )


So in short:

Partially because of for-mentioned reasons there's a big chance I'll fork the project.
Another reason is that my  targeted  userbase is completely different > I don't need fancy checkpointing on 500 node clusters / hot adding / removing etc... 
Most users of this fork will cluster less then 10 computers ( so no need for infiniband / myrinet ).

I've already set up a bug tracker so ....


2 routes to get this done > 

-use venture capital ( or other private funding ) > which will make software de-facto proprietary
-use donations ... and keep it open sourced ...


More ideas ?

---

### Post by ajt on 2009-01-14
Hello, djamu.

Not sure why you think it's a bad idea to use Ubuntu?

The Kerrighed kernel is based on the 'vanilla' kernel sources, so it doesn't make much difference if you compile it under Debian or Ubuntu.

I think it does make a difference which distro you run: I used Debian from Potato to Etch, but I'm now using Ubuntu because I prefer it. I know that Ubuntu is Debian really, but I think it's much better presented and easier to use both as a server and a desktop. In fact, I use our Beowulf as a terminal server and we run 'embarrasingly' parallel HPC tasks from NX sessions using openMosix or use MPI. I've not looked at Debian Lenny, but Sarge and Etch were crude on the Desktop compared to Ubuntu 6.06...

openSSI looks very interesting but, despite several attempts, I've now abandoned any thought of using it. We must be careful not to accuse anyone of using the 'MOSIX' source, because that's proprietary! I guess you are talking about the GPL version when openMosix was forked ;-)

The three main contenders for FLOSS (Free/Libre Open Source Software) versions of SSI (Single System Image) Linux kernels seem to be openMosix, openSSI and Kerrighed. It's now unlikely the openMosix will continue (but I'm watching development of PMI:

[http://linuxpmi.org/trac/]("http://linuxpmi.org/trac/")

I agree that the openSSI project seems inactive (but don't dismiss it, because it has a lot of good points too). That leaves Kerrighed, which is still an active EU FP6 (Framework 6) funded project until 2010.

Why does venture capital mean something has to be proprietary?

Canonical have invested a lot in Ubuntu...

Thanks for joining in :-)

Bye,

    Tony.

---

### Post by kvk on 2009-01-14
This is wonderful information- thanks for posting it. I've been interested for a while now in constructing a small cluster (8-16 nodes) for running ecological models, but both my hardware abilities and programming need a bit more development. This will be great stuff to read through!

---

### Post by djamu on 2009-01-15
> **ajt said:**
> Hello, djamu.

Not sure why you think it's a bad idea to use Ubuntu?

The Kerrighed kernel is based on the 'vanilla' kernel sources, so it doesn't make much difference if you compile it under Debian or Ubuntu.


True, aside from the upstream implementations on ubuntu that might not work on a downgraded kernel... can't think of any right now but I had my share of those before switching my servers back to debian ( hopeless outdated IDS packages for example,  ). 
Also a base debian install installs much less "bloat" then ubuntu server does.
For example > there's a new service in intrepid (forgot the name) , that let's you sign up for server monitoring... 
Now I understand the need for Canonical to generate income.. but not letting me choose whether I want to install it is of a complete different magnitude... ( I try avoid using windows for the very same reason ).... 

In a server environment this is of less importance as the performance penalty is negligible...
But for tuned HPC cluster kernels ( to reduce interrupt jitter > whether NUMA / SMP ) every unnecessary service interrupt is 1 to many ... 
So if I have the option to install a really minimal system (netinstall) or I have to search thru a stock Ubuntu server install to manually delete all unnecessary  "helpful" services ...  the choice should be obvious, at least common sense dictates the obvious


> 
....
but Sarge and Etch were crude on the Desktop compared to Ubuntu 6.06...
....


That's a long time ago,  they still don't install sudo in the base install :smile:
 
Another point in me using debian is that a lot more packages (not desktop related) are available and rigorously tested > the very reason of it's slow cycle...
( A good example is the fail2ban package, stable on debian, typo bug in the 8.04-LTS, preventing it from restart on boot ... submitted to launchpad with fix...., intrepid has proper version ) > BTW as a matter of fact, this kind of package regression is by LTS policy forbidden. The tight release cycle prevents thorough testing...


But let's not get into any kind of flaming, IMO I really think ubuntu is a great desktop distro..., just my personal opinion..


> 
openSSI looks very interesting but, despite several attempts, I've now abandoned any thought of using it. We must be careful not to accuse anyone of using the 'MOSIX' source, because that's proprietary! I guess you are talking about the GPL version when openMosix was forked ;-)

Oops sorry my bad.. yes I did mean OpenMosix...

As for OpenSSI, I do think it's dead for 2 reasons.
1. Kerrighed uses a a substantial part of it's source > making OpenSSI practically obsolete
2. The XtreemOS project, which has (about) the same goal as OpenSSI ( where kerrighed is going to be part of )
[http://www.xtreemos.eu/](http://www.xtreemos.eu/)


> 
...
It's now unlikely the openMosix will continue (but I'm watching development of PMI:


isn't PMI a rebranded OpenMOSIX ?


> 
I agree that the openSSI project seems inactive (but don't dismiss it, because it has a lot of good points too). That leaves Kerrighed, which is still an active EU FP6 (Framework 6) funded project until 2010.


True, but since OpenSSI lacks the funding of the XtreemOS consortium ... chances are little it will emerge again.. 
[http://www.xtreemos.eu/overview/plonearticlemultipage.2006-06-08.9297943452/partners](http://www.xtreemos.eu/overview/plonearticlemultipage.2006-06-08.9297943452/partners)

System Architecture Overview:
[http://www.xtreemos.eu/science-and-research/plonearticlemultipage.2007-05-03.6408426978/copy_of_xtreemos-architecture](http://www.xtreemos.eu/science-and-research/plonearticlemultipage.2007-05-03.6408426978/copy_of_xtreemos-architecture)

> 
Why does venture capital mean something has to be proprietary?

It doesn't, it's just easier then providing just a service... 
And I wouldn't if a couple of kernel devs chip in..


Canonical have invested a lot in Ubuntu... &  Mark Shuttleworth flew in space 
:lolflag:



On a more serious note. 
Tony (AJT) you seem like a knowledgeable guy, I'd like to discuss in depth a couple of things ( compare my trunk compile kernel configs with yours / discuss different types of distributed FS's / tuning & jitter etc ... ) ..
But I'm a little afraid the title of the thread is not well chosen > I'll elaborate .. quite a lot of people reading this have will have a hard time grasping the type of cluster were discussing. To me it's obvious were talking (headless) HPC clustering...
In other words this thread is prone to pollution as soon as people start suggesting for example RHEL or SAN failover mechanisms as an alternative...

It's getting really late now, let's see where this is going..


Jan

---

### Post by altonbr on 2009-01-15
Here's an amazing article on how to turn Xboxs into a Beofwulf cluster. Looks inherently more simple than I thought.

[http://www.anandtech.com/linux/showdoc.aspx?i=2271&p=8](http://www.anandtech.com/linux/showdoc.aspx?i=2271&p=8)

---

### Post by altonbr on 2009-01-15
I also had these resources in [another thread]("http://ubuntuforums.org/showpost.php?p=5935648&postcount=4")...

> **Here are some resources I found:**
_Beowulf:_
[http://www.beowulf.org/overview/index.html](http://www.beowulf.org/overview/index.html)
[http://www.cacr.caltech.edu/beowulf/tutorial/building.html](http://www.cacr.caltech.edu/beowulf/tutorial/building.html)
[http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book/beowulf_book/node9.html](http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book/beowulf_book/node9.html)

_Related Projects:_
[https://computing.llnl.gov/linux/slurm/](https://computing.llnl.gov/linux/slurm/)
[http://www.rocksclusters.org/](http://www.rocksclusters.org/)

_Showcasing & Concepts:_
[http://helmer.sfe.se/](http://helmer.sfe.se/)
[http://helmer2.sfe.se/](http://helmer2.sfe.se/)
[http://helmer3.sfe.se/](http://helmer3.sfe.se/)
[http://www.calvin.edu/~adams/research/microwulf/](http://www.calvin.edu/~adams/research/microwulf/)

_Articles:_
[http://www.ibm.com/developerworks/library/l-halinux/](http://www.ibm.com/developerworks/library/l-halinux/)
[http://www.scribd.com/doc/312186/THE-GOOGLE-CLUSTER-ARCHITECTURE](http://www.scribd.com/doc/312186/THE-GOOGLE-CLUSTER-ARCHITECTURE)
[http://www.clustermonkey.net//content/view/211/1/](http://www.clustermonkey.net//content/view/211/1/)
[http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book/beowulf_book/node21.html](http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book/beowulf_book/node21.html)

_Comic:_
[http://imgs.xkcd.com/comics/network.png](http://imgs.xkcd.com/comics/network.png)

---

### Post by kloplop321 on 2009-01-15
I would simply be interested in using 3 old computers running as a cluster to slightly speed things up and add some elbow room. I have tried some live CD's but my old laptop's LAN card isn't supported(odd), and I would need to run a fan control program on one of the computers because it's fan control is not automatic from the bios(I find that stupid)
the last one is a pentium MMX machine.

---

### Post by machoo02 on 2009-01-15
altonbr,

You could add this to you list o' links:
[http://www.calvin.edu/~adams/research/microwulf/]("http://www.calvin.edu/~adams/research/microwulf/")

---

### Post by altonbr on 2009-01-15
> **machoo02 said:**
> altonbr,

You could add this to you list o' links:
[http://www.calvin.edu/~adams/research/microwulf/]("http://www.calvin.edu/~adams/research/microwulf/")

It's already in there ;)

---

### Post by djamu on 2009-01-15
> **kloplop321 said:**
> I would simply be interested in using 3 old computers running as a cluster to slightly speed things up and add some elbow room. I have tried some live CD's but my old laptop's LAN card isn't supported(odd), and I would need to run a fan control program on one of the computers because it's fan control is not automatic from the bios(I find that stupid)
the last one is a pentium MMX machine.

Don't want to discourage you but.
If it's a desktop OS which load you want to automatically share between computers..... come back in a couple of years... this is not possible (yet)... Kerrighed is closest for what you want to do & can migrate processes of standard applications to other computer(s) BUT can't split an application using a single process over 2 computers and doesn't distribute threads... 

Brief recap of types:

The term supercomputer might be misleading, as in most cases it's not a single OS that runs over a group of CPU's but rather independent computers that run a common application(s) over a shared network(s) > in other words it would be more correct to talk about an HPC cluster then a supercomputer... ( not 1 computer )

Depending on the type of application / dataset(s) more or less speed is required for the interconnects. 

An example:
Meet the most powerfull supercomputer on the planet... in everyones :) home.
Folding@home / Seti@home ( BOINC ) > [http://boinc.berkeley.edu/](http://boinc.berkeley.edu/)
This is an extreme case of an Embarrassingly Parallel ( the correct term for this kind of HPC clustering ) very little data is send over the network by a scheduler to each compute node.. 
This kind of number crunching doesn't require intermediate data from other processes and doesn't need distributed RAM.
A classical renderfarm is another example ( with a bit more network traffic )
[http://en.wikipedia.org/wiki/Embarrassingly_parallel](http://en.wikipedia.org/wiki/Embarrassingly_parallel)


On the other end you have those applications / dedicated clusters that require massive amounts of intermediate data / huge databases / shared memory > The big boys from the pictures...
These monsters usually have 3D torus shaped high speed networks ( infiniband / myrinet / 10Gb ) with multiple connections / node and are usually build for a single purpose ( you can't run any app on them because they would run inefficient )
These type of clusters usually run a kind of MPI flavor and can't run stock applications
[http://en.wikipedia.org/wiki/Message_Passing_Interface](http://en.wikipedia.org/wiki/Message_Passing_Interface)
[http://en.wikipedia.org/wiki/OpenMP](http://en.wikipedia.org/wiki/OpenMP)

Closest to a real supercomputer ( in the correct sense of the word ) and what you most likely want to achieve, unrelated to the previous mentioned MPI systems ( which are individual machines connected thru a network ) are the SSI systems. > Kerrighed / (Open)Mosix ( now PMI ) / OpenSSI 
[http://en.wikipedia.org/wiki/Single-system_image](http://en.wikipedia.org/wiki/Single-system_image)



One more thing worth noting:
The reason why more and more clusters are built from COTS ( commodity of the shelf > normal desktop computers ) parts instead of custom hardware is that before you had 2 distinct types of CPU's 

scalar > fast for single instruction single out
[http://en.wikipedia.org/wiki/Scalar_processor](http://en.wikipedia.org/wiki/Scalar_processor)
[http://en.wikipedia.org/wiki/SISD](http://en.wikipedia.org/wiki/SISD)

vector > fast for single instruction multiple out
[http://en.wikipedia.org/wiki/Vector_processor](http://en.wikipedia.org/wiki/Vector_processor)
[http://en.wikipedia.org/wiki/SIMD](http://en.wikipedia.org/wiki/SIMD)

more: [http://en.wikipedia.org/wiki/MIMD](http://en.wikipedia.org/wiki/MIMD)

While the x86 family originally was a pure scalar CPU it was unsuited ( very slow ) to do any vector processing..  The addition of the MMX and later 3Dnow / SSE etc.. extensions ( which are vector capabilities ) made the x86 hybrid.
So every modern x86 currently has  1 scalar + 1 vector + floating point  + .... / core   ( the P4 with hyperthreading had 2 scalar cores with 1 vector and 1 floating point core )

The CELL CPU has 1 scalar + 8 vector cores

Roadrunner ( currently the fastest supercomp ) uses hybrid nodes ( 1 AMD Opteron coupled to 1 CELL )

wanted to keep it brief ... pfff look at all that text again  :lolflag:

Jan

---

### Post by meatpan on 2009-01-17
The scope of EasyUbuntuClustering is very wide, which might be why the discussions on this thread have been so broad.

Is it realistic for an 'easy' clustering solution to cater to inexperienced developers, offer portable environments via VM's, provide automated load-balancing, and still maintain high QoS?

These are great goals to shoot for, but IMO you will likely have more success if you just pick one or two of the major features.

I can't comment much on the process migration (automated load balancing), since it's been more than 4 years since I've used OpenMosix.  These features typically require savvy system admins, and configuration problems can be difficult to diagnose.

Automated deployment of VM's on a cluster or grid (not going to get into a definition war here.  I'm referring to a grid as a federated assembly of heterogeneous clusters) is a hot topic that industry giants such as VMware (EMC), IBM, Microsoft, and Amazon are investigating.  There are numerous technical subtleties relating this topic, and a logical solution might be to create a specific flavor of debian or ubuntu server that is adapted to hosting the popular VM's.  This is especially relevant considering the CISC vendors have product roadmap plans that address common VM bottlenecks.

I admire your efforts to approach this complicated technical issue, and my only suggestion is to consider narrowing your scope a bit.

---

### Post by tinkertim on 2009-01-18
> **ajt said:**
> Hello, djamu.

Not sure why you think it's a bad idea to use Ubuntu?

The Kerrighed kernel is based on the 'vanilla' kernel sources, so it doesn't make much difference if you compile it under Debian or Ubuntu.


Its not just a question of building, its how the kernel is built (i.e. using the Debian / Ubuntu patching and build system). The current Kerrighed 2.6.20 kernel (the way its patched and built) would make this problematic.

However, the jump to 2.6.29 would make it much easier.

> 
I agree that the openSSI project seems inactive (but don't dismiss it, because it has a lot of good points too). That leaves Kerrighed, which is still an active EU FP6 (Framework 6) funded project until 2010.


I remain subscribed to the OpenSSI lists. Once in a while you'll see a flurry of activity, then radio silence for a few months. I'm still a big fan of the project, I think it will continue to advance for years to come. Its one of those projects where you need a solid block of time to actually do anything useful, so I'd imagine the devs devote what they can to it.

> 
Why does venture capital mean something has to be proprietary?
Canonical have invested a lot in Ubuntu...


For a long time many people used the word 'commercial' to refer to non-free software which now causes a lot of confusion and mistrust.

Kerrighed has a very good, very honest and very transparent business model. Use / share / modify the software any way you like .. if you get stuck, paid support and development is available.

You will always have those who are a little over-sensitive to this kind of arrangement. For instance, someone might ask for help to implement thread migration and get a reply that they'll be better off hiring Kerlabs (which they would be). Then, the person will start screaming 'baitware' or worse.

I don't know if you'd be able to find a MOTU that would be interested in keeping up with Kerrighed, but surely nothing is preventing someone from making it available via PPA.

---

### Post by crazy___cow on 2009-01-19
In the next month I'll try to setup a small cluster (using kerrighed or mosix) to research purpose ([http://afni.nimh.nih.gov/afni](http://afni.nimh.nih.gov/afni)). I have two dell poweredge 2900 monster (2cpu x 4 core) and several "old" dual CPU Xeon 3Ghz. The first idea is to use ubuntu hardy with a custom kernel (2.6.20 for kerrighed or 2.6.28 for mosix (it's free for researchers)). I think that it'will be a tricky job patching the kernel (with 64 bit support and all the modules to load onto pe2900 and others pcs)...but I'll try to do it, because ubuntu/debian is the most easy and powerful distro to use, configure and administrate.

---

### Post by djamu on 2009-01-19
rereading previous posts it seems I overlooked this argument  I've failed to notice since I thought we're talking headless compute nodes.
> **ajt said:**
> 
....
but Sarge and Etch were crude on the **Desktop** compared to Ubuntu 6.06...
....

So just out of curiosity.
Tony are you really implying an  X server / client in the SSI nodes ? Aside from the unnecessary  cost this would cause major problems as all GPU's should be of the same brand. Considering you'd only install the client X libraries on the nodes and use a remote X > XDMCP  ( the machine which renders the image on screen / has display is the X server ) then still it's nearly impossible since kerrighed doesn't support LVS ( common cluster IP address ) that the X client could use to communicate with a standalone X server > could be handy for a multiseat system :).
I have some experience with OpenGL clusters, and that is a completely different topic in all aspects ( would be nice though ).....
In any case, the easiest way to implement a GUI is a web-based one tied to a job scheduler.

> **tinkertim said:**
> .
...
However, the jump to 2.6.29 would make it much easier.

in all aspects ... kerrighed being part of the kernel instead of a module, changes things drastically....

> **tinkertim said:**
> .
For a long time many people used the word 'commercial' to refer to non-free software which now causes a lot of confusion and mistrust.

Kerrighed has a very good, very honest and very transparent business model. Use / share / modify the software any way you like .. if you get stuck, paid support and development is available.

You will always have those who are a little over-sensitive to this kind of arrangement. For instance, someone might ask for help to implement thread migration and get a reply that they'll be better off hiring Kerlabs (which they would be). Then, the person will start screaming 'baitware' or worse.

I feel I need to clarify my statement on this.
The amount of money involved to develop thread migration ( the estimate I got from Kerlabs ) is considerable ( for a person ) and enough to buy myself a nice house.....
Knowing that its very hard to turn OSS into something commercial / proprietary, one could only try to commercialize a web-based front-end / scheduler....

> **tinkertim said:**
> 
I don't know if you'd be able to find a MOTU that would be interested in keeping up with Kerrighed, but surely nothing is preventing someone from making it available via PPA.
I doubt an ubuntu MOTU will be interested/has time so yes PPA is a valid option...

Jan

---

### Post by ajt on 2009-01-20
> **kvk said:**
> This is wonderful information- thanks for posting it. I've been interested for a while now in constructing a small cluster (8-16 nodes) for running ecological models, but both my hardware abilities and programming need a bit more development. This will be great stuff to read through!

Hello, kvk.

I'm a biologist, turned bioinformatician, and there are lots of people just like me and you building our own DIY Beowulf clusters :-)

The real essence of this thread is to try and make it as 'easy' as possible for Ubuntu users to build this type of Beowulf cluster. I'm sure you already know that it can be quite a steep learning curve if you've never done anything like this before. However, there is nothing magic or particularly difficult about putting the hardware together. To give you a flavour of this approach, there is a chemical modeling cluster called 'COBALT' (Computers On Benches All Linked Together):

[http://www.cobalt.chem.ucalgary.ca/]("http://www.cobalt.chem.ucalgary.ca/")

We do some of this type of quantum chemistry modeling under Ubuntu ;-)

The Kerrighed links I posted recently give examples of setting up DHCP and PXE booting of cluster nodes. I'm using this to PXE boot eight of our compute nodes to experiment with Kerrighed. Anyway, thanks for joining the discussion.

Bye,

    Tony.

---

### Post by ajt on 2009-01-20
> **altonbr said:**
> Here's an amazing article on how to turn Xboxs into a Beofwulf cluster. Looks inherently more simple than I thought.

[http://www.anandtech.com/linux/showdoc.aspx?i=2271&p=8](http://www.anandtech.com/linux/showdoc.aspx?i=2271&p=8)

Hello, altonbr.

Connecting the boxes together is easy - Getting them to do something useful is the tricky bit :-)

Actually, I'm quite interested in clustering PS3's...

Not this one:

[http://www.engadget.com/2007/08/11/sony-erects-massive-ps3-server-cluster-for-warhawk-mayhem/]("http://www.engadget.com/2007/08/11/sony-erects-massive-ps3-server-cluster-for-warhawk-mayhem/")

More like this:

[http://gravity.phy.umassd.edu/ps3.html]("http://gravity.phy.umassd.edu/ps3.html")

Bye,

Tony.

---

### Post by ajt on 2009-01-20
> **djamu said:**
> [...]
But let's not get into any kind of flaming, IMO I really think ubuntu is a great desktop distro..., just my personal opinion..


Hello, Jan.

Good to know you like Ubuntu ;-)

> **djamu said:**
> [...]
isn't PMI a rebranded OpenMOSIX ?


It's a continuation of the project to port openMosix to the 2.6 kernel. 

> **djamu said:**
> [...]
True, but since OpenSSI lacks the funding of the XtreemOS consortium ... chances are little it will emerge again.. 
[http://www.xtreemos.eu/overview/plonearticlemultipage.2006-06-08.9297943452/partners](http://www.xtreemos.eu/overview/plonearticlemultipage.2006-06-08.9297943452/partners)
[...]


In my (now obsolete) 'biobuntu' blue-print, you will see that I'm also interested in XtreemOS as well as Kerrighed:

[https://blueprints.launchpad.net/ubuntu/+spec/biobuntu]("https://blueprints.launchpad.net/ubuntu/+spec/biobuntu")

> **djamu said:**
> [...]
[...]
But I'm a little afraid the title of the thread is not well chosen > I'll elaborate .. quite a lot of people reading this have will have a hard time grasping the type of cluster were discussing. To me it's obvious were talking (headless) HPC clustering...
In other words this thread is prone to pollution as soon as people start suggesting for example RHEL or SAN failover mechanisms as an alternative...


I disagree - I've got more than 26 years experience of 'parallel' computing but I obtained most of my computing (and image analysis) experience working as a biologist. I now work as a bioinformatician.

There are lots of people like me working in bioinformatics: A common thread in discussions like this is that it is MUCH more difficult to grasp the scientific questions being asked than it is to build a Beowulf. The technology is a means to an end. The draconian 'lock-down' policies of some highly centralised IT departments lack the flexibility to allow R&D approaches to be used by scientists who often know more about the technology than people trained in provision of IT for the 'enterprise'.

BTW, That's not a criticism of people providing IT for the 'enterprise'. it's an observation, borne of my own experience, that IT for science and IT provided for the 'enterprise' have completely different objectives. My intention in starting a thread in this forum is to try to draw together opinions and help from other people with similar objectives to my own. I agree that it's important to keep the topic clear: It is how we make it 'easy' to cluster Ubuntu systems in order to use the aggregate resources of many computers to solve one problem. This is the essence of Beowulf:

[http://www.beowulf.org/]("http://www.beowulf.org/")

Bye,

Tony.

---

### Post by ajt on 2009-01-20
> **kloplop321 said:**
> I would simply be interested in using 3 old computers running as a cluster to slightly speed things up and add some elbow room.


Hello, kloplop321.

I think that using a few old computers to learn about Beowulf clusters is fine, but at the end of the day they are still old computers and there is an overhead involved in communication between the compute nodes in a cluster. The first rule of 'parallel' computing is to determine what can be done independently by the nodes: That's where you gain an advantage.

> **kloplop321 said:**
> 
I have tried some live CD's but my old laptop's LAN card isn't supported(odd), and I would need to run a fan control program on one of the computers because it's fan control is not automatic from the bios(I find that stupid)
the last one is a pentium MMX machine.

Maybe this would be a good time to learn how to compile the Linux kernel?

It's not that difficult the second time you do it, but the first time takes a bit longer ;-)

Check the Kerrighed links I posted earlier in this thread for more info.

Thanks for joining in.

Bye,

Tony.

---

### Post by ajt on 2009-01-20
> **altonbr said:**
> It's already in there ;)

Hello, altonbr.

Why not add things like this to the Wiki:

[https://wiki.ubuntu.com/EasyUbuntuClustering]("https://wiki.ubuntu.com/EasyUbuntuClustering")

Bye,

Tony.

---

### Post by ajt on 2009-01-20
> **djamu said:**
> [...]

scalar > fast for single instruction single out
[http://en.wikipedia.org/wiki/Scalar_processor](http://en.wikipedia.org/wiki/Scalar_processor)
[http://en.wikipedia.org/wiki/SISD](http://en.wikipedia.org/wiki/SISD)

vector > fast for single instruction multiple out
[http://en.wikipedia.org/wiki/Vector_processor](http://en.wikipedia.org/wiki/Vector_processor)
[http://en.wikipedia.org/wiki/SIMD](http://en.wikipedia.org/wiki/SIMD)

more: [http://en.wikipedia.org/wiki/MIMD](http://en.wikipedia.org/wiki/MIMD)


Hello, Jan.

The BIG difference is using SIMD/MIMD instead of Von Neumann Arhitecture:

[http://en.wikipedia.org/wiki/Von_Neumann_architecture]("http://en.wikipedia.org/wiki/Von_Neumann_architecture")

SIMD (Single Instruction Multiple Data) is fast, but extremely limited. I used a 9216 SIMD processor array for image analysis some time ago (CLIP4R). There is a brief summary of this type of processor here if anyone is interested:

[http://homepages.inf.ed.ac.uk/rbf/CVonline/LOCAL_COPIES/GASTERATOS/iii.htm]("http://homepages.inf.ed.ac.uk/rbf/CVonline/LOCAL_COPIES/GASTERATOS/iii.htm")

However, we concluded that the advantages of using 'exotic' processor architectures like this does not outweigh the difficulty of programming them, or the 'corner-turning' problem of actually getting images into the SIMD processor array. Our CLIP4R was a very interesting machine, but its CPU boards ended up being made into wall clocks. Sad, but well worth the lessons learned. The host controller for the CLIP4R was a pdp11/34, so you can tell how long about this was (1986). I replaced the pdp11 with a Vax 750, which had less than 1MIP integer performance (a MIP is defined as an integer perfomance of one million VAX780 instructions per second).

Enough nostalgia for now - This has little to do with Ubuntu clustering, but might rectify some misunderstandings about what 'parallel' computing involves. What we are talking about in the Easy Ubuntu Clustering blue-print, and this thread, is using a collection of Von Neumann architecture processors in different computers as if they were one large SMP (Symmetric Multi-Processing) computer. This is the SSI (Single System Image) approach to parallel computing used by openMosix, openSSI and Kerrighed. It's also the approach taken by Donald Becker, who invented the Beowulf cluster at NASA and commercialised it:

[http://www.scyld.com/home.html]("http://www.scyld.com/home.html")

[Scyld, was Beowulf's companion in the Beowulf poem]

[http://en.wikipedia.org/wiki/Beowulf]("http://en.wikipedia.org/wiki/Beowulf")

Bye,

Tony.

---

### Post by ajt on 2009-01-20
> **meatpan said:**
> The scope of EasyUbuntuClustering is very wide, which might be why the discussions on this thread have been so broad.

Is it realistic for an 'easy' clustering solution to cater to inexperienced developers, offer portable environments via VM's, provide automated load-balancing, and still maintain high QoS?

These are great goals to shoot for, but IMO you will likely have more success if you just pick one or two of the major features.


Hello, meatpan.

I found the previous discussions dispersed over several different forums difficult to follow, and repeating many of the same questions. Yes, the discussion so far has been quite broad but, as we realise what people are actually interested in, I think the discussion will become more focussed.

> **meatpan said:**
> 
I can't comment much on the process migration (automated load balancing), since it's been more than 4 years since I've used OpenMosix.  These features typically require savvy system admins, and configuration problems can be difficult to diagnose.


Not really - I run a 90-node openMosix system and I'm a biologist ;-)

> **meatpan said:**
> 
Automated deployment of VM's on a cluster or grid (not going to get into a definition war here.  I'm referring to a grid as a federated assembly of heterogeneous clusters) is a hot topic that industry giants such as VMware (EMC), IBM, Microsoft, and Amazon are investigating.  There are numerous technical subtleties relating this topic, and a logical solution might be to create a specific flavor of debian or ubuntu server that is adapted to hosting the popular VM's.  This is especially relevant considering the CISC vendors have product roadmap plans that address common VM bottlenecks.


Hmm... 'cloudy' today?

The BIG problem with VM's is that they are designed to be using for HAC (High Availablility Computing) not HPC (High Performance Computing). It's not HPC to virtualise instances of e.g. Ubuntu then merge them again into a 'virtual' SSI. It's a way of making your IT provisioning resilient and platform-independant. Nothing wrong with that, if you're an ISP...

> **meatpan said:**
> 
I admire your efforts to approach this complicated technical issue, and my only suggestion is to consider narrowing your scope a bit.

Thanks - The technical aspects are really not that difficult, but the advantage of packaging up Kerrighed for Ubuntu would make it a lot easier!

Bye,

Tony.

---

### Post by ajt on 2009-01-20
> **tinkertim said:**
> Its not just a question of building, its how the kernel is built (i.e. using the Debian / Ubuntu patching and build system). The current Kerrighed 2.6.20 kernel (the way its patched and built) would make this problematic.

However, the jump to 2.6.29 would make it much easier.


Hello, tinkertim.

I'm a bit confused by what you say about patching: The 'patch' program is the same under Debian and Ubuntu, and the Kerrighed patches are relative to the 'vanilla' kernel sources for 2.6.20. The kernel Makefile includes a 'deb-pkg' target, which has nothing to do with the Debian or Ubuntu patches to their kernels. I built and installed Kerrighed kernel debs under Ubuntu 6.06 using only the 2.6.20 sources and kerrighed patches.

> **tinkertim said:**
> 
I remain subscribed to the OpenSSI lists. Once in a while you'll see a flurry of activity, then radio silence for a few months. I'm still a big fan of the project, I think it will continue to advance for years to come. Its one of those projects where you need a solid block of time to actually do anything useful, so I'd imagine the devs devote what they can to it.


I've followed openSSI developmenmts for years, and I tried quite hard to get openSSI running, to use as a replacement for openMosix, but gave up in the end.

> **tinkertim said:**
> 
[...]
I don't know if you'd be able to find a MOTU that would be interested in keeping up with Kerrighed, but surely nothing is preventing someone from making it available via PPA.

OK, I'll take that as you volunteering to help me do it :-)

Bye,

Tony.

---

### Post by ajt on 2009-01-20
> **crazy___cow said:**
> In the next month I'll try to setup a small cluster (using kerrighed or mosix) to research purpose ([http://afni.nimh.nih.gov/afni](http://afni.nimh.nih.gov/afni)). I have two dell poweredge 2900 monster (2cpu x 4 core) and several "old" dual CPU Xeon 3Ghz. The first idea is to use ubuntu hardy with a custom kernel (2.6.20 for kerrighed or 2.6.28 for mosix (it's free for researchers)). I think that it'will be a tricky job patching the kernel (with 64 bit support and all the modules to load onto pe2900 and others pcs)...but I'll try to do it, because ubuntu/debian is the most easy and powerful distro to use, configure and administrate.

Hello, crazy___cow.

Be very careful how you interpret "free for researchers" - I looked into this too, and the deal is you are given one 'free' snapshot of MOSIX2 kernel patches plus *binaries* of the MOSIX2 utilities. The snapshot is the current release, which is good, but you have to pay $1,000 per year to get updates and you don't get any sources other than the kernel patches. It depends what your objectives are. MOSIX2 looks very good, but it's not FLOSS. That might not matter to everyone, but it matters to me.

Bye,

Tony.

---

### Post by ajt on 2009-01-20
> **djamu said:**
> 
[...]
Tony are you really implying an  X server / client in the SSI nodes ? Aside from the unnecessary  cost this would cause major problems as all GPU's should be of the same brand. Considering you'd only install the client X libraries on the nodes and use a remote X > XDMCP  ( the machine which renders the image on screen / has display is the X server ) then still it's nearly impossible since kerrighed doesn't support LVS ( common cluster IP address ) that the X client could use to communicate with a standalone X server > could be handy for a multiseat system :).


Hello, Jan.

The Xserver runs on the client PC, where it displays the output of the Xclient running on the SSI. My present openMosix system has two servers and 88 compute nodes. One server is the 'head' node of the cluster, providing PXE + DHCP + NFSROOT and a web server:

[http://bioinformatics.rri.sari.ac.uk]("http://bioinformatics.rri.sari.ac.uk")

The other server is for interactive logins via SSH/NX/VNC and is where the user's home directories are stored. They are exported via NFS to the nodes. Only the servers are allowed to migrate processes away to other nodes. The Beowulf becomes unstable if all nodes are allowed to migrate processes. The compute nodes accept migrated processes from the servers, but do NOT migrate their own local processes. This allows us to run MPI and SGE as local processes without them being migrated off nodes...

> **djamu said:**
> 
I have some experience with OpenGL clusters, and that is a completely different topic in all aspects ( would be nice though ).....
In any case, the easiest way to implement a GUI is a web-based one tied to a job scheduler.


I've been looking at eyeOS:

[http://eyeos.org/]("http://eyeos.org/")

I've installed it, but not done much with it yet.

Most of the time, we just login using NX. If we want to run 'batch' jobs, we use SGE "qmon", or command-line tools to submit jobs. The webapps we run provide a web-based interface via the Beowulf web server using the Apache JK connector. Some, but not all, of the work accepted by these webapps is migrated automatically to compute nodes by openMosix. Any jobs using shared memory, in particular, are not migrated. This is due to the limitations of openMosix, as you know. Interrestingly, I did experiment with the openMosix 'MIGSHM' patch: My processes migrated away fine, but the didn't come back!

Bye,

Tony.

---

### Post by zkovax on 2009-01-23
Hi,

How about porting Perceus to ubuntu/debian?

[http://www.linux-mag.com/id/6386](http://www.linux-mag.com/id/6386)

To be frank I am a cluster newbie, I have just built my own cluster to learn the technology, and after lot of reading and digging I have started to use Perceus, more precisely Caoslinux, for the same reason you started this wiki, as it makes cluster management easy, and it realy does the job. On the other hand, I am an Ubuntu fun, I am familiar with it, so I would love to do the same with Ubuntu. Unfortunately I am not a linux/ubuntu admin guru, otherwise I would have started the porting already.

Probably you do not know, that Perceus is the provisioning part of Warewulf, Caoslinux is the distribution to manage them, and the whole lot is maintained by Infiscale.

[http://www.perceus.org/portal/](http://www.perceus.org/portal/)
[http://www.caoslinux.org/index.html](http://www.caoslinux.org/index.html)
[http://www.infiscale.com/](http://www.infiscale.com/)

Cheers,

Zsolt

---

### Post by masulli on 2009-01-23
Hi all!!

Can anyone post a simple and exaustive guide on how to install a cluster of pc using Kerrighed 2.3.0 and Ubuntu 8.10 or 8.04 ?

Thanks

---

### Post by ajt on 2009-01-25
> **masulli said:**
> Hi all!!

Can anyone post a simple and exaustive guide on how to install a cluster of pc using Kerrighed 2.3.0 and Ubuntu 8.10 or 8.04 ?

Thanks

Hello, masulli.

Not yet, but I hope we can create a guide:

[https://blueprints.launchpad.net/ubuntu/+spec/easy-ubuntu-clustering]("https://blueprints.launchpad.net/ubuntu/+spec/easy-ubuntu-clustering")

Bye,

Tony.

---

### Post by ajt on 2009-01-25
> **zkovax said:**
> Hi,

How about porting Perceus to ubuntu/debian?

[http://www.linux-mag.com/id/6386](http://www.linux-mag.com/id/6386)

[...]
Probably you do not know, that Perceus is the provisioning part of Warewulf, Caoslinux is the distribution to manage them, and the whole lot is maintained by Infiscale.

[http://www.perceus.org/portal/](http://www.perceus.org/portal/)
[http://www.caoslinux.org/index.html](http://www.caoslinux.org/index.html)
[http://www.infiscale.com/](http://www.infiscale.com/)


Hello, Zsolt.

Actually, I do know about Warewulf, but 'cAos' is an rpm-based distro and I want to use a deb-based distro - preferably Ubuntu ;-)

There are similar systems like DRBL:

[http://drbl.sourceforge.net/]("http://drbl.sourceforge.net/")

These systems are very useful for 'jumpstarting' or administering Beowulf clusters - DRBL has been used to deploy Kerrighed:

[http://trac.nchc.org.tw/grid/wiki/krg_DRBL]("http://trac.nchc.org.tw/grid/wiki/krg_DRBL")

However, systems like this do not address the issue of how to actually use a cluster for HPC (High performance Computing). A Beowulf is not just a COW (Collection Of Workstations), it's more than that...

What is interesting about openMosix, openSSI and Kerrighed is that they do kernel-level load balancing in a similar way that an SMP (Symmetric Multi-Processing) computer does, to make use of multiple CPU's. There is a HUGE difference in cost between e.g. building a Beowulf cluster from 16 ordinary COTS (Commodity Off The Shelf) PC's and buying in a commercial 16p SMP computer system, which is why this is a popular approach.

The BIG difference is that, without non-COTS cluster node interconnects, node latency can be extremely large in comparison to local SMP processor interconnects. Kerrighed uses an optimised 'kernel' TCP/IP communication protocol to minimise the latency in communication between Linux kernels running on processors in different Kerrighed nodes. That's one reason why I think Kerrighed is well worth looking at.

Bye,

Tony.

---

### Post by zander1013 on 2009-01-26
hi,

i have tried to cover all the posts here (at least one time) so far. there has been allot of lofty discussion of architecture and so forth that drifts from (and imo confuses) the issue.

i have only read joel adams paper on how he configures his microwulf using ubuntu one time.  but it appears that he has got what the original thread post requested.

except for the fact that he gives the instructions where the assumption is that the slave nodes will be diskless the description of how to configure a cluster using ubuntu where the nodes are connected by a cots switch is as easy as it will get without some kind of cluster installer like that for the .iso distro of ubuntu.


once again that link is...
[http://www.calvin.edu/~adams/research/microwulf/](http://www.calvin.edu/~adams/research/microwulf/)
...that's it folks!

that is the answer to this thread.


i intend to use it as a guide to try and establish my first cluster of two identical ibm t60 laptops run by ubuntu by simply connecting them with a cat-5 patch chord (no switch) and configuring them using his configuration instructions as a guide. i don't think there will be any problem doing this (without the switch) to get started.

perhaps the best way for those interested in actually building a cluster is to follow my lead with whatever hardware they have available. that is to say just use two boxes that run ubuntu, connect them with a cat-5 patch chord and use joel's configuration instructions as a guide.

once you have two machines that are an actual cluster just scale up.


peace!

-zander

---

### Post by antony_css on 2009-01-27
What I am curious about is how the computers are connected... Certainly it won't work by just connecting two computers with a LAN cable, so it seems that a router or sth more advanced is needed...

All I have is a modem which is provided by my ISP. I guess it is something that you connect it with a LAN cable and a telephone line so that you can access the web.

This is what I have done a month before:
==================================================
**Hardware:**
1. a win95 box with 133MHz CPU & 32Mb RAM
2. an xp box with 2GHz CPU,256Mb RAM
3. an ADSL modem with 4 slots for LANs
4. two LAN cables

**Procedures:**
I connected the two boxes to the modem with the LAN cables. Then, I tried to boot both boxes using liveCDs like [CHAOS]("http://midnightcode.org/projects/chaos/") and [ClusterKnoppix]("http://bofh.be/clusterknoppix/"). Afterthat, I tried some floppies like [GoMF]("http://gomf.sourceforge.net/index.html") and [openMosixLOAF]("http://openmosixloaf.sourceforge.net/"). Finally, I tried to start the following shell-script in background:
> s=0
for (( i=1; i>0; i=i+1 ))
do
	s=$(($s+$i))
done



**Results.**
_liveCDs_: cannot boot on the old box. success to boot on the new box but cannot configure itself as a node - sth called "DHCP server" was misssing.

_floppies_:
a. _GoMF_ can boot on both boxes, but the same problem occured - "DHCP server" was absent. 
b. _openMosixLOAF_ can boot on both boxes, success to configure as nodes by manually entering  private IPs and Gateway. can view cpu loads, ram utilization in real time from any boxes. cannot migrate the shell script because the floppy is not shipped with commands like "mosrun".
=========================================================

To sum up, any attempt to construct openmosix-cluster using a modem failed (without compiling, of course). Could anyone tell me what is a "DHCP server"?

It seems that the so called "DHCP" is related to auto-detection & auto-configuration, and cannot be turned off. Is it possible to solve this without having to buy new hardware(s)?

---

### Post by antony_css on 2009-01-27
Well, after surfing Wikipedia, I found that my ADSL modem is actually a router... :P
But that changes nothing... my ISP provided me this "modem" as a part of the internet service, but they didn't provide any further support on "advanced" usage, even a not a manual...

---

### Post by ajt on 2009-01-27
> **zander1013 said:**
> hi,

i have tried to cover all the posts here (at least one time) so far. there has been allot of lofty discussion of architecture and so forth that drifts from (and imo confuses) the issue.


Hello, zander.

I think it's important to place what we are discussing in context: In fact, SIMD instructions are now used in the FPU's of modern processors and I think it's quite useful to have a little background information :-)

> **zander1013 said:**
> 
i have only read joel adams paper on how he configures his microwulf using ubuntu one time.  but it appears that he has got what the original thread post requested.

except for the fact that he gives the instructions where the assumption is that the slave nodes will be diskless the description of how to configure a cluster using ubuntu where the nodes are connected by a cots switch is as easy as it will get without some kind of cluster installer like that for the .iso distro of ubuntu.


I don't think that building a Microwulf could be described as 'easy', and what I've read about Microwulf focusses more on the hardware aspects of how to construct a DIY Beowulf. Segregating 'system' and 'application' network traffic is a good idea, but it's not an original one:

[http://bioinformatics.rri.sari.ac.uk/bobcat/]("http://bioinformatics.rri.sari.ac.uk/bobcat/")

> **zander1013 said:**
> 
once again that link is...
[http://www.calvin.edu/~adams/research/microwulf/](http://www.calvin.edu/~adams/research/microwulf/)
...that's it folks!

that is the answer to this thread.


I think the Microwulf project is great, in terms of its hardware, but it doesn't bring anything new to the software requirements of building Ubuntu clusters. In relation to 'diskless' booting, for example, there has been an Ubuntu 'diskless' wiki for a long time:

[https://help.ubuntu.com/community/DisklessUbuntuHowto]("https://help.ubuntu.com/community/DisklessUbuntuHowto")

The type of Beowulf cluster installation/management packages that are discussed by the Microwulf project are well known. What I suggested is that we try to package Kerrighed for Ubuntu, because Kerrighed is a state of the art SSI (Single System Image) Linux kernel load-balancing system that has already been packaged for Mandriva Linux. I think it would be useful to package it for Ubuntu too.

> **zander1013 said:**
> 
i intend to use it as a guide to try and establish my first cluster of two identical ibm t60 laptops run by ubuntu by simply connecting them with a cat-5 patch chord (no switch) and configuring them using his configuration instructions as a guide. i don't think there will be any problem doing this (without the switch) to get started.


Make sure you use a crossover cable if you do (or check that your laptop has autosensing NIC's). It's quite common for ISP's to provide a combined ADSL modem + router + WiFi these days, but a passive ethernet hub would be another solution for a low-cost experimental setup.

> **zander1013 said:**
> 
perhaps the best way for those interested in actually building a cluster is to follow my lead with whatever hardware they have available. that is to say just use two boxes that run ubuntu, connect them with a cat-5 patch chord and use joel's configuration instructions as a guide.

once you have two machines that are an actual cluster just scale up.


As Bart says: "Don't have a COW, man...", but that is exactly what you will create if you just connect together a Collection Of Workstations. There's a lot more to building a cluster than simply connecting computers together. However, connecting them up *is* quite important ;-)

> **zander1013 said:**
> 
peace!


A friend of mine saw graffiti in Florence recently that read:

*Make tea, not war*

I like that :-)

Bye,

Tony.

---

### Post by ajt on 2009-01-27
> **antony_css said:**
> [...]
To sum up, any attempt to construct openmosix-cluster using a modem failed (without compiling, of course). Could anyone tell me what is a "DHCP server"?

It seems that the so called "DHCP" is related to auto-detection & auto-configuration, and cannot be turned off. Is it possible to solve this without having to buy new hardware(s)?

Hello, antony_css.

A DHCP (Dynamic Host Configuration Protocol) server listens for computers on the network broadcasting DHCPDISCOVER requests and supplies them with a dynamic network configuration. This normally consists of an IP address, netmask and default router addess. Often, the DHCP server also supplies DNS name server addresses and DNS domains to search. In addition, modern DHCP servers support network booting and supply information about TFTP (Trivial File Transfer Protocol) where a boot image can be downloaded.

Although this might sound complicated, many routers run DHCP servers so all you have to do is connect your devices to the router, and find out what their IP addresses are by running:

ipconfig -a

This is necessary if you want to connect your computers together, because they need to know each other's IP address. This is a common private IP network:

192.168.0.254   router
192.168.0.1     node1
192.168.0.2     node2
...

For a small network, you can put this information in the /etc/hosts file.

Bye,

Tony.

---

### Post by punong_bisyonaryo on 2009-01-28
Hi All!

I'm researching for a paper for our company (sadly, the paper is proprietary) on how to use existing open source solutions for cluster computing and balancing the loads between computers that merely do spreadsheets or emails with computers that do intensive compiles/builds. Looks like I found the right source of info!:D

I'll try to catch up on all the info you've guys have written. Interesting stuff.

---

### Post by ajt on 2009-01-28
> **punong_bisyonaryo said:**
> Hi All!

I'm researching for a paper for our company (sadly, the paper is proprietary) on how to use existing open source solutions for cluster computing and balancing the loads between computers that merely do spreadsheets or emails with computers that do intensive compiles/builds. Looks like I found the right source of info!:D

I'll try to catch up on all the info you've guys have written. Interesting stuff.

Hello, punong_bisyonaryo.

It's a popular wish to harness all the 'idle' CPU cycles on under-used office desktops, but the people using them will not be very happy when your intensive compile/build makes their web browser go catatonic!

What works best under these circumstances is 'volunteer' computing:

[http://www.volunteerathome.com/]("http://www.volunteerathome.com/")

The point about volunteer computing is that the donor computer decides when to volunteer its resources (e.g. when a screen saver starts up).

In contrast, MOSIX/openMosix was actually designed to work the way that you want to by using the idle CPU's on workstations but the computers all have to run Linux. In practice, though, it's difficult to avoid someone switching a computer off, or rebooting it in the middle of your job that has been migrated onto it. When that happens your job is lost...

Clustering systems are only as reliable as the nodes they contain: If you don't control the nodes, then you don't control the cluster. For that reason, most people build a private cluster LAN with dedicated compute nodes connected to it. Even if you do control your company's desktops, you will still have problems running cluster software on the public (company) LAN, because you will be using up a lot of the available network bandwidth migrating programs and data to and from 'idle' desktops.

I think there are circumstances where it might work if e.g. you take over the company LAN and reboot Linux on the desktop PC's during out-of-hours and run your compile farm then. This is common practice in University PC teaching labs that run Micro$oft Windows by day, but Linux HPC software by night :-)

Good luck + please do post your conclusions here!

Bye,

Tony.

---

### Post by antony_css on 2009-01-29
Well, somehow i found that dhcp can be set up as a daemon...
A floppy distribution "[eucaristOS]("http://eucaristos.sourceforge.net/")" actually use this technique to set up cluster on old computers...
However it does not support my network card... so sad...

---

### Post by altonbr on 2009-01-29
Maybe we can take this information and start collecting it under [https://help.ubuntu.com/community/Clustering](https://help.ubuntu.com/community/Clustering) ???

---

### Post by ajt on 2009-02-01
> **antony_css said:**
> Well, somehow i found that dhcp can be set up as a daemon...
A floppy distribution "[eucaristOS]("http://eucaristos.sourceforge.net/")" actually use this technique to set up cluster on old computers...
However it does not support my network card... so sad...

Hello, antony_css.

Beware, eucaristOS is based on an even older version of openMosix than I'm using!

You could compile in support for your network card, if you download the openMosix kernel sources, However, I think you would be better off trying out the Kerrighed 'live' CD, which also runs DHCP for you:

[http://www.kerlabs.com/dl/kerrighed-live.iso]("http://www.kerlabs.com/dl/kerrighed-live.iso")

Bye,

Tony.

---

### Post by ajt on 2009-02-01
> **altonbr said:**
> Maybe we can take this information and start collecting it under [https://help.ubuntu.com/community/Clustering](https://help.ubuntu.com/community/Clustering) ???

Hello, altonbr.

OK, I've created a '[Clustering]("https://help.ubuntu.com/community/Clustering")' page...

Bye,

Tony.

---

### Post by swisspipe on 2009-02-02
Hi all!
I am trying to create a little home cluster with Ubunto 8.04 and Kerrighed, but I am facing some problems. 
I run the build.sh script located in wiki page, but at some point he run the command vi Makefile and stop waiting for something, what i have to do at this point? The comment say "# edit Extraversion" what i need to chage/edit?
Thanks and cherrs ;)

---

### Post by ajt on 2009-02-02
> **swisspipe said:**
> Hi all!
I am trying to create a little home cluster with Ubunto 8.04 and Kerrighed, but I am facing some problems. 
I run the build.sh script located in wiki page, but at some point he run the command vi Makefile and stop waiting for something, what i have to do at this point? The comment say "# edit Extraversion" what i need to chage/edit?
Thanks and cherrs ;)

Hello, swisspipe.

That build.sh describes the commands I used to compile the Kerrighed kernel under Ubuntu 8.04. You have to edit the 'Extraversion' in the Makefile if you are building a 'deb' because the kernel name must obey the Debian package name conventions. The build failed with the default Kerrighed 'Extraversion', so I tried changing it to:

EXTRAVERSION = -krg-2.3.0

That resulted in a valid Debian package name :-)

The commands in "build.sh" only compile and package the kernel. I've not packaged the Kerrighed user-land tools yet.

Bye,

Tony.

---

### Post by antony_css on 2009-02-17
I really wish to have a workable eucaristOS disk for my computers...
Is it possible to merge the latest kernel in ajt's deb to the eucaristOS source?

Looking into the source directory of eucaristOS, I didn't find any related folders like "/boot" for me to replace the kernel... Isn't that because the disk does not use grub as bootloader?

BTW, I keep making stupid mistakes even when I tried to make the floppy image from the source. It crashes due to an unknown error...like the one below:
> 
$ sudo make all
Building floppy image.../bin/sh: Syntax error: Bad fd number
make: *** [floppy] Error 2

What should I do?

---

### Post by antony_css on 2009-02-17
Haha! this is the clue!
[http://ubuntuforums.org/showthread.php?t=382548]("http://ubuntuforums.org/showthread.php?t=382548")

---

### Post by kgkv on 2009-02-17
> **zkovax said:**
> Hi,

How about porting Perceus to ubuntu/debian?

[http://www.linux-mag.com/id/6386](http://www.linux-mag.com/id/6386)

To be frank I am a cluster newbie, I have just built my own cluster to learn the technology, and after lot of reading and digging I have started to use Perceus, more precisely Caoslinux, for the same reason you started this wiki, as it makes cluster management easy, and it realy does the job. On the other hand, I am an Ubuntu fun, I am familiar with it, so I would love to do the same with Ubuntu. Unfortunately I am not a linux/ubuntu admin guru, otherwise I would have started the porting already.

Probably you do not know, that Perceus is the provisioning part of Warewulf, Caoslinux is the distribution to manage them, and the whole lot is maintained by Infiscale.

[http://www.perceus.org/portal/](http://www.perceus.org/portal/)
[http://www.caoslinux.org/index.html](http://www.caoslinux.org/index.html)
[http://www.infiscale.com/](http://www.infiscale.com/)

Cheers,

Zsolt

We have already "ported" perceus (and warewulf) to debian.. It needs 
a lot of polishing but it works for i386 and amd64 on our cluster
of ~80 machines.


deb [http://biodev.ece.ucsb.edu/debian/](http://biodev.ece.ucsb.edu/debian/)  main contrib

On you server:
  aptitude install perceus-server 

There are scripts for creating debian VNFS there.

---

### Post by zkovax on 2009-02-21
> **kgkv said:**
> We have already "ported" perceus (and warewulf) to debian.


Hi kgkv,

This looks really good. I will have a look.

Zsolt

---

### Post by antony_css on 2009-02-22
It sounds interesting:
[http://code.google.com/p/distcc/]("http://code.google.com/p/distcc/")

Anyway, what is that?

---

### Post by bigjimjams on 2009-02-23
> **masulli said:**
> Hi all!!

Can anyone post a simple and exaustive guide on how to install a cluster of pc using Kerrighed 2.3.0 and Ubuntu 8.10 or 8.04 ?

Thanks

Hi Masulli, are you or anyone else still looking for a guide to do this? I've recently managed to get a small Kerrighed 2.3.0 cluster up and running under Ubuntu 8.04 with the 2.6 kernel. I'm currently in the process of writing a guide covering the setup process so other people at work know how to maintain it. If anyone is interested I can post a link on here.

---

### Post by punong_bisyonaryo on 2009-02-23
> **bigjimjams said:**
> Hi Masulli, are you or anyone else still looking for a guide to do this? I've recently managed to get a small Kerrighed 2.3.0 cluster up and running under Ubuntu 8.04 with the 2.6 kernel. I'm currently in the process of writing a guide covering the setup process so other people at work know how to maintain it. If anyone is interested I can post a link on here.

Yes please! Definitely interested.:D

---

### Post by bigjimjams on 2009-02-23
> **punong_bisyonaryo said:**
> Yes please! Definitely interested.:D

Seeing as there is a demand for it, I'll get it finished quickly and post it here. :D

---

### Post by mips on 2009-02-23
> **antony_css said:**
> What I am curious about is how the computers are connected... Certainly it won't work by just connecting two computers with a LAN cable, so it seems that a router or sth more advanced is needed...

For two PC's all that is required is a cross-over LAN cable & a configured hosts file. Multiple PCs will require a LAN Switch. A router is not required.

---

### Post by xingmu on 2009-02-23
bigjimjams,

I am another person who would love to see a tutorial for this.  I have been following tutorial at [http://trac.nchc.org.tw/grid/wiki/krg_DRBL](http://trac.nchc.org.tw/grid/wiki/krg_DRBL).  But since I am using a more recent version of Kerrighed, it seems there are some problems towards the end with actually starting the cluster.  I am also very frustrated that this and other tutorials (e.g. [http://www.in2dwok.com/indawok/?page_id=16](http://www.in2dwok.com/indawok/?page_id=16)) don't *explain* what is being done but just tell you to do it.

If you can at least get a draft of your tutorial,  I would offer to help extend it based on my experiences.  I think the owner of this thread started a page for EasyUbuntuClustering on the wiki.  We should do the same (either add to that page or start a dedicated one).  In my view, before anyone can help make clustering "easy", we need to have more people actually able to start a cluster. :}

---

### Post by bigjimjams on 2009-02-24
> **xingmu said:**
> bigjimjams,

I am another person who would love to see a tutorial for this.  I have been following tutorial at [http://trac.nchc.org.tw/grid/wiki/krg_DRBL](http://trac.nchc.org.tw/grid/wiki/krg_DRBL).  But since I am using a more recent version of Kerrighed, it seems there are some problems towards the end with actually starting the cluster.  I am also very frustrated that this and other tutorials (e.g. [http://www.in2dwok.com/indawok/?page_id=16](http://www.in2dwok.com/indawok/?page_id=16)) don't *explain* what is being done but just tell you to do it.

If you can at least get a draft of your tutorial,  I would offer to help extend it based on my experiences.  I think the owner of this thread started a page for EasyUbuntuClustering on the wiki.  We should do the same (either add to that page or start a dedicated one).  In my view, before anyone can help make clustering "easy", we need to have more people actually able to start a cluster. :}

Hi Xingmu, sounds like a good plan, as I'd be interested in other peoples opinions on what I did. If you are using kerrighed 2.3.0, there is a known issue with the krgadm tool, which always states that the cluster is not running even when it is! I'll put a draft of the guide up on the "Easy" Clustering Wiki in the next day or so, as I'm currently swamped with a couple of tasks.

---

### Post by bigjimjams on 2009-02-26
> **bigjimjams said:**
> Hi Xingmu, sounds like a good plan, as I'd be interested in other peoples opinions on what I did. If you are using kerrighed 2.3.0, there is a known issue with the krgadm tool, which always states that the cluster is not running even when it is! I'll put a draft of the guide up on the "Easy" Clustering Wiki in the next day or so, as I'm currently swamped with a couple of tasks.

Hi Xingmu and anybody else interested, as promised in my earlier post I've added a draft guide for setting up a kerrighed 2.3.0 cluster in Ubuntu 8.04 on the Easy Ubuntu Clustering Wiki. Here is the link:

[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide")

If you have any questions, comments, suggestions or improvements let me know.

---

### Post by ajt on 2009-02-28
> **bigjimjams said:**
> Hi Xingmu and anybody else interested, as promised in my earlier post I've added a draft guide for setting up a kerrighed 2.3.0 cluster in Ubuntu 8.04 on the Easy Ubuntu Clustering Wiki. Here is the link:

[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide")

If you have any questions, comments, suggestions or improvements let me know.

Hello, bigjimjams.

Thanks for your excellent installation guide!

I've done more or less the same installation, but I've not documented it quite so well :-)

One difference is that I use [UNFS3]("http://unfs3.sourceforge.net/") with 'ClusterNFS' extensions enabled for the NFSROOT. This allows all the nodes to share the same NFSROOT filesystem read-only, with 'tagged' links into a writable area for node-specific files.

Bye,

    Tony.

---

### Post by xingmu on 2009-03-02
> **bigjimjams said:**
> Hi Xingmu and anybody else interested, as promised in my earlier post I've added a draft guide for setting up a kerrighed 2.3.0 cluster in Ubuntu 8.04 on the Easy Ubuntu Clustering Wiki. Here is the link:

[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide")

If you have any questions, comments, suggestions or improvements let me know.

Thanks bigjimjams!  I actually got the cluster up and running right after I saw your note about the "no running cluster" bug in krgadm.  I ended using a package DRBL which configures the dhcp-server, tftp, etc. automatically.  I am thinking it might be useful to add this to your tutorial as an alternative installation method.

On another note and somewhat off-topic, has anyone tried installing Kerrighed straight from the SVN?  I see that above-mentioned bug has already been fixed in the SVN.  I am also having troubles with processes not migrating to multi-core CPUs.  I am hoping newer revisions might have fixed these problems. If so, are there any suggested revision numbers to use?  Or is every revision supposed to be a working version?

---

### Post by bigjimjams on 2009-03-02
> **ajt said:**
> Hello, bigjimjams.

Thanks for your excellent installation guide!

I've done more or less the same installation, but I've not documented it quite so well :-)

One difference is that I use [UNFS3]("http://unfs3.sourceforge.net/") with 'ClusterNFS' extensions enabled for the NFSROOT. This allows all the nodes to share the same NFSROOT filesystem read-only, with 'tagged' links into a writable area for node-specific files.

Bye,

    Tony.

No problem Tony, happy to help out! I was creating the guide for documenting it at work anyway, so thought I'd share what I'd done to save other people having to search around the web like I did. Thanks for the tip about UNFS. I'll have a look at it, as it may be useful when we build our larger Kerrighed cluster in a couple of weeks. :D

---

### Post by bigjimjams on 2009-03-02
> **xingmu said:**
> Thanks bigjimjams!  I actually got the cluster up and running right after I saw your note about the "no running cluster" bug in krgadm.  I ended using a package DRBL which configures the dhcp-server, tftp, etc. automatically.  I am thinking it might be useful to add this to your tutorial as an alternative installation method.

On another note and somewhat off-topic, has anyone tried installing Kerrighed straight from the SVN?  I see that above-mentioned bug has already been fixed in the SVN.  I am also having troubles with processes not migrating to multi-core CPUs.  I am hoping newer revisions might have fixed these problems. If so, are there any suggested revision numbers to use?  Or is every revision supposed to be a working version?

Hi xingmu, I did see the DRBL option on the Kerrighed documentation webpage, but preferred to do it by hand on a first attempt. I agree that it might be useful to maybe add this as an alternative option. Are there any other benefits or drawbacks? 

I'm planning on using the SVN version of kerrighed in a couple of weeks, as mentioned in my previous post. So I can let you know how it goes then if you haven't beaten me to it! ;) I think they've fixed a number bugs since 2.3, from looking at the responses on the mailing list.

As for you multi-core cpu problem, that seems quite strange, as I did plug an intel quad into my kerrighed test cluster and it worked fine with process migration. Was it using a 32-bit or 64-bit kernel?

---

### Post by NurChiN on 2009-03-02
a

---

### Post by xingmu on 2009-03-03
> **bigjimjams said:**
> Hi xingmu, I did see the DRBL option on the Kerrighed documentation webpage, but preferred to do it by hand on a first attempt. I agree that it might be useful to maybe add this as an alternative option. Are there any other benefits or drawbacks? 

I'm planning on using the SVN version of kerrighed in a couple of weeks, as mentioned in my previous post. So I can let you know how it goes then if you haven't beaten me to it! ;) I think they've fixed a number bugs since 2.3, from looking at the responses on the mailing list.

As for you multi-core cpu problem, that seems quite strange, as I did plug an intel quad into my kerrighed test cluster and it worked fine with process migration. Was it using a 32-bit or 64-bit kernel?

Ok, I've tried some of the SVN revisions now.  I can confirm that r4762 and r5069 (latest) are working versions.  They have "sort of" fixed the cluster status bug.  I say "sort of" because krgadm cluster status outputs "0:1".  My session_id is 1, but I can't understand what the "0" means (nb_min?).  My node_id's are from 1 to 3, so 0 is not a node_id.  
Also, auto-migration in the newer revisions doesn't work without setting up a scheduler ([http://www.kerrighed.org/wiki/index.php/SchedConfig](http://www.kerrighed.org/wiki/index.php/SchedConfig)).  I got that part figured out, but I *still* cannot get processes to properly use my dual-core CPUs.  I am wondering if there are options I need to change when building the kernel?

BTW, I am using a 32-bit kernel, although the chips are 64-bit Xeon's.

---

### Post by ajt on 2009-03-03
> **bigjimjams said:**
> No problem Tony, happy to help out! I was creating the guide for documenting it at work anyway, so thought I'd share what I'd done to save other people having to search around the web like I did. Thanks for the tip about UNFS. I'll have a look at it, as it may be useful when we build our larger Kerrighed cluster in a couple of weeks. :D

Hello, bigjimjams.

The '3' in UNFS3 means NFS version 3, so you have to be tell the Kerrighed kernel to look for an NFSROOT on using the NFSv3 protocol because the default is NFSv2. This is how I do it:

```
default linux
label linux
        kernel vmlinuz-kerrighed
        append root=/dev/nfs ip=dhcp nfsroot=192.168.0.254:/NFSROOT,v3 node_id=65 session_id=1

```

Bye,

    Tony.

---

### Post by bigjimjams on 2009-03-03
> **xingmu said:**
> Ok, I've tried some of the SVN revisions now.  I can confirm that r4762 and r5069 (latest) are working versions.  They have "sort of" fixed the cluster status bug.  I say "sort of" because krgadm cluster status outputs "0:1".  My session_id is 1, but I can't understand what the "0" means (nb_min?).  My node_id's are from 1 to 3, so 0 is not a node_id.  
Also, auto-migration in the newer revisions doesn't work without setting up a scheduler ([http://www.kerrighed.org/wiki/index.php/SchedConfig](http://www.kerrighed.org/wiki/index.php/SchedConfig)).  I got that part figured out, but I *still* cannot get processes to properly use my dual-core CPUs.  I am wondering if there are options I need to change when building the kernel?

BTW, I am using a 32-bit kernel, although the chips are 64-bit Xeon's.

Hi xingmu, the "0" in "0:1" is normally the node id, as far as I know the manual assignment of node id's in 2.3 was broken and the node id's were automatically assigned from the ip address of each node, so for example a node with ip address 192.168.1.0 would automatically be assigned node id 0.

As I mentioned earlier, I used the 32-bit kernel on a intel Q6600 with the other nodes being AthlonXPs and it seemed to work fine with the process migration stuff, as all cores hit 100% usage. Therefore, I'm guessing its something to do with the kernel settings.

---

### Post by bigjimjams on 2009-03-03
> **ajt said:**
> Hello, bigjimjams.

The '3' in UNFS3 means NFS version 3, so you have to be tell the Kerrighed kernel to look for an NFSROOT on using the NFSv3 protocol because the default is NFSv2. This is how I do it:

```
default linux
label linux
        kernel vmlinuz-kerrighed
        append root=/dev/nfs ip=dhcp nfsroot=192.168.0.254:/NFSROOT,v3 node_id=65 session_id=1

```

Bye,

    Tony.

Thanks Tony, I guessed it was to do with NFS version 3, but the code snippet helps. :D

---

### Post by jedi453 on 2009-03-12
Hi BigJimJams,

Thanks for the great guide!

I did notice a few problems with the guide however...:

 - The guide doesn't show how to set up /etc/network/interfaces on the server

 - In /etc/default/dhcp3-server your missing a semi-colon at the end of the third to last line

 - In /etc/default/tftpd-hpa RUN_DAEMON should equal "yes" (all lowercase), mine was yelling at me without this (I was using debian so maybe that's why).


Just as a side note, I was having trouble at the tftp stage. DHCP assigned an IP address ok, but I recieved the "PXE-E32" error. This only happened on two of the three computers I was using.
So as this source ([http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg32044.html](http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg32044.html)) suggests I tried booting from a pxe cd. I used GPXE.
I went to their website ([http://kernel.org/pub/software/utils/boot/gpxe/](http://kernel.org/pub/software/utils/boot/gpxe/)) and downloaded the latest version. Then I untarred it (tar -xzf gpxe-*), then I changed directories into the new folder (cd gpxe-*).
Then I changed directory into src (cd src) then ran "make bin/gpxe.iso" Then the iso was in "bin/gpxe.iso". I was able to boot from this which resolved the problem.

---

### Post by robasc on 2009-03-15
Hello everyone, My name is Rob and I am new to clustering and I am looking to find some people to chat with that can help me learn about clustering. Thanks to the help of ajt I am in the right place. 

I have got a cluster put together using the idea from Joel Adams and their project Microwulf. 

I thought this Idea would be a good way to start. 

First off Let me just say that I am not an expert Linux guru but I do know the basics and I have been playing around for quite some time using various Linux OS systems; however, I am new to Ubuntu.

I am also very serious about getting this project done. I have already spent a good amount of money building this cluster and now I want to get it up and running.

One other thing I also liked the tutorial on kerrighed. I would be interested in learning more if anyone would care to help.

Thanks everyone!

---

### Post by bigjimjams on 2009-03-16
> **robasc said:**
> Hello everyone, My name is Rob and I am new to clustering and I am looking to find some people to chat with that can help me learn about clustering. Thanks to the help of ajt I am in the right place. 

I have got a cluster put together using the idea from Joel Adams and their project Microwulf. 

I thought this Idea would be a good way to start. 

First off Let me just say that I am not an expert Linux guru but I do know the basics and I have been playing around for quite some time using various Linux OS systems; however, I am new to Ubuntu.

I am also very serious about getting this project done. I have already spent a good amount of money building this cluster and now I want to get it up and running.

One other thing I also liked the tutorial on kerrighed. I would be interested in learning more if anyone would care to help.

Thanks everyone!

Hi robasc, I'm happy to help (if I can). What sort of things do you need help with? It might be worth posting your questions on here.

---

### Post by ajt on 2009-03-16
> **robasc said:**
> [...]
I am also very serious about getting this project done. I have already spent a good amount of money building this cluster and now I want to get it up and running.

One other thing I also liked the tutorial on kerrighed. I would be interested in learning more if anyone would care to help.

Thanks everyone!

Hello, robasc.

Thanks for joining this thread :-)

I'm interested in SSI (Single System Image). This is like SMP (Symmetric Multi Processing), but the interconnect between the CPU's spans different computer systems rather than just the memory bus or hyper transport used in multi CPU systems. In COTS (Commodity Off The Shelf) Beowulf clusters the interconnect is usually 100-BaseT or Gigabit ethernet.

In the recent past, three SSI projects were popular: OpenSSI, openMosix and Kerrighed. The OpenSSI project looks good, but seems to be dormant because the code releases are quite old, and the openMosix project is now closed down. That leaves Kerrighed, which is being actively developed by an enthusiastic team:

[http://www.kerrighed.org]("http://www.kerrighed.org")

I run a 90-node openMosix Beowulf, which we are hoping to upgrade to Kerrighed as soon as we can get it to run long enough to use ;-)

There are other ways of using a cluster, but the idea of a 'type 2' Beowulf class machine is that it has a distributed process space and automatically balances the load on different nodes. Older 'type 1' Beowulf clusters use a DRM (Distributed Resource Manager) like SGE (Sun Grid Engine) to balance the load and schedule jobs. Both types of Beowulf are used to run MPI (Message Passing Interface) programs to split the load of a single job over multiple nodes in order to use the aggregate performance of the cluster. SSI is best for 'embarrasingly' parallel computation. A good starting point to learn is ClusterMonkey:

[http://www.clustermonkey.net/]("http://www.clustermonkey.net/")

Bye,

    Tony.

---

### Post by robasc on 2009-03-17
Thanks for the info ajt. I will be checking it out for sure.

Meanwhile, I have got something here that I need some of you to look over. I decided to go with a kerrighed setup using BigJimJams instructions; however, I was unsuccessful an getting the diskless nodes to boot up. I think you guys could probably help me to find my problems.

Ok, here is every thing wrapped up in a webpage that I have done from beginning to end which includes where I am with the project and what problems I am having. I know the page is lengthy, but I did not want to leave out anything on my setup.Please let me know what I am doing wrong and where I need to start.

Ok, here is the website to got to:

[KerrighedCluster.htm]("http://www.cpsspecialties.webhop.org/kerrighedCluster.htm")

---

### Post by ajt on 2009-03-17
> **robasc said:**
> Thanks for the info ajt. I will be checking it out for sure.
[...]
Ok, here is every thing wrapped up in a webpage that I have done from beginning to end which includes where I am with the project and what problems I am having. I know the page is lengthy, but I did not want to leave out anything on my setup.Please let me know what I am doing wrong and where I need to start.

Ok, here is the website to got to:

[KerrighedCluster.htm]("http://www.cpsspecialties.webhop.org/kerrighedCluster.htm")

Hello, robasc.

That's a bit of a long read!

The server 192.168.1.128 is excluded from your network:

192.168.1.128/25 = 192.168.1.0/255.255.255.128

The lowest address in this network is 192.168.1.129

Why do you not just use:

192.168.1.0/24 = 192.168.1.0/255.255.255.0

Bye,

    Tony.

---

### Post by robasc on 2009-03-17
I know it is a very long read but I did not want to leave anything out. 

I changed the network to 192.168.1.0/255.255.255.0 as you stated and now I get a PXE-E51 No DHCP or proxyDHCP offers were received.

I sure do appreciate everyone's help on this.

---

### Post by robasc on 2009-03-18
Well it seems to be booting up but I get this:

Done.

Gave up waiting for root device. Common problems:

-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/nfs does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(intitramfs)_

Not really sure what this all means but I believe I am missing some files but not sure. That is my best guess.

I updated the bottom of the webpage with a screen capture if you care to look at it.

---

### Post by bigjimjams on 2009-03-18
> **robasc said:**
> Well it seems to be booting up but I get this:

Done.

Gave up waiting for root device. Common problems:

-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/nfs does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(intitramfs)_

Not really sure what this all means but I believe I am missing some files but not sure. That is my best guess.

I updated the bottom of the webpage with a screen capture if you care to look at it.

Hi robasc, not sure if this would help but it seems that its booting the kernel from tftp fine but just not mounting the NFS. Have you tried editing /etc/network/interfaces on the server, and changing the ethernet card to manual, like you did with the nodes?

---

### Post by bigjimjams on 2009-03-18
> **robasc said:**
> Well it seems to be booting up but I get this:

Done.

Gave up waiting for root device. Common problems:

-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/nfs does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(intitramfs)_

Not really sure what this all means but I believe I am missing some files but not sure. That is my best guess.

I updated the bottom of the webpage with a screen capture if you care to look at it.

Hi robasc, just had another thought. When you updated the subnet mask from 255.255.255.128 to 255.255.255.0 in the DHCP server config file, did you also update the /etc/exports for the nfs server, as I've just noticed on your webpage it was still using 255.255.255.128, which might explain why the NFS isn't mounting.

---

### Post by bigjimjams on 2009-03-18
> **jedi453 said:**
> Hi BigJimJams,

Thanks for the great guide!

I did notice a few problems with the guide however...:

 - The guide doesn't show how to set up /etc/network/interfaces on the server

 - In /etc/default/dhcp3-server your missing a semi-colon at the end of the third to last line

 - In /etc/default/tftpd-hpa RUN_DAEMON should equal "yes" (all lowercase), mine was yelling at me without this (I was using debian so maybe that's why).


Just as a side note, I was having trouble at the tftp stage. DHCP assigned an IP address ok, but I recieved the "PXE-E32" error. This only happened on two of the three computers I was using.
So as this source ([http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg32044.html](http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg32044.html)) suggests I tried booting from a pxe cd. I used GPXE.
I went to their website ([http://kernel.org/pub/software/utils/boot/gpxe/](http://kernel.org/pub/software/utils/boot/gpxe/)) and downloaded the latest version. Then I untarred it (tar -xzf gpxe-*), then I changed directories into the new folder (cd gpxe-*).
Then I changed directory into src (cd src) then ran "make bin/gpxe.iso" Then the iso was in "bin/gpxe.iso". I was able to boot from this which resolved the problem.

Hi Jedi453, thanks for the feedback, from what I remember the only change I made to the /etc/network/interface file on the server (which should have been in the guide) was to edit the configuration for eth0 from auto to manual. The IP address and subnet mask were then assigned  manually, as mentioned in the guide. Question2 has been updated in the guide. Thanks for spotting that, there was bound to have been a typo in there somewhere! ;) I think point 3 is a distribution thing, as I've used capitals (if I remember correctly, it was written like this when the file was automatically created) and it works fine.

---

### Post by robasc on 2009-03-18
> 
Hi robasc, just had another thought. When you updated the subnet mask from 255.255.255.128 to 255.255.255.0 in the DHCP server config file, did you also update the /etc/exports for the nfs server, as I've just noticed on your webpage it was still using 255.255.255.128, which might explain why the NFS isn't mounting.


Hello BigJimJams, Yes I did, in fact I freshly installed the whole thing again using the subnet you gave in the tutorial.

But still having the same problem.

There are a couple of things I am wondering here and you might have already noticed on the webpage is that I am using intrepid amd64 version. 

I had to modify the updates for intrepid rather than hardy. Also I had to modify:

> 
debootstrap --arch i386 hardy /nfsroot/kerrighed [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)


To:

> 
debootstrap --arch amd64 intrepid /nfsroot/kerrighed [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)


I am not sure if this has anything to do with it.

Another problem I experienced is when I had to add a user in /nfsroot/kerrighed.

When I checked the /etc/sudoers file there was no user installed so I had to manually install the user as noted in the webpage.

This was just a couple of things I have been wondering about.

I really do not know what else to do but I am trying to think of something.

---

### Post by robasc on 2009-03-18
> 
Hi robasc, not sure if this would help but it seems that its booting the kernel from tftp fine but just not mounting the NFS. Have you tried editing /etc/network/interfaces on the server, and changing the ethernet card to manual, like you did with the nodes?


Ok, I set the server to:

> 
auto lo
iface lo inet loopback

iface eth0 inet manual


Just like the nodes. 

Then I manually configured the server ip address like so:

> 
sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up


Then  restarted the network and dhcp3

and I still have the same issue.

---

### Post by cstrrider on 2009-03-18
Hi 
I am fairly new to clustering and I've been having a hard time finding an up to date guide that works. I really appriciate your Kerrighed guide on Ubuntu, it's the best clustering guide I have tried yet. I am running ubuntu server 8.10 with the ubunu-desktop package install. when I try to run DHPC3-server I always get this error:
```
sudo /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]

```
I hope someone can help me with this.
Thanks,
Cstrrider

---

### Post by robasc on 2009-03-18
Assuming you are using the same addressing scheme as the guide try manually configuring your ip like so:
> 

sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up


Then:

> 
sudo /etc/init.d/networking restart


---

### Post by robasc on 2009-03-19
Everyone, I updated the webpage. I took some material and updated the  /etc/dhcp3/dhcpd.conf so my data would not become cluttered and confusing.


[kerrighedCluster.htm]("http://www.cpsspecialties.webhop.org/kerrighedCluster.htm")

---

### Post by jedi453 on 2009-03-19
Hi robasc, 

I got this problem too. Are you using an initramfs? I think I fixed it by changing my initramfs.conf file (which I think is in 

/etc/initramfs-tools/).

 Make sure initramfs-tools is installed
	```
sudo apt-get install initramfs-tools
```

 Copy /etc/initramfs-tools/initramfs.conf to a backup file
	```
sudo cp /etc/initramfs-tools/initramfs.conf{,.old}
```

 Edit /etc/initramfs-tools/initramfs.conf change the line BOOT=local to BOOT=nfs

 Copy your current initramfs to a backup. Replace "<kernelversion>" with your kernel version in the form 2.6.xx-something (if 

you don't know what it is and your using your running kernel just replace it with "$(uname -r)" without quotes)
	```
sudo cp /boot/initrd.img-<kernel-version>{,.old}
```


 If that fails I recommend against continuing.

 We're going to overwrite /srv/tftp/initrd.img (if it exists). So move it to a backup file
	```
sudo mv /srv/tftp/initrd.img{,.old}
```

 Then I remade my initramfs (making sure not to overwrite the initramfs I was using). Replace "<kernelversion>" with your 

kernel version in the form vmlinuz-2.6.xx-something (if you don't know what it is and your using your running kernel just 

replace it with "vmlinuz-$(uname -r)" without quotes (notice the "vmlinuz-" this time)) 
	```
sudo mkinitramfs -o /srv/tftp/initrd.img <kernel-version>
```	

 Change /srv/tftp/pxelinux.cfg/default to accept the new initrd now called "initrd.img"

 Then copy the old initramfs.conf back to the old name
	```
sudo cp /etc/initramfs-tools/initramfs.conf{.old,}
```	

 I found this idea from a post on [http://www.howtoforge.com/pxe_booting_debian](http://www.howtoforge.com/pxe_booting_debian) .

Good luck

---

### Post by robasc on 2009-03-19
> 
Hi robasc,

I got this problem too. Are you using an initramfs? I think I fixed it by changing my initramfs.conf file (which I think is in

/etc/initramfs-tools/).

Make sure initramfs-tools is installed
Code:

sudo apt-get install initramfs-tools

Copy /etc/initramfs-tools/initramfs.conf to a backup file
Code:

sudo cp /etc/initramfs-tools/initramfs.conf{,.old}

Edit /etc/initramfs-tools/initramfs.conf change the line BOOT=local to BOOT=nfs

Copy your current initramfs to a backup. Replace "<kernelversion>" with your kernel version in the form 2.6.xx-something (if

you don't know what it is and your using your running kernel just replace it with "$(uname -r)" without quotes)
Code:

sudo cp /boot/initrd.img-<kernel-version>{,.old}






I appreciate that help jedi, unfortunately for me it did not work. I went up to the point above.

Any other suggestions would be appreciated as well.

Thanks

---

### Post by bigjimjams on 2009-03-19
> **jedi453 said:**
> Hi robasc, 

I got this problem too. Are you using an initramfs? I think I fixed it by changing my initramfs.conf file (which I think is in 

/etc/initramfs-tools/).

 Make sure initramfs-tools is installed
	```
sudo apt-get install initramfs-tools
```

 Copy /etc/initramfs-tools/initramfs.conf to a backup file
	```
sudo cp /etc/initramfs-tools/initramfs.conf{,.old}
```

 Edit /etc/initramfs-tools/initramfs.conf change the line BOOT=local to BOOT=nfs

 Copy your current initramfs to a backup. Replace "<kernelversion>" with your kernel version in the form 2.6.xx-something (if 

you don't know what it is and your using your running kernel just replace it with "$(uname -r)" without quotes)
	```
sudo cp /boot/initrd.img-<kernel-version>{,.old}
```


 If that fails I recommend against continuing.

 We're going to overwrite /srv/tftp/initrd.img (if it exists). So move it to a backup file
	```
sudo mv /srv/tftp/initrd.img{,.old}
```

 Then I remade my initramfs (making sure not to overwrite the initramfs I was using). Replace "<kernelversion>" with your 

kernel version in the form vmlinuz-2.6.xx-something (if you don't know what it is and your using your running kernel just 

replace it with "vmlinuz-$(uname -r)" without quotes (notice the "vmlinuz-" this time)) 
	```
sudo mkinitramfs -o /srv/tftp/initrd.img <kernel-version>
```	

 Change /srv/tftp/pxelinux.cfg/default to accept the new initrd now called "initrd.img"

 Then copy the old initramfs.conf back to the old name
	```
sudo cp /etc/initramfs-tools/initramfs.conf{.old,}
```	

 I found this idea from a post on [http://www.howtoforge.com/pxe_booting_debian](http://www.howtoforge.com/pxe_booting_debian) .

Good luck

Hi Jedi453, this is a good point to note for doing a diskless-boot. Now that you've mentioned it, I vaguely recall doing something similar. However, when you get round to using the kerrighed kernel, you don't use a initrd.img when booting.

---

### Post by bigjimjams on 2009-03-19
> **robasc said:**
> Ok, I set the server to:



Just like the nodes. 

Then I manually configured the server ip address like so:



Then  restarted the network and dhcp3

and I still have the same issue.

Hi robasc, sorry to hear that your still having troubles! I noticed you we're using the 64-bit kernel and intrepid. I've actually been setting up another kerrighed cluster today, this time using the 64-bit kernel and 8.04. I followed the same guide as documented and setup eth0, as you've just mentioned, and it seemed to diskless boot fine. So maybe something has changed in 8.10 that I'm missing! 

Also, from when adding a new user in the diskless boot system, it isn't automatically added to the sudoers file, which is why I mentioned adding them in the guide. I'll keep thinking about possible solutions.

---

### Post by robasc on 2009-03-19
Cool, well it looks like were on to a new idea then. Let's solve the mystery.

Thanks

---

### Post by agungaryo on 2009-03-19
hi everyone

I tried to create cluster for a simulation for the 1st time
and I followed the tutorial ,
for installing process until the end of tutorial ,everything works fine with some problems which were solved. ^_^

for an intro ,i just try to use 2 nodes and 1 server ( UBUNTU server hardy )
i check with "top" in node cluster , it appears 3 CPUs

when i try to execute my simulation in server (reach the CPU USAGE =100%)
but when i see in node cluster ,all of CPUs ( 3 CPUs) doesn't appear CPU USAGE (100%),it means none of them shows CPU USAGE =100% or share the LOAD from server.

i think ,the problem is i dont know how to use kerrighed ,so it can share the load of server

thank you 


agung aryo

---

### Post by agungaryo on 2009-03-19
hi robasc,
I'm beginner in ubuntu,
i've read yours ,it's long to read 
but it's nice
i just want to know,
does your current kernel have NFS module ?

---

### Post by bigjimjams on 2009-03-20
> **agungaryo said:**
> hi everyone

I tried to create cluster for a simulation for the 1st time
and I followed the tutorial ,
for installing process until the end of tutorial ,everything works fine with some problems which were solved. ^_^

for an intro ,i just try to use 2 nodes and 1 server ( UBUNTU server hardy )
i check with "top" in node cluster , it appears 3 CPUs

when i try to execute my simulation in server (reach the CPU USAGE =100%)
but when i see in node cluster ,all of CPUs ( 3 CPUs) doesn't appear CPU USAGE (100%),it means none of them shows CPU USAGE =100% or share the LOAD from server.

i think ,the problem is i dont know how to use kerrighed ,so it can share the load of server

thank you 


agung aryo

Hi agung aryo, the server should not be running the kerrighed kernel, only the nodes should. Therefore any application run on the server won't migrate to the nodes. You have to ssh into one of the nodes, and launch the application/simulation from a node. If the application/simulation uses multiple processes, then you should see the processes migrate to all CPUs in the cluster and all of the nodes should reach CPU USAGE = 100% if you're working it hard enough.:D

---

### Post by robasc on 2009-03-20
Hello agungaryo, I am not sure about an nfs module. I am very new to this as well. Hopefully everyone together can solve this issue.

Also, I would like to inform everyone that I installed 8.04 amd64 on the cluster and it booted up just fine and was able to log in on the nodes.

But I did run across a problem when installing kerrighed.

Here is the issue:

1. ) When I began performing the downloads awk was not found. The program asked me to download gawk. So I did. Don't know if anyone else run in to this before.

2. ) When I got down to configuring the kernel I left this at default. I am not sure of how to configure the kernel and check the nfs and network card driver?

3. ) And finally I run the make install and it failed. Here is the fault instructions:

> 
root@master-node:/usr/src/kerrighed-2.3.0# make
Making all in modules
make[1]: Entering directory `/usr/src/kerrighed-2.3.0/modules'
make -C "/usr/src/linux-2.6.20" modules_prepare
make[2]: Entering directory `/usr/src/linux-2.6.20'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: Leaving directory `/usr/src/linux-2.6.20'
touch .modules_prepare
rm -f "/usr/src/kerrighed-2.3.0/modules/asm"
[ "/usr/src/kerrighed-2.3.0" == "/usr/src/kerrighed-2.3.0" ] || lndir -silent "/usr/src/kerrighed-2.3.0/modules"
[: 1: ==: unexpected operator
/usr/src/kerrighed-2.3.0/modules: From and to directories are identical!
make[1]: *** [all-y] Error 1
make[1]: Leaving directory `/usr/src/kerrighed-2.3.0/modules'
make: *** [all-recursive] Error 1
root@master-node:/usr/src/kerrighed-2.3.0# 



Not sure what is going on here. It seems there is a duplicate of /usr/src/kerrighed-2.3.0?

Anyone?

Going back to the ubuntu 8.10 amd64 version, I am going to install another partition so I can keep hammering away at it. Hopefully I will find the reason for nfs not working.

---

### Post by agungaryo on 2009-03-20
> **robasc said:**
> Hello agungaryo, I am not sure about an nfs module. I am very new to this as well. Hopefully everyone together can solve this issue.

Also, I would like to inform everyone that I installed 8.04 amd64 on the cluster and it booted up just fine and was able to log in on the nodes.

But I did run across a problem when installing kerrighed.

Here is the issue:

1. ) When I began performing the downloads awk was not found. The program asked me to download gawk. So I did. Don't know if anyone else run in to this before.

2. ) When I got down to configuring the kernel I left this at default. I am not sure of how to configure the kernel and check the nfs and network card driver?

3. ) And finally I run the make install and it failed. Here is the fault instructions:



Not sure what is going on here. It seems there is a duplicate of /usr/src/kerrighed-2.3.0?

Anyone?

Going back to the ubuntu 8.10 amd64 version, I am going to install another partition so I can keep hammering away at it. Hopefully I will find the reason for nfs not working.

(1) I think that's fine 
(2) even the default has selected the necessary module but you must ensure that your network driver and NFS is included in kernel because I've seen the default setting doesn't include some network drivers, I'm also got a problem from this step, my node has SIS network Card . but after i compiled the kernel n node try to boot ,the network card wasn' detected even I've included the SIS driver module.my solution is "i change the network card" ,hi2
(3) I see, yup it's true. . .it's "numpuk" (indo)
     i guess , U must try to enter the kerrighed directory and 
 do " make clean" and " make uninstall"
and repeat the step


for the interpid amd64 ,u can try to check Ur current kernel with .
"lsmod | grep nfs" , i think nfs ( maybe client) must present because "test diskless boot "is node try to boot with our current kernel

sorry if my answer above is wrong 

thank you

agung aryo ( AccessNet )

---

### Post by bigjimjams on 2009-03-20
> **robasc said:**
> Hello agungaryo, I am not sure about an nfs module. I am very new to this as well. Hopefully everyone together can solve this issue.

Also, I would like to inform everyone that I installed 8.04 amd64 on the cluster and it booted up just fine and was able to log in on the nodes.

But I did run across a problem when installing kerrighed.

Here is the issue:

1. ) When I began performing the downloads awk was not found. The program asked me to download gawk. So I did. Don't know if anyone else run in to this before.

2. ) When I got down to configuring the kernel I left this at default. I am not sure of how to configure the kernel and check the nfs and network card driver?

3. ) And finally I run the make install and it failed. Here is the fault instructions:



Not sure what is going on here. It seems there is a duplicate of /usr/src/kerrighed-2.3.0?

Anyone?

Going back to the ubuntu 8.10 amd64 version, I am going to install another partition so I can keep hammering away at it. Hopefully I will find the reason for nfs not working.

Hi robasc, yet I've noted a couple of errors in the guide when doing the fresh install yesterday. I response to 1) it should be gawk you install and not awk. 2) the default config doesn't necessarily install you NIC in the kernel. I think if I remember correctly, if you go to Device Drivers ---> Network Drivers ---> and then 10/100 or 1000 you can choose to install your network card. Make sure it isn't installed as a module (not a "M"). The NFS v3 is normally installed by the default config. As for 3) I'll have a look at what I did, as I can remember getting this error before I managed to get it working but somehow managed to find a work around. I'll let you know.

---

### Post by jedi453 on 2009-03-20
> **robasc said:**
> Hello agungaryo, I am not sure about an nfs module. I am very new to this as well. Hopefully everyone 

together can solve this issue.

Also, I would like to inform everyone that I installed 8.04 amd64 on the cluster and it booted up just fine and was able to log 

in on the nodes.

But I did run across a problem when installing kerrighed.

Here is the issue:

1. ) When I began performing the downloads awk was not found. The program asked me to download gawk. So I did. Don't know if 

anyone else run in to this before.

2. ) When I got down to configuring the kernel I left this at default. I am not sure of how to configure the kernel and check 

the nfs and network card driver?

3. ) And finally I run the make install and it failed. Here is the fault instructions:



Not sure what is going on here. It seems there is a duplicate of /usr/src/kerrighed-2.3.0?

Anyone?

Going back to the ubuntu 8.10 amd64 version, I am going to install another partition so I can keep hammering away at it. 

Hopefully I will find the reason for nfs not working.

Interesting. I think problem three is a result of installing build-essential. I think it installs version 4.x of gcc. This 

would cause a problem with kerrighed, as it only likes 3.3 of gcc. Gcc-3.3 is installed to /usr/bin/gcc-3.3 instead of 

/usr/bin/gcc. You'll probably have to copy gcc-3.3 to /usr/bin/gcc , or create a symbolic link. As I don't know much about 

symbolic links I'll tell you how to copy gcc-3.3 . I don't know why there would be a duplicate of /usr/src/kerrighed-2.3.0

First chroot to /nfsroot/kerrighed
```
sudo chroot /nfsroot/kerrighed
```

Then check for /usr/bin/gcc-3.3
```
ls /usr/bin/gcc-3.3
```

If there was no output for that, the following won't work. The output should be "/usr/bin/gcc-3.3" . If there was no output 

install gcc-3.3 ( sudo apt-get install gcc-3.3 ) and try again.

First back up your old version of gcc:
```
cp /usr/bin/gcc{,.old}
```

Then copy gcc-3.3 to /usr/bin/gcc
```
cp /usr/bin/gcc{-3.3,}
```

You may need to delete your /usr/src/kerrighed-2.3.0 and /usr/src/linux-2.6.20 (in chroot [/nfsroot/kerrighed]) and redownload 

them. 

```
rm -rf /usr/src/kerrighed-2.3.0 /usr/src/linux-2.6.20
```

Then start from the third code line (right after chrooting and apt-get) in part 2.1 in bigjimjams's guide. Make sure to compile the kernel with the correct options. See above posts for how to do that.

Then the compile should go ok, unless you had another problem too.

If you want to change back things once you're done just move /usr/bin/gcc.old to /usr/bin/gcc

---

### Post by agungaryo on 2009-03-20
> **bigjimjams said:**
> Hi agung aryo, the server should not be running the kerrighed kernel, only the nodes should. Therefore any application run on the server won't migrate to the nodes. You have to ssh into one of the nodes, and launch the application/simulation from a node. If the application/simulation uses multiple processes, then you should see the processes migrate to all CPUs in the cluster and all of the nodes should reach CPU USAGE = 100% if you're working it hard enough.:D

hi bigjimjams,


client (10.14.200.0/24)<---------->server simulation (ubuntu server)<-------> nodes cluster (192.168.1.0/24)

my simulation is in server ( ubuntu server) 
- u mean that I must reinstall the simulation at node cluster ?
- my simulation has client server application if i install at node cluster the client should access 192.168.1.0 network ,it means I should redirect from 10.14.200.0 to 192.169.1.0 ?
- I've two nodes cluster,but why "top" result (execute in node ) 3 CPUs, does it mean server include in ??


thank you 


agung aryo

---

### Post by robasc on 2009-03-21
Well Jedi, I tried what you said but I still came up with the same message duplicate found. 

I am going to try and reinstall it and see if this works.

---

### Post by jedi453 on 2009-03-21
> **robasc said:**
> Well Jedi, I tried what you said but I still came up with the same message duplicate found. 

I am going to try and reinstall it and see if this works.

Sorry I gave you two wrong answers.:( It's just tough diagnose the errors over the net. I assumed you got errors for the same reasons I did the first time I tried it. Maybe it's because I used Debian. You still might need to use gcc-3.3 to compile (as this source says [http://www.kerrighed.org/wiki/index.php/Installing_Kerrighed_2.3.0](http://www.kerrighed.org/wiki/index.php/Installing_Kerrighed_2.3.0)). But if you try the code below and it returns version 4.1.x or 3.3.x then you might be fine according to the same source:
```
gcc --version
```

Don't give up!:)

Good luck!

---

### Post by robasc on 2009-03-21
I agree it is not easy fixing problems over the internet.

gcc -version actually returned 4.2.4 

Something else I noticed when configuring the kernel. My ethernet card is not listed

It shows a rtk 8169 but does not show a rtk 8111c?

---

### Post by bigjimjams on 2009-03-23
> **robasc said:**
> Hello agungaryo, I am not sure about an nfs module. I am very new to this as well. Hopefully everyone together can solve this issue.

Also, I would like to inform everyone that I installed 8.04 amd64 on the cluster and it booted up just fine and was able to log in on the nodes.

But I did run across a problem when installing kerrighed.

Here is the issue:

1. ) When I began performing the downloads awk was not found. The program asked me to download gawk. So I did. Don't know if anyone else run in to this before.

2. ) When I got down to configuring the kernel I left this at default. I am not sure of how to configure the kernel and check the nfs and network card driver?

3. ) And finally I run the make install and it failed. Here is the fault instructions:



Not sure what is going on here. It seems there is a duplicate of /usr/src/kerrighed-2.3.0?

Anyone?

Going back to the ubuntu 8.10 amd64 version, I am going to install another partition so I can keep hammering away at it. Hopefully I will find the reason for nfs not working.

Hi robasc, regarding point 3 above, I've been tinkering around and have possibly found a workaround, however, I didn't get chance to boot up the kerrighed cluster to test it out. Once more it involves a couple of things I missed out of the guide but remember doing, since I saw your message. Firstly, in the chroot'ed nfsboot system, you need to check your environment variables, so do the following.
```
$ export
```
Look to see if you have the variables CC=gcc-3.3, CXX=g++-3.3 and CPP=cpp-3.3. If not, then you may also not have the packages installed. So do the following:
```
apt-get install gcc-3.3 g++-3.3 cpp-3.3
export CC=gcc-3.3
export CXX=g++-3.3
export CPP=cpp-3.3
```
Once you've got these installed and the variables setup, you can do the following to install Kerrighed, which is pretty much what the guide does.
```
cd /usr/src/kerrighed-*
./configure --with-kernel=/usr/src/linux-2.6.20
make patch
make defconfig
cd ../linux-2.6.20
make menuconfig
cd ../kerrighed-*
make kernel
make -i
make kernel-install
make install -i
```

The -i flag will ignore errors, so you'll still get the error message but it seems to build and install all the necessary tools, modules, etc in the correct places. Hope this helps!:D

---

### Post by agungaryo on 2009-03-24
hi everyone,

I've two interface in server (ubuntu server with DHCP,NFS,PXE server)
eth0 (192.168.1.0/24)--> hub which contains some nodes
eth1 (10.14.200.0/24)--> client for simulation (server client application)


I've installed kerrighed cluster according with tutorial,
bigjimjam says that i must run my simulation at node (192.168.0/24),but see my client simulation is at (10.14.200.0/24)
my simulation has been installed at server (ubuntu server) and it needs to be triggered by client 

1) do i have to reinstall my simulation at node if i want to implement this clustering?
2) client has some problems if the simulation run at node (192.168.1.0/24) while client is at (10.14.200.0/24). even i can force my client move to (192.168.1.0/24)network.but I imagine if this kerrighed cluster is implemented for a web server which has IP PUBLIC ,how to manage the IP while I guess node at IP PRIVATE,any idea with this problems?

thank you
agung aryo,

---

### Post by bigjimjams on 2009-03-24
> **agungaryo said:**
> hi everyone,

I've two interface in server (ubuntu server with DHCP,NFS,PXE server)
eth0 (192.168.1.0/24)--> hub which contains some nodes
eth1 (10.14.200.0/24)--> client for simulation (server client application)


I've installed kerrighed cluster according with tutorial,
bigjimjam says that i must run my simulation at node (192.168.0/24),but see my client simulation is at (10.14.200.0/24)
my simulation has been installed at server (ubuntu server) and it needs to be triggered by client 

1) do i have to reinstall my simulation at node if i want to implement this clustering?
2) client has some problems if the simulation run at node (192.168.1.0/24) while client is at (10.14.200.0/24). even i can force my client move to (192.168.1.0/24)network.but I imagine if this kerrighed cluster is implemented for a web server which has IP PUBLIC ,how to manage the IP while I guess node at IP PRIVATE,any idea with this problems?

thank you
agung aryo,


Hi Agung Aryo, what type of simulation are you running? In my opinion, I can see too different options:

1) The client connects to the simulation on the server, which can then execute other programs/processes of the simulation on the cluster nodes via ssh.
2) The client connects to the server, which then grabs the information from the client and passes this to the cluster nodes when executing the simulation on the cluster nodes via ssh.

In order to have kerrighed working properly, only the cluster nodes should run the kerrighed kernel, the server should just be running a standard Ubuntu kernel. Also, the cluster nodes should have there own private network with the server. A client should not be connected to this private network, as all a client should see is the server, which then submits jobs to the cluster nodes. Hope this helps?

---

### Post by koukoobangoo on 2009-03-26
Hi everyone
I'm a new user of Kerrighed. I set uo a cluster composed of three machines just like it is said in the easy ubuntu clustering tutorial fo kerrighed.

The problem is, the disks in each node seem not to be working.
It is said that one of the features of kerrighed is cluster file systems which means total virtualization of all the node's disks.

Is Kerrighed really able to show all the disks as an only one disk??

---

### Post by ajt on 2009-03-26
> **koukoobangoo said:**
> Hi everyone
I'm a new user of Kerrighed. I set uo a cluster composed of three machines just like it is said in the easy ubuntu clustering tutorial fo kerrighed.

The problem is, the disks in each node seem not to be working.
It is said that one of the features of kerrighed is cluster file systems which means total virtualization of all the node's disks.

Is Kerrighed really able to show all the disks as an only one disk??

Hello, koukoobangoo.

KerFS was (temporarily) removed at Kerrighed 2.0.0 because it caused kernel crashes. It now seems to be developed as a separate module:

[http://www.kerrighed.org/wiki/index.php/KernelDevelKdFS]("http://www.kerrighed.org/wiki/index.php/KernelDevelKdFS")

Bye,

    Tony.

---

### Post by apprentice_clusterer on 2009-03-29
> **bigjimjams said:**
> In order to have kerrighed working properly, only the cluster nodes should run the kerrighed kernel, the server should just be running a standard Ubuntu kernel.

Hello bigjimjams,

why can't the server participate to the kerrighed cluster ? I couldn't find a technical explanation for this on their website, but maybe I haven't looked hard enough :confused:

Since kerrighed is an SSI cluster, it would be nice to be able to use also the server as an additional node; excluding from the migration, of course, some of the processes (e.g. X).

I'm building a very small experimental cluster, with less than 5 nodes... giving up on one would make quite a difference :)

---

### Post by bigjimjams on 2009-03-29
> **apprentice_clusterer said:**
> Hello bigjimjams,

why can't the server participate to the kerrighed cluster ? I couldn't find a technical explanation for this on their website, but maybe I haven't looked hard enough :confused:

Since kerrighed is an SSI cluster, it would be nice to be able to use also the server as an additional node; excluding from the migration, of course, some of the processes (e.g. X).

I'm building a very small experimental cluster, with less than 5 nodes... giving up on one would make quite a difference :)

Hi apprentice_clusterer, as far as I know it's because all the nodes that are part of the SSI cluster have to share a root file system of some sort, whether this is via NFS, UNFS3, etc. The server can't be in the cluster as it can't share the same root file system. Hope this helps.

---

### Post by bigjimjams on 2009-03-29
> **robasc said:**
> I agree it is not easy fixing problems over the internet.

gcc -version actually returned 4.2.4 

Something else I noticed when configuring the kernel. My ethernet card is not listed

It shows a rtk 8169 but does not show a rtk 8111c?

Hi robasc, I've managed to get kerrighed running using the 64-bit version of Hardy. However, I ended up using the revision 4762 of the SVN version of kerrighed, as I seemed to run into issues compiling 2.3 for a 64-bit kernel. I followed the same procedure as the guide on Easy Ubuntu Clustering, but the following was different in the kerrighed install:

```
sudo apt-get install subversion
svn checkout svn://scm.gforge.inria.fr/svn/kerrighed/trunk /nfsroot/kerrighed/usr/src/trunk -r 4762
sudo chroot /nfsroot/kerrighed
apt-get install automake autoconf libtool pkg-config gawk rsync bzip2 gcc-3.3 ncurses-dev wget lsb-release xmlto patchutils xutils-dev build-essential grub g++-3.3
cd /usr/src/trunk
./autogen.sh
./configure CC=gcc-3.3 CXX=g++-3.3
make defconfig
cd kernel
make menuconfig
cd ..
make kernel
make -i
make kernel-install
make install -i
```

I'll update the wiki soon so that it details how to install the SVN version too. In later revisions from the svn, you can drop the -i flag, as they seem to have corrected the src folder == dest folder issue. You also have to ensure you install certain things into the kernel for the new scheduler in Kerrighed. These can be found on the [SchedConfig]("http://www.kerrighed.org/wiki/index.php/SchedConfig") page.

As for the network card, I had the same chipset in my old machine and just enabled the 8169 in the kernel and it worked fine.

---

### Post by ajt on 2009-03-29
> **bigjimjams said:**
> Hi apprentice_clusterer, as far as I know it's because all the nodes that are part of the SSI cluster have to share a root file system of some sort, whether this is via NFS, UNFS3, etc. The server can't be in the cluster as it can't share the same root file system. Hope this helps.

Hello, bigjimjams and apprentice_clusterer.

That's not quite right - They have to share configuration information, and an easy way to achieve that is to use a single NFSROOT. However, you could just replicate the information manually. We've run Kerrighed on four independant Debian compute servers without any problem - Well, at least not relating to sharing the root filesystem ;-)

In our case, I could share the server root filesystem, but I don't, because it's already being shared with openMosix compute nodes using UNFS3 with 'cluster' extensions enabled as I mentioned previously. I'll post instructions about UNFS3 and clusterNFS on the Wiki when I've got time. Basically, the UNFS3 server interprets 'tags' for different client IP addresses or for clients in general.g.:

```

unique_file
unique_file$$192.168.1.98$$
unique_file$$192.168.1.99$$

shared_file
shared_file$$CLIENT$$

```

When "unique_file" is requested by a client, the UNFS3 server checks for the presence of 'tagged' files on the server. If tagged files are found, they are interpreted, otherwise the normal file is served. This makes it possible to share the root filesystem of the NFSROOT server with the PXE-booted compute nodes.

The contents of "unique_file" on the server are different to either file on the nodes with the  IP addresses. The contents of "shared_file" on the server are different to the contents of "shared_file" on the clients, but are the same on all clients. There is a performance overhead when interpreting tags, so I don't use it where it is not actually needed.

This is all documented at:

[http://unfs3.sourceforge.net/]("http://unfs3.sourceforge.net/")

Bye,

Tony.

---

### Post by floz23 on 2009-03-29
Greetings everyone! I've been watching this thread for a while now, and decided that I have to help a few friends try and reduce their povray rendering times :P

Now, I have a few questions that I can't seem to find clear answers to.

1. The server for the cluster will be a core i7 machine with 12gb of ram, so its obvious that i'd run a 64bit os.  Does this mean that all of my nodes have to run 64bit Kerrighed kernels too? Or can the nodes run both 32bit and 64bit builds of Kerrighed?

2. povray 3.7 is now natively multithreaded.  Can anyone confirm that the threads from povray 3.7 are distributed through all the nodes? 

Much thanks,
-Adam

---

### Post by bigjimjams on 2009-03-30
> **floz23 said:**
> Greetings everyone! I've been watching this thread for a while now, and decided that I have to help a few friends try and reduce their povray rendering times :P

Now, I have a few questions that I can't seem to find clear answers to.

1. The server for the cluster will be a core i7 machine with 12gb of ram, so its obvious that i'd run a 64bit os.  Does this mean that all of my nodes have to run 64bit Kerrighed kernels too? Or can the nodes run both 32bit and 64bit builds of Kerrighed?

2. povray 3.7 is now natively multithreaded.  Can anyone confirm that the threads from povray 3.7 are distributed through all the nodes? 

Much thanks,
-Adam

Hi Adam, depends on what setup you choose to use, but normally the server doesn't take part in the kerrighed cluster, therefore the server runs a different kernel to the nodes, so it doesn't matter if this is 32-bit or 64-bit. However, I'm unable to comment if you can mix 32-bit and 64-bit kernels in the cluster, my guess is probably not. As for 2), kerrighed only supports process migration, so threads will only be processed on the CPU they are launched. If this CPU is multi-core, then the threads have access to all the cores of the CPU. Hope this helps.

---

### Post by koukoobangoo on 2009-03-30
Hi everybody..
I'm working now Clustering. I set up a trial cluster of three machines just the way it is said in the EasyUbuntuClustering. I'm using kerrighed.

The problem is that, I couldn't find a sultion for storage. It is said that kerrighed could virtualize all the disks on each node. Is it true??

And if not, what shared disk file system shall I use??

Need help

Thanks

---

### Post by koukoobangoo on 2009-03-30
Hi tony..

I know this is a separate module. There is no way i can download it. I went to the repository of INRIA, and finally founed a version of Kerrighed containing KDFS instead of KerFS. I installed it. But id doesn't seem to be working.

Has anyone else found a solution for storage with kerrighed??

---

### Post by djamu on 2009-03-30
> **floz23 said:**
> floz23 

Did you try to contact me thru my site ? 



> **koukoobangoo said:**
> 
.....
Has anyone else found a solution for storage with kerrighed??

You could use OCFS2 > wouldn't try if I was you / on a small setup. It's designed for SAN storage with LUN's ( either iSCSI / fiber ) 

GlusterFS > works quite well ( albeit some parts run in userspace ), supports load balancing / HA configs / 

or..
Just stick to NFS > you can tremendously speed it up using AUFS & a COW loop ( you only read from the server > changes are written to a local FS ( use tempfs ) ...

---

### Post by floz23 on 2009-03-30
> **djamu said:**
> Did you try to contact me thru my site

I sent you a message a few moments ago...

---

### Post by agungaryo on 2009-03-31
> **bigjimjams said:**
> Hi Agung Aryo, what type of simulation are you running? In my opinion, I can see too different options:

1) The client connects to the simulation on the server, which can then execute other programs/processes of the simulation on the cluster nodes via ssh.
2) The client connects to the server, which then grabs the information from the client and passes this to the cluster nodes when executing the simulation on the cluster nodes via ssh.

In order to have kerrighed working properly, only the cluster nodes should run the kerrighed kernel, the server should just be running a standard Ubuntu kernel. Also, the cluster nodes should have there own private network with the server. A client should not be connected to this private network, as all a client should see is the server, which then submits jobs to the cluster nodes. Hope this helps?

hi bigjimjams ,thank in advance for responding 

I'm new in clustering
my simulation can be described like web server
I want to analyze how much the capacity of web server if I use clustering

cluster nodes ------- server (web server )----- clients (web clients)

the thousands client will request the site , it makes web server overload ( CPU usage 100%), I try to solve that problem with clustering 

any idea with my problem ?


thank you
agung aryo

---

### Post by ajt on 2009-03-31
> **agungaryo said:**
> hi bigjimjams ,thank in advance for responding 

I'm new in clustering
my simulation can be described like web server
I want to analyze how much the capacity of web server if I use clustering

cluster nodes ------- server (web server )----- clients (web clients)

the thousands client will request the site , it makes web server overload ( CPU usage 100%), I try to solve that problem with clustering 

any idea with my problem ?


Hello, agung aryo.

A Beowulf is not the same thing as a web server farm: Most people use a DNS 'round-robin' to spread the load between multiple web servers. That means when clients request a page from the web server IP address the local DNS redirects it to one machine in the available pool of servers.

Bye,

Tony.

---

### Post by agungaryo on 2009-03-31
> **ajt said:**
> Hello, agung aryo.

A Beowulf is not the same thing as a web server farm: Most people use a DNS 'round-robin' to spread the load between multiple web servers. That means when clients request a page from the web server IP address the local DNS redirects it to one machine in the available pool of servers.

Bye,

Tony.

thank you,ajt.
but I've tried to use multiple server with round robin balancing,but the result is not satisfied . some issues appear like crash on database,DNS cache (while server get hundreds request from client),n I've checked the common error isn't at bandwidth but in CPU USAGE which causes "time out" error at client.
does kerrighed really not help my problem ?

by the way ,do I have to install my simulation at cluster node (kerrighed kernel) to use clustering ?

thank you 
agung aryo

---

### Post by robasc on 2009-04-02
Hello everyone, It's been a little while since I last posted. BigJimJams, I have not had a chance to try what you said yet, been busy working. I will try it this week when I get a chance.

---

### Post by apprentice_clusterer on 2009-04-04
Hello, bigjimjams and ajt,

thank you  both for having explained the problem and for having also suggested a solution.

I will try to put in practise the suggestions.

regards

---

### Post by robasc on 2009-04-13
Well BigJimJams

I did everything you said and I got this error:

trying to load: pxelinux.cfg/default

could not find kernel image: linux
boot:

---

### Post by robasc on 2009-04-13
Hey BigJimJams, I got it to boot and I am logged in to all of my nodes but I am still having some trouble though. 

I am trying to use the commands from the setup files for kerrighed and they are not doing anything.

Check to see if nodes in the cluster are running

sudo krgadm nodes

when I try to run this i get command not found

So then I tried to run it chroot /nfsroot/kerrighed and then it says are you sure you want to run kerrighed? and it does not let me type yes or no. It just goes to the command prompt.

I looked at the processes and only seen cpu 1 and 2 running if I am viewing it correctly.

I do not think I understand how to use kerrighed yet.

---

### Post by Rickles65 on 2009-04-15
Maybe I'm just thick headed today... So is there nothing out there any more that does process (thread) migration?

We have a need (and it's just 3 machines) for high CPU threads to be moved off to the more idle machines.

We'd done this before (about 5 years ago) with OpenMosix. We just added the appropriate kernel mods, NFS mounts and off we went.

The machines are fully loaded in this config as well so there's no need for SSI in the current config either. Just the net mounts and kernel changes.

---

### Post by bigjimjams on 2009-04-17
> **robasc said:**
> Hey BigJimJams, I got it to boot and I am logged in to all of my nodes but I am still having some trouble though. 

I am trying to use the commands from the setup files for kerrighed and they are not doing anything.

Check to see if nodes in the cluster are running

sudo krgadm nodes

when I try to run this i get command not found

So then I tried to run it chroot /nfsroot/kerrighed and then it says are you sure you want to run kerrighed? and it does not let me type yes or no. It just goes to the command prompt.

I looked at the processes and only seen cpu 1 and 2 running if I am viewing it correctly.

I do not think I understand how to use kerrighed yet.

Hi Robasc, it might be the case that the kernel was built but the tools were not. What is in the contents of /usr/local/bin on the nodes? Also, are you using the svn version of kerrighed? If so, did you create the /config directory, modify the fstab of the nodes, and configure the new scheduler that kerrighed uses by running sudo krg_legacy_scheduler? Can you give us the tail of dmesg from one of the nodes.

---

### Post by jbbjshlws on 2009-04-20
Hello all!,

Firstly i would like to say fantastic guide, it has helped a lot.

I have ran into a few problems, but nothing a google search didn't find (the problems are/were moslty from lack of experience with linux).

The problem i am facing now that google couldnt help out with is this error after i have pxe booted the client node:


Gave up waiting for root device. Common problems:

-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/nfs does not exist. Dropping to a shell!


I have read through and seen that robasc has had this same error, but i didn't see any solution to the problem. My setup differs from Rob's in i am running all i386 32 bit machines, and stayed with the suggested:
$ sudo apt-get install debootstrap
debootstrap --arch i386 hardy /nfsroot/kerrighed [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

for the bootable file system.

I am not sure why i am getting this error, and any help would be greatly appreciated. let me know if you need any logs (and let me know how to get them...lol)

Cheers,
Josh

---

### Post by bigjimjams on 2009-04-21
> **jbbjshlws said:**
> Hello all!,

Firstly i would like to say fantastic guide, it has helped a lot.

I have ran into a few problems, but nothing a google search didn't find (the problems are/were moslty from lack of experience with linux).

The problem i am facing now that google couldnt help out with is this error after i have pxe booted the client node:


Gave up waiting for root device. Common problems:

-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/nfs does not exist. Dropping to a shell!


I have read through and seen that robasc has had this same error, but i didn't see any solution to the problem. My setup differs from Rob's in i am running all i386 32 bit machines, and stayed with the suggested:
$ sudo apt-get install debootstrap
debootstrap --arch i386 hardy /nfsroot/kerrighed [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

for the bootable file system.

I am not sure why i am getting this error, and any help would be greatly appreciated. let me know if you need any logs (and let me know how to get them...lol)

Cheers,
Josh

Hi Josh, is this with the standard Ubuntu kernel, rather than the kerrighed kernel? If so, then I can only suggest that the problem may lie in the /etc/exports file or in the /srv/tftp/pxelinux.cfg/default file. Can you put the contents of both files on here to see if I can spot something out of the ordinary. However, if this is using the kerrighed kernel, have you made sure to include the drivers for your network card and nfs when configuring the kernel? Hope this may lead in the right direction.

---

### Post by jbbjshlws on 2009-04-21
Hello bigjimjams!
I have followed the how to guide exactly step by step, i am very new to linux so i am nost 100% sure what kernal has been used, but it should be exactly what was in your how to.

Now the default contents of etc/exports is:

> # /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
# /etc/exports #
/nfsroot/kerrighed 192.168.1.0/255.255.255.0(rw,no_subtree_check,async,no_root_squash)

and the contents of /srv/tftp/pxelinux is:

> LABEL linux
KERNEL vmlinuz-2.6.27-7-generic
APPEND root=/dev/nfs initrd=initrd.img-2.6.27-7-generic nfsroot=192.168.1.1:/nfsroot/kerrighed ip=dhcp rw 


I am able to boot through to where it says:
> ALERT! /dev/nfs does not exist. Dropping to a shell!

Now i have looked and i do not have /dev/nfs in either the root of my file system or at /nfsroot/kerrighed/dev/nfs for the bootable file system, is this normal?

if it helps i am using 2.6.27-7-generic as my ubuntu instalation, i havn't upgraded to 2.6.27-11-generic, as i figured this could throw more spanners in the works.

I can give you my msn details if it would help speed things up with communication, i will then transcribe the solutions to this forum

---

### Post by bigjimjams on 2009-04-22
> **jbbjshlws said:**
> Hello bigjimjams!
I have followed the how to guide exactly step by step, i am very new to linux so i am nost 100% sure what kernal has been used, but it should be exactly what was in your how to.

Now the default contents of etc/exports is:



and the contents of /srv/tftp/pxelinux is:




I am able to boot through to where it says:


Now i have looked and i do not have /dev/nfs in either the root of my file system or at /nfsroot/kerrighed/dev/nfs for the bootable file system, is this normal?

if it helps i am using 2.6.27-7-generic as my ubuntu instalation, i havn't upgraded to 2.6.27-11-generic, as i figured this could throw more spanners in the works.

I can give you my msn details if it would help speed things up with communication, i will then transcribe the solutions to this forum

Hi Josh, I think I may have just spotted a mistake in the guide. In /etc/exports the ip address should read 192.168.1.1/255.255.255.0 and not 192.168.1.0/255.255.255.0 as it states. This is then the same as the ip address in /srv/tftp/pxelinux.cfg/default which states where to get the nfsroot from. Hope this helps.

---

### Post by jbbjshlws on 2009-04-22
Hello, 
I have changed the ip address to match the ip of the server in both of those files, but i am still getting the same error:

> ALERT! /dev/nfs does not exist. Dropping to a shell! 

I will double check all of the other files used are referring to the same ip address. could anything else be causing this problem?

do i need to repeat any of the steps now that i have changed the values in those files (besides restarting the daemon's)?

---

### Post by mmcastig on 2009-04-22
Bigjimjams,
I am experiencing the exact same problem as jbbjshlws. My /etc/exports and /srv/tftp/pxelinux.cfg/default read respectively as follows: 

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
# /etc/exports #
/nfsroot/kerrighed 192.168.1.1/255.255.255.0(rw,no_subtree_check,async,no_root_squash)
--------------------------------------------------------------------------
LABEL linux
KERNEL vmlinuz-2.6.27-13-generic
APPEND root=/dev/nfs initrd=initrd.img-2.6.27-13-generic nfsroot=192.168.1.1:/nfsroot/kerrighed ip=dhcp rw
--------------------------------------------------------------------------
The node just says that it can't find /dev/nfs and drops to a shell. 
Hopefully this helps.

-mmcastig

P.S I do have the 2.6.27-14 kernel image, but it panics on boot for some reason, so I've reverted the whole thing back to the 13 image. Not sure if that means my computer is wack or something like that.

---

### Post by jbbjshlws on 2009-04-23
That makes me feel a little less silly, if two of us had the same issue!

I have tried a couple of things, but nothing seems to get away from this error!, 

please make sure if you work it out to post the results for me, and vice versa.

Cheers,
Josh

---

### Post by mmcastig on 2009-04-23
It occurs to me that I might be barking up the wrong tree in pursuing Kerrighed. I'm trying to setup a load balancing cluster. Mostly for mass music manipulation (i.e ID3 tag editing, mass filename changes, and CDDB matching) with the program Easytag. I'd also like to just bolster the performance of my tower (I have 4 other computers sitting around). Should I be trying to setup a Kerrighed cluster for all this, or should I be headed in more of a Mosix direction? Or something I haven't tried yet?

---

### Post by jbbjshlws on 2009-04-23
From what i understand Kerrighed can do everything that Openmosix can do and is still supported, both are SSI systems. I am not the guru of clustering though

---

### Post by cfrieler on 2009-04-23
If anyone can venture a guess or provide references.....

I played with the first versions of OpenMosix not too long after I began seriously pursueing clustering. I've been happily using Caos Linux with Warewulf and now Caos-NSA, but I've always wanted the transparency of SSI. One issue that I can't find info on is the following - I routinely compile my MCMC simulations to use OpenMP on each 4-CPU node and then distribute tasks among the nodes using MPI. If thread migration is allowed to occur on an SSI cluster, will it be smart enough to move all the threads that need the same local memory? 

Also...
I'm about to try the procedure in the HowTo on a collection of older SMP boxes I have, but they are all based on the Intel 450nx chipset. Past versions of Ubuntu have had issues with this chipset, and the problem has been resolved and reintroduced a few times. Any idea whether the latest kernel works on these older quad slot systems?

Thanks, and when I get something up and running, I'd be happy to perform testing for others.
Cliff

---

### Post by jbbjshlws on 2009-04-24
Hello,
I am still getting the same error:

Gave up waiting for root device. Common problems:

-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/nfs does not exist. Dropping to a shell!

i have looked up the /dev/nfs issue through google and tried some of the tips and tricks to get it working, but none have worked so far, still would love a helping hand, happy to send a paypal $$ donation towards the project or someone (your choice) who can get the issue fixed before Sunday, (issue fixed means i can get past this issue and if you stick around long enough to help me out to get into running the Kerrighed kernel it would be appreciated also). If you are interested please let me know asap so i can pass on my details.

Kind Regards,
Joshua

---

### Post by jedi453 on 2009-04-24
> **jbbjshlws said:**
> Hello,
I am still getting the same error:

Gave up waiting for root device. Common problems:

-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/nfs does not exist. Dropping to a shell!

i have looked up the /dev/nfs issue through google and tried some of the tips and tricks to get it working, but none have worked so far, still would love a helping hand, happy to send a paypal $$ donation towards the project or someone (your choice) who can get the issue fixed before Sunday, (issue fixed means i can get past this issue and if you stick around long enough to help me out to get into running the Kerrighed kernel it would be appreciated also). If you are interested please let me know asap so i can pass on my details.

Kind Regards,
Joshua

It looks like you're using the initrd ( or initramfs) that came with your install, this might not work as it's not built for running over nfs. See my post ( # 86 in this thread ) about this problem and a way that fixed it for me. Don't worry about doing this for the kerrighed kernel, as you wont need an initrd.

Good Luck!

---

### Post by jbbjshlws on 2009-04-25
Ok i have tried what you suggested jedi453, and i am now getting a different error:

read: Connection refused

and when it finally realises that the connection has actually been refused (about 1 hour of tring)

it comes up with 

mount call failed:13
Done.
Begin: Running /scripts/nfs-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


so i am not sure if this is what you were expecting, but this is the result i got, i am not sure where to go from here. the offer still stands if someone can help me out really quick!.

Cheers,
Josh

---

### Post by jedi453 on 2009-04-25
> **jbbjshlws said:**
> Ok i have tried what you suggested jedi453, and i am now getting a different error:

read: Connection refused

and when it finally realises that the connection has actually been refused (about 1 hour of tring)

it comes up with 

mount call failed:13
Done.
Begin: Running /scripts/nfs-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


so i am not sure if this is what you were expecting, but this is the result i got, i am not sure where to go from here. the offer still stands if someone can help me out really quick!.

Cheers,
Josh

OK, I've searched the Internet without perfect matches, I've found "tftpd: read: connection refused" ( [http://forum.soft32.com/linux2/tftpd-read-Connection-refused-ftopict11717.html](http://forum.soft32.com/linux2/tftpd-read-Connection-refused-ftopict11717.html) ) which suggests shutting off your firewall. I can only guess at this point, so it might help if you posted all the files the kerrighed guide tells you to edit and create, or double check them yourself. Also look here: [http://www.howtoforge.com/pxe_booting_debian](http://www.howtoforge.com/pxe_booting_debian) to learn a little more about pxe booting, many of the problems I faced setting up kerrighed were from lack of understanding on my part. It could be the version of tftpd you're using or the edition of ubuntu, or a mistake in following the guide. You should try reinstalling all the required software then rebooting the servers. I also had an odd problem (granted not the same one) setting mine up because I hadn't rebooted in a long while, so rebooting might help also. 

Good Luck!

---

### Post by jbbjshlws on 2009-04-25
ok, everychange i have made i have restarted the servers afterwords, just incase it needed to refresh something in the daemon, i guess this stems back to the old windows restart when there is a problem, but this has not changed any of the output, the version ofubuntu i am using is 2.6.27-7 kept it the same as the guide to cause less confusion i will try redoing the entire how to on another box to see if that changes anything,

Cheers,
Josh

---

### Post by ajt on 2009-04-26
> **mmcastig said:**
> It occurs to me that I might be barking up the wrong tree in pursuing Kerrighed. I'm trying to setup a load balancing cluster. Mostly for mass music manipulation (i.e ID3 tag editing, mass filename changes, and CDDB matching) with the program Easytag. I'd also like to just bolster the performance of my tower (I have 4 other computers sitting around). Should I be trying to setup a Kerrighed cluster for all this, or should I be headed in more of a Mosix direction? Or something I haven't tried yet?

Hello, mmcastig.

I run a 90-node openMosix cluster and it works very well, but I'm going to start using Kerrighed instead soon because the openMosix project was officially closed over a year ago and openMosix is now unsupportable. It uses the 2.4 kernel, which does not support SATA hard drives. I would try to get Kerrighed running on your kit - It does work ;-)

Bye,

  Tony.

---

### Post by ajt on 2009-04-26
> **cfrieler said:**
> If anyone can venture a guess or provide references.....

[...]If thread migration is allowed to occur on an SSI cluster, will it be smart enough to move all the threads that need the same local memory? 


Hello, Cliff.

Neither openMosix or Kerrighed support 'thread' (i.e. lightweight processes) migration. In fact, POSIX threads are usually implemented as separate processes under Linux and communicate using shared memory. That means they will not migrate under openMosix or the 'stable' version of Kerrighed.

What you want is NUMA (Non-Uniform Memory Architecture) where the kernel attempts to observe data locality using memory management hardware to keep data in the memory of the CPU where it is actually being processed.

SSI (Single System Image) is more like SMP (Symmetric Multi Processing) where data locality is not considered by the load balancing algorithm, which just distributes the CPU load independently of memory bandwidth. The openMosix load balancing algorithm does try to avoid memory depletion on a processing element by migrating processes away, but it only supports uniprocessor architecture and will only use one CPU even if two or more are present. I'm not sure how stable Kerrighed support for SMP is yet.

Bye,

  Tony.

---

### Post by ajt on 2009-04-26
> **jedi453 said:**
> OK, I've searched the Internet without perfect matches, I've found "tftpd: read: connection refused" ( [http://forum.soft32.com/linux2/tftpd-read-Connection-refused-ftopict11717.html](http://forum.soft32.com/linux2/tftpd-read-Connection-refused-ftopict11717.html) ) which suggests shutting off your firewall. I can only guess at this point, so it might help if you posted all the files the kerrighed guide tells you to edit and create, or double check them yourself. Also look here: [http://www.howtoforge.com/pxe_booting_debian](http://www.howtoforge.com/pxe_booting_debian) to learn a little more about pxe booting, many of the problems I faced setting up kerrighed were from lack of understanding on my part. It could be the version of tftpd you're using or the edition of ubuntu, or a mistake in following the guide. You should try reinstalling all the required software then rebooting the servers. I also had an odd problem (granted not the same one) setting mine up because I hadn't rebooted in a long while, so rebooting might help also. 

Good Luck!

Hello, jedi453 and Josh.

There are two different issues here:

#1 Does tftpd work
#2 Does NFS work

You can test both of these independently from any Linux client. Just use the tftpd client on a stand-alone Ubuntu manchine to see if you can download the pxelinux secondary bootstrap. Then, try to mount the NFSROOT on e.g. /mnt. [tip] Use "showmount -e server_name" on the client to see what filesystems server_name' is exporting. You should also restart the NFS server after making changes to /etc/exports.

Bye,

  Tony.

---

### Post by ajt on 2009-04-26
> **mmcastig said:**
> Bigjimjams,
I am experiencing the exact same problem as jbbjshlws. My /etc/exports and /srv/tftp/pxelinux.cfg/default read respectively as follows: 

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
# /etc/exports #
/nfsroot/kerrighed 192.168.1.1/255.255.255.0(rw,no_subtree_check,async,no_root_squash)


Hello, mmcastig.

Did you intend to export your NFSROOT to exacly one host?

Your exports config only exports the filesystem to the single host 192.168.1.1, To export it to the network 192.168.1.0 you should use:

/nfsroot/kerrighed 192.168.1.0/255.255.255.0(rw,no_subtree_check,async,no_root_squash)

Bye,

  Tony.

---

### Post by ajt on 2009-04-26
> **Rickles65 said:**
> Maybe I'm just thick headed today... So is there nothing out there any more that does process (thread) migration?

We have a need (and it's just 3 machines) for high CPU threads to be moved off to the more idle machines.

We'd done this before (about 5 years ago) with OpenMosix. We just added the appropriate kernel mods, NFS mounts and off we went.

The machines are fully loaded in this config as well so there's no need for SSI in the current config either. Just the net mounts and kernel changes.

Hello, Rickles65.

Did you really migrate threads, using the MIGSHM patch?

I never got this to work properly - It was only ever 'alpha' release software. We stopped using it because it makes openMosix unstable.

Bye,

  Tony.

---

### Post by ajt on 2009-04-26
> **jbbjshlws said:**
> Hello bigjimjams!
I have followed the how to guide exactly step by step, i am very new to linux so i am nost 100% sure what kernal has been used, but it should be exactly what was in your how to.


Hello, Josh.

I don't think you did follow bigjimjams guide exactly ;-)

```

LABEL linux
KERNEL vmlinuz-2.6.27-7-generic
APPEND root=/dev/nfs initrd=initrd.img-2.6.27-7-generic nfsroot=192.168.1.1:/nfsroot/kerrighed ip=dhcp rw 

```

You're trying to boot the 'generic' Ubuntu kernel, not the patched kerrighed kernel! The generic kernel does not support NFSROOT...

Bye,

  Tony.

---

### Post by ajt on 2009-04-26
> **agungaryo said:**
> thank you,ajt.
but I've tried to use multiple server with round robin balancing,but the result is not satisfied . some issues appear like crash on database,DNS cache (while server get hundreds request from client),n I've checked the common error isn't at bandwidth but in CPU USAGE which causes "time out" error at client.
does kerrighed really not help my problem ?


Hello, Agung.

The Apache web server spawns multiple threads which can be executed on different SMP processors local to the machine that Apache is running on. The Apache server keeps track of these threads using shared memory, so the SSI you use must support thread (as opposed to process) migration: At present, Kerrighed does not support thread migration.

> 
by the way ,do I have to install my simulation at cluster node (kerrighed kernel) to use clustering ?


Yes, and you need to give the parent apache2 process inheritable migration capability using:

```

krgcapset -d <apache2.pid> +CAN_MIGRATE

```

Where <apache2.pid is the process ID of the apache2 server.

Bye,

  Tony.

---

### Post by cfrieler on 2009-04-27
> **ajt said:**
> ...  In fact, POSIX threads are usually implemented as separate processes under Linux and communicate using shared memory. That means they will not migrate under openMosix or the 'stable' version of Kerrighed.


Tony,
Thanks for the very informative reply. A lot of complexity here that is going to require some study. But since you apparently command a broad range within this topic area, let me ask a couple additional questions.  

Does OpenMP produced threads, POSIX compliant threads, or it's own seperate processes? Is it compiler dependent?

To keep my programming model simple, I've built a relatively homogeneous cluster. All nodes are quad CPU with 4GB RAM, and they are run diskless, using CAOS-NSA. Currently, I write a task processing code that is compiled for 4 CPUs, highly optimized and benchmarked to run several orders of magnitude longer than the comm time necessary to transfer it, the supporting data and the results. These tasks are kicked off by a seperate MPI code that has a single instance on each node. 

My thought was that with SSI I could do away with the MPI code. I had hoped that if I kicked off all the tasks on the master node, they would migrate as necessary to available nodes for processing. This would relieve me of coordinating, and make it easier to mix very different speeds of nodes.

Given that context, any additional comments about Ubuntu/Kerrighed? Any suggestions on other approaches/technologies I should look at?

Again, thanks for your insight.
Regards, Cliff

---

### Post by jbbjshlws on 2009-04-28
> **ajt said:**
> Hello, Josh.

I don't think you did follow bigjimjams guide exactly ;-)

```

LABEL linux
KERNEL vmlinuz-2.6.27-7-generic
APPEND root=/dev/nfs initrd=initrd.img-2.6.27-7-generic nfsroot=192.168.1.1:/nfsroot/kerrighed ip=dhcp rw 

```

You're trying to boot the 'generic' Ubuntu kernel, not the patched kerrighed kernel! The generic kernel does not support NFSROOT...

Bye,

  Tony.

This was taken from the how to guide:
> This guide is split into two parts: the first covers how to setup the server for diskless booting the nodes using the current kernel, the second part of the guide covers setting up Kerrighed 2.3.0 and incorporating it into the diskless boot configuration of part one.

It states that you are using the current kernel, then later to set up the Kerrighed kernel and incorporating it. so at the moment, I am using the current kernel, this is until I have been able to successfully boot and then start part two of the guide. so for the moment I think that it is set up as per the guide for where I am upto, sorry for the confusion.

I am still having this issue, I installed Ubuntu onto another box, and I can connect to the nfs share on the server without a problem. so it is being shared, but the problem persists. i have tried the guide on post 86, but it comes up with other errors so i reinstalled the machine from scratch to make sure I didn't stuff any settings up, but have the same problem. I have replicated the same setup on some virtual pc's, with the same problem. so I am consistently doing the same thing wrong, or the guide is not catering for my version of Ubuntu (2.6.27-7-generic). 

I have followed [http://www.cpsspecialties.webhop.org/kerrighedCluster.htm](http://www.cpsspecialties.webhop.org/kerrighedCluster.htm) guide as well with the same issues. he is running the same version of Ubuntu as I and had the same issue earlier on and got it solved two weeks ago, but has not posted the solution yet. This could be the key, thanks for the help so far, I'm sure we can work this out! as I have said before I can give SSH details to people if they need to have a look around to see a silly setting I have done wrong, this might make solving this over the Internet a little bit easier!,


Cheers,
Josh

---

### Post by jedi453 on 2009-04-28
> **jbbjshlws said:**
> This was taken from the how to guide:

It states that you are using the current kernel, then later to set up the Kerrighed kernel and incorporating it. so at the moment, I am using the current kernel, this is until I have been able to successfully boot and then start part two of the guide. so for the moment I think that it is set up as per the guide for where I am upto, sorry for the confusion.

I am still having this issue, I installed Ubuntu onto another box, and I can connect to the nfs share on the server without a problem. so it is being shared, but the problem persists. i have tried the guide on post 86, but it comes up with other errors so i reinstalled the machine from scratch to make sure I didn't stuff any settings up, but have the same problem. I have replicated the same setup on some virtual pc's, with the same problem. so I am consistently doing the same thing wrong, or the guide is not catering for my version of Ubuntu (2.6.27-7-generic). 

I have followed [http://www.cpsspecialties.webhop.org/kerrighedCluster.htm](http://www.cpsspecialties.webhop.org/kerrighedCluster.htm) guide as well with the same issues. he is running the same version of Ubuntu as I and had the same issue earlier on and got it solved two weeks ago, but has not posted the solution yet. This could be the key, thanks for the help so far, I'm sure we can work this out! as I have said before I can give SSH details to people if they need to have a look around to see a silly setting I have done wrong, this might make solving this over the Internet a little bit easier!,


Cheers,
Josh


Edit: did you set up the server with a static ip address? 

> Our server has two network cards, one is setup for internet access, the other is connected to a switch, which connects the four nodes. The server network card connected to the switch is manually configured with the IP address 192.168.1.1 and subnet mask 255.255.255.0.

See here for details: [http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html)

/Edit

So you've done the guide twice without success. It is made for hardy heron (8.04), looks like you're running intrepid ibex (8.10). I can't guarantee it's the problem, but if you've tried twice without success installing hardy heron and restarting the guide might be a reasonable alternative. As kerrighed depends on 2.6.20, you aren't getting a better kernel by using intrepid, so the only thing you would be giving up is the newer packages and maybe some time.

The other thing to consider is skipping that test and continue with the guide (beginning at the beginning of part two) as if it worked. After all it is just a test. At any rate I would post all the files the guide tells you to edit/create as a zip file attachment or in a post.

---

### Post by djdirty on 2009-04-30
There has got to be a global issue here... Or at least something that is so insignificantly stupid that its funny!

I have tried on a multitude of different versions of Ubuntu to get this working! From 6.10 right up to 9.10! This is just getting annoying now!

I am working with Josh on this one.. And I haven't got any further than he has.. I am stuck at the dropping to busy box..

I have done as the Error Message says and checked /proc/cmdline and the UUID is in fact exactly the same UUID as /dev/sda1/ (which is my root partition) is this the correct UUID? Or is it meant to be something different.. My understanding to that is that when the client is trying to boot it it waiting for the Root Device of that UUID and the fact that it has already booted (on the server) is an issue..

Can anyone help in this issue? Would be much appreciated! We have big plans for this!

Cheers,

Dave

---

### Post by jbbjshlws on 2009-04-30
Hello All, 
I have tried to complete the setup as jedi suggested, but it still did not work, i have got numerious errors probably stemming back to:

apt-get install automake autoconf libtool pkg-config awk rsync bzip2 gcc-3.3 libncurses5 libncurses5-dev wget lsb-release xmlto patchutils xutils-dev build-essential

this threw a lot of errors. the version of awk i was not sure of and many other settings (linux menus etc)

I will be investigating these further before i post about them on the forum.

what my question is, when this is fully setup, how come someone cant just upload a vm image of a working system? it would only be a few small settings that would need to be changed to have it work for your own network, and seems it would be a lot more reliable and repeatable. could anyone who has managed to be graced with a working system do this? i can give ftp details, and i am more than happy to host files on my server to better the community (any files). please let me know, and i can give ftp details.

Cheers,
Josh

---

### Post by jedi453 on 2009-04-30
> **jbbjshlws said:**
> Hello All, 
I have tried to complete the setup as jedi suggested, but it still did not work, i have got numerious errors probably stemming back to:

apt-get install automake autoconf libtool pkg-config awk rsync bzip2 gcc-3.3 libncurses5 libncurses5-dev wget lsb-release xmlto patchutils xutils-dev build-essential

this threw a lot of errors. the version of awk i was not sure of and many other settings (linux menus etc)

I will be investigating these further before i post about them on the forum.

what my question is, when this is fully setup, how come someone cant just upload a vm image of a working system? it would only be a few small settings that would need to be changed to have it work for your own network, and seems it would be a lot more reliable and repeatable. could anyone who has managed to be graced with a working system do this? i can give ftp details, and i am more than happy to host files on my server to better the community (any files). please let me know, and i can give ftp details.

Cheers,
Josh

Sorry I've had such a bad record fixing these problems :( .

Are you still using intrepid ibex (8.10)? It doesn't have gcc-3.3 (see here [http://packages.ubuntu.com/intrepid/allpackages](http://packages.ubuntu.com/intrepid/allpackages) (takes a long time to load, even with broadband) ) which would cause a lot of errors... none of the packages would install, and nothing would work after that...

---

### Post by djdirty on 2009-04-30
I have tried running through the installation with Hardy (8.04) and i get the error:0

Begin: Running /scripts/nfs-premount
Connect: Connection timed out

Then it just sits there... Whats the go there?


~Davo

---

### Post by nerdopolis on 2009-04-30
Hi. I got my server to boot (not yet with Kerrighed). The problem was in the initrd.

On the root server (not /nfsroot/kerrighed) try:


Backup your current initrd:
```
sudo cp /boot/initrd.img-$(uname -r) /boot/initrd.img-$(uname -r).bak 
```Backup your initrd config file
```
sudo cp /etc/initramfs-tools/initramfs.conf ~/initrdconfig
```This command will replace your initramfs config with the one required to get nfs booting:
```
sudo echo -e "MODULES=netboot" "\nBUSYBOX=y" "\nCOMPCACHE_SIZE=\"\"" "\nBOOT=nfs" "\nDEVICE=eth0" "\nNFSROOT=auto" > /etc/initramfs-tools/initramfs.conf
```Create the new initrd:
```
sudo  update-initramfs -u
```Restore the initramfs config:
```
sudo mv ~/initrdconfig /etc/initramfs-tools/initramfs.conf
```copy the new initrd to the /srv/tftp folder:
```
sudo cp  /boot/initrd.img-$(uname -r) /srv/tftp/ 
sudo cp /boot/vmlinuz-$(uname -r) /srv/tftp/
```remove the nfs initrd:
```
sudo rm /boot/initrd.img-$(uname -r)
```put the old initrd in place:
```
sudo mv /boot/initrd.img-$(uname -r).bak /boot/initrd.img-$(uname -r)
```update the configuration. this whole block is a single command!
```
printf "LABEL linux  
KERNEL vmlinuz-$(uname -r)  
APPEND root=/dev/nfs initrd=initrd.img-$(uname -r) nfsroot=192.168.1.0:/nfsroot/kerrighed ip=dhcp rw" > /srv/tftp/pxelinux.cfg/default
```After that, it booted and froze to "Starting NFS Common Utilities" I was able to remove it from the startup script with out any problems. it still boots and I am able to browse and write to the file system, but just in case, move it to your home folder:
```
sudo mv /nfsroot/kerrighed/etc/init.d/nfs-common ~/nfs-common
```

---

### Post by nerdopolis on 2009-04-30
djdirty: sounds like your nfs server isn't working... (thats just my guess)

Assuming you are using the guides ([https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)) folders and ip addresses:

does your /etc/exports look like this?
```
/nfsroot/kerrighed 192.168.1.0/255.255.255.0(rw,no_subtree_check,async,no_root_squash)
```

did you run:
```
sudo exportfs -avr
```

[FONT=monospace]did you run:
[/FONT]```
sudo /etc/init.d/nfs-kernel-server restart
```

Thats just my guess...

---

### Post by djdirty on 2009-04-30
Thanks Nerdopolis..
 
I did edit those configs to look exactly like that..
 
I will have a go at your other suggestion and see where that gets me.
 
 
~Davo

---

### Post by jbbjshlws on 2009-05-01
Hello, Good news!
It seems the 3rd time is the charm as i am able to go get to the login screen now, the error i am having is when i go to "make kernel" it tells me:

From and to directories are identical!
[all-y] Error 1
Leaving directory /usr/src/kerrighed-2.3.0/modules
[all-recursive] Error 1


i hope this is something simple,....please!!

Cheers,
Josh

---

### Post by bigjimjams on 2009-05-01
> **jbbjshlws said:**
> Hello, Good news!
It seems the 3rd time is the charm as i am able to go get to the login screen now, the error i am having is when i go to "make kernel" it tells me:

From and to directories are identical!
[all-y] Error 1
Leaving directory /usr/src/kerrighed-2.3.0/modules
[all-recursive] Error 1


i hope this is something simple,....please!!

Cheers,
Josh

Hi Josh, are you using a 32-bit or 64-bit kernel? If its the 32-bit version, I found that if you use the make kernel -i command it will ignore this error and still make everything required. Just to note, that if you use the SVN trunk version of kerrighed, instead of 2.3.0 this error seems to have been fixed. However, if you are using a 64-bit kernel, I never managed to get 2.3.0 working with that, but did get the SVN trunk version working.

Also, when the guide states to install awk, it should actaully be gawk. It might also be worth installing grub so when you run the command make kernel-install later on it won't complain. Hope this helps.

---

### Post by djdirty on 2009-05-01
This is so weird! We both got it working on seperate boxes! What the heck..

I'm at the same error.. Will try the -i switch when I get a chance. :-) Thanks Bigjimjams!

---

### Post by jbbjshlws on 2009-05-01
Hello bigjimjams!!!

This worked wonderfully!!, this is to say it is able to get past this issue, and i have got to 2.3, Starting Kerrighed. when i go to boot the machines now 
i get to:

Trying to load:pxelinux.cfg/default
Could not find kernel image: linux
boot:

could this be related to using the -i parameter or something else?


Cheers,
Joshua

---

### Post by nerdopolis on 2009-05-01
Try updating your
```
/srv/tftp/pxelinux.cfg/default
```

file.

make sure the Kerrighed kernel is in [FONT=monospace]
```
[/FONT]/srv/tftp/
```

---

### Post by nerdopolis on 2009-05-01
If anyone ran my commands, in my previous post I realized an error in one of them. ```
 sudo update-initramfs -u 
``` if you ran them.

---

### Post by jbbjshlws on 2009-05-01
Hello,
I have checked /srv/tftp/pxelinux.cfg/default and i have:

```
LABEL kerrighedlinux
KERNEL vmlinuz-2.6.20-krg
APPEND console=tty1 root=/dev/nfs nfsroot=10.54.12.5:/nfsroot/kerrighed ip=dhcp rw
```




i have restarted the daemons, and the server that they are on

also in /srv/tftp/ i have:
initrd.img-2.6.24-23-generic  
pxelinux.cfg	  
vmlinuz-2.6.24-23-generic
pxelinux.0		      
vmlinuz-2.6.20-krg

so i see no reason it is not working, please help!

---

### Post by macotto on 2009-05-02
clustering as well, but because of no ubuntu availability I have been trying live CD's, and one of the computers I want to use it on doesn't have support for my LAN card. :sad: and it doesn't know how to do WiFi either, it thinks it is just an ethernet connection

---

### Post by bigjimjams on 2009-05-02
> **jbbjshlws said:**
> Hello,
I have checked /srv/tftp/pxelinux.cfg/default and i have:

```
LABEL kerrighedlinux
KERNEL vmlinuz-2.6.20-krg
APPEND console=tty1 root=/dev/nfs nfsroot=10.54.12.5:/nfsroot/kerrighed ip=dhcp rw
```



If you try changing the LABEL to linux instead of kerrighedlinux (I think the guide may have said this - Whoops!) it may work. I think I found this problem recently when I performed another kerrighed install but haven't got around to changing the guide.

---

### Post by jbbjshlws on 2009-05-03
Hello Bigjimjams!!

that LABEL defiantly needed to be linux, that fixed that error. and i was able to successfully boot to the next error...(sigh...)

the error is:

```
Looking up ort of RPC 100005/1 on 10.54.12.5
Portmap: server 10.54.12.5 not responding, timedout
Root-NFS: unable to get mountd port number from server, using default mount: Server 10.54.12.5 not responding, timed out
Root-NFS: Server returned error-5 while mounting /nfsroot/kerrighed
VFS: unable to mount root fs via NFS, tyring floppy.
VFS: Insert root floppy and press ENTER
```

Now if i press enter i get the following error:

```
1VFS: Cannot open root device "nfs" or unknown-block (2,0)
Please append a correct "root=" boot option
Kernal panic- not syncing VFS: Unable to mount root fs on unknown-block (2,0)
```

When i run the command rpcinfo -p on the server and i look at the results for 100005 i get:

100005  1  udp  35644  mountd
100005  1  tcp  46678  mountd

not sure if this is the port that program should be running on or if those settings are correct. this error consistently comes up on 3 different machines (out of 3) all with different motherboards and hardware, so i don't think that this error is hardware dependent. soo close!!!

Cheers,
Josh

---

### Post by biggels on 2009-05-03
I have enjoyed reading your article and it has given me some insight into creating the clustered SSI system with Kerrighed. I have a question, I would be setting this up at home, and I would like to use the systems around the home in the bedrooms, my plan was to send out a Wake On Lan packet to have them boot to PXE before the HD and then start processing any work necessary. Can you have Kerrighed working with the Ubuntu GUI as well?
   
  this way if my family wants to use the machines and they do any heavy duty processing, they are still usable and all of them have the advantage of the cluster.
   
  If this is not possible, is there anyway I could have Kerrighed installed on one machine that has a GUI as the "master" machine so any overheads of CPU cycles are then dealt off to other machines, and it is not all terminal based?


much appreciated,


Cat

---

### Post by jbbjshlws on 2009-05-03
this is a good question, is there any display with Kerrighed at all? 
I have played around with Xgrid a little bit, and that is quite graphical, but im not sure about Kerrighed, i will let you know when i get it solved if you dont find out sooner!,

Cheers,
Josh

---

### Post by bigjimjams on 2009-05-03
> **jbbjshlws said:**
> this is a good question, is there any display with Kerrighed at all? 
I have played around with Xgrid a little bit, and that is quite graphical, but im not sure about Kerrighed, i will let you know when i get it solved if you dont find out sooner!,

Cheers,
Josh

I can't see why you can't install the ubuntu-desktop package on the kerrighed nodes to have a GUI on each machine that you can log into. This can be done over an NFS boot. Also, using the setup described in the ubuntu kerrighed guide, you can login to any of the kerrighed nodes via a terminal and launch processes which can then be distributed, so why not using a GUI frontend? It's possible I'm overlooking something here...

---

### Post by jbbjshlws on 2009-05-03
Any ideas from an expert about this?

> **jbbjshlws said:**
> Hello Bigjimjams!!

that LABEL defiantly needed to be linux, that fixed that error. and i was able to successfully boot to the next error...(sigh...)

the error is:

```
Looking up ort of RPC 100005/1 on 10.54.12.5
Portmap: server 10.54.12.5 not responding, timedout
Root-NFS: unable to get mountd port number from server, using default mount: Server 10.54.12.5 not responding, timed out
Root-NFS: Server returned error-5 while mounting /nfsroot/kerrighed
VFS: unable to mount root fs via NFS, tyring floppy.
VFS: Insert root floppy and press ENTER
```

Now if i press enter i get the following error:

```
1VFS: Cannot open root device "nfs" or unknown-block (2,0)
Please append a correct "root=" boot option
Kernal panic- not syncing VFS: Unable to mount root fs on unknown-block (2,0)
```

When i run the command rpcinfo -p on the server and i look at the results for 100005 i get:

100005  1  udp  35644  mountd
100005  1  tcp  46678  mountd

not sure if this is the port that program should be running on or if those settings are correct. this error consistently comes up on 3 different machines (out of 3) all with different motherboards and hardware, so i don't think that this error is hardware dependent. soo close!!!

Cheers,
Josh


I will try installing it on a GUI system as soon as i can get this whole setup working (one step at a time!) don't want to introduce more variables into it atm.

Cheers,
Josh

---

### Post by bigjimjams on 2009-05-04
> **jbbjshlws said:**
> Any ideas from an expert about this?




I will try installing it on a GUI system as soon as i can get this whole setup working (one step at a time!) don't want to introduce more variables into it atm.

Cheers,
Josh

Hi Josh, can  you give the full listing of rpcinfo -p so we can see if you have a mountd, a portmapper and an nfs running. Can you also check if you have a portmapper installed on the nfsroot filesystem. Also can you post the contents of /etc/hosts, /etc/hosts.allow and /etc/hosts.deny for the server and nodes.

---

### Post by jbbjshlws on 2009-05-04
Hey!
This is the settings for the / server system
rcpinfo -p

```
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  41200  status
    100024    1   tcp  47208  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  38440  nlockmgr
    100021    3   udp  38440  nlockmgr
    100021    4   udp  38440  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  34066  nlockmgr
    100021    3   tcp  34066  nlockmgr
    100021    4   tcp  34066  nlockmgr
    100005    1   udp  60030  mountd
    100005    1   tcp  35569  mountd
    100005    2   udp  60030  mountd
    100005    2   tcp  35569  mountd
    100005    3   udp  60030  mountd
    100005    3   tcp  35569  mountd

```



etc/hosts
```
127.0.0.1	localhost
127.0.1.1	clustered

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```



etc/hosts.allow
```
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
```


etc/hosts.deny

```
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
```


These are the settings for the /nfsroot/kerrighed client system

etc/hosts
```
# /etc/hosts #
127.0.0.1 localhost

10.65.12.5  clustered
10.65.12.6  kerrighednode1
10.65.12.7  kerrighednode2
10.65.12.8  kerrighednode3
10.65.12.9  kerrighednode4
10.65.12.10  kerrighednode5




```


etc/hosts.allow
```
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
```

/etc/hosts.deny

```
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
```

How can i check for a port mapper on the nfsroot system?

This is the code from all of the places asked, please let me know if you need anything else

Cheers, Joshua

---

### Post by djdirty on 2009-05-04
From what i can work out it is an issue with the Kernel... Because the generic kernel can boot and is a completely working version of Ubuntu..

Can anyone upload there Kerrighed Kernel? Wouldn't that be the easiest thing to do?

~Davo

---

### Post by bigjimjams on 2009-05-04
> **jbbjshlws said:**
> 
How can i check for a port mapper on the nfsroot system?

This is the code from all of the places asked, please let me know if you need anything else

Cheers, Joshua

You could try to put all the node ip adresses in the server /etc/hosts file too. Also, did you remember to include the network card drivers and nfs in the kerrighed kernel and not as modules? Does the /sbin directory contain portmap on the nodes?

Also, just noticed that your /etc/hosts on the server doesn't contain the ip address for itself only the localhost, if you add it, it may solve the problem, as I believe portmap uses the /etc/host* files.

---

### Post by jbbjshlws on 2009-05-04
Hello bigjimjams,
I have tested with the changed etc/hosts file, and it does not change the problem. the /sbin directory does contain portmap on the nodes.

> Also, just noticed that your /etc/hosts on the server doesn't contain the ip address for itself only the localhost, if you add it, it may solve the problem, as I believe portmap uses the /etc/host* files.

the server name is clustered, ip address 10.65.12.5, it is in the list

> did you remember to include the network card drivers and nfs in the kerrighed kernel and not as modules?

I did include them for most of the systems around the home, i did not include them for the laptop here, and the laptop has a different error (don't care about atm). this tells me that the network card drivers are functioning correctly in the desktop computers.

Hope this helps, 

Cheers,
Josh

---

### Post by bigjimjams on 2009-05-04
> **jbbjshlws said:**
> Hello bigjimjams,
I have tested with the changed etc/hosts file, and it does not change the problem. the /sbin directory does contain portmap on the nodes.



the server name is clustered, ip address 10.65.12.5, it is in the list



I did include them for most of the systems around the home, i did not include them for the laptop here, and the laptop has a different error (don't care about atm). this tells me that the network card drivers are functioning correctly in the desktop computers.

Hope this helps, 

Cheers,
Josh

Hi Josh, from the /etc/hosts files you posted for the server and client, it appeared as though it was in the client list but not the server list. It should be present in both with the correct IP addresses, as the server may have more than one. Have you changed this and tried it since the post?

---

### Post by jbbjshlws on 2009-05-04
Yes i had changed the server file, and put it and all of the clients into the list, checked it on 3 systems and all did the same thing, restarted the server and the daemons. 

Cheers,

---

### Post by bigjimjams on 2009-05-04
> **jbbjshlws said:**
> Yes i had changed the server file, and put it and all of the clients into the list, checked it on 3 systems and all did the same thing, restarted the server and the daemons. 

Cheers,

Hi Josh, sorry to hear you're still having trouble! The only other thing I can think of at the moment is have you checked /etc/network/interfaces on the server and made sure that the ethernet adapter which is being used with the static IP address for the kerrighed network is set to manual and not auto. This should look something like the following if this is eth0:

iface eth0 inet manual

and not like this:

iface eth0 inet auto

The nodes should already have a configuration like this, as mentioned in the guide. Also did you sudo the exportfs -avr command for the server?

---

### Post by jbbjshlws on 2009-05-04
Hello, i checked the /etc/network/interfaces, and it is set correctly (this is to say i have it set to eth2, but that's because i have got it as the 2nd card in the server. i did sudo the exportfs command, as without doing this it produced an error. So we are still stuck!
Bugger!,

Any other suggestions?

Cheers,
Josh

---

### Post by bigjimjams on 2009-05-05
> **jbbjshlws said:**
> Hello, i checked the /etc/network/interfaces, and it is set correctly (this is to say i have it set to eth2, but that's because i have got it as the 2nd card in the server. i did sudo the exportfs command, as without doing this it produced an error. So we are still stuck!
Bugger!,

Any other suggestions?

Cheers,
Josh

Hi Josh, one thing I've just noticed is that in your earlier error message at boot up the portmap was looking for server 10.54.12.5, whereas in your /etc/hosts lists your server is 10.65.12.5. I think this is what is causing the problem. Can you check all your config files, especially the dhcp and dns settings. I think somewhere the ip address of your server has been entered wrongly. If you can't find anything you could always change the ip addresses you are using to 10.54.*.* instead of 10.65.*.* to see if this works.

---

### Post by djdirty on 2009-05-05
Im at the same issue and all my IP addresses are consistent...

---

### Post by jbbjshlws on 2009-05-05
OK! good eyes! that worked, i have now been able to finish this guide!!
yahoo!!!, now what can i run on it that would test it?

something that would normally run on one computer and take X time, that i can run on the cluster and take X/nodes??

as soon as i can see that it is fully functional i will start on your request biggles, and try to integrate it into a gui system to allow all of the nodes to still be of some use while sharing the processes. does anyone else know the best way to skin this cat?

Cheers, thankyou heaps for getting me this far,

Joshua!

---

### Post by bigjimjams on 2009-05-05
> **jbbjshlws said:**
> OK! good eyes! that worked, i have now been able to finish this guide!!
yahoo!!!, now what can i run on it that would test it?

something that would normally run on one computer and take X time, that i can run on the cluster and take X/nodes??

as soon as i can see that it is fully functional i will start on your request biggles, and try to integrate it into a gui system to allow all of the nodes to still be of some use while sharing the processes. does anyone else know the best way to skin this cat?

Cheers, thankyou heaps for getting me this far,

Joshua!

No problems, happy to help! Glad you've finally got it all working!! :) You could try some benchmarking software to start, what was the one they used on Microwulf?

---

### Post by jbbjshlws on 2009-05-06
Hmm spoke to soon, it seems i was able to get all the correct prompts as per the howto guide, but on further inspection it seems as if it is not working, i went to the link below to check to see if it was running:


> [http://www.kerrighed.org/wiki/index.php/FAQ](http://www.kerrighed.org/wiki/index.php/FAQ)
How do I know if the cluster is running? (aka How can I check that krgadm cluster start succeeded?)

Several ways:

    * On the cluster nodes, the kernel log contains a line like

      Kerrighed is running on XX nodes

      where XX is the number of nodes.
    * /proc/cpuinfo shows all CPUs of the cluster
    * /proc/meminfo shows all memory of the cluster
    * /proc/stat shows stats about all CPUs of the cluster 



and all of the log files are blank, in fact the entire /proc directory is empty, (/nfsboot/kerrighed/proc  from the server) so i am not sure what has gone wrong. i have backed up the whole system just in case something really weird happens and i loose everything!...

I also checked the info when i type in the "top" command into terminal and from what i understand my result should have several lines of cpu's, please let me know if this looks correct (only posted the top half of the output)

```
top - 04:09:46 up 19:29,  0 users,  load average: 0.10, 0.04, 0.01
Tasks:  43 total,   1 running,  42 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.6%us,  0.3%sy,  0.0%ni, 78.1%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:    256400k total,   138540k used,   117860k free,     9848k buffers
Swap:   262120k total,        0k used,   262120k free,   102368k cached

```


any help is appreciated,
Cheers,
Josh

---

### Post by bigjimjams on 2009-05-06
> **jbbjshlws said:**
> Hmm spoke to soon, it seems i was able to get all the correct prompts as per the howto guide, but on further inspection it seems as if it is not working, i went to the link below to check to see if it was running:






and all of the log files are blank, in fact the entire /proc directory is empty, (/nfsboot/kerrighed/proc  from the server) so i am not sure what has gone wrong. i have backed up the whole system just in case something really weird happens and i loose everything!...

I also checked the info when i type in the "top" command into terminal and from what i understand my result should have several lines of cpu's, please let me know if this looks correct (only posted the top half of the output)

```
top - 04:09:46 up 19:29,  0 users,  load average: 0.10, 0.04, 0.01
Tasks:  43 total,   1 running,  42 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.6%us,  0.3%sy,  0.0%ni, 78.1%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:    256400k total,   138540k used,   117860k free,     9848k buffers
Swap:   262120k total,        0k used,   262120k free,   102368k cached

```


any help is appreciated,
Cheers,
Josh

Hi Josh, */nfsroot/kerrighed/proc* on the server should be blank but when the nodes are up and running the */proc* directory on each of them should contain information about that machine and the rest of the cluster nodes. Have you set *nbmin=0* and the *session=1* in */nfsroot/kerrighed/etc/kerrighed_nodes*? Also, the line in dmesg kerrighed running on xx nodes will not be present until you run: *sudo krgadm cluster start* on one of the nodes. Does *sudo krgadm nodes* from a node list all the kerrighed nodes in the form *node_id:session*? Can you post your dmesg from a cluster node.

---

### Post by djdirty on 2009-05-06
Hi.. 

My nodes are still not booting..

Here is a screen shot..

[IMG]http://img159.imageshack.us/img159/6350/kerrighgehdu.png[/IMG]

Obviously im all in Virtualbox.. Is that an issue?

I have run through the entire setup process again to make sure i havent missed anything for a 5th time...

---

### Post by jbbjshlws on 2009-05-06
ok i have checked the /nfsroot/kerrighed/etc/kerrighed_nodes file and it is as you described,

when sudo krgadm nodes is ran, i get the result of 4 nodes (out of 4) in the list (6:1, 7:1, 8:1, 10:1),

If i try to access the proc directory from a node it seems to hang, if i look in the proc directory on the server, it is still empty even after i have typed in krgadm cluster start

i cannot post the dmesg from a node as there is nothing in the directory,

Cheers,

---

### Post by djdirty on 2009-05-06
All sorted..

For anyone setting up in Virtualbox.. The Adapter type needs to be the Intel Server for the server and Intel Desktop for clients..

:-)

---

### Post by djdirty on 2009-05-06
Ok.. Ive mucked around with my dhcpd.conf for a bit.. I want the DHCP to give any pc that asks for an IP address and start to load Kerrighed.. Anyone wanna upload there conf file that has this setup!

I dont want to have to enter in allll MAC addresses..

---

### Post by nerdopolis on 2009-05-06
djdirty: This seems to work for me:

```
# /etc/dhcp3/dhcpd.conf #
subnet 192.168.1.0 netmask 255.255.255.0 {
      option routers 192.168.1.1;            
      option broadcast-address 192.168.1.255;  
    range 192.168.1.1 192.168.1.254;
    option subnet-mask 255.255.255.0;
    filename "pxelinux.0";} 
```

jbbjshlws: try installing and running htop. htop showed multiple processors when I sampled the Kerrighed live disk. top did not.

---

### Post by bigjimjams on 2009-05-06
> **nerdopolis said:**
> djdirty: This seems to work for me:
jbbjshlws: try installing and running htop. htop showed multiple processors when I sampled the Kerrighed live disk. top did not.

I believe top should do if you press the "1" key to display all CPUs.

---

### Post by bigjimjams on 2009-05-06
> **jbbjshlws said:**
> ok i have checked the /nfsroot/kerrighed/etc/kerrighed_nodes file and it is as you described,

when sudo krgadm nodes is ran, i get the result of 4 nodes (out of 4) in the list (6:1, 7:1, 8:1, 10:1),

If i try to access the proc directory from a node it seems to hang, if i look in the proc directory on the server, it is still empty even after i have typed in krgadm cluster start

i cannot post the dmesg from a node as there is nothing in the directory,

Cheers,

/proc should display information from the machine that has booted that file system, which explains why it is empty on the server, as it never booted the kerrighed file system. Kerrighed modifies some of the information found in /proc to represent the whole cluster rather than the individual system.

Your problem may be related to a bad driver or something missing from the kernel or filesystem. Does the /nfsroot/kerrighed/etc/fstab contain the correct mount information for /proc?

---

### Post by djdirty on 2009-05-07
Thanks Nerdopolis.. I tried that then my TFTP wouldnt even boot.. So i reverted back to my old dhcpd.conf and my tftp STILL wont boot! Heres my file..
 
```
# /etc/dhcp3/dhcpd.conf #
# General options
option dhcp-max-message-size 2048;
use-host-decl-names on;
deny unknown-clients;
deny bootp;
# DNS settings
option domain-name "kerrighed";          # Just an example name, call it whatever you want tp.
option domain-name-servers 10.65.12.5;  # The ip address of the dhcp/tftp/nfs server.
# Information about the network setup
subnet 10.65.12.0 netmask 255.255.253.0 {
  option routers 10.65.12.5;              # IP addreess of the dhcp/tftp/nfs server.
  option broadcast-address 10.65.12.255;  # Broadcast address for your network.
}
# Declaring IP addresses for nodes and PXE info
group {
  filename "pxelinux.0";                 # location of PXE bootloader. Path is relative to tftpd's root(/srv/tftp/)
  option root-path "10.65.12.5:/nfsroot/kerrighed";  # Location of the bootable filesystem on NFS server
  host kerrighednode1 {
        fixed-address 10.65.12.101;          # IP address for kerrighednode1.
        hardware ethernet 08:00:27:E5:41:49;  # MAC address of the kerrighednode1's ethernet adapter
  }
  server-name "kerrighedserver"; # Name of the PXE server
  next-server 10.65.12.5;       # The IP address of the dhcp/tftp/nfs server
}
```
 
And my :srv/tftp/pxelinux.cfg/default file:-
 
```
LABEL linux
KERNEL vmlinuz-2.6.20-krg
APPEND console=tty1 root=/dev/nfs nfsroot=10.65.12.5:/nfsroot/kerrighed ip=dhcp rw
```
 
Grrrr..
 
And yes i have restarted all daemons and even the server...

---

### Post by djdirty on 2009-05-07
Fail.. Firewall LOL

---

### Post by djdirty on 2009-05-07
> **nerdopolis said:**
> djdirty: This seems to work for me:

```
# /etc/dhcp3/dhcpd.conf #
subnet 192.168.1.0 netmask 255.255.255.0 {
      option routers 192.168.1.1;            
      option broadcast-address 192.168.1.255;  
    range 192.168.1.1 192.168.1.254;
    option subnet-mask 255.255.255.0;
    filename "pxelinux.0";}' > /etc/dhcp3/dhcpd.conf

apt-get install tftpd-hpa -y

printf   '#Defaults for tftpd-hpa
#RUN_DAEMON="no"
#OPTIONS="-l -s /var/lib/tftpboot"
# /etc/default/tftp-hpa #
#Defaults for tftp-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /srv/tftp"
```
jbbjshlws: try installing and running htop. htop showed multiple processors when I sampled the Kerrighed live disk. top did not.


Any other ones? Me and Josh dont wanna sit here and type in over 400 MAC addresses!

---

### Post by bigjimjams on 2009-05-07
> **djdirty said:**
> Any other ones? Me and Josh dont wanna sit here and type in over 400 MAC addresses!

Did you see my reply to the message you sent me earlier? Hope that dhcp config may help!

---

### Post by nerdopolis on 2009-05-07
I made a critical mistake the /etc/dhcp3/dhcpd.conf. it was supposed to be:

```
# /etc/dhcp3/dhcpd.conf #
subnet 192.168.1.0 netmask 255.255.255.0 {
      option routers 192.168.1.1;            
      option broadcast-address 192.168.1.255;  
    range 192.168.1.1 192.168.1.254;
    option subnet-mask 255.255.255.0;
    filename "pxelinux.0";} 
```I accidentally copied and pasted too much information from the batch file I was working on. Sorry.

---

### Post by djdirty on 2009-05-08
Rito.. Seen as we have all these pcs! They all have differing network cards.. How do we install drivers into the kernel for different cards?
\
Cheers,

Davo

---

### Post by jbbjshlws on 2009-05-09
Hello!
After many tests and re-installations (even since the last post!) i have been able to successfully get the top command to work. I am able to see the 3 processors (over 3 nodes) in one view. Kerrighed is not migrating the processes across to the other nodes though. i have a node setup with "top" running to view the processors on the network (where it is showing all 3 processors), and on another machine i am running hardinfo to bench test the system. When it is running you can see the node running hardinfo go up to 100% usage, but the other two processors in the cluster don't change there value (sitting around 0.3%~~).
I have also tried john -test (apt-get install john), and crafty (apt-get install crafty) to test and they all have the same results as hardinfo.

So this brings me to two questions, does kerrighed speed up both multi-threaded and single-threaded applications?

and how can i migrate the tasks from one node to another? (i have tried ```
$ sudo krgcapset -d +CAN_MIGRATE
``` and also 
```

krgcapset -k  [pid] --effective +CAN_MIGRATE
migrate [pid] [node_id]
```
where i had the pid as hardinfo and the node_id as the node that it was running on (kerrighednode1)

So once again i am stuck with a cluster nearly working!!.

any ideas?
Cheers

---

### Post by jbbjshlws on 2009-05-09
Like Davo, i also need to install the drivers to have all of the computers on the network being able to work. i need the drivers for the DELL Optiplex 755 and 745 series computers, the nic's are:

Broadcom® 5754 Gigabit Ethernet LAN solution 10/100/1000 Ethernet
Intel® 82566DM Gigabit LAN 10/100/1000
Broadcom  5721C1 NetXtreme Gigabit Ethernet PCI-E

How can i get these and integrate them into the kernel?

Cheers, Josh

---

### Post by bigjimjams on 2009-05-09
> **jbbjshlws said:**
> Hello!
After many tests and re-installations (even since the last post!) i have been able to successfully get the top command to work. I am able to see the 3 processors (over 3 nodes) in one view. Kerrighed is not migrating the processes across to the other nodes though. i have a node setup with "top" running to view the processors on the network (where it is showing all 3 processors), and on another machine i am running hardinfo to bench test the system. When it is running you can see the node running hardinfo go up to 100% usage, but the other two processors in the cluster don't change there value (sitting around 0.3%~~).
I have also tried john -test (apt-get install john), and crafty (apt-get install crafty) to test and they all have the same results as hardinfo.

So this brings me to two questions, does kerrighed speed up both multi-threaded and single-threaded applications?

and how can i migrate the tasks from one node to another? (i have tried ```
$ sudo krgcapset -d +CAN_MIGRATE
``` and also 
```

krgcapset -k  [pid] --effective +CAN_MIGRATE
migrate [pid] [node_id]
```
where i had the pid as hardinfo and the node_id as the node that it was running on (kerrighednode1)

So once again i am stuck with a cluster nearly working!!.

any ideas?
Cheers

Hi Josh, are those benchmark tests multi-process or just multi-threaded? Kerrighed only migrates processes to other nodes and has no support for migrating threads at the moment. If you run krgcapset -s does it show that the inheritable and effective sets have the CAN_MIGRATE option? An easy way to test if kerrighed is working is to write a simple C program that is an infinite loop and spawn it the same time as you have cores. If every core in your cluster is at 100% then you know it works!

---

### Post by jbbjshlws on 2009-05-09
Hello Bigjimjams,

> Hi Josh, are those benchmark tests multi-process or just multi-threaded? Kerrighed only migrates processes to other nodes and has no support for migrating threads at the moment. If you run krgcapset -s does it show that the inheritable and effective sets have the CAN_MIGRATE option? An easy way to test if kerrighed is working is to write a simple C program that is an infinite loop and spawn it the same time as you have cores. If every core in your cluster is at 100% then you know it works!

when i run krgcapset -s it does show "CAN_MIGRATE" under "Inheritable Effective Capabilities: 03

I made an infinite loop in a sh script (not sure how to do it in c) and it did not migrate. those bench test programs to my knowledge have multi-threaded support, not sure about multi-process. what is everyone else running on there clusters? surely i could test with the same application.

Do you get an advantage when you use normal (aka written by other people with no intention to run on a cluster, eg video encoding etc)  Single-threaded applications with the kerrighed cluster?

so i have a list of cpu's in top, they dont migrate tasks, and everything seems setup correctly, (but clearly isn't) whats the next attack?

Cheers,
Joshua

---

### Post by nerdopolis on 2009-05-10
Try it with yes. yes is a program that comes with Linux, and with no arguments brings the CPU usage up to 100%. try running two instances of yes, and see if they migrate (two CPU's should be at 100%). If it doesn't try manually migrating them.

---

### Post by jbbjshlws on 2009-05-13
Hello nerdopolis, i have tried using yes, i filled half a screen with text and i was only able to get a single cpu to reach a maximum of 3.7% usage, even with several instances of it running.  how were you able to have it reach 100% (the computers i am testing on are around 2.4ghz machines) . thanks for the dhcp code, this really helped....now silly me i still need the mac addresses for the wol anyway!


Do you get an advantage when you use normal (aka written by other people with no intention to run on a cluster, eg video encoding etc) Single-threaded applications with the kerrighed cluster?

Also I am still unsure how to integrate the:
> Broadcom® 5754 Gigabit Ethernet LAN solution 10/100/1000 Ethernet
Intel® 82566DM Gigabit LAN 10/100/1000
Broadcom® 5721C1 NetXtreme Gigabit Ethernet PCI-E
Drivers into the kernel. How can i get these and integrate them into the kernel?


I am in the process of trying out the latest svn for kerrighed on a different machine. Can any one please verify that when they try to download it from ```
svn checkout svn://scm.gforge.inria.fr/svn/kerrighed/trunk
``` it stops and they cannot get the full package, it comes up with an error:
```
'/SVNTrunk/kernel/include/linux/netfilter_ipv4' locked
```
although the file is not locked, and i have ran cleanup and tried unlocking it, and tried this on a couple of machines and have had the same result.

---

### Post by nerdopolis on 2009-05-13
1. 
wierd... try
```
 yes > /dev/null 
```2.
I don't think single threaded application will be accelerated by a cluster. I don't think there is a way to run a single thread on two cpus.  but you can multitask, one cpu can be loaded running the process and a second can be running your web browser or something. 

And by the looks of it, threaded apps won't even benefit much until Kerrighed has thread migration. (but I am wondering if performance will increase if an application developer splits his program into multiple processess somehow)

3.
in my home directory I made a folder /svn in my home directory, and ran your command. It worked on my box, maybe it was the SVN revision. Try redownloading in a new folder again, and see if it works.

---

### Post by jbbjshlws on 2009-05-14
Hello nerdopolis, 
I am downloading the svn again, onto a different machine, in a different folder, so it should work, (hopefully,) it seems to have gotten further than last time.
typing  yes > /dev/null into a machine deffanatly brings a CPU to 100%

I can't test it on my cluster as currently when i boot them up, and type in ```
krgadm nodes status
```, it comes up with a blank list of no nodes (not even the one i am logged onto). I am thinking this has something to do with possibly the need to reset a cluster session or maybe i am terminating the session in a weird way. it is not consistent.

Also the other issue i face is, when they do occasionally appear int he list, when i type in ```
krgadm cluster start
``` then followed by ```
top
``` the computer that i run the command on freezes. all of the nodes in the cluster are not communicating and i think this could also have something to do with a session issue, is there a limit to how many nodes or the ip addresses of nodes across subnet's that could affect kerrigheds stability? 

I was able to integrate the Broadcom drivers through the "make menuconfig" menu and ticking all of the drivers that were available and integrating them, they seem to be booting. I am still unsure how to integrate the Intel 82566DM Gigabit LAN drivers. they were not in the list.


Cheers,

Joshua

---

### Post by nerdopolis on 2009-05-15
In the menuconfig is there any option for something like Intel e1000 or something like that? because I think that card may fall under that category.

I wouldn't know what the maximum number of nodes is... on the Kerrighed web page it talks about a 110 node cluster though... 
[http://www.kerrighed.org/forum/viewtopic.php?p=606#606](http://www.kerrighed.org/forum/viewtopic.php?p=606#606)

When the nodes fail to appear in krgadm nodes status, can you ping them?

for your Kerrighed problems, all I can think of right now is to try a shut-down on all nodes, rebooting the master node, and then powering up the other nodes again.

EDIT: I almost forgot, did the SVN download successfully?

---

### Post by jbbjshlws on 2009-05-16
Hello nerdopolis,
I have checked the menuconfig and i have got Intel(R) PRO/1000 Gigabit Ethernet support there, i had it checked as built-in, but it still does not work. I could not find Intel e1000 in the list at all.

I am able to ping the computer without a problem

```
cluster@kerrighednode249:~$ krgadm nodes status

cluster@kerrighednode249:~$ ping 10.65.12.5
PING 10.65.12.5 (10.65.12.5) 56(84) bytes of data.
64 bytes from 10.65.12.5: icmp_seq=1 ttl=64 time=0.202 ms
64 bytes from 10.65.12.5: icmp_seq=2 ttl=64 time=0.334 ms

--- 10.65.12.5 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.202/0.268/0.334/0.066 ms
cluster@kerrighednode249:~$
```

You can see the result above when i type in krgadm nodes status, nothing...

The network is spread across 3 subnet's, i wouldn't think this would cause a problem, dhcp seems to be dealing out the files completely fine, but maybe i am wrong.

when i run:
```
cluster@kerrighednode249:~$ krgadm cluster poweroff
cluster@kerrighednode249:~$

```

the computer/computers do not turn off, also when i run the restart command they do not turn off. both of these commands used to restart the computers, and seem to work when there is nodes in that status list.

Not sure if this matters, but i have got my etc/dhcp3/dhcpd.conf file automatically assigning ip addresses, and my etc/hosts file set with a list of all of the ip addresses in the range and then an assigned name kerrighednode1 -kerrighednode500. clearly not all of these will be used at any one time, but if i didn't do this change in the hosts file, it got the server name assigned. 

how do u define the master node?
and how can u shut down just the master node? (or any single node)

I tried "krgadm nodes poweroff -n" followed by its ip address,  name or id, but it didn't work.

Also have you tried updating your install to the latest svn? anything i should know before i proceed?


I am checking the svn now, the folder is 230.7 MB and has 23,221 files in it, it seemed to lock the computer while it was downloading not sure if that is the expected (i would think not..., please let me know if this is your result. I tried downloading it again to compare sizes, but i got the error
```
svn: Can't create directory 'trunk/kernel/include/asm-m32r/m32104ut/.svn/props': Operation not supported
```
**FIXED: **Problem was restore to a file system that was not able to cope with the structure, (both fat and ntfs didn't work) was able to download to linux file system. also second issue was i was originally downloading from svn checkout svn://scm.gforge.inria.fr/svn/kerrighed/  as it happens there is over 1 million files and over 11 gig of files, it crashed the ubuntu system and locked it out completely. So when downloading the svn, make sure to have enough room, and to go to the correct file system!

Cheers,
Josh

---

### Post by nerdopolis on 2009-05-16
On each node individually, run 
```
sudo poweroff
```then do the same on the server.
I think those krgadm shutdown commands are stubs. I'm not sure...

BTW: When I said "master node" I meant to say the server. Sorry. 


For the drivers:
You may need to use an initramfs... The driver seemingly supports your card, but I read somewhere its only supported as a module. In the make menuconfig, try creating modules for the PRO/1000. once it finishes compiling run:

In the nfs file system change /etc/initramfs-tools/initramfs.conf to look like
MODULES=netboot
BUSYBOX=y
COMPCACHE_SIZE=""
BOOT=nfs
DEVICE=eth0
NFSROOT=auto

and in the nfs file system run:
```
update-initramfs -c -k 2.6.20-krg 
```
copy the kernel and the new initramfs to /srv/tftp

change your  /srv/tftp/pxelinux.cfg/default:
```

LABEL linux  
KERNEL vmlinuz-2.6.20-krg  
APPEND root=/dev/nfs initrd=initrd.img-2.6.20-krg nfsroot=10.54.12.5:/nfsroot/kerrighed ip=dhcp rw" 

```




I didn't get to try out the SVN version yet. I didn't get much time with my cluster this week...

---

### Post by robasc on 2009-05-20
Well it's been a while since my last posting. I have been so busy with work I have not had time to do anything. 

Anyways, here is where I left off. 

Section: 2.2: configure kerrighed of the guide

I went to edit the /etc/kerrighed_nodes file but there was no file existing by that name?

I must have made a mistake somewhere but I do not see one anywhere? 

Any thoughts anyone?

---

### Post by bigjimjams on 2009-05-21
> **robasc said:**
> Well it's been a while since my last posting. I have been so busy with work I have not had time to do anything. 

Anyways, here is where I left off. 

Section: 2.2: configure kerrighed of the guide

I went to edit the /etc/kerrighed_nodes file but there was no file existing by that name?

I must have made a mistake somewhere but I do not see one anywhere? 

Any thoughts anyone?

Hi robasc, have you tried creating the file yourself and adding the lines:
```
session=1
nbmin=0
```
I think I may have had to do this myself before. Hope it helps.

---

### Post by robasc on 2009-05-21
Yes I did, I was not sure if I had to or not. It's been a while since I last played with the cluster.

I have had some other issues with kerrighed. I noticed when I tried to configure the scheduler for kerrighed like so at [http://www.kerrighed.org/wiki/index.php/SchedConfig:](http://www.kerrighed.org/wiki/index.php/SchedConfig:)

> 
Enabling the configurable scheduler framework
[edit] Kernel configuration

To (re-)enable the scheduler framework, select "Cluster support" --> "Kerrighed support for global scheduling" --> "Run-time configurable scheduler framework" (CONFIG_KRG_SCHED_CONFIG). 


Well just to fill you in, the whole point of this is because I cannot get my nodes to boot up with kerrighed.

I keep getting r8169 eth0: link down

sending DHCP requests <3>DHCP/BOOTP: reply not for us 
timed out!

and it just keeps looping through this.

I believe that my network card does not like the r8169 configured by the kerrighed kernel?

If I switch this back to boot from the linux kernel for nfs it boots fine. Not sure what do to from here yet.

any clues? Could it be that my chipset is not supported?

I did notice that you said you had the same chipset in your model and it worked is that correct Bigjimjams?

It would not let me choose enter into kerrighed support for global scheduling to choose the Run-time configurable schedule framework. It has me blocked out of this.

I used the install you provided from post #109, added the svn and configured schedulers in /etc/fstab with:

> 
configfs        /config         configfs        defaults        0 0



---

### Post by bigjimjams on 2009-05-22
> **robasc said:**
> Yes I did, I was not sure if I had to or not. It's been a while since I last played with the cluster.

I have had some other issues with kerrighed. I noticed when I tried to configure the scheduler for kerrighed like so at [http://www.kerrighed.org/wiki/index.php/SchedConfig:](http://www.kerrighed.org/wiki/index.php/SchedConfig:)



Well just to fill you in, the whole point of this is because I cannot get my nodes to boot up with kerrighed.

I keep getting r8169 eth0: link down

sending DHCP requests <3>DHCP/BOOTP: reply not for us 
timed out!

and it just keeps looping through this.

I believe that my network card does not like the r8169 configured by the kerrighed kernel?

If I switch this back to boot from the linux kernel for nfs it boots fine. Not sure what do to from here yet.

any clues? Could it be that my chipset is not supported?

I did notice that you said you had the same chipset in your model and it worked is that correct Bigjimjams?

It would not let me choose enter into kerrighed support for global scheduling to choose the Run-time configurable schedule framework. It has me blocked out of this.

I used the install you provided from post #109, added the svn and configured schedulers in /etc/fstab with:

Hi, I know there have been some issues with the 8169.ko driver being outdated on the kerrighed.users mailing list. One solution was to change to the skge.ko driver. My chipset was actaully the 8111, but the 8169 driver worked. The configuration options for the svn kernel should already be chosen. The only one you may have to check is the "Automatic module loading" one, which I've found to have been disabled before.

To activate the new scheduler, you run:
```
sudo krg_legacy_scheduler
``` from a node when the cluster is booted. Also, I've found that "nbmin" actually works again in the svn version, so you could set this in /etc/kerrighed_nodes to the number of nodes in your cluster.

As for the booting of nodes, I noticed that a BOOTP line appeared, I think the DHCP server should have a line which denies BOOTP but allows booting via DHCP/TFTP.

---

### Post by d_chall on 2009-05-22
> **kgkv said:**
> We have already "ported" perceus (and warewulf) to debian.. It needs 
a lot of polishing but it works for i386 and amd64 on our cluster
of ~80 machines.


deb [http://biodev.ece.ucsb.edu/debian/](http://biodev.ece.ucsb.edu/debian/)  main contrib

On you server:
  aptitude install perceus-server 

There are scripts for creating debian VNFS there.
kgkv - Are you still working with Perceus on Ubuntu/Debian? I tried installing you package and everything seemed to work great at first, but whenever I try to boot the worker nodes, I get the error: "failed to execute / init, Kernel panic - not syncing: No init found. Try passing init = option to kernel".  I've tried talking to people on the Perceus support IRC channel, but so far they've mostly just said that they don't test it on Debian.  Did you every face this problem, or do you know any possible solutions?  Also, if you know where I could find newer packages or premeade Debian/Ubuntu VNFS files that would be great.  Thanks for you work on this!

---

### Post by jbbjshlws on 2009-05-25
> **nerdopolis said:**
> I made a critical mistake the /etc/dhcp3/dhcpd.conf. it was supposed to be:

```
# /etc/dhcp3/dhcpd.conf #
subnet 192.168.1.0 netmask 255.255.255.0 {
      option routers 192.168.1.1;            
      option broadcast-address 192.168.1.255;  
    range 192.168.1.1 192.168.1.254;
    option subnet-mask 255.255.255.0;
    filename "pxelinux.0";} 
```I accidentally copied and pasted too much information from the batch file I was working on. Sorry.

> I can't test it on my cluster as currently when i boot them up, and type in
Code:

krgadm nodes status

, it comes up with a blank list of no nodes (not even the one i am logged onto). I am thinking this has something to do with possibly the need to reset a cluster session or maybe i am terminating the session in a weird way. it is not consistent.

Hello Nerdopolis,
This was related to the DHCP issue, if i have the mac addresses in the list, it seems to work without a problem, when they are automatically all added, i get a blank list of no nodes. I have a feeling that it worked for a while because the mac address was still in the dhcp lease time, when that expired they all disappeared out of the krgadm nodes list. So for now until i can actually get some tasks migrating across on the 3 node network i will put this issue off, as it is introducing more problems. 


I ran yes with "yes > /dev/null" and it does bring the cpu to 100% without question, but even with several instances of it running it does not migrate across to any other cpu's.

I am now able to see the nodes on the network when i type in "krgadm nodes status" and the cpu's from them in "top" 1 (or htop).

does anyone else have any other ideas on having tasks migrate from one cpu to another?

I have decided i will get the cluster working on 3 computers before stuffing around with upgraded svn's, new nic drivers or automatic dhcp config, i feel this is a good move...

Let me know what i can test to see that the tasks are migrating, bigjimjams, if you could please post the code you used to write a simple C program that is an infinite loop, it would be appreciated, i have not tested this, i did test a sh script but it didn't migrate.

Cheers,

---

### Post by nerdopolis on 2009-05-26
Hi. I looked at some files in a Kerrighed live CD session for hints, and one thing I noticed is that they are passing session_id, and node_id arguments to the Kerrighed kernel. (from the tftp config).

I think that's what *might* be keeping Kerrighed from working (although I'm not sure, but I did read from a somewhat incomplete tutorial that you have to pass the two arguments, after I found out about them) 

The problem with the node_id argument is that it will require a seperate configuration file in the /srv/tftp/pxelinux.cfg/ folder for each node's IP, so that each node can get a different node_id argument (instead of just the /srv/tftp/pxelinux.cfg/default file). 

How many nodes are you planning to connect? I can create a bash script that creates these files for you, once I have the number of nodes.

---

### Post by jbbjshlws on 2009-05-27
I am starting with about 120, then in mid June i will have access to about 400. towards the end of July about 800. i can get exact figures for you, but at the moment i cannot reliably have more than 4 computers connect and see the processors in top. and can't get even two computers to share the cpu usage.

Cheers,
Joshua

---

### Post by nerdopolis on 2009-05-27
Below I have the contents of the bash script file that defines the boot command line for 1016 nodes. They all have different node_id passed, and it also has tftp pass the session_id=1 to the nodes . The bash script defines the node_id for ip addresses 10.54.12.1 to 10.25.16.254 (assuming that's what you use, if its not I'll tweak it). The files are put into /srv/tftp/pxelinux.cfg, and the file names are the ip address they define the kernel command line for in hex. 
 
```

#! /bin/bash
nodeid=1
a=10
b=54
c=12
d=1
for (( runtimes=1; runtimes<=$65535; runtimes-- ))
do
IP_ADDR=$a.$b.$c.$d 
filename=$( printf '%0X' ${IP_ADDR//./ } )  
printf 'LABEL linux  
KERNEL vmlinuz-2.6.20-krg  
APPEND root=/dev/nfs initrd=initrd.img-2.6.20-krg nfsroot=10.54.12.5:/nfsroot/kerrighed ip=dhcp rw session_id=1 node_id=' > /srv/tftp/pxelinux.cfg/$filename
printf $nodeid >> /srv/tftp/pxelinux.cfg/$filename
d=$[$d+1]
nodeid=$[$nodeid+1]
if (( 255==$d ));
then
d=1
c=$[$c+1]
fi
if (( 16==$c )); 
then
exit 0
fi
done 

```If the idea works, I'll attach one that does ip addressess 192.168.1.1-192.168.1.254 which is what the guide uses.

---

### Post by schreck494 on 2009-05-27
I have no idea if you guys know anything about Open MPI, but I figured it couldn't hurt to ask.  I am trying to build a beowulf cluster that will be used with this program:
[http://parsec.ices.utexas.edu/](http://parsec.ices.utexas.edu/)
Right now, I have something that is just an updated version of the microwulf cluster running 8.04.  I installed Open MPI from the repositories, and then used the Open MPI compilers to compile a parallel version of parsec.  I think, however, that Open MPI is not configured correctly (I haven't changed anything since it installed), or I just don't know how to properly run parallel applications with MPI.  Any suggestions would be greatly appreciated.
Thanks,
Mark

---

### Post by jbbjshlws on 2009-05-27
Hello nerdopolis, i will be trying this tonight, before i do, i just wanted to double check with you why the new range would be 10.54.12.1 to 10.25.16.254, if it is going over 1016 nodes, i would have thought the range would have been 10.54.12.1-10.54.15.254, i might be missing somthing here. the server ip we are using is 10.65.12.5, and the current range is 10.65.12.6-10.65.15.254. I tried the live cd  and i was able to ge the server computer up and running, but any other computers to boot to it did not work, are others successfully able to have the live cd working?

Cheers,
Joshua

---

### Post by nerdopolis on 2009-05-27
Oops. You're right. it would have stopped at 10.54.15.254. I just wasn't thinking correctly when I wrote the post.

[COLOR=Red]
[/COLOR] [COLOR=Red][COLOR=Red]EDIT: I found and fixed a problem that caused a glitch in tftp. the bash script would output 10.54.12.1 as A41C1. TFTP wanted it to be 0A410C01. If your ran my file, you're going to need to run it again.

**EDIT 2: I also found another issue with the bash script. If you ran the bash script, your going to need to run it again. I am sorry for any inconvenience this might have caused**

[/COLOR][/COLOR] Try this: 
```
[COLOR=Yellow][COLOR=Black]#! /bin/bash
nodeid=1
a=10
b=65
c=12
d=6
for (( runtimes=1; runtimes<=$65535; runtimes-- ))
do
IP_ADDR=$a.$b.$c.$d 
filename=$( printf '%02X' ${IP_ADDR//./ } )  
printf 'LABEL linux  
KERNEL vmlinuz-2.6.20-krg  
APPEND root=/dev/nfs nfsroot=10.65.12.5:/nfsroot/kerrighed ip=dhcp rw session_id=1 node_id=' > /srv/tftp/pxelinux.cfg/$filename
printf $nodeid >> /srv/tftp/pxelinux.cfg/$filename
d=$[$d+1]
nodeid=$[$nodeid+1]
if (( 255==$d ));
then
d=1
c=$[$c+1]
fi
if (( 16==$c )); 
then
exit 0
fi
done[/COLOR][/COLOR]
```I was able to get the live cd to work but its a little hacky: when the server is booting, you need to attach it to a DHCP server, so that it can get its own IP address, after the server loads when you go to boot your nodes you need to disconnect the DHCP server so that the nodes don't get the first DHCP server's information.
[COLOR=Red][COLOR=Red][/COLOR]
[/COLOR]

---

### Post by cfrieler on 2009-05-28
@Mark

I haven't used OpenMPI, but have used MPICH in several installations over the years. 
It's not easy to convert a standard program to efficiently use MPI on a cluster. If all you did was to recompile using the MPI library, you shouldn't expect any computation on the other nodes. You haven't broken the code into distributable pieces yet!

My recommendation would be to stick to a simple demo program until you can confirm that MPI is working. There is a common "Hello World!" and a pi calculator that are both very easy to compile and run. Note that for MPICH, there are special compile and run commands that must be used. Use this simple program to touch each of the compute nodes and confirm that the MPI daemons are communicating. Then you can move on to learning how to convert your target code to distribute part of the task and really use the cluster.

Good Luck!

---

### Post by schreck494 on 2009-05-28
The program is already programmed to be run in a parallel environment.  My problem is I have no idea how to set up Open MPI.

---

### Post by jbbjshlws on 2009-06-11
Hello,
I have been very busy mucking around with this cluster, and i am trying to run an application on a clustered node that was written to test clusters with open_mp, the problem is the program is written for windows pc's, so i have installed "apt-get install ubuntu-desktop" and also "apt-get install wine" and had wine do all of its updates [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) 

after this, i installed winetricks, ran "sh winetricks dotnet20 vcrun2008" and proceeded through the prompts. it came up with errors for vcrun2008 with write permission issues, i chmod and chown the .wine directories to the logged in root user (cluster) and i still got the same errors for vcrun2008, (vcrun2005sp2 worked with no problems) so i played around for a while, the solution was to extract the files in vcrun2008 in a windows environment then copy the directories across to ubuntu then run the files, and it seems to install with no issue.

when i go to run the attached file, i get the attached error, (too long to post)

I do not get this or the above error when i run the file on a machine that has been installed from scratch (with 8.04), and not booted into ubuntu 8.04 from the nfs kerrighed kernel. i do not understand the error or how to fix it. i am posting this here because it does not seem to be a wine issue, as it works fine with wine on a normal un-clustered machine, so it seems related to the cluster setup.

Any help is appreciated,

Kind Regards,
Joshua

---

### Post by nerdopolis on 2009-06-14
I think if that program was to run on a Kerrighed cluster in wine, it would still fail because Kerrighed has no thread migration, so I don't think kerrighed can support spanning processes' threads across multiple nodes yet, and I think that program would just create another thread in the wine process.

Kerrighed's live CD has a bash script that starts the cluster (I saw some weird ssh stuff come up when I ran it...), and runs a test. If you want it I'll attach it for you.

---

### Post by jbbjshlws on 2009-06-15
Hello nerdopolis

thank you for your reply, it would be awesome if you could attach that ssh file for me to test with.

So the best way to test the file i have would be porting this to mono is this correct?

---

### Post by directhex on 2009-06-15
> **jbbjshlws said:**
> Hello,
I have been very busy mucking around with this cluster, and i am trying to run an application on a clustered node that was written to test clusters with open_mp, the problem is the program is written for windows pc's, so i have installed "apt-get install ubuntu-desktop" and also "apt-get install wine" and had wine do all of its updates [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) 

after this, i installed winetricks, ran "sh winetricks dotnet20 vcrun2008" and proceeded through the prompts. it came up with errors for vcrun2008 with write permission issues, i chmod and chown the .wine directories to the logged in root user (cluster) and i still got the same errors for vcrun2008, (vcrun2005sp2 worked with no problems) so i played around for a while, the solution was to extract the files in vcrun2008 in a windows environment then copy the directories across to ubuntu then run the files, and it seems to install with no issue.

when i go to run the attached file, i get the attached error, (too long to post)

I do not get this or the above error when i run the file on a machine that has been installed from scratch (with 8.04), and not booted into ubuntu 8.04 from the nfs kerrighed kernel. i do not understand the error or how to fix it. i am posting this here because it does not seem to be a wine issue, as it works fine with wine on a normal un-clustered machine, so it seems related to the cluster setup.

Any help is appreciated,

Kind Regards,
Joshua

OpenMP is explicitly NOT designed to run code spanning multiple nodes. Performance when doing so with an OpenMP emulator is generally terrible, even with a high-speed Infiniband network.

---

### Post by nerdopolis on 2009-06-15
I have the bash scripts for starting Kerrighed attached. it contains executables from the Kerrighed Live CD. demokrg is the one you run. it calls all the weird ssh commands I told you about, and then it runs another bash script that starts Kerrighed, and then a cpu eater, and then brings up htop. If it works it should show the number of cpus, all at 100%. 

I think the best place to run this is on the nfs server as chroot. Extract the files to /bin, or another folder where Linux sees executables.

EDIT: I missed a file in the archive, so I reattached it.

---

### Post by DiabolicalGamer on 2009-06-21
Hello Everyone, I've been trying to get a cluster running in VMWare using Kerrighed. I tried version 2.3.0 as well as the latest SVN version. I am able to get a 2 node cluster running and am able to manually migrate a process between them. I would however like to have this happen automatically. I realized last night that I hadn't configured krg_legacy_scheduler which I originally assumed was an old package. Today I've been struggling getting the /config mounted as ConfigFS. Not sure where to go from here. Is there any specific changes I need to make to the kernel when I'm compiling to get it to work or does it only work with a certain version? I could really use some help. Thanks in advance for your speedy replies.  /DG

---

### Post by Sir Trysalot on 2009-06-23
[FONT=Times New Roman][SIZE=3]Hello All![/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]I&#8217;m Tony, and I would like to hear some of you opinions of what I&#8217;m planning and also some more information on the benefits of running [COLOR=black]Kerrighed over some of the other ways of setting up a cluster[/COLOR][/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman][COLOR=black]I am planning a system using the Atom 330 based [/COLOR]D945GCLF2 Intel board, with 2 Gb of ram per node. I have thoughts of eventually growing to 8 &#8211; 16 total boards. Am I wasting my time setting up a cluster with these?[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]This is the most current and most relevant forum and threat that I have found concerning Beowulf cluster computing. [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]Thank you for taking the time to read and respond to my post.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Tony.[/SIZE][/FONT]
):P

---

### Post by DiabolicalGamer on 2009-07-07
Hey Tony, I have been trying to setup a cluster using Kerrighed for about a week or two now and I've gotta say its not as easy as it looked originally. It's still in beta and documentation is either missing or scattered across the forums. I wouldn't discourage you from trying as I've learned a lot during the process, but if you've got a specific time schedule I'd definitely caution you. I hope to write a good How-To once I've got everything working so check this thread soon. :)  /DG

---

### Post by a.mason on 2009-07-09
Hi all - I'm Alicia Mason; I work with Tony / ajt at the Rowett Institute in Aberdeen. We now have a 7-node Beowulf running Kerrighed under a spin of Ubuntu, Bio-Linux 5, which I set up with Tony's help.

In doing this, I've made a lot of revisions, fleshings-out and corrections to BigJimJams' guide, which was excellent; it just needed a little work. I'd appreciate it if anyone has feedback, more suggestions, questions etc. The guide as is will produce a working 4-node Beowulf if you follow it exactly, and I'm working on adding instructions to make the server also a functioning node as we've done with our cluster.

Thanks everyone

AM

---

### Post by nerdopolis on 2009-07-09
I think I read on some incomplete Kerrighed tutorial somewhere that you have to pass the session_id (which is the same for each node), and the node_id (which is different for each node) to the kerrighed kernel with tftp, for Kerrighed to work.  

BTW: Kerrighed 2.4.0 is out.

EDIT: just reading on the release notes for 2.4.0, and it says you need to pass session_id=xx but nothing about node_id which simplifies alot of things.

---

### Post by gabrielaca on 2009-07-19
to **a.manson** i will apreciate your effort to post those instructions, i´m planning on building a 6 node myself and your expirience would be very helpful.

---

### Post by artefact on 2009-07-22
By default, Kerrighed use the last digit of your IP address as node_id, but can still pass node_id parameter, if you want. It is still true for 2.4.0.

Jean

---

### Post by lrilling on 2009-07-22
Hi BigJimJams,

> **bigjimjams said:**
> Hi Xingmu and anybody else interested, as promised in my earlier post I've added a draft guide for setting up a kerrighed 2.3.0 cluster in Ubuntu 8.04 on the Easy Ubuntu Clustering Wiki. Here is the link:

[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)

If you have any questions, comments, suggestions or improvements let me know.

I've setup a link to your guide from Kerrighed's documentation page.

As you probably noticed, a few changes are required for Kerrighed 2.4, mostly because of the new global scheduler framework. In short:

[LIST]
[*]A script called [FONT=Courier New]krg_legacy_scheduler[/FONT] is now installed, and is automatically run at cluster start, provided that [FONT=Courier New]/etc/init.d/kerrighed[/FONT] was properly installed.
[*]The bugs of [FONT=Courier New]krgadm[/FONT] should now be fixed. If not, please tell us on [EMAIL="kerrighed.users@listes.irisa.fr"]kerrighed.users@listes.irisa.fr[/EMAIL].
[/LIST]
You could check the release notes ([http://www.kerrighed.org/wiki/index.php/Release2_4_0](http://www.kerrighed.org/wiki/index.php/Release2_4_0)) and the updated howto ([http://www.kerrighed.org/wiki/index.php/Installing_Kerrighed_2.4.0](http://www.kerrighed.org/wiki/index.php/Installing_Kerrighed_2.4.0)) for details.

Thanks!

Louis

---

### Post by lrilling on 2009-07-22
Hello,

Although this post is getting old, I would like to fix a few wrong statements.

> **djamu said:**
> 2. Someone mentioned OpenSSI which is nearly dead > know
that Kerrighed re-used most of the OpenSSI + Mosix source.

Kerrighed does not (and never did) borrow any source code from OpenSSI + openMosix.
The only piece of code that could matter is the global scheduler, which algorithm is only
inspired from MOSIX' one (openMosix one should be almost identical to the one of
MOSIX).

> **djamu said:**
>  3. While it's being the most likely candidate to be used
by mere mortals, it lacks some elementary functionality ( aside from the
outdated howto's & documentation ).
Despite the info on their site, some advertised functionality will not ( ever )
be available
[http://www.kerrighed.org/wiki/index.php/Status](http://www.kerrighed.org/wiki/index.php/Status)
Roadmap >november 2008 > thread migration will NOT be implemented any time soon.
This is very misleading,

It's true that thread migration is not on any roadmap yet. The status page does
not mention it anymore. The roadmap was given as we, Kerrighed developers,
wished it to be, but like with any free software project time cannot be
guaranteed.

> **djamu said:**
>  and leaves me with mixed feeling knowing that it is (was)
a EU funded operation, that is now run by Kerlabs.

Kerlabs was actually created one year before EU decided to fund XtreemOS (not
Kerrighed). XtreemOS only planned contributions to Kerrighed, and it's still the
case since Kerlabs entered XtreemOS in June 2009. Before Kerlabs was created,
Kerrighed was funded by various french institutes (INRIA, University of Rennes
1, french department of defense, EDF).

> **djamu said:**
>  I made some inquiries via a major german corporation in
regard to aforementioned feature ( Just to make sure I got an honest
reply).

That's an offending statement, really. Every post on the kerrighed.users mailing
list is considered, especially regarding threads (and you surely noticed it).
The poster's identity is interesting, but not a reason for not daring to reply.

> **djamu said:**
>  I cannot fully disclose the document but in short it reads
that Kerlabs doesn't see any benefit in developing thread migration any further.

This is quite wrong. The reasons for not making it a priority to develop threads
are publicly detailed, and even mentioned in
[http://www.kerrighed.org/wiki/index.php/FAQ](http://www.kerrighed.org/wiki/index.php/FAQ). Kerlabs never stated (and it's
not Kerlabs' opinion) that thread migration does not deserve being developed.

> **djamu said:**
> This because of the small user base that might actually use it ..... (sic)
It must have been a prank if this wasn't a genuine answer. Nothing wrong with
out-of-this-world academics, but really how can a company / management be so
ignorant for not seeing the huge benefits to the community..
About everyone I know ( in 3D ) would hook up their computers to create a mini
cluster(s) ..

And how a guy knowing nothing about Kerrighed internals (the statements above
prove it, sorry) can despise the technical reasons mentioned in
[http://article.gmane.org/gmane.linux.cluster.kerrighed.user/181](http://article.gmane.org/gmane.linux.cluster.kerrighed.user/181). Ask anyone from
the parallel and distributed community about the chances for software DSM (this
is the scientific word for memory sharing in COTS clusters) to provide
performance, and they will confirm what I stated.

> **djamu said:**
> So in short:

Partially because of for-mentioned reasons there's a big chance I'll fork the
project.
Another reason is that my targeted userbase is completely different > I don't
need fancy checkpointing on 500 node clusters / hot adding / removing etc...
Most users of this fork will cluster less then 10 computers ( so no need for
infiniband / myrinet ).

I've already set up a bug tracker so ....

Forking is totally pointless! If you think that you can get people working on
thread migration (and seriously I doubt on this, Kerrighed is already short on
developers), why wouldn't they contribute to the original project? This is in no
way incompatible with other developments, and nobody from the Kerrighed
community ever discouraged contributions.

Really, Kerrighed does need contributors (developers, testers, users' feedack, etc), not pure criticism followed by forking.

Louis

---

### Post by nerdopolis on 2009-07-23
To Artefact: Last digit of the IP or last segment? would 192.168.1.2 and 192.168.1.12 be duplicate nodes?

---

### Post by lrilling on 2009-07-24
> **nerdopolis said:**
> To Artefact: Last digit of the IP or last segment? would 192.168.1.2 and 192.168.1.12 be duplicate nodes?

Least significant byte. 192.168.1.2 and 192.168.1.12 will have node id 2 and 12 respectively.

Louis

---

### Post by ajt on 2009-07-26
> **lrilling said:**
> Hello,

Although this post is getting old, I would like to fix a few wrong statements.
[...]


Hello, Louis.

Thanks very much for your post: I started this thread in an effort to bring together several disconnected discussions about SSI and clustering under Ubuntu, and to promote Kerrighed in a forum read by people involved in education and science. Quite often, discussions that are of practical value to people who are NOT developers are buried on lists and forums that are only read by developers. However, as you've seen on this list, I believe that there is quite a lot of interest from the Ubuntu community about using, rather than developing, Kerrighed in teaching and research.

In a post off-list, you asked me if I intend to use a Kerrighed kernel for my 'biobuntu' live DVD. Indeed I do: I would like to create an Ubuntu-based replacement for ClusterKnoppix, the Knoppix/OpenMosix-based  live CD that can be used to transform a classroom of WIndows PC's into a useful Beowulf cluster. Any help and advice that you can give us would be welcome. I've tried out your existing Kerrighed live CD, and I would like to create an Ubuntu equivalent.

One issue I have with your existing live CD is that it should, clearly, not be booted on a LAN, because it advertises services that conflict with LAN servers. This is not a problem, of course, when booting computers that are on a private LAN. However, for the use-case of converting a classroom of Windows PC's into a Kerrighed cluster it is likely that there will already be servers set up by central IT services and, as is the case at our University, drastic action will be taken to avoid such conflicts happening - Like preventing people from booting the live CD!

Thanks again for joining the EasyUbuntuClustering discussion, and for making Kerrighed available. If you have time, please correct errors on the Ubuntu Kerrighed installation wiki started by Bigjimjams. Alicia will be updating it for Kerrighed 2.4.0 once we get it working on her 'kitcat' cluster at RINH. We also have a prototype Kerrighed cluster called 'santabarbara' built by my colleague Luca in Milan. Our project is to get these two clusters talking using XtreemOS, and Alicia will be in Milan next week helping Luca to install Kerrighed 2.4.0 on 'santabarbara'.

Bye,

  Tony.

---

### Post by ajt on 2009-07-26
> **schreck494 said:**
> The program is already programmed to be run in a parallel environment.  My problem is I have no idea how to set up Open MPI.

Hello, schreck494.

Try using LAM (Local Area Multicomputer) MPI instead
```

aptitude install lam-dev lam-mpidoc

```

You need to create a file lam-bhost.def telling LAM that your node has the number of processors (nn) available in your Kerrighed cluster
```

node-name cpu=nn

```

This file is used by default when you start LAM
```

lamboot
lamnodes

```

Active MPI processes will then be migrated to other nodes by Kerrighed.

Bye,

  Tony.

---

### Post by Merc248 on 2009-07-26
I personally use RHEL 5.3 and OSCAR 5.1rc1 for managing a ten node cluster.  OSCAR seems pretty good for deploying an HPC cluster, but how does Kerrighed stack up against it?

---

### Post by ajt on 2009-07-27
> **Merc248 said:**
> I personally use RHEL 5.3 and OSCAR 5.1rc1 for managing a ten node cluster.  OSCAR seems pretty good for deploying an HPC cluster, but how does Kerrighed stack up against it?

Hello, Merc248.

OSCAR is used to set up clusters of Red-Hat derivative Linux PC's for HPC using MPI, not SSI. There was an SSI-OSCAR project for kerrighed in 2005:

  [http://ssi-oscar.gforge.inria.fr/](http://ssi-oscar.gforge.inria.fr/)

SSI-OSCAR is now part of OSCAR, but it has been dormant for two years:

  [http://svn.oscar.openclustergroup.org/trac/oscar/changeset/6146](http://svn.oscar.openclustergroup.org/trac/oscar/changeset/6146)

I think OSCAR is good, but I don't think it can be used by people who want to build HPC clusters of Ubuntu PC's using an SSI kernel.

There was talk on this forum of using Warewulf/Perceus to deploy Kerrighed under Ubuntu, but I don't know if anyone has actually done it yet?

Our wiki, started by Bigjimjams, documents how to deploy Kerrighed under Ubuntu manually. Of course, it would be great if someone can automate the process of creating an Ubuntu SSI cluster using ideas from the RHEL-based cluster provisioning world. The best system I've seen is Scyld, but you have to pay for that :-)

Bye,

  Tony.

---

### Post by Merc248 on 2009-07-27
Ahhh, so I'm comparing apples and oranges. :)  Forgive my ignorance, I'm still learning a lot about setting up clusters.  I'm not too sure if I can stray too far away from building a cluster with MPI unfortunately.

I wonder, however, if there's a clustering solution on Ubuntu that uses MPI and is about as easy to deal with as OSCAR?  Doesn't seem like OSCAR installs all too cleanly on Debian systems (if it does at all.)

---

### Post by Syndr on 2009-07-27
I am interested in setting up a small cluster using kerrighed.  However, I do have a couple of basic questions about the general system.  

My main use of such a system would be for standard desktop applications.  As such I would need to run the X window system and a full desktop environment of some sort.  How realistic would this be?  Would it significantly impact the performance (assuming older systems)?

My understanding of the file system is that all nodes would use the '/nfsroot/kerrighed' directory on the server as a root filesystem.  So something like X would have to be run on all the nodes, correct?

Also, in order to actually use the cluster, you have to run applications on the nodes themselves, and not the server.  Therefore, to use for a desktop system you would likely want to interact directly with one of the nodes instead of the server?

I have not actually worked with clustering before, and as such want to have a fairly good grasp of how it would work before I attempt to set it up.


Thanks

---

### Post by ajt on 2009-07-28
> **Syndr said:**
> I am interested in setting up a small cluster using kerrighed.  However, I do have a couple of basic questions about the general system.  

My main use of such a system would be for standard desktop applications.  As such I would need to run the X window system and a full desktop environment of some sort.  How realistic would this be?  Would it significantly impact the performance (assuming older systems)?


Hello, Syndr.

I think it's realistic, but most of the documentation I've seen about Kerrighed assumes that the 'head' server (i.e. the DHCP/NFSROOT server) doesn't run the kerrighed kernel. However, that's not how we use it!

You need to compile a stand-alone version of the Kerrighed klernel to run on the head node, and use UNFS3 with ClusterNFS extensions enabled to share the '/' filesystem of the head node with the compute nodes. Alicia will add instructions about how to do this to the wiki. Then, you make the head node a terminal server using FreeNX, and run your desktop apps. from an NX client.

> 
My understanding of the file system is that all nodes would use the '/nfsroot/kerrighed' directory on the server as a root filesystem.  So something like X would have to be run on all the nodes, correct?


Yes, and no - You run X11 apps. on the head node and it migrates them other compute nodes automatically. The X11 server runs on your client PC. If you use UNFS3 as I described, you don't need '/nfsroot/kerrighed' at all, just share the '/' filesystem of the head node with the compute nodes.

> 
Also, in order to actually use the cluster, you have to run applications on the nodes themselves, and not the server.  Therefore, to use for a desktop system you would likely want to interact directly with one of the nodes instead of the server?


That's wrong: An SSI system is not a COW (Collection Of Workstations)!

The whole idea of the Kerrighed kernel is to make your Beowulf cluster look like a large SMP machine to applications. You can, if you want, run apps. on the nodes. However, that does not require an SSI kernel and is really just a pool of computers that you can run your apps. on manually.

> 
I have not actually worked with clustering before, and as such want to have a fairly good grasp of how it would work before I attempt to set it up.


People use computer clusters in many different ways: recently, 'cloud' computing has become popular. However, 'cloud' computing is really just a new name for buying computer time commercially from a computer bureau instead of owning your own computers.

In fact, I think it's a good idea if you seldom use computers but it becomes less and less attractive the more you use and pay for 'cloud' computing. An alternative is to build your own Beowulf cluster, and present it to your users as their own 'cloud'. This is now happening at major computing centres like the NSF, where users want the simplicity of 'cloud' computing, but they don't want to pay commerical 'cloud' fees.

Your idea of using a Kerrighed cluster to run desktop applications is realistic, and it's what I do now with openMosix. We're still testing Kerrighed 2.4.0, but we will upgrade our Beowulf from openMosix as soon as we think it is stable enough for 'production' work.

Good luck with your project, and post here to tell us how you get on.

Bye,

  Tony.

---

### Post by gabrielaca on 2009-07-28
**hello ajt**, i just read the wiki, and correct me if i´m wrong, i can have as many nodes as i can aford following the instructions, since the only diference will be the number of ip adresses and the corresponding hostname; am i correct?


now some questions,  Kerrighed will recognize a multicore procesor? i´m guessing this one is easy, but what about multiprocesor boards, 2 or 4 multicore processors on a single board? :confused:

this install is based on a i386 Ubuntu but can it be done in a 64AMD Ubuntu? what i mean is if something will change drastically in the install process?

thanks.

---

### Post by Syndr on 2009-07-29
Using the server itself as part of the cluster definitely does make sense here.  Not only would you have more power available to the actual cluster, but it would make it easier to interact with the cluster itself, as the server is actually part of it.
How would a stand-alone version of the Kerrighed kernel be different from the kernel run on the nodes?  I would assume that the nodes would run a different kernel than the server, correct?

I'll have to find out more about UNFS3, as I know very little about it.  Instructions would definitely be very helpful here.  Do you have any suggestions on where to look to learn more about it?  How is it different from NFS?

I had not actually considered using something like FreeNX to interact with the cluster, but that would definitely open up some interesting possibilities.

Thanks for your help on this, and I will definitely let you know how it works out.


-Syndr

---

### Post by lrilling on 2009-08-03
> **ajt said:**
>  In a post off-list, you asked me if I intend to use a Kerrighed kernel for my 'biobuntu' live DVD. Indeed I do: I would like to create an Ubuntu-based replacement for ClusterKnoppix, the Knoppix/OpenMosix-based  live CD that can be used to transform a classroom of WIndows PC's into a useful Beowulf cluster. Any help and advice that you can give us would be welcome. I've tried out your existing Kerrighed live CD, and I would like to create an Ubuntu equivalent.

One issue I have with your existing live CD is that it should, clearly, not be booted on a LAN, because it advertises services that conflict with LAN servers. This is not a problem, of course, when booting computers that are on a private LAN. However, for the use-case of converting a classroom of Windows PC's into a Kerrighed cluster it is likely that there will already be servers set up by central IT services and, as is the case at our University, drastic action will be taken to avoid such conflicts happening - Like preventing people from booting the live CD!

I understand your use case, but this is exactly what we did not want to deal with when building the live CD. I suspect that the live CD should be customized for every use case because of the various configurations of other servers on the LAN, which is definitely against the idea of easy testing. Ideas are welcome though!

> **ajt said:**
>  If you have time, please correct errors on the Ubuntu Kerrighed installation wiki started by Bigjimjams. Alicia will be updating it for Kerrighed 2.4.0 once we get it working on her 'kitcat' cluster at RINH.

AFAICS the update for Kerrighed 2.4.0 is the only "error".

> **ajt said:**
>  We also have a prototype Kerrighed cluster called 'santabarbara' built by my colleague Luca in Milan. Our project is to get these two clusters talking using XtreemOS, and Alicia will be in Milan next week helping Luca to install Kerrighed 2.4.0 on 'santabarbara'.

According to some XtreemOS demo I've seen, it should work :) Thanks for the update, we are always interested by users' experiences with Kerrighed.

Louis

---

### Post by ajt on 2009-08-07
> **gabrielaca said:**
> **hello ajt**, i just read the wiki, and correct me if i´m wrong, i can have as many nodes as i can aford following the instructions, since the only diference will be the number of ip adresses and the corresponding hostname; am i correct?


Hello, gabrielaca.

It depends how deep your pockets are ;-)

Kerrighed does have a limit on the number of nodes at 32766 defined in the source file "include/kerrighed/sys/types.h":

```

#define KERRIGHED_MAX_NODES      (1<<NR_BITS_IN_MAX_NODE_ID)        /* Real limit 32766 */

```

> 
now some questions,  Kerrighed will recognize a multicore procesor? i´m guessing this one is easy, but what about multiprocesor boards, 2 or 4 multicore processors on a single board? :confused:


Kerrighed has a limit on the number of CPU's it can support defined in the same file "include/kerrighed/sys/types.h". As you see, the limit is currently set to four CPU's per node (i.e. motherboard):

```

#define KERRIGHED_MAX_CPU_PER_NODE 4
#define KERRIGHED_MAX_CPU (KERRIGHED_MAX_NODES * KERRIGHED_MAX_CPU_PER_NODE)

```

> 
this install is based on a i386 Ubuntu but can it be done in a 64AMD Ubuntu? what i mean is if something will change drastically in the install process?

thanks.

I don't know because we've not tried it yet, but I don't expect it to.

Please post a message here if you try it out, and tell us how you got on.

Bye,

  Tony.

---

### Post by ajt on 2009-08-07
> **Syndr said:**
> Using the server itself as part of the cluster definitely does make sense here.  Not only would you have more power available to the actual cluster, but it would make it easier to interact with the cluster itself, as the server is actually part of it.
How would a stand-alone version of the Kerrighed kernel be different from the kernel run on the nodes?  I would assume that the nodes would run a different kernel than the server, correct?


Hello, Syndr.

Just disable ROOT on NFS:

```

diff .config.old .config
...
< CONFIG_ROOT_NFS=y
---
> # CONFIG_ROOT_NFS is not set

```

> 
I'll have to find out more about UNFS3, as I know very little about it.  Instructions would definitely be very helpful here.  Do you have any suggestions on where to look to learn more about it?  How is it different from NFS?


Alicia will update the wiki soon: UNFS3 is a user-space, as opposed to kernel-space, NFS server. That means it's not as efficient as the kernel NFS server, but it's more flexible for our purposes. UNFS3 adopted the ClusterNFS project, which was based on an older version of UNFS. If you configure UNFS3 with ClusterNFS extensions when it is built, you can get it to read 'tags' with IP addresses etc. and serve particular files to particular hosts, or one set of files to clients, and another locally.

We just use UNFS3 from the Ubuntu repositories, with this config in "/etc/default/unfs3":

```

...
# Cluster extensions
# Enable cluster extensions. When this option is enabled, so-called tagged
# files are handled differently from normal files, making it possible to
# serve different file  contents to different clients for the same filename.
# See tags(7) for a description of tagged files. This option causes a
# performance hit.
CLUSTER_EXTENSION="-c"

```

> 
I had not actually considered using something like FreeNX to interact with the cluster, but that would definitely open up some interesting possibilities.


It does - we use it all the time: Works great over WAN or broadband!

> 
Thanks for your help on this, and I will definitely let you know how it works out.


Please do, because what I hope we can do here is help each other get useful Kerrighed clusters running under Ubuntu.

Bye,

  Tony.

---

### Post by Qwas on 2009-08-08
Hi,how about using ubuntu ltsp as a base system? Afaik it has dhcp,tftp etc... already integrated so i guess its a better startpoint than the basic ubuntu. Right now im trying to install kerrighed this way but im having issues with building kerrighed kernel, so if you know about some precompiled kernel links are welcome.
One more thing, if somebody made it thru the tutorial, is it possible to create working virtual machine from this project and share it?

---

### Post by ajt on 2009-08-08
> **Qwas said:**
> Hi,how about using ubuntu ltsp as a base system? Afaik it has dhcp,tftp etc... already integrated so i guess its a better startpoint than the basic ubuntu. Right now im trying to install kerrighed this way but im having issues with building kerrighed kernel, so if you know about some precompiled kernel links are welcome.
One more thing, if somebody made it thru the tutorial, is it possible to create working virtual machine from this project and share it?

Hello, Qwas.

I have looked at LTSP, but its aims and objectives are different to those of a typical Beowulf cluster: Each LTSP node is intended to be booted diskless as a 'thin' client that runs its programs on the LTSP server. The nodes are 'thin', because they are only used to run what is, to all intents and purposes, an X-terminal.

The advantage of LTSP is that you can reuse old PC's as 'thin' clients instead of buying expensive X-terminals. You still need to buy quite a powerful LTSP server, which runs all the programs for the 'thin' clients. However, this is where Kerrighed might help if you cluster several systems to provide an SSI (Single System Image) LTSP server.

Indeed, it is possible to produce an SSI system using 'fat' workstations each of which run an SSI kernel, and share their resources with each other, but that is very different to LTSP. This is how openMosix has sometimes been used: A group of people agree to share their workstation resources, so that when they are not busy, other people can use their compute resources. However, this model is vulnerable to at least two serious problems: #1 People complain that their workstation is slow because 'everyone' else is sharing it, #2 People switch off their own workstation without telling anyone else and crash the Beowulf cluster.

Conventional wisdom is that you have to use dedicated compute nodes that are under your administrative control to build a useful Beowulf. Of course, you may only have temporary control of the compute nodes for the duration of a transient Beowulf cluster running on a classroom of Windows PC's overnight for example. However, you can ensure that nobody switches off a compute node that your job has been migrated to while the classroom is under your control and dedicated to running the Beowulf cluster.

Bye,

  Tony.

---

### Post by Qwas on 2009-08-09
Hi Tony, thanks for the answer
No i dont mean the clients will be used by people,they will provide computing power,they wont be terminals at all-they will be indeed truly dedicated for the computing. Its just that ltsp and kerrighed share the same idea-nodes(or thin clients) use tftp-ed image from the control computer, and this is exactly the same what ltsp does, right? My idea was about to use the ltsp services which are otherwise complicated to install (dhcp,tftp and so on) and swap the original ltsp client image stored in the system plus tune the configuration files for the kerrighed node image and boot the nodes with it so they become cluster nodes

---

### Post by ajt on 2009-08-09
> **Qwas said:**
> Hi Tony, thanks for the answer
No i dont mean the clients will be used by people,they will provide computing power,they wont be terminals at all-they will be indeed truly dedicated for the computing. Its just that ltsp and kerrighed share the same idea-nodes(or thin clients) use tftp-ed image from the control computer, and this is exactly the same what ltsp does, right? My idea was about to use the ltsp services which are otherwise complicated to install (dhcp,tftp and so on) and swap the original ltsp client image stored in the system plus tune the configuration files for the kerrighed node image and boot the nodes with it so they become cluster nodes

Hello, Qwas.

Well, the main point about LTSP is that the 'thin' clients DON'T provide any computing power, the LTSP server does that and all LTSP applications run on the LTSP server, not the 'thin' clients - That's why they are called 'thin'. All the LTSP clients provide is a GUI for applications that are actually running on the LTSP server.

Kerrighed nodes are 'fat' clients in this sense because they DO provide computing power to the SSI (Single System Image).

Setting up DHCP and TFTP are not really all that complicated, and I think we could probably do everything in a few deb's to create an Ununtu-based Kerrighed Beowulf cluster. The idea you have does make sense but, in my opinion, using LTSP as the basis for setting up DHCP/TFTP for Kerrighed doesn't.

There are several existing projects used for 'provisioning' of compute nodes in HPC: Perceus/Warewulf, for example has already been suggested earlier on this thread:

  [http://www.perceus.org/portal/](http://www.perceus.org/portal/)

I think that Perceus looks like a more promising way forward than trying to customise LTSP, but I can see that Kerrighed might be useful as a way of improving the performance of an LTSP server and in that respect, I do see a useful link between the two projects.

Bye,

  Tony.

---

### Post by lrilling on 2009-08-10
> **ajt said:**
>  Kerrighed has a limit on the number of CPU's it can support defined in the same file "include/kerrighed/sys/types.h". As you see, the limit is currently set to four CPU's per node (i.e. motherboard):

```

#define KERRIGHED_MAX_CPU_PER_NODE 4
#define KERRIGHED_MAX_CPU (KERRIGHED_MAX_NODES * KERRIGHED_MAX_CPU_PER_NODE)

```

There  is actually no valuable reason for this limit, and it was removed on the 2.6.30 port. It wasn't in Kerrighed 2.4 because nobody seemed to complain about it, so that it was forgotten...

Louis

---

### Post by mike919 on 2009-08-10
Hey everyone,

I was working on following the network boot part of this guide with Ubuntu server 8.04.3 and I was running into a problem with the NFS server that a few people might also have encountered earlier in this thread.

Everything would work with the network booting _until_ I rebooted the main node.  At that point the NFS kernel daemon took a long time to start and I would get connection refused errors when the other nodes tried to boot over network.

Checking the /var/log/messages of the main node I found this reason for NFS taking a long time to start:
```

RPC: failed to contact local rpcbind server (errno 5).
rpcbind: server localhost not responding, timed out
```

This presumably also was causing the connection refused errors.  Finally, I found a solution to this here ([http://www.linuxquestions.org/questions/mandriva-30/service-nfs-start-not-working-598581/](http://www.linuxquestions.org/questions/mandriva-30/service-nfs-start-not-working-598581/)).

This was for mandriva, but the ubuntu equivalent was this:

```
sudo apt-get install sysvconfig
sudo service portmap start
sudo service nfs-common start
sudo service nfs-kernel-server start
```

From this point on the network boot worked even after rebooting!  Thanks for the great guide, and hopefully this prevents some frustration for other people.

Mike

---

### Post by count_dracula on 2009-08-11
Thank you all for your messages.  I'm wondering if you could help me with this issue I have.  

This is what I want to achieve:

I do basic multimedia editing for my home videos.  My current distro is Debian Lenny.
Since I have some old computers at home, I'm thinking I can use their CPU power to help me on the editing/rendering.

Would the guide posted by BigJimJams help achieve that? Would Perceus do it?

If any of above ...

My main computer (the one I'm interacting with for video editing) should be the main node -the server- or just a regular node?

[ or if you have a network design that would allow me to achieve my objective that's cool too ]

Thanks in advance.

---

### Post by 1024Jon on 2009-08-12
Solved.  Just in case any1 else has run into the same problem, it appears to be a bug with kerrighed 2.4.  I tried again using 2.3 and everything went fine.

Hey, great guide.  I ran into one snag, and im not really sure where to look to fix it.  Everything works fine until i get to ./configure... then make patch.  When i run make patch i get make: *** No rule to make target `patch'. Stop.  If i continue on skipping over this step everything else seems ok until i boot up the nodes and log in.  When i try to run krgadm, i get krgadm:  error while loading shared libraries:  libkerrighed.so.1:  cannot open shared object file:  No such file or directory.  And ive checked the file is present in /usr/local/lib.  Another thing i noticed is that /etc/kerrighed_nodes was missing.  My questions are, first do you think the problems are related, which i my first thought.  And second any thoughts on the make patch, im not really sure where to look.  Any input would be appreciated.  Thanks

---

### Post by artefact on 2009-08-13
As written on this page [1], 'make patch' is not needed anymore, from version 2.4.0.

Regarding the library issue, you may need to run ldconfig after 'make install' and/or adjust paths in /etc/ld.so.conf.

And, finally, kerrighed_nodes is not really necessary. You can just pass session_id and, eventually, node_id as boot params, session_id being the same for all nodes. node_id can be compute automatically if autonodeid enabled in kernel config CONFIG_KRG_AUTONODEID=y.

The given link has been updated recently to include some notices about the configuration of session_id and node_id.


Regards,
Jean

[1] [http://kerrighed.org/wiki/index.php/Installing_Kerrighed_2.4.0](http://kerrighed.org/wiki/index.php/Installing_Kerrighed_2.4.0)

---

### Post by 1024Jon on 2009-08-13
Thanks, i will recompile with 2.4 and try again.

---

### Post by ajt on 2009-08-17
> **artefact said:**
> 
And, finally, kerrighed_nodes is not really necessary. You can just pass session_id and, eventually, node_id as boot params, session_id being the same for all nodes. node_id can be compute automatically if autonodeid enabled in kernel config CONFIG_KRG_AUTONODEID=y.
[...]


Hello, Jean.

We've found that auto-configuration of Kerrighed does not work properly on the 'head' node unless "kerrighed_nodes" is present. In our case, we use "kerrighed_nodes" because our nodes are sharing the root filesystem of the NFSROOT server using UNFS3 with ClusterNFS extensions enabled.

Bye,

  Tony.

---

### Post by Baleyba on 2009-08-27
HI all!

I'm trying to compile the kerrighed kernel for node.

I'm using the version 2.4.0.
I'm using this tutorial: [https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide) and the official Kerrighed doc for 2.4.0 compilation.

PXE boot is okay but I'm getting problems with kernel compilation.

After launching "make install", at the end I'm getting:


> 
Checking for ELILO...No

Checking for LILO...No

Checking for SILO...No

Checking for PALO...No

Should I make a bootdisk? (y/N) 

WARNING: Your system is probably unbootable now.  After correcting any
problems, rerun this script with the command `mkboot -i'.
make[6]: *** [install] Error 1
make[5]: *** [install] Error 2
make[4]: *** [install] Error 2
make[3]: *** [install] Error 2
make[3]: Leaving directory `/usr/src/kerrighed-2.4.0/kernel'
make[2]: *** [kernel-install] Error 2
make[2]: Leaving directory `/usr/src/kerrighed-2.4.0'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/usr/src/kerrighed-2.4.0'
make: *** [install-recursive] Error 1


I don't understand what happend???

I answer no to the "bootdisk" question and just after that, i'm getting these errors.

After that, if I check generated files: "/lib/modules/2.6.20-krg" is missing...

Please can you help me.

thanks a lot.
Regards,

Bal.

---

### Post by Baleyba on 2009-08-27
Ok I found the solution ;)

I should answer Yes to the bootdisk question ... sorry.

---

### Post by Baleyba on 2009-08-28
Hi,

I'm getting one other problem.

All is installed and working.

I followed tutorial and added CAN_MIGRATE capabilities.
But It doesn't work.

I see all the cpu and all the memory of the cluster. But all the applications I run only use the node CPU.
It become 100% and the others aren't used :(


I tried to run krg_legacy_scheduler but it fails.

I'm getting:
> 
toto@kerrighednode1:~$ krg_legacy_scheduler 
[: 21: ==: unexpected operator
configfs is not mounted on /config, aborting.

configfs has to be mounted on /config.

To do so:
  1. mkdir /config (as root)
  2. Have the following line in /etc/fstab (reboot, or mount it
     manually on each node once it has just been addded):
        configfs /config configfs defaults 0 0

Aborting, please adjust your system configuration and try again.
I don't understand because configfs exists and is mounted:

> 
toto@kerrighednode1:~$ mount
rootfs on / type rootfs (rw)
/dev/root on / type nfs (rw,vers=2,rsize=4096,wsize=4096,hard,nolock,proto=udp,timeo=11,retrans=2,sec=sys,addr=192.168.2.23)
proc on /proc type proc (rw,nosuid,nodev,noexec)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec)
tmpfs on /var/run type tmpfs (rw,nosuid,nodev,noexec)
tmpfs on /var/lock type tmpfs (rw,nosuid,nodev,noexec)
/dev/root on /dev/.static/dev type nfs (rw,vers=2,rsize=4096,wsize=4096,hard,nolock,proto=udp,timeo=11,retrans=2,sec=sys,addr=192.168.2.23)
udev on /dev type tmpfs (rw)
tmpfs on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw)
tmpfs on /var/run type tmpfs (rw,nosuid,nodev,noexec)
tmpfs on /var/lock type tmpfs (rw,nosuid,nodev,noexec)
tmpfs on /var/run type tmpfs (rw,nosuid,nodev,noexec)
tmpfs on /var/lock type tmpfs (rw,nosuid,nodev,noexec)
**configfs on /config type configfs (rw)**
tmpfs on /var/run type tmpfs (rw,nosuid,nodev,noexec)
tmpfs on /var/lock type tmpfs (rw,nosuid,nodev,noexec)




So the first time I mounted "config" directory, kerrighed wrote inside ???

> 
/config/krg_scheduler/probes and
/config/krg_scheduler/schedulers
...


So why doesn't it find this mounted point ??

Thanks for your help.

regards,
Bal.

---

### Post by squallgoh on 2009-09-05
Sorry to hijack this thread, I do not know which forum is appropriate for questions on Beowulf.

I plan to build a server cluster that supports multiple X-Terminals. Would doing it Beowulf style be of any advantage as the applications I'll run are the usual business apps (OpenOffice etc) that are not programmed to take advantage of Parallel computing.

The main reason behind me wanting a cluster instead of a single server machine is for easier scalability (to handle more X-terminals). Is Beowulf a completely wrong direction to look at? In essence I want my server to be easily maintainable and scalable, and to save total computer hardware cost. Main environment is the business desktop: email, web browsing, OpenOffice etc.

Sorry if this is the wrong forum to post in, would the experts kindly point me in the right direction if I happen to post in the wrong place.

Thank you.

---

### Post by jvin248 on 2009-09-06
What you'll want to do is build the server stack with Kerrighed (the 'Beowulf' module you're working on).  Then use LTSP installed on that instance to run the clients.  LTSP is very easy (about five commands, there's a Ubuntu recipe that's in the Ubuntu forums/tutorials or IRC #ltsp - very helpful group).

The hard part is the Kerrighed system (that's discussed in this forum) - it's supposed to combine many machines into a 'single machine' - at least as far as network/users interacting with it - and allow adding/removing server horsepower as the tasks require.  Most other projects, like Beowulf etc, are building parallel machines that require parallel aware software to run them as parallel instances.

My question, since I'm here, is what is the easiest recipe to get the Kerrighed system running on Ubuntu (8.04.3 or 9.04)?  Any links?

---

### Post by ajt on 2009-09-07
> **squallgoh said:**
> Sorry to hijack this thread, I do not know which forum is appropriate for questions on Beowulf.


Hello, squallgoh.

You're not really hijacking this thread - I started it here because I wanted to encourage people involved in education and science to think about how we might put together a *useful* Ubuntu-based Beowulf!

> 
I plan to build a server cluster that supports multiple X-Terminals. Would doing it Beowulf style be of any advantage as the applications I'll run are the usual business apps (OpenOffice etc) that are not programmed to take advantage of Parallel computing.


That depends on what you want to do: I agree with jvin248's reply to your question. LTSP is designed for this sort of thing, but it just might be useful to use a Beowulf as the LTSP 'back-end' server. However, there are lots of other solutions to 'virtualise' user sessions. The main point to grasp is that a Beowulf is normally used to aggregate compute resources, not divide them up virtually...

> 
The main reason behind me wanting a cluster instead of a single server machine is for easier scalability (to handle more X-terminals). Is Beowulf a completely wrong direction to look at? In essence I want my server to be easily maintainable and scalable, and to save total computer hardware cost. Main environment is the business desktop: email, web browsing, OpenOffice etc.


I understand that, and it's a reasonable suggestion to consider using a Beowulf in terms of scalability etc., but you could use e.g. a DNS round-robin as a simple solution to provide a server from a compute farm to each individual client. 

> 
Sorry if this is the wrong forum to post in, would the experts kindly point me in the right direction if I happen to post in the wrong place.


It's not the wrong place to post: Please let us know what you find out about running your desktop applications this way. I'm sure that many other people, myself included, are interested in using an Ubuntu Beowulf as the back end server for LTSP for all the reasons you mention.

Bye,

  Tony.

---

### Post by ajt on 2009-09-07
> **jvin248 said:**
> What you'll want to do is build the server stack with Kerrighed (the 'Beowulf' module you're working on).  Then use LTSP installed on that instance to run the clients.  LTSP is very easy (about five commands, there's a Ubuntu recipe that's in the Ubuntu forums/tutorials or IRC #ltsp - very helpful group).


Hello, jvin248.

I agree, but we don't really know yet how well 'office' type desktop applications will migrate under Kerrighed. My experience with openMosix is that things work quite well, but the delays introduced when processes migrate can be quite long and disruptive to interactive work. This is not a problem if, for example, you're running a computationally intensive task in the background. However, if you have to wait a few seconds for a response to a GUI application because the process is being migrated it makes it very difficult to use.

I've used a GUI application "consed" for editing DNA assembly consensus sequences under openMosix. It works quite well as long as it is either 'locked' to a node or not allowed to migrate(!). If we allow the openMosix load-balancer to move the "consed" GUI app. between different nodes to balance the (dynamic) load then it is not very easy to use. I think the same would be true of 'office' applications (spreadsheets etc.).

> 
[...]
My question, since I'm here, is what is the easiest recipe to get the Kerrighed system running on Ubuntu (8.04.3 or 9.04)?  Any links?


Our own Wiki?

[http://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide]("http://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide")

Bye,

  Tony.

---

### Post by Arceliar on 2009-09-10
> **Baleyba said:**
> 
So why doesn't it find this mounted point ??

Thanks for your help.

regards,
Bal.

I had the same problem here. The krg_legacy_scheduler is calling /bin/sh which is dash on newer [Ubuntu] releases, but the script doesn't seem to be dash friendly.

Editing /usr/bin/krg_legacy_scheduler (or /usr/local/bin, wherever you put it) to begin with
>  #!/bin/bash should do the trick--at least, for me it did.

---

### Post by mo0nykit on 2009-09-25
Hello!

As far as I know, Kerrighed allows the head node to see multiple processors as its own. So here's my situation:

Blender (an open source 3D modeling, animation, rendering package), has options that set the number of threads to start when rendering. So if I have 8 dual-core nodes (16 processors), that means that I can set this option to 16? And will Blender automatically take advantage of those nodes (thanks to the Kerrighed multi-processor abstraction layer)?

Thanks!

---

### Post by nerdopolis on 2009-09-25
Unfortunately I don't think so. Kerrighed 2.4.1 (the current version) supports process migration, but not thread migration. 

There are older experimental versions which do support thread migration, but you lose the added stability/features of the new versions.

They removed thread migration for stability reasons when they wrote version 2.0.0, because they changed their focus from an experimental proof of concept to be a stable product. (I don't even think they even have thread migration in a compile option in 2.4.1 for adventurous types) but they do plan to add it in again if they have enough resources/developers.

---

### Post by mo0nykit on 2009-09-25
**@nerdopolis**

Thanks! So that means I'll have to read up more on render queue managers for now :)

---

### Post by Gun1Dwn on 2009-09-29
Hi, I've been following this thread for a few days now. I have my own kerrighed/ubuntu cluster setup with 3 nodes one is a quad core and the others are single P4's. My problem is that when i start several instances of "yes > /dev/null &" it migrates but only to 4 of the cpu's on the cluster and its not always the same cpu's  sometimes its one of the P4's and 3 of the cores on the quad. its kinda random. I was wondering why it wont migrate to all six? any help is much appriciated. I love the guide and keep up the good work!!

---

### Post by Gun1Dwn on 2009-09-29
i figured it out.... my krgcapset settings are 01067 for -e -d- -i -p . each core on the quad is 2.4Ghz and the P4's are 1.8Ghz. so it took around 10 instances of "yes > /dev/null &" to max them all out. I think this is because when kerrighed tries to migrate the processes it sees that my quad core is about twice as fast so it issues each core two processes to compensate. that comes out to about 10 instances. I really hope they get true thread migration implemented. It would be nice.

---

### Post by nerdopolis on 2009-09-30
How can I setup the master node to also participate in the Kerrighed cluster? Do I just have the master node boot off the Kerrighed kernel?

Thanks in advance.

---

### Post by Gun1Dwn on 2009-09-30
I too am interested in haveing the server as part of the cluster. I see a lot of benefit from having it as part of the cluster rather than separate.

---

### Post by Gun1Dwn on 2009-09-30
Im wondering if it would be possible to have a harddrive in each node with all the nodes mirrored to seem as one drive. this would cut down on the overhead used on a single drive setup if each node had a local resource. I just dont see the sense in having a single drive serve an entire cluster of machines.

---

### Post by ajt on 2009-10-03
> **nerdopolis said:**
> How can I setup the master node to also participate in the Kerrighed cluster? Do I just have the master node boot off the Kerrighed kernel?

Thanks in advance.

Hello, nerdopolis.

Not quite - You have to disable NFSROOT support in the kernel config or it won't boot stand-alone. There are also some issues about files having to be *identical* on all nodes or processes won't migrate. Louis explained that files are re-opened by the kernel on the remote node for reasons of efficiency when a process migrates.

We've got Kerrighed 2.4.0 running OK stand-alone and on PXE-booted nodes.

Bye,

  Tony.

---

### Post by ajt on 2009-10-03
> **Gun1Dwn said:**
> Im wondering if it would be possible to have a harddrive in each node with all the nodes mirrored to seem as one drive. this would cut down on the overhead used on a single drive setup if each node had a local resource. I just dont see the sense in having a single drive serve an entire cluster of machines.

Hello, Gun1Dwn.

HPC 'provisioning' systems replicate/mirror a system image onto a new or replacement node. This can be done via PXE, but many people just use the local disk for swap and /tmp. It's a lot easier to manage a cluster of 'stateless' nodes, and this seems to be a popular compromise.

Sun Microsystems had a 'cache' filesystem that made use of local drives on 'dataless' nodes to store a copy of any files that were accessed from an NFS server. Not mirroring, but replicating files locally where needed.

Bye,

  Tony.

---

### Post by lrilling on 2009-10-06
> **ajt said:**
> Louis explained that files are re-opened by the kernel on the remote node for reasons of efficiency when a process migrates.

To be precise, non-NFS files before migration are not re-opened after migration, but the application could re-open them, and thus requires them to be identical. Conversely, NFS files before migration are re-opened after migration, and thus *must* be NFS files on the target machine.

Louis

---

### Post by lrilling on 2009-10-06
> **ajt said:**
> 
Sun Microsystems had a 'cache' filesystem that made use of local drives on 'dataless' nodes to store a copy of any files that were accessed from an NFS server. Not mirroring, but replicating files locally where needed.


Linux 2.6.30, and thus the Kerrighed port on it, has a similar facility called FS-cache [http://people.redhat.com/dhowells/fscache/FS-Cache.pdf](http://people.redhat.com/dhowells/fscache/FS-Cache.pdf). NFS is FS-Cache aware, but it can be used for OpenAFS and iso9660 too for instance.

Louis

---

### Post by Gun1Dwn on 2009-10-07
The FS-cache is an interesting idea. Ill have to look into it more. Right now I have an issue with bandwidth as I only have 100Mbit cards. I have 2 cards for each node and i was wondering how i can go about using both cards on each machine. I think it would be difficult to do since there is only one root FS and one set of config files from which all the nodes share. Is there a way to do this without having to make a separate root for each node as they did with [microwulf]("http://www.calvin.edu/%7Eadams/research/microwulf/"). and if so would bonding the cards be beneficial?

---

### Post by o0splitpaw0o on 2009-10-25
I been going the Beowulf route recently. Raninto this thread. Notice it's quite for awhile. I been using the notes from [http://www.calvin.edu/~adams/research/microwulf/](http://www.calvin.edu/~adams/research/microwulf/)

They are a bit outdated, but I got the partitions completed & the PXE going. I can get up to TFTP'ing at this time, but can't get it for the life of me to boot off the mentioned mounted node folders to get them kicking in. Kind of puzzled about the pxelinux.0 section. I not sure if the notes were for devices without PXE built in, so don't know if I need to add tis to my tftp boot folder. I copied the kernel copy over.. but I guess I am a bit confused on this..

Hence why I'm admit in learning it. I could use some better information on this. I've been posting my progress on this here [http://www.youtube.com/watch?v=0KwP6hDk2dc](http://www.youtube.com/watch?v=0KwP6hDk2dc)
Thanks!

---

### Post by ajt on 2009-10-26
> **o0splitpaw0o said:**
> I been going the Beowulf route recently. Raninto this thread. Notice it's quite for awhile. I been using the notes from [http://www.calvin.edu/~adams/research/microwulf/](http://www.calvin.edu/~adams/research/microwulf/)


Hello, o0splitpaw0o.

Yes, the thread has been a bit quiet - thanks for posting :-)

> 
They are a bit outdated, but I got the partitions completed & the PXE going. I can get up to TFTP'ing at this time, but can't get it for the life of me to boot off the mentioned mounted node folders to get them kicking in. Kind of puzzled about the pxelinux.0 section. I not sure if the notes were for devices without PXE built in, so don't know if I need to add tis to my tftp boot folder. I copied the kernel copy over.. but I guess I am a bit confused on this..


This is how I've done it: First you need to configure your DHCP server:

```

# @(#)bobcat:/etc/dhcp3/dhcpd.conf  2009-04-02  A.J.Travis

ddns-update-style ad-hoc;

subnet 192.168.0.0 netmask 255.255.255.0 {
	option subnet-mask 255.255.255.0;
	option broadcast-address 192.168.0.255;
	option domain-name-servers 192.168.0.254;
	option routers 192.168.0.254;
	allow booting;
	allow bootp;
	filename "pxelinux.0";
}
[...]

```

Then configure pxelinux:

```

manager@bobcat:/var/lib/tftpboot/pxelinux.cfg$ cat C0A80041
default linux
label linux
	kernel vmlinuz-kerrighed
	append root=/dev/nfs ip=dhcp nfsroot=192.168.0.254:/NFSROOT,v3 node_id=65 session_id=1

```

In this case, the file "C0A80041" is hex for node 192.168.0.65

> 
Hence why I'm admit in learning it. I could use some better information on this. I've been posting my progress on this here [http://www.youtube.com/watch?v=0KwP6hDk2dc](http://www.youtube.com/watch?v=0KwP6hDk2dc)
Thanks!

Just watched it ;-)

Bye,

  Tony.

---

### Post by baggzy on 2009-10-30
In reply to post #213... which I haven't found a solution for anywhere else...
 
> **robasc said:**
> 
I cannot get my nodes to boot up with kerrighed.
 
I keep getting r8169 eth0: link down
 
sending DHCP requests <3>DHCP/BOOTP: reply not for us timed out!
 
and it just keeps looping through this.
 
I believe that my network card does not like the r8169 configured by the kerrighed kernel?
 
If I switch this back to boot from the linux kernel for nfs it boots fine. Not sure what do to from here yet.
 
any clues? Could it be that my chipset is not supported?
 
I had the exact same problem. Days of scouring the internet revealed that there are problems with this family of Realtek cards which have been resolved in kernel 2.6 but not in 2.4. The solution back then was to get a new or patched r8168 driver from Realtek and replace the r8169 module in the initrd image. Unfortunately, since NFS set-up of kerrighed needs the card to work before it can run the initrd, the module can't be loaded. Doh! So the new driver *has* to be compiled into the kernel but doesn't seem to be compatible with that. Or at least I was unable to get that to compile. Nor did any of the other fixes out there help. So I finally resorted to hacking the driver code. And would you believe it, the solution couldn't be simpler! It's quick and dirty, but works:
 
```
 
cd /usr/src/kerrighed-2.4.1/_kernel/drivers/net  #Don't miss out the underscore!
edit r8169.c                                     #Replace "edit" with any editor.

```
 
Search for the text "link down" and you'll find the routine rtl8169_check_link_status:
 
```
 
static void rtl8169_check_link_status(struct net_device *dev,
struct rtl8169_private *tp, void __iomem *ioaddr) {
unsigned long flags;
spin_lock_irqsave(&tp->lock, flags);
if (tp->link_ok(ioaddr)) {
netif_carrier_on(dev);
if (netif_msg_ifup(tp))
printk(KERN_INFO PFX "%s: link up\n", dev->name);
} else {
if (netif_msg_ifdown(tp))
printk(KERN_INFO PFX "%s: link down\n", dev->name);
[COLOR=red]netif_carrier_off[/COLOR](dev);
}
spin_unlock_irqrestore(&tp->lock, flags);
}

```
 
Change [COLOR=red]netif_carrier_off[/COLOR] to netif_carrier_on and then recompile the kernel.
 
That's it! Insanely simple, isn't it? :)

---

### Post by baggzy on 2009-11-02
By the way, it's unclear what the effect of that hack will be on network stability.  Since my Kerrighed system hung every time I brought up the second node I've given up.  This may be the result of the above hack, or may not.  Still, hope it helps!

---

### Post by lrilling on 2009-11-06
> **baggzy said:**
> By the way, it's unclear what the effect of that hack will be on network stability.  Since my Kerrighed system hung every time I brought up the second node I've given up.  This may be the result of the above hack, or may not.  Still, hope it helps!

Wait a minute. You're starting a cluster of one node and then you try adding a second node? Could you describe the sequence of Kerrighed commands that you are using?
I wonder if you are trying to use the not-yet-working-but-being-worked-on dynamic node addition feature of Kerrighed.

Louis

---

### Post by baggzy on 2009-11-06
It's entirely possible I was doing something stupid.  I'd followed the instructions from start to finish, then booted up the head node fine.  Logged in, wandered around a bit, all looked fine.  I ran "top" and could see my quad cores happily waiting for flops to process.  Then I nfs booted the second node, which booted up fine (once I hacked that r8169.c driver), and again wandered around the file system and all appeared to be well.  But then when I ran "top", or "ps", or anything that actually used some cpu, both nodes would hard freeze.  I think I had kerrighed configured to auto-start once 2 nodes were available, so I guess it was running.  Am I being a dolt?

---

### Post by baggzy on 2009-11-06
Sorry - correction!  The "head node" as I called it was also nfs-booted, so I should have referred to it as node1, and the other as node2 in my previous post.  Both nfs-booted off another PC.  (Sorry about that, I've been playing with so many different systems they're all blurring together...)

---

### Post by lrilling on 2009-11-07
> **baggzy said:**
> Sorry - correction!  The "head node" as I called it was also nfs-booted, so I should have referred to it as node1, and the other as node2 in my previous post.  Both nfs-booted off another PC.  (Sorry about that, I've been playing with so many different systems they're all blurring together...)

Ok, I see nothing wrong with your setup. The autostart detail is interesting. Do you have the same issue if you disable autostart (just do not give the parameter), and, after having booted both nodes, run
```
# krgadm cluster start
``` instead?

Anyway, we need kernel logs in order to figure out what went wrong. To collect those logs you could follow this guide [http://www.kerrighed.org/wiki/index.php/KernelLogs](http://www.kerrighed.org/wiki/index.php/KernelLogs).

Thanks,

Louis

---

### Post by baggzy on 2009-11-08
No, I didn't try that.  I'm away this weekend, but I'll set it up again next week and give that a try. If it still fails I'll send the logs...  Would be nice to get it working! :D Cheers.

---

### Post by baggzy on 2009-11-11
Ok, so I have a freshly installed kerrighed system.  Two nodes to start with.  They both nfs boot fine, and run fine when kerrighed isn't running.  But once I start kerrighed they both freeze within about 10 seconds...  The last entries in the kern.log file are:

```

Nov 11 23:01:50 node1 kernel: kerrighed: Cluster start with nodes 101-102 ...
Nov 11 23:01:50 node1 kernel: kerrighed: Cluster start succeeded.
Nov 11 23:01:50 node1 kernel: Kerrighed is running on 2 nodes: 101-102
Nov 11 23:01:50 node1 kernel: successfully registered scheduler_policy_type round_robin_balancer
Nov 11 23:01:50 node1 kernel: successfully registered scheduler_policy_type mosix_load_balancer

```Any ideas?

---

### Post by ajt on 2009-11-12
> **baggzy said:**
> Ok, so I have a freshly installed kerrighed system.  Two nodes to start with.  They both nfs boot fine, and run fine when kerrighed isn't running.  But once I start kerrighed they both freeze within about 10 seconds...  The last entries in the kern.log file are:
[...]
[/code]Any ideas?

Hello, baggzy.

Are you running a 32-bit or 64-bit kernel?

As Louis pointed out recently, the Kerrighed developers are giving priority to the 64-bit kernel and he commends using Kerrighed 2.3.0 for i386/x86_32.

We have two stable 32-bit Kerrighed 2.3.0 clusters running at RINH, but had a nighmare experience trying to upgrade them. We've now gone back to 2.3.0 until we upgrade to 64-bit Kerrighed at the end of our current project, which depends on Bio-Linux 5.0 (32-bit Ubuntu 8.04 LTS).

Bye,

  Tony.

---

### Post by baggzy on 2009-11-12
Hi Tony & Louis,
 
I'm running the 64-bit 2.4.1 kerrighed and linux 2.6.20 kernel on two quad core AMD Phenom 9950's on two similar mainboards (an MSI DKA790GX and an MSI KA790GX). I pretty much followed bigjimjams guide exactly, so that's my basic set-up. Am I the first person to have this freezing problem? :-k Any idea how I can find out what the probem is?
 
Cheers!

---

### Post by ajt on 2009-11-12
> **baggzy said:**
> Hi Tony & Louis,
 
I'm running the 64-bit 2.4.1 kerrighed and linux 2.6.20 kernel on two quad core AMD Phenom 9950's on two similar mainboards (an MSI DKA790GX and an MSI KA790GX). I pretty much followed bigjimjams guide exactly, so that's my basic set-up. Am I the first person to have this freezing problem? :-k Any idea how I can find out what the probem is?
 
Cheers!

Hello, baggzy.

Are you sharing the same NFSROOT for both systems r/w?

Try using two completely separate NFSROOT filesystems or, as I've previously mentioned here, use UNFS3 with 'cluster' extensions enabled to avoid multiple nodes attempting to write to (or create) the same file:

```

aptitude install unfs3

```

HTH,

  Tony.

---

### Post by baggzy on 2009-11-12
No joy I'm afraid.  I installed completely separate nfsroot's for each node but they still freeze when I do "top" or "ps" after starting kerrighed. Weird thing is that I can still ping them, so they are alive.  But I can't log in - they ask for my password, print the login message, then freeze.

---

### Post by ajt on 2009-11-13
> **baggzy said:**
> No joy I'm afraid.  I installed completely separate nfsroot's for each node but they still freeze when I do "top" or "ps" after starting kerrighed. Weird thing is that I can still ping them, so they are alive.  But I can't log in - they ask for my password, print the login message, then freeze.

Hello, baggzy.

I had similar symptoms to this because "udev" isn't working properly in our setup on Alicia's cluster "kitcat" - Seems the tty's devices are not created and the /dev/random|urandom devices were not created either so SSH was broken. My current work-around is:

  login on "kitcat"
  cd /lib/udev/devices
  sudo ./MAKEDEV generic

This directory is then used by diskless clients sharing the root filesystem of "kitcat" to populate /dev in memory at boot time.

Is everything that you need in /dev on your nodes?

If "udev" is working the devices should be created automatically.

Bye,

  Tony.

---

### Post by lrilling on 2009-11-13
> **baggzy said:**
> Ok, so I have a freshly installed kerrighed system.  Two nodes to start with.  They both nfs boot fine, and run fine when kerrighed isn't running.  But once I start kerrighed they both freeze within about 10 seconds...  The last entries in the kern.log file are:

```

Nov 11 23:01:50 node1 kernel: kerrighed: Cluster start with nodes 101-102 ...
Nov 11 23:01:50 node1 kernel: kerrighed: Cluster start succeeded.
Nov 11 23:01:50 node1 kernel: Kerrighed is running on 2 nodes: 101-102
Nov 11 23:01:50 node1 kernel: successfully registered scheduler_policy_type round_robin_balancer
Nov 11 23:01:50 node1 kernel: successfully registered scheduler_policy_type mosix_load_balancer

```Any ideas?

Hi baggzy,

There is nothing wrong with this log. Are the logs of the other node similar?

Thanks,

Louis

---

### Post by renkinjutsu on 2009-11-13
for some reason, i got the impression that the server can share computer power with the cluster, but after reading the wiki on setting up the kerrighed cluster, i realized that the cluster shares  computer power between nodes, and the server is just a server..


Is it possible to turn the cluster into an extention of the server's computer power?

---

### Post by ajt on 2009-11-14
> **renkinjutsu said:**
> for some reason, i got the impression that the server can share computer power with the cluster, but after reading the wiki on setting up the kerrighed cluster, i realized that the cluster shares  computer power between nodes, and the server is just a server..


Is it possible to turn the cluster into an extention of the server's computer power?

Hello, renkinjutsu.

The answer to your question is a definite maybe ;-)

I also want to use Kerrighed, with the 'head' node (i.e. login server) being part of the SSI cluster. However, it's not as easy as setting up a Kerrighed cluster consisting entirely of PXE booted NFSROOT compute nodes.

We have set up a 32-bit Kerrighed 2.3.0 cluster, but it is unstable when the NFS server "kitcat" is included in the cluster. Our "kitcat" cluster is stable when only the PXE-booted nodes form the cluster, but not when "kitcat" itself is a Kerrighed node. We're investigating what the problem is, but it appears to be related to autoconfiguration of Kerrighed nodes.

Look out for my student Alicia posting details about this on the Wiki.

Bye,

  Tony.

---

### Post by baggzy on 2009-11-14
Tony - thanks for the idea.  My /dev directory looked fine but I ran MAKEDEV anyway.  The /lib/udev/devices directory is now fully populated, but the nodes still freeze.

Louis - the logs on the two nodes look like this:

node1 (which I issue "krgadm cluster start" on):
```

Nov 14 01:24:54 node1 kernel: Start loading Kerrighed...
Nov 14 01:24:54 node1 kernel: Init Kerrighed worker(s)...Init Kerrighed low-level framework...
Nov 14 01:24:54 node1 kernel: Init kerrighed syscall mechanism
Nov 14 01:24:54 node1 kernel: Kerrighed tools - init module
Nov 14 01:24:54 node1 kernel: TIPC: Started in network mode
Nov 14 01:24:54 node1 kernel: TIPC: Own node address <1.1.102>, network identity 1
Nov 14 01:24:54 node1 kernel: RPC initialisation done
Nov 14 01:24:54 node1 kernel: Init Kerrighed low-level framework (nodeid 101) : done
Nov 14 01:24:54 node1 kernel: Init Kerrighed distributed services...
Nov 14 01:24:54 node1 kernel: KDDM initialisation : start
Nov 14 01:24:54 node1 kernel: KDDM set init
Nov 14 01:24:54 node1 kernel: KDDM set init : done
Nov 14 01:24:54 node1 kernel: KDDM initialisation done
Nov 14 01:24:54 node1 kernel: KerMM initialisation : start
Nov 14 01:24:54 node1 kernel: KerMM initialisation done
Nov 14 01:24:54 node1 kernel: DVFS initialisation : start
Nov 14 01:24:54 node1 kernel: FAF: initialisation : start
Nov 14 01:24:54 node1 kernel: FAF: initialisation : done
Nov 14 01:24:54 node1 kernel: DVFS initialisation done
Nov 14 01:24:54 node1 kernel: KerIPC initialisation : start
Nov 14 01:24:54 node1 kernel: KerIPC initialisation done
Nov 14 01:24:54 node1 kernel: Proc initialisation: start
Nov 14 01:24:54 node1 kernel: Proc initialisation: done
Nov 14 01:24:54 node1 kernel: EPM initialisation: start
Nov 14 01:24:54 node1 kernel: EPM initialisation: done
Nov 14 01:24:54 node1 kernel: Init Kerrighed distributed services: done
Nov 14 01:24:54 node1 kernel: scheduler initialization succeeded!
Nov 14 01:24:54 node1 kernel: Kerrighed... loaded!
Nov 14 01:24:54 node1 kernel: Try to enable bearer on lo:<5>TIPC: Enabled bearer <eth:lo>, discovery domain <1.1.0>, priority 10
Nov 14 01:24:54 node1 kernel: ok
Nov 14 01:24:54 node1 kernel: Try to enable bearer on eth0:<5>TIPC: Enabled bearer <eth:eth0>, discovery domain <1.1.0>, priority 10
Nov 14 01:24:54 node1 kernel: ok
Nov 14 01:26:06 node1 kernel: TIPC: Established link <1.1.102:eth0-1.1.103:eth0> on network plane B
Nov 14 01:26:39 node1 kernel: kerrighed: Cluster start with nodes 101-102 ...
Nov 14 01:26:39 node1 kernel: kerrighed: Cluster start succeeded.
Nov 14 01:26:39 node1 kernel: Kerrighed is running on 2 nodes: 101-102
Nov 14 01:26:39 node1 kernel: successfully registered scheduler_policy_type round_robin_balancer
Nov 14 01:26:39 node1 kernel: successfully registered scheduler_policy_type mosix_load_balancer

```node2:
```

Nov 14 01:25:50 node2 kernel: Start loading Kerrighed...
Nov 14 01:25:50 node2 kernel: Init Kerrighed worker(s)...Init Kerrighed low-level framework...
Nov 14 01:25:50 node2 kernel: Init kerrighed syscall mechanism
Nov 14 01:25:50 node2 kernel: Kerrighed tools - init module
Nov 14 01:25:50 node2 kernel: TIPC: Started in network mode
Nov 14 01:25:50 node2 kernel: TIPC: Own node address <1.1.103>, network identity 1
Nov 14 01:25:50 node2 kernel: RPC initialisation done
Nov 14 01:25:50 node2 kernel: Init Kerrighed low-level framework (nodeid 102) : done
Nov 14 01:25:50 node2 kernel: Init Kerrighed distributed services...
Nov 14 01:25:50 node2 kernel: KDDM initialisation : start
Nov 14 01:25:50 node2 kernel: KDDM set init
Nov 14 01:25:50 node2 kernel: KDDM set init : done
Nov 14 01:25:50 node2 kernel: KDDM initialisation done
Nov 14 01:25:50 node2 kernel: KerMM initialisation : start
Nov 14 01:25:50 node2 kernel: KerMM initialisation done
Nov 14 01:25:50 node2 kernel: DVFS initialisation : start
Nov 14 01:25:50 node2 kernel: FAF: initialisation : start
Nov 14 01:25:50 node2 kernel: FAF: initialisation : done
Nov 14 01:25:50 node2 kernel: DVFS initialisation done
Nov 14 01:25:50 node2 kernel: KerIPC initialisation : start
Nov 14 01:25:50 node2 kernel: KerIPC initialisation done
Nov 14 01:25:50 node2 kernel: Proc initialisation: start
Nov 14 01:25:50 node2 kernel: Proc initialisation: done
Nov 14 01:25:50 node2 kernel: remove_proc_entry: /proc/meminfo busy, count=1
Nov 14 01:25:50 node2 kernel: remove_proc_entry: /proc/loadavg busy, count=1
Nov 14 01:25:50 node2 kernel: remove_proc_entry: /proc/stat busy, count=1
Nov 14 01:25:50 node2 kernel: remove_proc_entry: /proc/uptime busy, count=1
Nov 14 01:25:50 node2 kernel: EPM initialisation: start
Nov 14 01:25:50 node2 kernel: EPM initialisation: done
Nov 14 01:25:50 node2 kernel: Init Kerrighed distributed services: done
Nov 14 01:25:50 node2 kernel: scheduler initialization succeeded!
Nov 14 01:25:50 node2 kernel: Kerrighed... loaded!
Nov 14 01:25:50 node2 kernel: Try to enable bearer on lo:<5>TIPC: Enabled bearer <eth:lo>, discovery domain <1.1.0>, priority 10
Nov 14 01:25:50 node2 kernel: ok
Nov 14 01:25:50 node2 kernel: Try to enable bearer on eth0:<5>TIPC: Enabled bearer <eth:eth0>, discovery domain <1.1.0>, priority 10
Nov 14 01:25:50 node2 kernel: ok
Nov 14 01:25:50 node2 kernel: TIPC: Established link <1.1.103:eth0-1.1.102:eth0> on network plane B
Nov 14 01:25:51 node2 kernel: de_put: deferred delete of uptime
Nov 14 01:25:51 node2 kernel: de_put: deferred delete of loadavg
Nov 14 01:25:51 node2 kernel: de_put: deferred delete of stat
Nov 14 01:25:51 node2 kernel: de_put: deferred delete of meminfo
Nov 14 01:26:24 node2 kernel: Kerrighed is running on 2 nodes: 101-102
Nov 14 01:26:24 node2 kernel: successfully registered scheduler_policy_type round_robin_balancer
Nov 14 01:26:24 node2 kernel: successfully registered scheduler_policy_type mosix_load_balancer

```Are those proc messages on node2 a problem?

Out of interest, am I correct that there's no way to NFS-boot the nodes using a module (i.e. not compiled-in) driver for my network card?  I've had a stab at it (editing initramfs.conf, creating an initrd.img, recompiling the kernel without the driver built-in, and reboot) but IP-config always reports that there are no network cards...

I'm wondering if the problem is that comms problems are causing a freeze like the one people report when a node goes down.  I've hacked the r8169.c driver so it doesn't issue false "link down" messages to the kernel, but there may be other issues too.  I can download the official driver from Realtec but can only install it as a module... ](*,)

---

### Post by lrilling on 2009-11-14
> **baggzy said:**
> 
Louis - the logs on the two nodes look like this:

node1 (which I issue "krgadm cluster start" on):
```

Nov 14 01:24:54 node1 kernel: Start loading Kerrighed...
Nov 14 01:24:54 node1 kernel: Init Kerrighed worker(s)...Init Kerrighed low-level framework...
Nov 14 01:24:54 node1 kernel: Init kerrighed syscall mechanism
Nov 14 01:24:54 node1 kernel: Kerrighed tools - init module
Nov 14 01:24:54 node1 kernel: TIPC: Started in network mode
Nov 14 01:24:54 node1 kernel: TIPC: Own node address <1.1.102>, network identity 1
Nov 14 01:24:54 node1 kernel: RPC initialisation done
Nov 14 01:24:54 node1 kernel: Init Kerrighed low-level framework (nodeid 101) : done
Nov 14 01:24:54 node1 kernel: Init Kerrighed distributed services...
Nov 14 01:24:54 node1 kernel: KDDM initialisation : start
Nov 14 01:24:54 node1 kernel: KDDM set init
Nov 14 01:24:54 node1 kernel: KDDM set init : done
Nov 14 01:24:54 node1 kernel: KDDM initialisation done
Nov 14 01:24:54 node1 kernel: KerMM initialisation : start
Nov 14 01:24:54 node1 kernel: KerMM initialisation done
Nov 14 01:24:54 node1 kernel: DVFS initialisation : start
Nov 14 01:24:54 node1 kernel: FAF: initialisation : start
Nov 14 01:24:54 node1 kernel: FAF: initialisation : done
Nov 14 01:24:54 node1 kernel: DVFS initialisation done
Nov 14 01:24:54 node1 kernel: KerIPC initialisation : start
Nov 14 01:24:54 node1 kernel: KerIPC initialisation done
Nov 14 01:24:54 node1 kernel: Proc initialisation: start
Nov 14 01:24:54 node1 kernel: Proc initialisation: done
Nov 14 01:24:54 node1 kernel: EPM initialisation: start
Nov 14 01:24:54 node1 kernel: EPM initialisation: done
Nov 14 01:24:54 node1 kernel: Init Kerrighed distributed services: done
Nov 14 01:24:54 node1 kernel: scheduler initialization succeeded!
Nov 14 01:24:54 node1 kernel: Kerrighed... loaded!
Nov 14 01:24:54 node1 kernel: Try to enable bearer on lo:<5>TIPC: Enabled bearer <eth:lo>, discovery domain <1.1.0>, priority 10
Nov 14 01:24:54 node1 kernel: ok
Nov 14 01:24:54 node1 kernel: Try to enable bearer on eth0:<5>TIPC: Enabled bearer <eth:eth0>, discovery domain <1.1.0>, priority 10
Nov 14 01:24:54 node1 kernel: ok
Nov 14 01:26:06 node1 kernel: TIPC: Established link <1.1.102:eth0-1.1.103:eth0> on network plane B
Nov 14 01:26:39 node1 kernel: kerrighed: Cluster start with nodes 101-102 ...
Nov 14 01:26:39 node1 kernel: kerrighed: Cluster start succeeded.
Nov 14 01:26:39 node1 kernel: Kerrighed is running on 2 nodes: 101-102
Nov 14 01:26:39 node1 kernel: successfully registered scheduler_policy_type round_robin_balancer
Nov 14 01:26:39 node1 kernel: successfully registered scheduler_policy_type mosix_load_balancer

```node2:
```

Nov 14 01:25:50 node2 kernel: Start loading Kerrighed...
Nov 14 01:25:50 node2 kernel: Init Kerrighed worker(s)...Init Kerrighed low-level framework...
Nov 14 01:25:50 node2 kernel: Init kerrighed syscall mechanism
Nov 14 01:25:50 node2 kernel: Kerrighed tools - init module
Nov 14 01:25:50 node2 kernel: TIPC: Started in network mode
Nov 14 01:25:50 node2 kernel: TIPC: Own node address <1.1.103>, network identity 1
Nov 14 01:25:50 node2 kernel: RPC initialisation done
Nov 14 01:25:50 node2 kernel: Init Kerrighed low-level framework (nodeid 102) : done
Nov 14 01:25:50 node2 kernel: Init Kerrighed distributed services...
Nov 14 01:25:50 node2 kernel: KDDM initialisation : start
Nov 14 01:25:50 node2 kernel: KDDM set init
Nov 14 01:25:50 node2 kernel: KDDM set init : done
Nov 14 01:25:50 node2 kernel: KDDM initialisation done
Nov 14 01:25:50 node2 kernel: KerMM initialisation : start
Nov 14 01:25:50 node2 kernel: KerMM initialisation done
Nov 14 01:25:50 node2 kernel: DVFS initialisation : start
Nov 14 01:25:50 node2 kernel: FAF: initialisation : start
Nov 14 01:25:50 node2 kernel: FAF: initialisation : done
Nov 14 01:25:50 node2 kernel: DVFS initialisation done
Nov 14 01:25:50 node2 kernel: KerIPC initialisation : start
Nov 14 01:25:50 node2 kernel: KerIPC initialisation done
Nov 14 01:25:50 node2 kernel: Proc initialisation: start
Nov 14 01:25:50 node2 kernel: Proc initialisation: done
Nov 14 01:25:50 node2 kernel: remove_proc_entry: /proc/meminfo busy, count=1
Nov 14 01:25:50 node2 kernel: remove_proc_entry: /proc/loadavg busy, count=1
Nov 14 01:25:50 node2 kernel: remove_proc_entry: /proc/stat busy, count=1
Nov 14 01:25:50 node2 kernel: remove_proc_entry: /proc/uptime busy, count=1
Nov 14 01:25:50 node2 kernel: EPM initialisation: start
Nov 14 01:25:50 node2 kernel: EPM initialisation: done
Nov 14 01:25:50 node2 kernel: Init Kerrighed distributed services: done
Nov 14 01:25:50 node2 kernel: scheduler initialization succeeded!
Nov 14 01:25:50 node2 kernel: Kerrighed... loaded!
Nov 14 01:25:50 node2 kernel: Try to enable bearer on lo:<5>TIPC: Enabled bearer <eth:lo>, discovery domain <1.1.0>, priority 10
Nov 14 01:25:50 node2 kernel: ok
Nov 14 01:25:50 node2 kernel: Try to enable bearer on eth0:<5>TIPC: Enabled bearer <eth:eth0>, discovery domain <1.1.0>, priority 10
Nov 14 01:25:50 node2 kernel: ok
Nov 14 01:25:50 node2 kernel: TIPC: Established link <1.1.103:eth0-1.1.102:eth0> on network plane B
Nov 14 01:25:51 node2 kernel: de_put: deferred delete of uptime
Nov 14 01:25:51 node2 kernel: de_put: deferred delete of loadavg
Nov 14 01:25:51 node2 kernel: de_put: deferred delete of stat
Nov 14 01:25:51 node2 kernel: de_put: deferred delete of meminfo
Nov 14 01:26:24 node2 kernel: Kerrighed is running on 2 nodes: 101-102
Nov 14 01:26:24 node2 kernel: successfully registered scheduler_policy_type round_robin_balancer
Nov 14 01:26:24 node2 kernel: successfully registered scheduler_policy_type mosix_load_balancer

```Are those proc messages on node2 a problem?


I don't think so. Those messages look very rare (I personally saw one only once, and it was not on a machine I was controlling), and just report about an unexpected but safely handled case. They are absolutely not Kerrighed-specific actually, although they were triggered by the initialization phase of Kerrighed.
  
> **baggzy said:**
> 
Out of interest, am I correct that there's no way to NFS-boot the nodes using a module (i.e. not compiled-in) driver for my network card?  I've had a stab at it (editing initramfs.conf, creating an initrd.img, recompiling the kernel without the driver built-in, and reboot) but IP-config always reports that there are no network cards...


You're not correct ;) It is possible to NFS-boot with a NIC driver in loadable module, but this requires to :

[LIST=1]
[*]use an initramfs (otherwise the kernel will try and fail to boot on NFS before any module can be loaded);
[*]configure the initramfs for NFS booting;
[*]ensure that the NIC driver is included in the initramfs;
[*]ensure that initramfs' udev is able to automatically load the NIC driver's module, or hack the initramfs to make it load the driver manually;
[*]Assign static node ids to your Kerrighed nodes (use the node_id= kernel command line parameter), since autoconfiguration only works when the NIC driver is built in the kernel.
[/LIST]
  > **baggzy said:**
> 
I'm wondering if the problem is that comms problems are causing a freeze like the one people report when a node goes down.  I've hacked the r8169.c driver so it doesn't issue false "link down" messages to the kernel, but there may be other issues too.  I can download the official driver from Realtec but can only install it as a module... ](*,)

This maybe the cause of your problem.
You should definitely try a module that is reported to work correctly with 2.6.20 kernels.

Louis

---

### Post by baggzy on 2009-11-14
Nope, *still* no joy.  I have fully functioning comms\\:D/, but the nodes still freeze. ](*,)

For anyone who has the same network driver problem...

I followed the instructions in nerdopolis' post #210, but when I unpacked the initrd.img file the module wasn't in there. :-k Strange. So I manually hacked it in there as follows:

- Go to [http://www.realtek.com.tw](http://www.realtek.com.tw) website and find the driver for your network card.
- Download the driver to /nfsroot/kerrighed/usr/src/
- Expand the tarball.  Note the [driver directory] created.
- cd [driver directory]. Following the instructions in the readme to make it.
- Note the name of the [driver].ko created (in the src directory).

- Recompile the kernel *without* the offending driver.
- Create an initrd as follows:

```

chroot /nfsroot/kerrighed
mkinitramfs -o /boot/initrd.img-2.6.20-krg 2.6.20-krg
exit
cp /nfsroot/kerrighed/boot/initrd.img-2.6.20-krg /var/lib/tftpboot/
cp /nfsroot/kerrighed/boot/vmlinuz-2.6.20-krg /var/lib/tftpboot/

```Edit your boot setup (/var/lib/tftpboot/pxelinux.cfg/default or whatever):

```

LABEL linux
KERNEL vmlinuz-2.6.20-krg
APPEND root=/dev/nfs initrd=initrd.img-2.6.20-krg nfsroot=192.168.1.1:/nfsroot/kerrighed ip=dhcp rw

```Hack the initrd:

```

mkdir /nfsroot/kerrighed/boot/initrd # The directory to unpack the initrd into.
cd /nfsroot/kerrighed/boot/initrd
gunzip < ../initrd.img-2.6.20-krg | cpio -i # Unpack the initrd.
cp /nfsroot/kerrighed/usr/src/[driver directory]/src/[driver].ko lib/modules/2.6.20-krg/kernel/drivers/net/
find | cpio -H newc -o | gzip -9 > ../initrd.img-2.6.20-krg # Repack the initrd.

```Apologies for any mistakes or typo's, since I'm writing this from memory.

Now if I could just get kerrighed to stop freezing... [-o<  Any other ideas welcome!

---

### Post by baggzy on 2009-11-14
Oh, and after all that copy the initrd again:

```
cp /nfsroot/kerrighed/boot/vmlinuz-2.6.20-krg /var/lib/tftpboot/
```

Can't believe I forgot to say that. #-o

---

### Post by renkinjutsu on 2009-11-15
> **ajt said:**
> Hello, renkinjutsu.

The answer to your question is a definite maybe ;-)

I also want to use Kerrighed, with the 'head' node (i.e. login server) being part of the SSI cluster. However, it's not as easy as setting up a Kerrighed cluster consisting entirely of PXE booted NFSROOT compute nodes.

We have set up a 32-bit Kerrighed 2.3.0 cluster, but it is unstable when the NFS server "kitcat" is included in the cluster. Our "kitcat" cluster is stable when only the PXE-booted nodes form the cluster, but not when "kitcat" itself is a Kerrighed node. We're investigating what the problem is, but it appears to be related to autoconfiguration of Kerrighed nodes.

Look out for my student Alicia posting details about this on the Wiki.

Bye,

  Tony.

thanks ajt, it reassures me when i know that a bunch of smart people are going after the same thing i want. I can't wait to hear the results of your experiments!!

---

### Post by lrilling on 2009-11-15
> **baggzy said:**
> Nope, *still* no joy.  I have fully functioning comms\\:D/, but the nodes still freeze. ](*,)


Ok. Maybe producing some debugging kernel logs could help. After observing the freeze, could you trigger sys request 'w' on both nodes and send the resulting logs?

Two ways of triggering sysrq:
- Hit Alt+SysRq+w on the machine's keyboard,
- (as root on the machine) echo w > /proc/sysrq-trigger

Thanks,

Louis

---

### Post by baggzy on 2009-11-15
Hi Louis,

Thanks for the suggestion.  Here are the logs...

node1:
```

Nov 15 15:23:45 node1 kernel: Start loading Kerrighed...
Nov 15 15:23:45 node1 kernel: Init Kerrighed worker(s)...Init Kerrighed low-level framework...
Nov 15 15:23:45 node1 kernel: Init kerrighed syscall mechanism
Nov 15 15:23:45 node1 kernel: Kerrighed tools - init module
Nov 15 15:23:45 node1 kernel: TIPC: Started in network mode
Nov 15 15:23:45 node1 kernel: TIPC: Own node address <1.1.102>, network identity 0
Nov 15 15:23:45 node1 kernel: RPC initialisation done
Nov 15 15:23:45 node1 kernel: Init Kerrighed low-level framework (nodeid 101) : done
Nov 15 15:23:45 node1 kernel: Init Kerrighed distributed services...
Nov 15 15:23:45 node1 kernel: KDDM initialisation : start
Nov 15 15:23:45 node1 kernel: KDDM set init
Nov 15 15:23:45 node1 kernel: KDDM set init : done
Nov 15 15:23:45 node1 kernel: KDDM initialisation done
Nov 15 15:23:45 node1 kernel: KerMM initialisation : start
Nov 15 15:23:45 node1 kernel: KerMM initialisation done
Nov 15 15:23:45 node1 kernel: DVFS initialisation : start
Nov 15 15:23:45 node1 kernel: FAF: initialisation : start
Nov 15 15:23:45 node1 kernel: FAF: initialisation : done
Nov 15 15:23:45 node1 kernel: DVFS initialisation done
Nov 15 15:23:45 node1 kernel: KerIPC initialisation : start
Nov 15 15:23:45 node1 kernel: KerIPC initialisation done
Nov 15 15:23:45 node1 kernel: Proc initialisation: start
Nov 15 15:23:45 node1 kernel: Proc initialisation: done
Nov 15 15:23:45 node1 kernel: EPM initialisation: start
Nov 15 15:23:45 node1 kernel: EPM initialisation: done
Nov 15 15:23:45 node1 kernel: Init Kerrighed distributed services: done
Nov 15 15:23:45 node1 kernel: scheduler initialization succeeded!
Nov 15 15:23:45 node1 kernel: Kerrighed... loaded!
Nov 15 15:23:45 node1 kernel: Try to enable bearer on lo:<5>TIPC: Enabled bearer <eth:lo>, discovery domain <1.1.0>, priority 10
Nov 15 15:23:45 node1 kernel: ok
Nov 15 15:23:45 node1 kernel: Try to enable bearer on eth0:<5>TIPC: Enabled bearer <eth:eth0>, discovery domain <1.1.0>, priority 10
Nov 15 15:23:45 node1 kernel: ok
Nov 15 15:23:45 node1 /usr/sbin/cron[425726071]: (CRON) INFO (pidfile fd = 3)
Nov 15 15:23:45 node1 /usr/sbin/cron[425726072]: (CRON) STARTUP (fork ok)
Nov 15 15:23:45 node1 /usr/sbin/cron[425726072]: (CRON) INFO (Running @reboot jobs)
Nov 15 15:24:05 node1 ntpd[425726012]: getaddrinfo: "::1" invalid host address, ignored
Nov 15 15:24:05 node1 ntpd[425726107]: signal_no_reset: signal 17 had flags 4000000
Nov 15 15:24:27 node1 ntpd_initres[425726107]: host name not found: ntp.ubuntu.com
Nov 15 15:24:27 node1 ntpd_initres[425726107]: couldn't resolve `ntp.ubuntu.com', giving up on it
Nov 15 15:28:08 node1 kernel: TIPC: Established link <1.1.102:eth0-1.1.103:eth0> on network plane B
Nov 15 15:28:42 node1 kernel: kerrighed: Cluster start with nodes 101-102 ...
Nov 15 15:28:42 node1 kernel: kerrighed: Cluster start succeeded.
Nov 15 15:28:42 node1 kernel: Kerrighed is running on 2 nodes: 101-102
Nov 15 15:28:42 node1 kernel: successfully registered scheduler_policy_type round_robin_balancer
Nov 15 15:28:42 node1 kernel: successfully registered scheduler_policy_type mosix_load_balancer
Nov 15 15:31:04 node1 kernel: SysRq : Show Blocked State
Nov 15 15:31:04 node1 kernel: 
Nov 15 15:31:04 node1 kernel: free                        sibling
Nov 15 15:31:04 node1 kernel: task                 PC        stack   pid father child younger older
Nov 15 15:31:04 node1 kernel: krg/0         D ffff810006122810     0 425726035     19       425726036 425724008 (L-TLB)
Nov 15 15:31:04 node1 kernel: ffff81011c7e1cc0 0000000000000046 0000000000000000 0000000000000001
Nov 15 15:31:04 node1 kernel: ffff810006122810 ffff81011c7e1c70 ffff81011d7ac2c0 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: Call Trace:
Nov 15 15:31:04 node1 kernel: [<ffffffff8804f8ec>] :kerrighed:__rpc_emergency_send_buf_alloc+0x55/0xb0
Nov 15 15:31:04 node1 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:31:04 node1 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:31:04 node1 kernel: [<ffffffff88023574>] :kerrighed:__get_kddm_obj_entry+0x4d/0xb7
Nov 15 15:31:04 node1 kernel: [<ffffffff8802b460>] :kerrighed:generic_kddm_grab_object+0x418/0x619
Nov 15 15:31:04 node1 kernel: [<ffffffff88045d61>] :kerrighed:update_dynamic_node_info_worker+0x0/0x30b
Nov 15 15:31:04 node1 kernel: [<ffffffff88045d8d>] :kerrighed:update_dynamic_node_info_worker+0x2c/0x30b
Nov 15 15:31:04 node1 kernel: [<ffffffff8804606c>] :kerrighed:update_dynamic_cpu_info_worker+0x0/0x16c
Nov 15 15:31:04 node1 kernel: [<ffffffff80244eeb>] run_workqueue+0x95/0x16a
Nov 15 15:31:04 node1 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:31:04 node1 kernel: [<ffffffff802459d6>] worker_thread+0x191/0x1e8
Nov 15 15:31:04 node1 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:31:04 node1 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:31:04 node1 kernel: [<ffffffff80245845>] worker_thread+0x0/0x1e8
Nov 15 15:31:04 node1 kernel: [<ffffffff802489c6>] kthread+0x125/0x163
Nov 15 15:31:04 node1 kernel: [<ffffffff8020a7b8>] child_rip+0xa/0x12
Nov 15 15:31:04 node1 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:31:04 node1 kernel: [<ffffffff802488a1>] kthread+0x0/0x163
Nov 15 15:31:04 node1 kernel: [<ffffffff8020a7ae>] child_rip+0x0/0x12
Nov 15 15:31:04 node1 kernel: 
Nov 15 15:31:04 node1 kernel: krg_legacy_sc D ffff810006122810     0 425726130 425726055                     (NOTLB)
Nov 15 15:31:04 node1 kernel: ffff81011bcedd58 0000000000000082 0000000000000000 0000000000000000
Nov 15 15:31:04 node1 kernel: ffffffff8066c950 ffff81011bcedd08 0000000000000000 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: Call Trace:
Nov 15 15:31:04 node1 kernel: [<ffffffff8804f8ec>] :kerrighed:__rpc_emergency_send_buf_alloc+0x55/0xb0
Nov 15 15:31:04 node1 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:31:04 node1 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:31:04 node1 kernel: [<ffffffff8802b2ad>] :kerrighed:generic_kddm_grab_object+0x265/0x619
Nov 15 15:31:04 node1 kernel: [<ffffffff8801e5ab>] :kerrighed:hashed_string_list_lock_hash+0x5f/0x66
Nov 15 15:31:04 node1 kernel: [<ffffffff8801f102>] :kerrighed:global_config_attr_store_begin+0x4e/0x69
Nov 15 15:31:04 node1 kernel: [<ffffffff8802234e>] :kerrighed:pset_attribute_store+0x28/0x86
Nov 15 15:31:04 node1 kernel: [<ffffffff802b7354>] configfs_write_file+0xc1/0xea
Nov 15 15:31:04 node1 kernel: [<ffffffff8027b2b0>] vfs_write+0xad/0x172
Nov 15 15:31:04 node1 kernel: [<ffffffff8027b9b0>] sys_write+0x88/0xc3
Nov 15 15:31:04 node1 kernel: [<ffffffff80209a0e>] system_call+0x7e/0x83
Nov 15 15:31:04 node1 kernel: 
Nov 15 15:31:04 node1 kernel: top           D ffff810006122810     0 425726203 425726096                     (NOTLB)
Nov 15 15:31:04 node1 kernel: ffff81011c233c38 0000000000000082 0000000000000000 0000000000000000
Nov 15 15:31:04 node1 kernel: 00000000f000000d ffff81011c233be8 ffff81011fc30000 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: Call Trace:
Nov 15 15:31:04 node1 kernel: [<ffffffff802a0b68>] inotify_d_instantiate+0x3e/0x68
Nov 15 15:31:04 node1 kernel: [<ffffffff802adc4d>] proc_root_lookup+0x12/0x30
Nov 15 15:31:04 node1 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:31:04 node1 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:31:04 node1 kernel: [<ffffffff88023574>] :kerrighed:__get_kddm_obj_entry+0x4d/0xb7
Nov 15 15:31:04 node1 kernel: [<ffffffff8802add5>] :kerrighed:generic_kddm_get_object+0x1f9/0x333
Nov 15 15:31:04 node1 kernel: [<ffffffff88045403>] :kerrighed:show_stat+0x1d1/0x56d
Nov 15 15:31:04 node1 kernel: [<ffffffff8026a742>] remove_vma_list+0x61/0x6e
Nov 15 15:31:04 node1 kernel: [<ffffffff80279407>] __get_unused_fd+0x66/0xe7
Nov 15 15:31:04 node1 kernel: [<ffffffff8029343a>] seq_read+0x105/0x28b
Nov 15 15:31:04 node1 kernel: [<ffffffff8027b41f>] vfs_read+0xaa/0x16e
Nov 15 15:31:04 node1 kernel: [<ffffffff8027b8ed>] sys_read+0x88/0xc3
Nov 15 15:31:04 node1 kernel: [<ffffffff80209a0e>] system_call+0x7e/0x83
Nov 15 15:31:04 node1 kernel: 

```node2:
```

Nov 15 15:27:53 node2 kernel: Start loading Kerrighed...
Nov 15 15:27:53 node2 kernel: Init Kerrighed worker(s)...Init Kerrighed low-level framework...
Nov 15 15:27:53 node2 kernel: Init kerrighed syscall mechanism
Nov 15 15:27:53 node2 kernel: Kerrighed tools - init module
Nov 15 15:27:53 node2 kernel: TIPC: Started in network mode
Nov 15 15:27:53 node2 kernel: TIPC: Own node address <1.1.103>, network identity 0
Nov 15 15:27:53 node2 kernel: RPC initialisation done
Nov 15 15:27:53 node2 kernel: Init Kerrighed low-level framework (nodeid 102) : done
Nov 15 15:27:53 node2 kernel: Init Kerrighed distributed services...
Nov 15 15:27:53 node2 kernel: KDDM initialisation : start
Nov 15 15:27:53 node2 kernel: KDDM set init
Nov 15 15:27:53 node2 kernel: KDDM set init : done
Nov 15 15:27:53 node2 kernel: KDDM initialisation done
Nov 15 15:27:53 node2 kernel: KerMM initialisation : start
Nov 15 15:27:53 node2 kernel: KerMM initialisation done
Nov 15 15:27:53 node2 kernel: DVFS initialisation : start
Nov 15 15:27:53 node2 kernel: FAF: initialisation : start
Nov 15 15:27:53 node2 kernel: FAF: initialisation : done
Nov 15 15:27:53 node2 kernel: DVFS initialisation done
Nov 15 15:27:53 node2 kernel: KerIPC initialisation : start
Nov 15 15:27:53 node2 kernel: KerIPC initialisation done
Nov 15 15:27:53 node2 kernel: Proc initialisation: start
Nov 15 15:27:53 node2 kernel: Proc initialisation: done
Nov 15 15:27:53 node2 kernel: EPM initialisation: start
Nov 15 15:27:53 node2 kernel: EPM initialisation: done
Nov 15 15:27:53 node2 kernel: Init Kerrighed distributed services: done
Nov 15 15:27:53 node2 kernel: scheduler initialization succeeded!
Nov 15 15:27:53 node2 kernel: Kerrighed... loaded!
Nov 15 15:27:53 node2 kernel: Try to enable bearer on lo:<5>TIPC: Enabled bearer <eth:lo>, discovery domain <1.1.0>, priority 10
Nov 15 15:27:53 node2 kernel: ok
Nov 15 15:27:53 node2 kernel: Try to enable bearer on eth0:<5>TIPC: Enabled bearer <eth:eth0>, discovery domain <1.1.0>, priority 10
Nov 15 15:27:53 node2 kernel: ok
Nov 15 15:27:53 node2 kernel: TIPC: Established link <1.1.103:eth0-1.1.102:eth0> on network plane B
Nov 15 15:27:53 node2 /usr/sbin/cron[429920407]: (CRON) INFO (pidfile fd = 3)
Nov 15 15:27:53 node2 /usr/sbin/cron[429920408]: (CRON) STARTUP (fork ok)
Nov 15 15:27:53 node2 /usr/sbin/cron[429920408]: (CRON) INFO (Running @reboot jobs)
Nov 15 15:28:13 node2 ntpd[429920348]: getaddrinfo: "::1" invalid host address, ignored
Nov 15 15:28:13 node2 ntpd[429920431]: signal_no_reset: signal 17 had flags 4000000
Nov 15 15:28:27 node2 kernel: Kerrighed is running on 2 nodes: 101-102
Nov 15 15:28:27 node2 kernel: successfully registered scheduler_policy_type round_robin_balancer
Nov 15 15:28:27 node2 kernel: successfully registered scheduler_policy_type mosix_load_balancer
Nov 15 15:28:35 node2 ntpd_initres[429920431]: host name not found: ntp.ubuntu.com
Nov 15 15:28:35 node2 ntpd_initres[429920431]: couldn't resolve `ntp.ubuntu.com', giving up on it
Nov 15 15:37:12 node2 kernel: input: AT Translated Set 2 keyboard as /class/input/input3
Nov 15 15:37:41 node2 kernel: SysRq : Show Blocked State
Nov 15 15:37:41 node2 kernel: 
Nov 15 15:37:41 node2 kernel: free                        sibling
Nov 15 15:37:41 node2 kernel: task                 PC        stack   pid father child younger older
Nov 15 15:37:41 node2 kernel: udevd         D ffff810006122810     0 429918484      1       429919452    19 (NOTLB)
Nov 15 15:37:41 node2 kernel: ffff81011e0cfc38 0000000000000082 0000000000000000 0000000000000000
Nov 15 15:37:41 node2 kernel: ffff81011e430e40 ffff81011e0cfbe8 ffffffff806bbc70 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: Call Trace:
Nov 15 15:37:41 node2 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:37:41 node2 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:37:41 node2 kernel: [<ffffffff88023574>] :kerrighed:__get_kddm_obj_entry+0x4d/0xb7
Nov 15 15:37:41 node2 kernel: [<ffffffff8802add5>] :kerrighed:generic_kddm_get_object+0x1f9/0x333
Nov 15 15:37:41 node2 kernel: [<ffffffff88045403>] :kerrighed:show_stat+0x1d1/0x56d
Nov 15 15:37:41 node2 kernel: [<ffffffff80279407>] __get_unused_fd+0x66/0xe7
Nov 15 15:37:41 node2 kernel: [<ffffffff8029343a>] seq_read+0x105/0x28b
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b41f>] vfs_read+0xaa/0x16e
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b8ed>] sys_read+0x88/0xc3
Nov 15 15:37:41 node2 kernel: [<ffffffff80209a0e>] system_call+0x7e/0x83
Nov 15 15:37:41 node2 kernel: 
Nov 15 15:37:41 node2 kernel: krg/0         D ffff810006122810     0 429920372     19       429920373 429918320 (L-TLB)
Nov 15 15:37:41 node2 kernel: ffff81011c145cc0 0000000000000046 0000000000000000 ffffffff807324a0
Nov 15 15:37:41 node2 kernel: 000000018066c950 ffff81011c145c70 0000000000000080 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: Call Trace:
Nov 15 15:37:41 node2 kernel: [<ffffffff8804f8ec>] :kerrighed:__rpc_emergency_send_buf_alloc+0x55/0xb0
Nov 15 15:37:41 node2 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:37:41 node2 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:37:41 node2 kernel: [<ffffffff88023574>] :kerrighed:__get_kddm_obj_entry+0x4d/0xb7
Nov 15 15:37:41 node2 kernel: [<ffffffff8802b460>] :kerrighed:generic_kddm_grab_object+0x418/0x619
Nov 15 15:37:41 node2 kernel: [<ffffffff88045d61>] :kerrighed:update_dynamic_node_info_worker+0x0/0x30b
Nov 15 15:37:41 node2 kernel: [<ffffffff88045d8d>] :kerrighed:update_dynamic_node_info_worker+0x2c/0x30b
Nov 15 15:37:41 node2 kernel: [<ffffffff80244eeb>] run_workqueue+0x95/0x16a
Nov 15 15:37:41 node2 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:37:41 node2 kernel: [<ffffffff802459d6>] worker_thread+0x191/0x1e8
Nov 15 15:37:41 node2 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:37:41 node2 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:37:41 node2 kernel: [<ffffffff80245845>] worker_thread+0x0/0x1e8
Nov 15 15:37:41 node2 kernel: [<ffffffff802489c6>] kthread+0x125/0x163
Nov 15 15:37:41 node2 kernel: [<ffffffff8020a7b8>] child_rip+0xa/0x12
Nov 15 15:37:41 node2 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:37:41 node2 kernel: [<ffffffff802488a1>] kthread+0x0/0x163
Nov 15 15:37:41 node2 kernel: [<ffffffff8020a7ae>] child_rip+0x0/0x12
Nov 15 15:37:41 node2 kernel: 
Nov 15 15:37:41 node2 kernel: top           D ffff810006122810     0 429920494 429920292                     (NOTLB)
Nov 15 15:37:41 node2 kernel: ffff81011eeebc38 0000000000000082 0000000000000000 0000000000000000
Nov 15 15:37:41 node2 kernel: 00000000f000000d ffff81011eeebbe8 ffff81011fc30000 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: Call Trace:
Nov 15 15:37:41 node2 kernel: [<ffffffff8804f8ec>] :kerrighed:__rpc_emergency_send_buf_alloc+0x55/0xb0
Nov 15 15:37:41 node2 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:37:41 node2 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:37:41 node2 kernel: [<ffffffff8802add5>] :kerrighed:generic_kddm_get_object+0x1f9/0x333
Nov 15 15:37:41 node2 kernel: [<ffffffff88045403>] :kerrighed:show_stat+0x1d1/0x56d
Nov 15 15:37:41 node2 kernel: [<ffffffff8026a742>] remove_vma_list+0x61/0x6e
Nov 15 15:37:41 node2 kernel: [<ffffffff80279407>] __get_unused_fd+0x66/0xe7
Nov 15 15:37:41 node2 kernel: [<ffffffff8029343a>] seq_read+0x105/0x28b
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b41f>] vfs_read+0xaa/0x16e
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b8ed>] sys_read+0x88/0xc3
Nov 15 15:37:41 node2 kernel: [<ffffffff80209a0e>] system_call+0x7e/0x83
Nov 15 15:37:41 node2 kernel: 
Nov 15 15:37:41 node2 kernel: bash          D ffff810006122810     0 429920495 429920430                     (NOTLB)
Nov 15 15:37:41 node2 kernel: ffff81011c175b48 0000000000000082 0000000000000000 ffff81011e6858b0
Nov 15 15:37:41 node2 kernel: ffff81011f3f0d80 ffff81011c175af8 000000001f498dc0 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: Call Trace:
Nov 15 15:37:41 node2 kernel: [<ffffffff80281ec9>] do_lookup+0x63/0x1ae
Nov 15 15:37:41 node2 kernel: [<ffffffff80283e83>] __link_path_walk+0xc43/0xd9a
Nov 15 15:37:41 node2 kernel: [<ffffffff804dc824>] xprt_timer+0x0/0x7f
Nov 15 15:37:41 node2 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:37:41 node2 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:37:41 node2 kernel: [<ffffffff88023574>] :kerrighed:__get_kddm_obj_entry+0x4d/0xb7
Nov 15 15:37:41 node2 kernel: [<ffffffff8802add5>] :kerrighed:generic_kddm_get_object+0x1f9/0x333
Nov 15 15:37:41 node2 kernel: [<ffffffff88044e9f>] :kerrighed:show_meminfo+0x105/0x498
Nov 15 15:37:41 node2 kernel: [<ffffffff8028b02e>] dput+0x21/0x14c
Nov 15 15:37:41 node2 kernel: [<ffffffff80283e83>] __link_path_walk+0xc43/0xd9a
Nov 15 15:37:41 node2 kernel: [<ffffffff8025f309>] get_page_from_freelist+0x2bf/0x348
Nov 15 15:37:41 node2 kernel: [<ffffffff8028ed75>] mntput_no_expire+0x1c/0x76
Nov 15 15:37:41 node2 kernel: [<ffffffff8029343a>] seq_read+0x105/0x28b
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b41f>] vfs_read+0xaa/0x16e
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b8ed>] sys_read+0x88/0xc3
Nov 15 15:37:41 node2 kernel: [<ffffffff80209a0e>] system_call+0x7e/0x83
Nov 15 15:37:41 node2 kernel: 

```

---

### Post by lrilling on 2009-11-16
> **baggzy said:**
> Hi Louis,

Thanks for the suggestion.  Here are the logs...

node1:
```

Nov 15 15:23:45 node1 kernel: Start loading Kerrighed...
Nov 15 15:23:45 node1 kernel: Init Kerrighed worker(s)...Init Kerrighed low-level framework...
Nov 15 15:23:45 node1 kernel: Init kerrighed syscall mechanism
Nov 15 15:23:45 node1 kernel: Kerrighed tools - init module
Nov 15 15:23:45 node1 kernel: TIPC: Started in network mode
Nov 15 15:23:45 node1 kernel: TIPC: Own node address <1.1.102>, network identity 0
Nov 15 15:23:45 node1 kernel: RPC initialisation done
Nov 15 15:23:45 node1 kernel: Init Kerrighed low-level framework (nodeid 101) : done
Nov 15 15:23:45 node1 kernel: Init Kerrighed distributed services...
Nov 15 15:23:45 node1 kernel: KDDM initialisation : start
Nov 15 15:23:45 node1 kernel: KDDM set init
Nov 15 15:23:45 node1 kernel: KDDM set init : done
Nov 15 15:23:45 node1 kernel: KDDM initialisation done
Nov 15 15:23:45 node1 kernel: KerMM initialisation : start
Nov 15 15:23:45 node1 kernel: KerMM initialisation done
Nov 15 15:23:45 node1 kernel: DVFS initialisation : start
Nov 15 15:23:45 node1 kernel: FAF: initialisation : start
Nov 15 15:23:45 node1 kernel: FAF: initialisation : done
Nov 15 15:23:45 node1 kernel: DVFS initialisation done
Nov 15 15:23:45 node1 kernel: KerIPC initialisation : start
Nov 15 15:23:45 node1 kernel: KerIPC initialisation done
Nov 15 15:23:45 node1 kernel: Proc initialisation: start
Nov 15 15:23:45 node1 kernel: Proc initialisation: done
Nov 15 15:23:45 node1 kernel: EPM initialisation: start
Nov 15 15:23:45 node1 kernel: EPM initialisation: done
Nov 15 15:23:45 node1 kernel: Init Kerrighed distributed services: done
Nov 15 15:23:45 node1 kernel: scheduler initialization succeeded!
Nov 15 15:23:45 node1 kernel: Kerrighed... loaded!
Nov 15 15:23:45 node1 kernel: Try to enable bearer on lo:<5>TIPC: Enabled bearer <eth:lo>, discovery domain <1.1.0>, priority 10
Nov 15 15:23:45 node1 kernel: ok
Nov 15 15:23:45 node1 kernel: Try to enable bearer on eth0:<5>TIPC: Enabled bearer <eth:eth0>, discovery domain <1.1.0>, priority 10
Nov 15 15:23:45 node1 kernel: ok
Nov 15 15:23:45 node1 /usr/sbin/cron[425726071]: (CRON) INFO (pidfile fd = 3)
Nov 15 15:23:45 node1 /usr/sbin/cron[425726072]: (CRON) STARTUP (fork ok)
Nov 15 15:23:45 node1 /usr/sbin/cron[425726072]: (CRON) INFO (Running @reboot jobs)
Nov 15 15:24:05 node1 ntpd[425726012]: getaddrinfo: "::1" invalid host address, ignored
Nov 15 15:24:05 node1 ntpd[425726107]: signal_no_reset: signal 17 had flags 4000000
Nov 15 15:24:27 node1 ntpd_initres[425726107]: host name not found: ntp.ubuntu.com
Nov 15 15:24:27 node1 ntpd_initres[425726107]: couldn't resolve `ntp.ubuntu.com', giving up on it
Nov 15 15:28:08 node1 kernel: TIPC: Established link <1.1.102:eth0-1.1.103:eth0> on network plane B
Nov 15 15:28:42 node1 kernel: kerrighed: Cluster start with nodes 101-102 ...
Nov 15 15:28:42 node1 kernel: kerrighed: Cluster start succeeded.
Nov 15 15:28:42 node1 kernel: Kerrighed is running on 2 nodes: 101-102
Nov 15 15:28:42 node1 kernel: successfully registered scheduler_policy_type round_robin_balancer
Nov 15 15:28:42 node1 kernel: successfully registered scheduler_policy_type mosix_load_balancer
Nov 15 15:31:04 node1 kernel: SysRq : Show Blocked State
Nov 15 15:31:04 node1 kernel: 
Nov 15 15:31:04 node1 kernel: free                        sibling
Nov 15 15:31:04 node1 kernel: task                 PC        stack   pid father child younger older
Nov 15 15:31:04 node1 kernel: krg/0         D ffff810006122810     0 425726035     19       425726036 425724008 (L-TLB)
Nov 15 15:31:04 node1 kernel: ffff81011c7e1cc0 0000000000000046 0000000000000000 0000000000000001
Nov 15 15:31:04 node1 kernel: ffff810006122810 ffff81011c7e1c70 ffff81011d7ac2c0 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: Call Trace:
Nov 15 15:31:04 node1 kernel: [<ffffffff8804f8ec>] :kerrighed:__rpc_emergency_send_buf_alloc+0x55/0xb0
Nov 15 15:31:04 node1 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:31:04 node1 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:31:04 node1 kernel: [<ffffffff88023574>] :kerrighed:__get_kddm_obj_entry+0x4d/0xb7
Nov 15 15:31:04 node1 kernel: [<ffffffff8802b460>] :kerrighed:generic_kddm_grab_object+0x418/0x619
Nov 15 15:31:04 node1 kernel: [<ffffffff88045d61>] :kerrighed:update_dynamic_node_info_worker+0x0/0x30b
Nov 15 15:31:04 node1 kernel: [<ffffffff88045d8d>] :kerrighed:update_dynamic_node_info_worker+0x2c/0x30b
Nov 15 15:31:04 node1 kernel: [<ffffffff8804606c>] :kerrighed:update_dynamic_cpu_info_worker+0x0/0x16c
Nov 15 15:31:04 node1 kernel: [<ffffffff80244eeb>] run_workqueue+0x95/0x16a
Nov 15 15:31:04 node1 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:31:04 node1 kernel: [<ffffffff802459d6>] worker_thread+0x191/0x1e8
Nov 15 15:31:04 node1 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:31:04 node1 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:31:04 node1 kernel: [<ffffffff80245845>] worker_thread+0x0/0x1e8
Nov 15 15:31:04 node1 kernel: [<ffffffff802489c6>] kthread+0x125/0x163
Nov 15 15:31:04 node1 kernel: [<ffffffff8020a7b8>] child_rip+0xa/0x12
Nov 15 15:31:04 node1 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:31:04 node1 kernel: [<ffffffff802488a1>] kthread+0x0/0x163
Nov 15 15:31:04 node1 kernel: [<ffffffff8020a7ae>] child_rip+0x0/0x12
Nov 15 15:31:04 node1 kernel: 
Nov 15 15:31:04 node1 kernel: krg_legacy_sc D ffff810006122810     0 425726130 425726055                     (NOTLB)
Nov 15 15:31:04 node1 kernel: ffff81011bcedd58 0000000000000082 0000000000000000 0000000000000000
Nov 15 15:31:04 node1 kernel: ffffffff8066c950 ffff81011bcedd08 0000000000000000 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: Call Trace:
Nov 15 15:31:04 node1 kernel: [<ffffffff8804f8ec>] :kerrighed:__rpc_emergency_send_buf_alloc+0x55/0xb0
Nov 15 15:31:04 node1 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:31:04 node1 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:31:04 node1 kernel: [<ffffffff8802b2ad>] :kerrighed:generic_kddm_grab_object+0x265/0x619
Nov 15 15:31:04 node1 kernel: [<ffffffff8801e5ab>] :kerrighed:hashed_string_list_lock_hash+0x5f/0x66
Nov 15 15:31:04 node1 kernel: [<ffffffff8801f102>] :kerrighed:global_config_attr_store_begin+0x4e/0x69
Nov 15 15:31:04 node1 kernel: [<ffffffff8802234e>] :kerrighed:pset_attribute_store+0x28/0x86
Nov 15 15:31:04 node1 kernel: [<ffffffff802b7354>] configfs_write_file+0xc1/0xea
Nov 15 15:31:04 node1 kernel: [<ffffffff8027b2b0>] vfs_write+0xad/0x172
Nov 15 15:31:04 node1 kernel: [<ffffffff8027b9b0>] sys_write+0x88/0xc3
Nov 15 15:31:04 node1 kernel: [<ffffffff80209a0e>] system_call+0x7e/0x83
Nov 15 15:31:04 node1 kernel: 
Nov 15 15:31:04 node1 kernel: top           D ffff810006122810     0 425726203 425726096                     (NOTLB)
Nov 15 15:31:04 node1 kernel: ffff81011c233c38 0000000000000082 0000000000000000 0000000000000000
Nov 15 15:31:04 node1 kernel: 00000000f000000d ffff81011c233be8 ffff81011fc30000 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:31:04 node1 kernel: Call Trace:
Nov 15 15:31:04 node1 kernel: [<ffffffff802a0b68>] inotify_d_instantiate+0x3e/0x68
Nov 15 15:31:04 node1 kernel: [<ffffffff802adc4d>] proc_root_lookup+0x12/0x30
Nov 15 15:31:04 node1 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:31:04 node1 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:31:04 node1 kernel: [<ffffffff88023574>] :kerrighed:__get_kddm_obj_entry+0x4d/0xb7
Nov 15 15:31:04 node1 kernel: [<ffffffff8802add5>] :kerrighed:generic_kddm_get_object+0x1f9/0x333
Nov 15 15:31:04 node1 kernel: [<ffffffff88045403>] :kerrighed:show_stat+0x1d1/0x56d
Nov 15 15:31:04 node1 kernel: [<ffffffff8026a742>] remove_vma_list+0x61/0x6e
Nov 15 15:31:04 node1 kernel: [<ffffffff80279407>] __get_unused_fd+0x66/0xe7
Nov 15 15:31:04 node1 kernel: [<ffffffff8029343a>] seq_read+0x105/0x28b
Nov 15 15:31:04 node1 kernel: [<ffffffff8027b41f>] vfs_read+0xaa/0x16e
Nov 15 15:31:04 node1 kernel: [<ffffffff8027b8ed>] sys_read+0x88/0xc3
Nov 15 15:31:04 node1 kernel: [<ffffffff80209a0e>] system_call+0x7e/0x83
Nov 15 15:31:04 node1 kernel: 

```node2:
```

Nov 15 15:27:53 node2 kernel: Start loading Kerrighed...
Nov 15 15:27:53 node2 kernel: Init Kerrighed worker(s)...Init Kerrighed low-level framework...
Nov 15 15:27:53 node2 kernel: Init kerrighed syscall mechanism
Nov 15 15:27:53 node2 kernel: Kerrighed tools - init module
Nov 15 15:27:53 node2 kernel: TIPC: Started in network mode
Nov 15 15:27:53 node2 kernel: TIPC: Own node address <1.1.103>, network identity 0
Nov 15 15:27:53 node2 kernel: RPC initialisation done
Nov 15 15:27:53 node2 kernel: Init Kerrighed low-level framework (nodeid 102) : done
Nov 15 15:27:53 node2 kernel: Init Kerrighed distributed services...
Nov 15 15:27:53 node2 kernel: KDDM initialisation : start
Nov 15 15:27:53 node2 kernel: KDDM set init
Nov 15 15:27:53 node2 kernel: KDDM set init : done
Nov 15 15:27:53 node2 kernel: KDDM initialisation done
Nov 15 15:27:53 node2 kernel: KerMM initialisation : start
Nov 15 15:27:53 node2 kernel: KerMM initialisation done
Nov 15 15:27:53 node2 kernel: DVFS initialisation : start
Nov 15 15:27:53 node2 kernel: FAF: initialisation : start
Nov 15 15:27:53 node2 kernel: FAF: initialisation : done
Nov 15 15:27:53 node2 kernel: DVFS initialisation done
Nov 15 15:27:53 node2 kernel: KerIPC initialisation : start
Nov 15 15:27:53 node2 kernel: KerIPC initialisation done
Nov 15 15:27:53 node2 kernel: Proc initialisation: start
Nov 15 15:27:53 node2 kernel: Proc initialisation: done
Nov 15 15:27:53 node2 kernel: EPM initialisation: start
Nov 15 15:27:53 node2 kernel: EPM initialisation: done
Nov 15 15:27:53 node2 kernel: Init Kerrighed distributed services: done
Nov 15 15:27:53 node2 kernel: scheduler initialization succeeded!
Nov 15 15:27:53 node2 kernel: Kerrighed... loaded!
Nov 15 15:27:53 node2 kernel: Try to enable bearer on lo:<5>TIPC: Enabled bearer <eth:lo>, discovery domain <1.1.0>, priority 10
Nov 15 15:27:53 node2 kernel: ok
Nov 15 15:27:53 node2 kernel: Try to enable bearer on eth0:<5>TIPC: Enabled bearer <eth:eth0>, discovery domain <1.1.0>, priority 10
Nov 15 15:27:53 node2 kernel: ok
Nov 15 15:27:53 node2 kernel: TIPC: Established link <1.1.103:eth0-1.1.102:eth0> on network plane B
Nov 15 15:27:53 node2 /usr/sbin/cron[429920407]: (CRON) INFO (pidfile fd = 3)
Nov 15 15:27:53 node2 /usr/sbin/cron[429920408]: (CRON) STARTUP (fork ok)
Nov 15 15:27:53 node2 /usr/sbin/cron[429920408]: (CRON) INFO (Running @reboot jobs)
Nov 15 15:28:13 node2 ntpd[429920348]: getaddrinfo: "::1" invalid host address, ignored
Nov 15 15:28:13 node2 ntpd[429920431]: signal_no_reset: signal 17 had flags 4000000
Nov 15 15:28:27 node2 kernel: Kerrighed is running on 2 nodes: 101-102
Nov 15 15:28:27 node2 kernel: successfully registered scheduler_policy_type round_robin_balancer
Nov 15 15:28:27 node2 kernel: successfully registered scheduler_policy_type mosix_load_balancer
Nov 15 15:28:35 node2 ntpd_initres[429920431]: host name not found: ntp.ubuntu.com
Nov 15 15:28:35 node2 ntpd_initres[429920431]: couldn't resolve `ntp.ubuntu.com', giving up on it
Nov 15 15:37:12 node2 kernel: input: AT Translated Set 2 keyboard as /class/input/input3
Nov 15 15:37:41 node2 kernel: SysRq : Show Blocked State
Nov 15 15:37:41 node2 kernel: 
Nov 15 15:37:41 node2 kernel: free                        sibling
Nov 15 15:37:41 node2 kernel: task                 PC        stack   pid father child younger older
Nov 15 15:37:41 node2 kernel: udevd         D ffff810006122810     0 429918484      1       429919452    19 (NOTLB)
Nov 15 15:37:41 node2 kernel: ffff81011e0cfc38 0000000000000082 0000000000000000 0000000000000000
Nov 15 15:37:41 node2 kernel: ffff81011e430e40 ffff81011e0cfbe8 ffffffff806bbc70 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: Call Trace:
Nov 15 15:37:41 node2 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:37:41 node2 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:37:41 node2 kernel: [<ffffffff88023574>] :kerrighed:__get_kddm_obj_entry+0x4d/0xb7
Nov 15 15:37:41 node2 kernel: [<ffffffff8802add5>] :kerrighed:generic_kddm_get_object+0x1f9/0x333
Nov 15 15:37:41 node2 kernel: [<ffffffff88045403>] :kerrighed:show_stat+0x1d1/0x56d
Nov 15 15:37:41 node2 kernel: [<ffffffff80279407>] __get_unused_fd+0x66/0xe7
Nov 15 15:37:41 node2 kernel: [<ffffffff8029343a>] seq_read+0x105/0x28b
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b41f>] vfs_read+0xaa/0x16e
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b8ed>] sys_read+0x88/0xc3
Nov 15 15:37:41 node2 kernel: [<ffffffff80209a0e>] system_call+0x7e/0x83
Nov 15 15:37:41 node2 kernel: 
Nov 15 15:37:41 node2 kernel: krg/0         D ffff810006122810     0 429920372     19       429920373 429918320 (L-TLB)
Nov 15 15:37:41 node2 kernel: ffff81011c145cc0 0000000000000046 0000000000000000 ffffffff807324a0
Nov 15 15:37:41 node2 kernel: 000000018066c950 ffff81011c145c70 0000000000000080 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: Call Trace:
Nov 15 15:37:41 node2 kernel: [<ffffffff8804f8ec>] :kerrighed:__rpc_emergency_send_buf_alloc+0x55/0xb0
Nov 15 15:37:41 node2 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:37:41 node2 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:37:41 node2 kernel: [<ffffffff88023574>] :kerrighed:__get_kddm_obj_entry+0x4d/0xb7
Nov 15 15:37:41 node2 kernel: [<ffffffff8802b460>] :kerrighed:generic_kddm_grab_object+0x418/0x619
Nov 15 15:37:41 node2 kernel: [<ffffffff88045d61>] :kerrighed:update_dynamic_node_info_worker+0x0/0x30b
Nov 15 15:37:41 node2 kernel: [<ffffffff88045d8d>] :kerrighed:update_dynamic_node_info_worker+0x2c/0x30b
Nov 15 15:37:41 node2 kernel: [<ffffffff80244eeb>] run_workqueue+0x95/0x16a
Nov 15 15:37:41 node2 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:37:41 node2 kernel: [<ffffffff802459d6>] worker_thread+0x191/0x1e8
Nov 15 15:37:41 node2 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:37:41 node2 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:37:41 node2 kernel: [<ffffffff80245845>] worker_thread+0x0/0x1e8
Nov 15 15:37:41 node2 kernel: [<ffffffff802489c6>] kthread+0x125/0x163
Nov 15 15:37:41 node2 kernel: [<ffffffff8020a7b8>] child_rip+0xa/0x12
Nov 15 15:37:41 node2 kernel: [<ffffffff8024871c>] keventd_create_kthread+0x0/0x65
Nov 15 15:37:41 node2 kernel: [<ffffffff802488a1>] kthread+0x0/0x163
Nov 15 15:37:41 node2 kernel: [<ffffffff8020a7ae>] child_rip+0x0/0x12
Nov 15 15:37:41 node2 kernel: 
Nov 15 15:37:41 node2 kernel: top           D ffff810006122810     0 429920494 429920292                     (NOTLB)
Nov 15 15:37:41 node2 kernel: ffff81011eeebc38 0000000000000082 0000000000000000 0000000000000000
Nov 15 15:37:41 node2 kernel: 00000000f000000d ffff81011eeebbe8 ffff81011fc30000 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: Call Trace:
Nov 15 15:37:41 node2 kernel: [<ffffffff8804f8ec>] :kerrighed:__rpc_emergency_send_buf_alloc+0x55/0xb0
Nov 15 15:37:41 node2 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:37:41 node2 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:37:41 node2 kernel: [<ffffffff8802add5>] :kerrighed:generic_kddm_get_object+0x1f9/0x333
Nov 15 15:37:41 node2 kernel: [<ffffffff88045403>] :kerrighed:show_stat+0x1d1/0x56d
Nov 15 15:37:41 node2 kernel: [<ffffffff8026a742>] remove_vma_list+0x61/0x6e
Nov 15 15:37:41 node2 kernel: [<ffffffff80279407>] __get_unused_fd+0x66/0xe7
Nov 15 15:37:41 node2 kernel: [<ffffffff8029343a>] seq_read+0x105/0x28b
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b41f>] vfs_read+0xaa/0x16e
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b8ed>] sys_read+0x88/0xc3
Nov 15 15:37:41 node2 kernel: [<ffffffff80209a0e>] system_call+0x7e/0x83
Nov 15 15:37:41 node2 kernel: 
Nov 15 15:37:41 node2 kernel: bash          D ffff810006122810     0 429920495 429920430                     (NOTLB)
Nov 15 15:37:41 node2 kernel: ffff81011c175b48 0000000000000082 0000000000000000 ffff81011e6858b0
Nov 15 15:37:41 node2 kernel: ffff81011f3f0d80 ffff81011c175af8 000000001f498dc0 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: ffffffff807321d0 ffffffff8072f910 ffffffff8072f910 ffffffff8072f910
Nov 15 15:37:41 node2 kernel: Call Trace:
Nov 15 15:37:41 node2 kernel: [<ffffffff80281ec9>] do_lookup+0x63/0x1ae
Nov 15 15:37:41 node2 kernel: [<ffffffff80283e83>] __link_path_walk+0xc43/0xd9a
Nov 15 15:37:41 node2 kernel: [<ffffffff804dc824>] xprt_timer+0x0/0x7f
Nov 15 15:37:41 node2 kernel: [<ffffffff88022e4c>] :kerrighed:__sleep_on_kddm_obj+0x12e/0x243
Nov 15 15:37:41 node2 kernel: [<ffffffff8022c5bc>] default_wake_function+0x0/0xe
Nov 15 15:37:41 node2 kernel: [<ffffffff88023574>] :kerrighed:__get_kddm_obj_entry+0x4d/0xb7
Nov 15 15:37:41 node2 kernel: [<ffffffff8802add5>] :kerrighed:generic_kddm_get_object+0x1f9/0x333
Nov 15 15:37:41 node2 kernel: [<ffffffff88044e9f>] :kerrighed:show_meminfo+0x105/0x498
Nov 15 15:37:41 node2 kernel: [<ffffffff8028b02e>] dput+0x21/0x14c
Nov 15 15:37:41 node2 kernel: [<ffffffff80283e83>] __link_path_walk+0xc43/0xd9a
Nov 15 15:37:41 node2 kernel: [<ffffffff8025f309>] get_page_from_freelist+0x2bf/0x348
Nov 15 15:37:41 node2 kernel: [<ffffffff8028ed75>] mntput_no_expire+0x1c/0x76
Nov 15 15:37:41 node2 kernel: [<ffffffff8029343a>] seq_read+0x105/0x28b
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b41f>] vfs_read+0xaa/0x16e
Nov 15 15:37:41 node2 kernel: [<ffffffff8027b8ed>] sys_read+0x88/0xc3
Nov 15 15:37:41 node2 kernel: [<ffffffff80209a0e>] system_call+0x7e/0x83
Nov 15 15:37:41 node2 kernel: 

```

Hi baggzy,

Those logs show that communications are not working well. It's unfortunately rather hard to debug this. You could however try one thing: unplug the network cables of your nodes and re-plug them, and then report about what happens (with logs and sysrq w please). I expect that this will temporarily unblock the system.

Another thing: I doubt that this can solve your issue, but you should assign a session_id between 1 and 9999 (TIPC's valid range of network id) to your cluster. Just use the session_id= parameter in kernel command line. Not specifying any lets it at 0, but I'm not sure that TIPC supports this well.

Thanks,

Louis

---

### Post by lrilling on 2009-11-17
> **lrilling said:**
> Hi baggzy,

Those logs show that communications are not working well.

Looking at your first hack on the NIC driver, this kind of hack can definitely cause such Kerrighed freeze, since it prevents TIPC (and Kerrighed) from retransmitting lost packets.

Don't know about the driver from realtek though.

Louis

---

### Post by baggzy on 2009-11-17
> **lrilling said:**
> Hi baggzy,

Those logs show that communications are not working well. It's unfortunately rather hard to debug this. You could however try one thing: unplug the network cables of your nodes and re-plug them, and then report about what happens (with logs and sysrq w please). I expect that this will temporarily unblock the system.

Another thing: I doubt that this can solve your issue, but you should assign a session_id between 1 and 9999 (TIPC's valid range of network id) to your cluster. Just use the session_id= parameter in kernel command line. Not specifying any lets it at 0, but I'm not sure that TIPC supports this well.

Thanks,

Louis

Hi Louis,

You're right!  Unplugging the network cables unfreezes the nodes.  Weird.  Does this help us fix it?  (I've set the session_id up as well, though I think this was being done in the /etc/kerrighed_nodes file anyway.)  I'll post the sysrq logs shortly.

I suspected that driver hack would prove unsatisfactory, though it did give me a chance to boot up the nodes and create an initrd, so not completely useless.  But I've now got the latest official Realtek driver, so you'd think I'd be ok...

Still, making progress... slowly...

---

### Post by baggzy on 2009-11-17
Hi Louis,

Well, I had a poke around and couldn't find any more comms issues, so I tried a bunch of other stuff... and it looks like I have an ACPI problem.  I have the following ACPI-related messages in the kern.log:

```
Nov 17 23:27:55 node1 kernel: Checking aperture...
Nov 17 23:27:55 node1 kernel: CPU 0: aperture @ 8000000 size 32 MB
Nov 17 23:27:55 node1 kernel: Aperture too small (32 MB)
Nov 17 23:27:55 node1 kernel: No AGP bridge found
Nov 17 23:27:55 node1 kernel: Your BIOS doesn't leave a aperture memory hole
Nov 17 23:27:55 node1 kernel: Please enable the IOMMU option in the BIOS setup
Nov 17 23:27:55 node1 kernel: This costs you 64 MB of RAM
Nov 17 23:27:55 node1 kernel: Mapping aperture over 65536 KB of RAM @ 8000000

``````
Nov 17 23:27:55 node1 kernel: ACPI: bus type pci registered
Nov 17 23:27:55 node1 kernel: PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
Nov 17 23:27:55 node1 kernel: PCI: Not using MMCONFIG.
Nov 17 23:27:55 node1 kernel: PCI: Using configuration type 1
Nov 17 23:27:55 node1 kernel: ACPI: Interpreter enabled
Nov 17 23:27:55 node1 kernel: ACPI: Using IOAPIC for interrupt routing
Nov 17 23:27:55 node1 kernel: Error attaching device data
Nov 17 23:27:55 node1 kernel: Error attaching device data
Nov 17 23:27:55 node1 kernel: Error attaching device data
Nov 17 23:27:55 node1 kernel: Error attaching device data
Nov 17 23:27:55 node1 kernel: Error attaching device data
Nov 17 23:27:55 node1 kernel: Error attaching device data

``````
Nov 17 23:27:55 node1 kernel: PCI-DMA: Disabling AGP.
Nov 17 23:27:55 node1 kernel: PCI-DMA: aperture base @ 8000000 size 65536 KB
Nov 17 23:27:55 node1 kernel: PCI-DMA: using GART IOMMU.
Nov 17 23:27:55 node1 kernel: PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Nov 17 23:27:55 node1 kernel: PCI: Ignore bogus resource 6 [0:0] of 0000:01:05.0

``````
Nov 17 23:27:55 node1 kernel: ACPI: (supports S0 S1 S3 S4 S5)
Nov 17 23:27:55 node1 kernel: IP-Config: No network devices available.
Nov 17 23:27:55 node1 kernel: error: -2
Nov 17 23:27:55 node1 kernel: Can't read /etc/hostname
Nov 17 23:27:55 node1 kernel: Kerrighed session ID : 1
Nov 17 23:27:55 node1 kernel: Kerrighed node ID    : 101
Nov 17 23:27:55 node1 kernel: Kerrighed nb nodes   : 0
Nov 17 23:27:55 node1 kernel: Kerrighed min nodes  : -1
Nov 17 23:27:55 node1 kernel: Freeing unused kernel memory: 216k freed
Nov 17 23:27:55 node1 kernel: r8168 Gigabit Ethernet driver 8.014.00-NAPI loaded
Nov 17 23:27:55 node1 kernel: ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Nov 17 23:27:55 node1 kernel: PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov 17 23:27:55 node1 kernel: r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
Nov 17 23:27:55 node1 kernel: eth0: Identified chip type is 'RTL8168C/8111C'.
Nov 17 23:27:55 node1 kernel: eth0: RTL8168B/8111B at 0xffffc2000004a000, 00:24:21:32:a6:22, IRQ 1278
Nov 17 23:27:55 node1 kernel: r8168  Copyright (C) 2009  Realtek NIC software team <nicfae@realtek.com> 
Nov 17 23:27:55 node1 kernel: This program comes with ABSOLUTELY NO WARRANTY; for details, please see <http://www.gnu.org/licenses/>. 
Nov 17 23:27:55 node1 kernel: This is free software, and you are welcome to redistribute it under certain conditions; see <http://www.gnu.org/licenses/>. 
Nov 17 23:27:55 node1 kernel: r8168: eth0: link down
Nov 17 23:27:55 node1 kernel: r8168: eth0: link up
Nov 17 23:27:55 node1 kernel: r8168: eth0: link up

```None of these looked serious to me.  (What do you think?) But if I disable ACPI with the "acpi=off" boot option, I don't get the freezing problem.

So problem (kind of) solved. \\:D/

I guess the obvious question is... will this have any effect on the performance of the cluster?

Cheers!

---

### Post by baggzy on 2009-11-17
I've narrowed it down a bit - seems like the problem is related to that IOMMU error.  If I use the following boot option (which I found on t'internet when I googled the IOMMU error I was getting):

```
iommu=noaperture,memaper=3
```

and delete the "acpi=off" boot option, I still don't get the freezing problem.

So I guess I'll go with that. :D

It's time to put this thing to work...

Many thanks to you and Tony for all your ideas & assistance!  You guys rock.

---

### Post by lrilling on 2009-11-18
> **baggzy said:**
> I've narrowed it down a bit - seems like the problem is related to that IOMMU error.  If I use the following boot option (which I found on t'internet when I googled the IOMMU error I was getting):

```
iommu=noaperture,memaper=3
```and delete the "acpi=off" boot option, I still don't get the freezing problem.

So I guess I'll go with that. :D

It's time to put this thing to work...

Many thanks to you and Tony for all your ideas & assistance!  You guys rock.

Happy that you finally got it working !

Looks like you guessed right. I don't know much about IOMMU and ACPI, so you probably did the right thing :)

Louis

---

### Post by gvpy on 2009-12-15
Correct me if I'm wrong:
The guide [https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide") sets up a cluster in which the **nodes** share resources.

Can the server also share resources with the nodes? I mean, what needs to be configured and how in order to make the processes of the server get migrated to the nodes?

I guess the kernel in the server also needs to be patched with Kerrighed, but I honestly have no idea about the other settings. Any thoughts?

---

### Post by quequotion on 2010-03-09
> **gvpy said:**
> Correct me if I'm wrong:
The guide [https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide") sets up a cluster in which the **nodes** share resources.

Can the server also share resources with the nodes? I mean, what needs to be configured and how in order to make the processes of the server get migrated to the nodes?

I guess the kernel in the server also needs to be patched with Kerrighed, but I honestly have no idea about the other settings. Any thoughts?

I have exactly the same question. I'm about half-way through setting this up, and I realized I can't see how the head could migrate processes *into* the cluster...

One thing does come to mind though, having mounted /proc into the chroot might allow it to see the head's processes. I don't really know how or if that works. If it does, how does one give those processes permission to migrate?

---

### Post by quequotion on 2010-03-09
> **ajt said:**
> 
Just disable ROOT on NFS:

```

diff .config.old .config
...
< CONFIG_ROOT_NFS=y
---
> # CONFIG_ROOT_NFS is not set

```

This appears to be an answer to my question.. and it's been posted and referenced a few times in the thread.... but what does it mean? (Sorry I think I'm going to need pictures or diagrams to wrap my head around this one...)

-edit-

Just to be sure, I mean to migrate processes from the pc *running* the head. This looks difficult to me as it does not have kerrighed installed and uses an entirely different kernel and architecture from the cluster. (although, even with the same kernel on the same arch I don't see how it could work)

like this:

Here's a minimal cluster, one head and one node.

[pxe/nfs [COLOR="RoyalBlue"]**server**[/COLOR], karmic - amd64]=([COLOR="Red"]**head**[/COLOR], hardy i386)

[pxe/nfs [COLOR="RoyalBlue"]**client**[/COLOR]]=([COLOR="Red"]**node**[/COLOR], hardy - i386)

[COLOR="Red"]**head**[/COLOR] and [COLOR="Red"]**node**[/COLOR] can create processes and migrate them.

[COLOR="RoyalBlue"]**client**[/COLOR] has no reason or means to create processes (it has no operating system without [COLOR="Red"]**node**[/COLOR]).

Can [COLOR="RoyalBlue"]**server**[/COLOR] introduce it's processes into [COLOR="Red"]**head**[/COLOR] and migrate them into the cluster?

---

### Post by ajt on 2010-03-10
> **quequotion said:**
> This appears to be an answer to my question.. and it's been posted and referenced a few times in the thread.... but what does it mean? (Sorry I think I'm going to need pictures or diagrams to wrap my head around this one...)

-edit-

Just to be sure, I mean to migrate processes from the pc *running* the head. This looks difficult to me as it does not have kerrighed installed and uses an entirely different kernel and architecture from the cluster. (although, even with the same kernel on the same arch I don't see how it could work)


Hello, quequotion.

I've been away from this thread for a while, but we've been working on the "server-as-node" configuration of Alicia's Beowulf here in Aberdeen.

We can migrate processes off the head now to PXE-booted compute nodes, but it requires some careful planning :-)

Basically, Kerrighed expects the same binaries in *exactly* the same place on all nodes. If you PXE-boot everything and share a common NFSROOT, there are few problems - Except the show-stopper that you can't migrate processes off the 'login' node.

We've addressed that by using UNFS3 with 'ClusterNFS' extensions enabled to share the '/' filesystem on the head node with the PXE-booted compute nodes. There are two difficulties with this approach, that we have now identified:

#1 The stand-alone node(s) must have statically configured id and session

#2 Any services provided by the node must be started *after* Kerrighed

We've now go a reasonably stable 10-node/18p 32-bit Kerrighed cluster running under Bio-Linux 5.0:

[http://kitcat.rri.sari.ac.uk](http://kitcat.rri.sari.ac.uk)

There are two stand-alone nodes, one the 'head' node and the other is "kitcat" itself, which is our login server. Processes will migrate off "kitcat" OK to the rest of the nodes. However, we still have problems if I enable USE_REMOTE_MEMORY, and Louis has said that the 32-bit version is not fully supported because they are giving priority to work on the 64-bit version. We will upgrade to 64-bit Ubuntu 10.04 and test Kerrighed in that environment until Bio-Linux 6.0 is released in June 2010.

Bye,

  Tony.

---

### Post by soulsage on 2010-03-25
i been playing with kerrighed for about 3 weeks now and i just have a few ?](*,) 
 
Has anyone been able to actaully use kerrighed features?
 
Is there a way to get java(ImageJ) to recognize all the memory in a kerrighed cluster?
(I've tried not success)
 
What programs are there for kerrighed or must everything be costume made?
 
Does migration /kerrighed always hang while running the linpack?

---

### Post by lrilling on 2010-03-26
> **soulsage said:**
> Is there a way to get java(ImageJ) to recognize all the memory in a kerrighed cluster?
(I've tried not success)

Memory aggregation is a feature that appeared in Kerrighed 2.4.0. Some configuration is required in order to use it. Please check the FAQ:
[http://kerrighed.org/wiki/index.php/FAQ#My_process_cannot_use_remote_memory](http://kerrighed.org/wiki/index.php/FAQ#My_process_cannot_use_remote_memory)
 
> **soulsage said:**
>  What programs are there for kerrighed or must everything be costume made?

I don't understand this question. Could you elaborate a bit?
 
> **soulsage said:**
> Does migration /kerrighed always hang while running the linpack?

There are known issues with sockets and migration, especially for MPI and X applications. Problems are still under investigation.

Thanks,

Louis

---

### Post by soulsage on 2010-03-26
*Thank you for your relpy*
* *
*What programs are there for kerrighed or must everything be costume made?*
 
...
Basically i am asking what programs fully work with  kerrighed  or must i just create my own program to work with it?
 
 
...
also i check the configuration  required in order to use it memory aggregation . Still no success

---

### Post by nerdopolis on 2010-03-26
As far as I know, you can distribute normal running programs throughout the cluster. (run 3 apps in node 1 and 3 apps in node 2 for example, and then migrate them between nodes)

but I dont think single programs themselves yet get the full benefit of the cluster, as in order to benefit from multiple processors, they have to be written to use multiple threads. Some programs use multiple threads already, because we have dual and quad core processors now (and dual processor motherboards). Unfortunately Kerrighed can not yet distribute a programs threads across the nodes, The threads can only be on one node at a time.

That feature is planned for Kerrighed in the future, but its a complex feature, and the devs don't have enough resources for that.

---

### Post by lrilling on 2010-03-29
> **nerdopolis said:**
>  but I dont think single programs themselves yet get the full benefit of the cluster, as in order to benefit from multiple processors, they have to be written to use multiple threads.
Some programs use multiple threads already, because we have dual and quad core processors now (and dual processor motherboards). Unfortunately Kerrighed can not yet distribute a programs threads across the nodes, The threads can only be on one node at a time.

If you replace "threads" by "processes" then it already works.

Louis

---

### Post by lrilling on 2010-03-29
> **soulsage said:**
> also i check the configuration  required in order to use it memory aggregation . Still no success

Could you show us detailed steps of what you did?

Thanks,

Louis

---

### Post by anitemp on 2010-03-31
I'm trying to get my Kerrighed system to work and I'm facing similar issues too. I recently found the 'live' version of Kerrighed 2.3.0 at [this]("http://www.kerlabs.com/dl/kerrighed-live.iso") link. Not a full fledged solution, though I could do what I wanted to.

Good luck!!

---

### Post by renomcdonald on 2010-04-02
Hey Ive looked all over and clustering has officially confused me! :-x

Would the *Ubuntu Enterprise Cloud* computing allow me to run a virtual machine and use the resources of all the nodes for processing? Cause that's what I want.

---

### Post by lrilling on 2010-04-02
> **renomcdonald said:**
> Hey Ive looked all over and clustering has officially confused me! :-x

That's why Kerrighed is developped: making people forget about what clusters really are. But for administrators, some knowledge will still be required.

> **renomcdonald said:**
>  Would the *Ubuntu Enterprise Cloud* computing allow me to run a virtual machine and use the resources of all the nodes for processing? Cause that's what I want.

As far as I know UEC will allow you to multiplex your nodes, that is deploy several virtual machines per node, but it won't allow you to aggregate nodes into a single virtual machine.

Regards,

Louis

---

### Post by renomcdonald on 2010-04-02
oh ok. so Kerrighed would be my best solution then?;)

---

### Post by lrilling on 2010-04-06
> **renomcdonald said:**
> oh ok. so Kerrighed would be my best solution then?;)

;)

---

### Post by amichaud on 2010-04-11
Has anyone tried Ansys/Fluent and also Matlab with Kerrighed.  I've been tasked with the building of a new cluster for the department and these are the programs we will run.
 
For the hardware I'm looking to run Dual Xeon 5520 quad core cpus in each node with 8 nodes (64 cores) and a master node with similar specs.  12Gigs ram on each node.  I've also been asked to include a hdd on each node which doesn't make sense to me...I'd rather use the money to buy more ram.
 
For storage I'm looking at 15TB SAN 
[FONT=Arial][SIZE=1][FONT=Verdana]Dell Powervault MD3000i[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=1][/SIZE][/FONT] 
[FONT=Arial][SIZE=1][FONT=Verdana]Will Kerrighed handle this hardware and software?[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=1][/SIZE][/FONT] 
[FONT=Arial][SIZE=1][FONT=Verdana]Any insight is much appreciated.[/FONT][/SIZE][/FONT]
**[FONT=Arial][SIZE=1][/SIZE][/FONT]** 
[SIZE=1][/SIZE]

---

### Post by lrilling on 2010-04-13
> **amichaud said:**
> For the hardware I'm looking to run Dual Xeon 5520 quad core cpus in each node with 8 nodes (64 cores) and a master node with similar specs.  12Gigs ram on each node.  I've also been asked to include a hdd on each node which doesn't make sense to me...I'd rather use the money to buy more ram.
 
For storage I'm looking at 15TB SAN 
[FONT=Arial][SIZE=1][FONT=Verdana]Dell Powervault MD3000i[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=1][FONT=Verdana]Will Kerrighed handle this hardware and software?[/FONT][/SIZE][/FONT]

Kerrighed is known to run Nehalem CPUs, so Xeon 5520 are ok.
For your storage, as long as it can be used to export a shared NFS root to the compute nodes, it's ok too.

Regards,

Louis

---

### Post by gabrielaca on 2010-04-13
i´m sorry, Kerrighed supports multiple cpu´s? amichaud said dual xeon´s quad cores, i thought only single cpu´s where supported at this time, could you clarify?

---

### Post by gabrielaca on 2010-04-13
yes it can handle up to 4 cpus per node, he he he sorry my mistake :lolflag:

---

### Post by lrilling on 2010-04-14
> **gabrielaca said:**
> yes it can handle up to 4 cpus per node, he he he sorry my mistake :lolflag:
This limitation of 4 cpus is mostly artificial and gone in the development version, which is based on Linux 2.6.30.

Regards,

Louis

---

### Post by renkinjutsu on 2010-04-14
I read somewhere on linux.com (article written in 2006) that kerrighed supports migrating individual threads themselves to balance CPUs .. but on the kerrighed website "support for distributed threads" is listed under "Futer Work"

can any one currently using kerrighed tell me if threaded processes are distributed over the cluster?

---

### Post by lrilling on 2010-04-15
> **renkinjutsu said:**
> I read somewhere on linux.com (article written in 2006) that kerrighed supports migrating individual threads themselves to balance CPUs .. but on the kerrighed website "support for distributed threads" is listed under "Futer Work"

can any one currently using kerrighed tell me if threaded processes are distributed over the cluster?

Thread migration used to work in now very old version 1.0.2 of Kerrighed which was based on Linux 2.4.29. This feature was dropped when porting Kerrighed to Linux 2.6.x. It should be re-introduced in the future. Please read this post for more details: [https://listes.irisa.fr/sympa/arc/kerrighed.users/2008-12/msg00024.html](https://listes.irisa.fr/sympa/arc/kerrighed.users/2008-12/msg00024.html)

Thanks,

Louis

---

### Post by quequotion on 2010-04-18
> **ajt said:**
> #1 The stand-alone node(s) must have statically configured id and session

I think this was the plan anyway.. was there something unusual about the way you specified their id and session?

> #2 Any services provided by the node must be started *after* Kerrighed

I don't really know what this means or how to implement it :(

Could you give examples of your /etc/exports, /etc/fstab, /etc/network/interfaces, and /etc/hosts?

By the way, thank you for helping out so patiently... This thread is very long, but having looked through a few more pages I see you've had to repeat yourself several times.

---

### Post by joshruehlig on 2010-04-22
Haven't had the time to read every single post in this thread yet but just wanted to ask a question before I headed to class. (Ill read through it after)

[https://wiki.edubuntu.org/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.edubuntu.org/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)
In this well written guide he talks about having a main machine, and nodes (one being the head node). **Would this mean my main computer with a gui wouldn't be doing any of the computing work?** The main computer in my case would be mp best one and I'd want it to be part of the cluster of computing power as well.

This is what my ideal setup would consist of, 

main computer with server install and gui + 3-5 nodes connected to it just for share of ram/cpu/hard drive. **Is this possible with this guide?**

Thanks for your help!

PS. the server is to host a few sites (motion webcam stream, files) Remote Desktop.

And the cluster is just for fun, and for testing...

---

### Post by renkinjutsu on 2010-04-22
yup, the nfs/tftp server will not be part of the cluster.

You can easily set the server up on a weaker machine.. it doesn't take much computing power to serve files and act as a boot server. it's mostly disk throughput and network speed that counts for the server.

Since kerrighed will only be installed onto ONE computer, the server, you can leave your main desktop as it is and just reboot it into kerrighed whenever you start your cluster.


that's all i've gathered.. i don't actually have a kerrighed cluster :P

---

### Post by joshruehlig on 2010-04-22
Thanks for the quick reply!

hmm still not sure what I want to do yet, the main reason for the server is for motion, I wonder how hard that would be to run on the cluster.

BTW the Ubuntu Enterprise Cloud seems way to much then I need but it also fills my requirement of several servers hooked together. Lol I guess Im just confusing myself now. **Has anyone here messed around with UEC?**

---

### Post by Benic on 2010-04-23
Very interesting thread!

I've been using for some time a specific R script to analyze textual data that uses a very large matrix as input. When I bootstrap the results it can take several days (4-5) to process. In order to save some time, as I need to do that frequently, I've decided to set up a small cluster since the script involves the Rmpi library (based on lam-mpi). Not an easy task!!!

Did anyone succeed in building such a cluster? I've implemented the exact same R and MPI setup on all computers, set up a passwordless ssh access, reconfigured my Guarddog firewall to allow parallel computing, but when I test lam on two computers, I can't turn the second one into a node, despite positive output of lamboot -v, as you can see below:

```
~$ lamboot -v

LAM 7.1.2/MPI 2 C++/ROMIO - Indiana University

n-1<3976> ssi:boot:base:linear: booting n0 (10.42.43.1)
n-1<3976> ssi:boot:base:linear: booting n1 (10.42.43.2)
n-1<3976> ssi:boot:base:linear: finished
```

When it comes to lamexec, I get that:

```
~$ lamexec C hostname
bureau1
dlo_inet (sendto): Operation not permitted
```

If I try:

```
~$ mpirun -np 1 R --no-save
```

I get this error when I run a function involving Rmpi:

--------------------------------------------------------------------------
mpirun noticed that process rank 0 with PID 5006 on node bureau1 exited on signal 13 (Broken pipe).
--------------------------------------------------------------------------

How could I get that error? If I force R to use Rmpi, I usually have to kill the process, same with ssh (or rsh) 10.42.43.2 R --slave. 

A simple question (that may be the answer to all that), do I need to set all computers as ssh servers or only one as it is in this case? 

Since I'm a complete newbie in the marvelous world of clustering computers, any help would be appreciated! 

Thanks!

---

### Post by ajt on 2010-04-29
> **Benic said:**
> Very interesting thread!
[...]
A simple question (that may be the answer to all that), do I need to set all computers as ssh servers or only one as it is in this case? 

Since I'm a complete newbie in the marvelous world of clustering computers, any help would be appreciated! 

Thanks!

Hello, Benic.

Yes, you need to have SSH servers on all your nodes and set-up password-less logins. LAM is very easy to use: First create SSH keys (use a 'null/empty' pass-phrase when prompted)

```

cd # go to your login directory
ssh-keygen -t rsa
cd .ssh
cp -ai id_rsa.pub authorized_keys

```

Now, either copy the .ssh directory to all the nodes or use NFS to mount your login folder on all the nodes. You will no longer be prompted for a password. When this is working, start up LAM (e.g. on node1,2,3 with 1 CPU in each)

```

cat >lam-bhost.def
node1 cpu=1
node2 cpu=1
node3 cpu=1
^D
lamboot -v
lamnodes

```

Now, you should be able to run your MPI programs!

Bye,

  Tony.

---

### Post by ajt on 2010-04-29
> **quequotion said:**
> I think this was the plan anyway.. was there something unusual about the way you specified their id and session?


Hello, quequotion.

Yes, we specified it to be consistent with the automatic configuration of the PXE-booted nodes.

> 
I don't really know what this means or how to implement it :(

Could you give examples of your /etc/exports, /etc/fstab, /etc/network/interfaces, and /etc/hosts?


```

manager@kitcat[manager] cat /etc/exports
# /etc/exports #
/ 192.168.0.0/255.255.255.0(ro,no_root_squash)
#/export 192.168.0.0/255.255.255.0(rw,no_root_squash)

manager@kitcat[manager] cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=dd20339c-d208-42e0-8311-f24e77dc128e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde3
UUID=fc839f2a-b004-486e-9153-13e357b6ea49 /backups        ext3    relatime,noauto        0       2
# /dev/sde2
UUID=a7479698-1258-47a6-925f-422c84f5a612 none            swap    sw              0       0
# /dev/md0
/dev/md0 /export           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

configfs	/config	configfs	defaults	0	0

manager@kitcat[manager] cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet static
address 143.234.32.16
netmask 255.255.240.0
gateway 143.234.36.2

auto eth0
iface eth0 inet static
address 192.168.0.254
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.168.1.254
netmask 255.255.255.0

manager@kitcat[manager] cat /etc/hosts                                                                                                     [ 4:45PM]
127.0.0.1 localhost
127.0.1.1 kitcat

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

# servers
192.168.1.254	krg254
192.168.0.254	node254 kitcat

# nodes
192.168.1.2	krg2
192.168.0.2	node2
192.168.1.3	krg3
192.168.0.3	node3
192.168.1.4	krg4
192.168.0.4	node4
192.168.1.5	krg5
192.168.0.5	node5
192.168.1.6	krg6
192.168.0.6	node6
192.168.1.7	krg7
192.168.0.7	node7
192.168.1.8	krg8
192.168.0.8	node8
192.168.1.1	krg1
192.168.0.1	node1

```

> 
By the way, thank you for helping out so patiently... This thread is very long, but having looked through a few more pages I see you've had to repeat yourself several times.


That's OK, I'm happy to help if I can - I'd like to spread the word about Kerrighed in the Ubuntu community.

Bye,

  Tony.

---

### Post by ajt on 2010-04-29
> **lrilling said:**
> This limitation of 4 cpus is mostly artificial and gone in the development version, which is based on Linux 2.6.30.


Hello, Louis.

In our tests, 32-bit Kerrighed seems very reluctant to use more than one core per processor chip and we had to get the cluster loaded significantly more than one CPU hog per CPU core before SMP processors on the same chip were used. Is this a result of the openMosix load-balancing algorithm?

Bye,

  Tony.

---

### Post by Benic on 2010-04-29
> **ajt said:**
> Hello, Benic.

Yes, you need to have SSH servers on all your nodes and set-up password-less logins. 

Thanks Tony, it was the missing piece in the puzzle!

---

### Post by lrilling on 2010-04-30
> **ajt said:**
> Hello, Louis.

In our tests, 32-bit Kerrighed seems very reluctant to use more than one core per processor chip and we had to get the cluster loaded significantly more than one CPU hog per CPU core before SMP processors on the same chip were used. Is this a result of the openMosix load-balancing algorithm?

This results from the simplification we made when implementing the load balancing algorithm. The implemented algorithm just does not consider the number of cores per node, which is equivalent to behave as if each node had only one core.

Some improvements to this algorithm are planned (eg number of cores per node, different CPU speeds), but right now I can't tell you when they will appear.

Thanks,

Louis

---

### Post by renkinjutsu on 2010-04-30
lrilling,

do you think kerrighed will pick up thread migration again once the desired stability is finally met? Or would it just be impossible at that point?

---

### Post by lrilling on 2010-05-03
> **renkinjutsu said:**
> lrilling,

do you think kerrighed will pick up thread migration again once the desired stability is finally met? Or would it just be impossible at that point?

We should start working on it in a near future. But I have no means to give a reliable estimate on when it will be done. There is no impossibility, just priorities.

Thanks,

Louis

---

### Post by exsecratus on 2010-05-11
Hi. Is it possible to use this with a software like blender or maya
to do render farm?
or even using vmware to use with 3dmax?
o/

---

### Post by jvin248 on 2010-05-16
Not having done it, [http://dynebolic.org/](http://dynebolic.org/) is supposed to be set up for clustering machines specifically for blender and related programs. I was a bit surprised to see last release was ~2007 as there used to be a lot of activity there.

Kerrighed should definitely allow doing this as well - build cluster then run any program on top of it across the group of computers.  Blender was set up to multi-thread and use all resources provided.  How to actually get it working .. I'm not sure, .. but it's been done by others already.

---

### Post by samshamolian on 2010-05-17
hello all.. a bunch of sweet words on how much this site rocks and everything(really, i just don't know how to write such stuff) 
  now am a computer science student, entering my final year.. am thinking about a graduation project.. 
  i have my mind set on doing something related to cluster computing.. i (personally) think it's a really neat subject, it may be needed in the near future as computer usage increases rapidly and the needs for high performance computing without paying tons of dollars is demanded by many organizations.. also i think of it as a good way to improve my gnu/linux capabilities and FOSS knowledge.. i have many other reasons to go on with this project, so long story short; i want to do a graduation project related to cluster computing.. now i have some questions.. - first, I'll appreciate any resources related to the subject, i of course found a lot of materials on the web(me love google).. but it'd be nice if someone pointed me to some of those underground, hidden, unknown, that are not too obvious to found and you had to bookmark it so u may make use of it one day kind of pages.. (i found alla mentioning that he wants to write something about clustering in more than one place of his writings) - secondly, and this is more important, i want to hear your opinions on what exactly can i do using clusters that can be useful as a graduation project.. because as i dig deeper on the web, i find that the subject is much more easier than i thought it would be in the first place, every thing is already implemented.. it'll get down to just connecting bunch of computers with a LAN, then install a clustering _distro_[]("http://eglug.org/glossary/term/85") to each node, and walla.. it's done(almost) so the issue now is what is going to run on the system, this is gonna be the sole benefit of the project, and this is my question.. i thought about some stuff:a web or database server, or any kind of server to make use of high availability and load balancing.. running a high demanding application that needs huge processing power..(am thinking about just installing one of those clients that work on large research projects) some other lame ideas.. ok, after i wrote this.. i thought it would be too large to post here, so if you find this post not informative enough, please let me know, and i'll explain more.. waiting for your comments :) thank you very much.. and keep the good work

---

### Post by noval on 2010-05-17
Dear all,
 I would like to ask question, I already finish do install kerrighed & compile kernel on my laptop following the guidance & check all the file needed by the system cluster server :


 /boot/vmlinuz-2.6.20-krg (Kerrighed kernel)
/boot/System.map (Kernel symbol table)
/lib/modules/2.6.20-krg (Kerrighed kernel module)
/etc/init.d/kerrighed (Kerrighed service script)
/etc/default/kerrighed (Kerrighed service configuration file)
/usr/local/share/man/* (Look inside these subdirectories for Kerrighed man pages)
/usr/local/bin/krgadm (The cluster administration tool)
/usr/local/bin/krgcapset (Tool for setting capabilities of processes on the cluster)
/usr/local/bin/krgcr-run (Tool for checkpointing processes)
/usr/local/bin/migrate (Tool for migrating processes)
/usr/local/lib/libkerrighed-* (Libraries needed by Kerrighed)
/usr/local/include/kerrighed (Headers for Kerrighed libraries)


 result all have
but then while try to boot hostnode1 & hostnode2 (client node) can’t get connected, eventough it already get it’s own IP static


 here is the error :

 
 intel 810_AC97 Audio,version 1.01,05:13:06 May 16 2010
oprofile :using timer interrupt
TCP cubic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
TIPC:Activated (version 1.7.5 compiled May 16 20101 05:18:38)
NET: Registered protocol family 30
TIPC: Started in single node mode
acpi_processor-0571 [00] processor_get_psd : invalid _PSD data
acpi_processor-0571 [00] processor_get_psd : invalid _PSD data
Using IPI Shortcut mode
Time : tsc clocksource has been installed.
r8169 : eth0: link up
Sending DHCP request…………timed out!
IP-Config:Retriying forever (NFS root)…
r8169 : eth0: link up
Sending DHCP request…………timed out!
IP-Config:Retriying forever (NFS root)…


Please help me, what should I do?



 Best regards
thanks
noval

---

### Post by lrilling on 2010-05-18
> **noval said:**
> 
 result all have
but then while try to boot hostnode1 & hostnode2 (client node) can’t get connected, eventough it already get it’s own IP static


 here is the error :

 
 intel 810_AC97 Audio,version 1.01,05:13:06 May 16 2010
oprofile :using timer interrupt
TCP cubic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
TIPC:Activated (version 1.7.5 compiled May 16 20101 05:18:38)
NET: Registered protocol family 30
TIPC: Started in single node mode
acpi_processor-0571 [00] processor_get_psd : invalid _PSD data
acpi_processor-0571 [00] processor_get_psd : invalid _PSD data
Using IPI Shortcut mode
Time : tsc clocksource has been installed.
r8169 : eth0: link up
Sending DHCP request…………timed out!
IP-Config:Retriying forever (NFS root)…
r8169 : eth0: link up
Sending DHCP request…………timed out!
IP-Config:Retriying forever (NFS root)…


You said that the nodes should get static IPs, but the kernel is trying to get a dynamic one. If your setup definitely targets static IPs, you should check that they are properly given to the kernel in its command line. Otherwise, you should check your DHCP server.

Thanks,

Louis

---

### Post by noval on 2010-05-18
[LEFT]    [FONT=&quot]Dear Louis,

I already check the DHCP server & get connected with PC that have OS (Ubuntu) the result are those PC get the IP static that was setting on the DHCP server like it should.
But while doing boot through network to get diskless booting, that's problem happened.
Here is my set up :
1.install the DHCP server package with aptitude or apt-get, as root: 
# aptitude install dhcp3-server

2.Check that the DHCP server configuration file /etc/default/dhcp3-server 
Make sure you know which is the right card,In this case it is eth0
# /etc/default/dhcp3-server #
interfaces="eth0"[/FONT][FONT=&quot]

[/FONT][FONT=&quot]3.Configure the DHCP daemon to issue addresses only to nodes, and tell it which addresses to give them.

# /etc/dhcp3/dhcpd.conf #
# General options
option dhcp-max-message-size 2048;
use-host-decl-names on;
deny unknown-clients; # This will stop any non-node machines from appearing on the cluster network.
deny bootp;

# DNS settings
option domain-name "kerrighed"; # Just an example name - call it whatever you want.
option domain-name-servers 10.11.13.1; # The server's IP address, manually configured earlier.

# Information about the network setup
subnet 10.11.13.0 netmask 255.255.255.0 {
option routers 10.11.13.1; # Server IP as above.
option broadcast-address 10.11.13.255; # Broadcast address for your network.
}

# Declaring IP addresses for nodes and PXE info
group {
filename "pxelinux.0"; # PXE bootloader. Path is relative to /var/lib/tftpboot
option root-path "10.11.13.1:/nfsroot/kerrighed"; # Location of the bootable filesystem on NFS server

host kerrighednode1 {
fixed-address 10.11.13.101; # IP address for the first node, kerrighednode1 for example.
hardware ethernet 00:26:18:B6:CD:19; # MAC address of the node's ethernet adapter
}

host kerrighednode2 {
fixed-address 10.11.13.102;
hardware ethernet 00:26:18:B6:C9:CB;
}

server-name "kerrighedserver"; # Name of the server. Call it whatever you like.
next-server 10.11.13.1; # Server IP, as above.
} 

4.As root, install the TFTP server package, tftp-hpa, with aptitude or apt-get:
# aptitude install tftpd-hpa

5.Open its configuration file, /etc/default/tftpd-hpa, and make sure it uses the following settings.# /etc/default/tftp-hpa #
#Defaults for tftp-hpa
RUN_DAEMON="NO"
OPTIONS="-l -s /var/lib/tftpboot"

6.Now we need to configure inetd to run the tftp server. tftp dgram udp wait root /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot

7.As root, install syslinux, which is the system required for you to be able to PXE boot the nodes, and copy the PXE bootloader code from it to the TFTP server directory. This is the bootloader you told the DHCP daemon about in its configuration file earlier.
# aptitude install syslinux
# cp /usr/lib/syslinux/pxelinux.0 /var/lib/tftpboot

8.Still as root, create a directory to store the default configuration for all the nodes. They will search in this directory for configuration files during the PXE boot process.
# mkdir /var/lib/tftpboot/pxelinux.cfg

9.Still as root, copy your current kernel and initrd from /boot to /var/lib/tftpboot/ in order to test the diskless-boot system. Replace <KERNEL_VERSION> with whatever you are using. # cp /boot/vmlinuz-2.6.24-16-generic /boot/initrd.img-2.6.24-16-generic /var/lib/tftpboot/

10.Create the file /var/lib/tftpboot/pxelinux.cfg/default.
This will be the fallback configuration file that the nodes use to PXE
boot when they can't find a file specific to their own IP address.

LABEL linux
KERNEL vmlinuz-2.6.24-16-generic
APPEND console=tty1 root=/dev/nfs initrd=initrd.img-2.6.24-16-generic nfsroot=10.11.13.1:/nfsroot/kerrighed ip=dhcp rw

11.As root, install the packages nfs-kernel-server and nfs-common, which comprise the NFS server program. Keep your root authorisation until you're done working with the NFS server. 
# apt-get install nfs-kernel-server nfs-common[/FONT][FONT=&quot]

12. [/FONT][FONT=&quot]Make a directory to store the bootable filesystem in: 
# mkdir /nfsroot/kerrighed

13.Edit /etc/exports,which configures NFS file transfers. Add the following in order to make NFS export the filesystem that will be stored in the directory you just
made:
 
# /etc/exports 
# /nfsroot/kerrighed 10.11.13.0/255.255.255.0(rw,no_subtree_check,async,no_root_squash)

14.Re-export the file systems, since you just changed how this is done: 
# exportfs -avr

15.use debootstrap to itself install a minimal Ubuntu Hardy system to the bootable filesystem directory:
# aptitude install debootstrap
# debootstrap --arch i386 hardy /nfsroot/kerrighed [[COLOR=blue]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/16")

16.Change the current root of the file system to the bootable filesystem directory (stay chrooted until the guide tells you otherwise.) This is so that you can work with the bootable filesystem directly, as if it were a separate machine, while we make some adjustments to it.
# chroot /nfsroot/kerrighed

17.Set the root password for the bootable filesystem 
# passwd

18 Mount the /proc directory of the current machine as the bootable system's /proc directory, so you can use programs on the bootable FS: 
# mount -t proc none /proc

19 .Edit /etc/apt/sources.list. 

deb [[COLOR=blue]http://archive.canonical.com/ubuntu[/COLOR]]("http://archive.canonical.com/ubuntu") hardy partner 
deb [[COLOR=blue]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") hardy main universe restricted multiverse 
deb [[COLOR=blue]http://security.ubuntu.com/ubuntu/[/COLOR]]("http://security.ubuntu.com/ubuntu/") hardy-security universe main multiverse restricted 
deb [[COLOR=blue]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") hardy-updates universe main multiverse restricted 
deb-src [[COLOR=blue]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") hardy main universe restricted multiverse deb-src [[COLOR=blue]http://security.ubuntu.com/ubuntu/[/COLOR]]("http://security.ubuntu.com/ubuntu/") hardy-security universe main multiverse restricted
deb-src [[COLOR=blue]http://archive.ubuntu.com/ubuntu/[/COLOR]]("http://archive.ubuntu.com/ubuntu/") hardy-updates universe main multiverse restricted

20.Update the current package
# aptitude update

21. Install some packages that our nodes need for using NFS and DHCP: 
$ apt-get install dhcp3-common nfs-common nfsbooted openssh-server

22. make it work with NFS. Edit /etc/fstab, the filesystem index, of the bootable filesystem to look like this: 

# /etc/fstab 
# 
#<file system> <mount point> <type> <options> <dump> <pass> 
proc /proc proc defaults 0 0 
/dev/nfs / nfs defaults 0 0

23. Edit /etc/hosts. This is so that the DHCP server will know which of the PXE-booted nodes get which IP and hostname. Add all your cluster nodes and the server to it. In our example case, it looks like this: 

# /etc/hosts # 
127.0.0.1 localhost
10.11.13.1 kerrighedserver 
10.11.13.101 kerrighednode1 
10.11.13.102 kerrighednode2

24.Do the following to create a symbolic link which will automount the bootable filesystem as /dev/nfs on the server, when it starts up. This should not collide with other existing services in the directory (e.g. anything that looks like /etc/rcS.d/S34xxxxxxx), so check carefully before you create the link. If there's a service with a similar name, disable it before you do anything else. 
$ ln -sf /etc/network/if-up.d/mountnfs /etc/rcS.d/S34mountnfs 

25. Edit /etc/network/interfaces and add a line to stop Network Manager from managing the nodes' Ethernet cards, as this can cause issues with NFS. Ours looks like the following: 

# ... 
# The loopback interface: 
auto lo 
iface lo inet loopback
# The primary network interface, manually configured to protect NFS: 
iface eth0 inet manual

26. Create a user for the bootable system. Replace <username> with whatever you want to call her. adduser will ask you for her real name and other details, so play along. 

# adduser <username>

27. Ensure that the new user is in the /etc/sudoers file so can run root commands on the cluster: 

# /etc/sudoers #
#User privilege specification
root ALL=(ALL) ALL 
<username> ALL=(ALL) ALL

28. Exit the root shell, and then exit from the chrooted bootable filesystem. You're done configuring the bootable FS and can now test it with your common-or-garden kernel. 
# exit
# exit 

29. Restart the servers on the head node, because you've been messing with them. You need to be root to do this: 
# /etc/init.d/tftpd-hpa restart 
# /etc/init.d/dhcp3-server restart 
# /etc/init.d/nfs-kernel-server restart[/FONT]
  
[LIST]
[*][FONT=&quot]Configure the BIOS of each node to have the following      boot order: your primary boot device should be PXE, which will usually be      described as "network boot" or "LAN boot". In certain      cases you may need to enable the network cards as boot devices in the      BIOS, reboot, and then set the boot priority. Remember also to disable      "halt on all errors", since this can mess up your PXE booting.[/FONT]
[*][FONT=&quot]Boot each of the nodes to see if it works. If so, you      should be presented with a login prompt, where you can log-in using the      username you defined earlier. When it all works, you're ready to try with      a Kerrighed kernel. [/FONT]
[/LIST]
  [FONT=&quot]
Now that we've got a diskless boot system setup to use as a server, we only need to build the Kerrighed kernel for the nodes to use, put it in the bootable FS, and configure the Kerrighed settings properly in order to have a working SSI (Single System Image) cluster.[/FONT]
  [/LEFT]

---

### Post by jetsam on 2010-05-18
No problem then.  Nothing to it, really.  Should have my cluster up and running in about 75 years.

---

### Post by lrilling on 2010-05-19
> **noval said:**
> [LEFT]    [FONT=&quot]Dear Louis,

I already check the DHCP server & get connected with PC that have OS (Ubuntu) the result are those PC get the IP static that was setting on the DHCP server like it should.
But while doing boot through network to get diskless booting, that's problem happened.
[/FONT]

If I understand correctly, a regular DHCP client running on top of Ubuntu with an Ubuntu kernel gets the IP address, but Kerrighed kernel's internal client fails to get the IP address. If you're not using Kerrighed 2.4.4, I recomment you to upgrade to this version since it contains fixes for your NIC driver (8169).

Thanks,

Louis
[/LEFT]

---

### Post by robinhoods on 2010-05-20
**Setting up the bootable filesystem**

 
[LIST]
[*]This isn't as simple as just copying the OS files into another directory - you'll need the debootstrap package to install the bootable filesystem, so install this first (you should still be root.) Once it's installed, use debootstrap to itself install a minimal Ubuntu Hardy system to the bootable filesystem directory: 
[/LIST]

# aptitude install debootstrap
# debootstrap --arch i386 hardy /nfsroot/kerrighed [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
[LIST]
[*]Change the current root of the file system to the bootable filesystem directory (stay chrooted until the guide tells you otherwise.) This is so that you can work with the bootable filesystem directly, as if it were a separate machine, while we make some adjustments to it. 
[/LIST]

# chroot /nfsroot/kerrighed
[LIST]
[*]Set the root password for the bootable filesystem. You can use a program called apg, the automated password generator, to create a good one. 
[/LIST]

# passwd
[LIST]
[*]Mount the /proc directory of the current machine as the bootable system's /proc directory, so you can use programs on the bootable FS: 
[/LIST]

# mount -t proc none /proc
[LIST]
[*]Edit /etc/apt/sources.list. We want to add access to some extra Ubuntu repositories in order to be able to download the necessary packages for the FS. Add these lines: 
[/LIST]

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
[LIST]
[*]Update the current package listing from the repositories you just added so you'll be able to install things from them: 
[/LIST]

]# aptitude update
[LIST]
[*]Install some packages that our nodes need for using NFS and DHCP: 
[/LIST]

$ apt-get install dhcp3-common nfs-common nfsbooted openssh-server
[LIST]
[*]Now we need to make it work with NFS. Edit /etc/fstab, the filesystem index, of the bootable filesystem to look like this: 
[/LIST]

# /etc/fstab
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc            /proc         proc   defaults       0      0
/dev/nfs        /             nfs    defaults       0      0
[LIST]
[*]Edit /etc/hosts. This is so that the DHCP server will know which of the PXE-booted nodes get which IP and hostname. Add all your cluster nodes and the server to it. In our example case, it looks like this: 
[/LIST]

# /etc/hosts #
127.0.0.1 localhost

192.168.1.1    kerrighedserver
192.168.1.101  kerrighednode1
192.168.1.102  kerrighednode2
192.168.1.103  kerrighednode3
192.168.1.104  kerrighednode4
192.168.1.105  kerrighednode5
192.168.1.106  kerrighednode6
[LIST]
[*]Do the following to create a symbolic link which will automount the bootable filesystem as /dev/nfs on the server, when it starts up. This should not collide with other existing services in the directory (e.g. anything that looks like /etc/rcS.d/S34xxxxxxx), so check carefully before you create the link. If there's a service with a similar name, disable it before you do anything else. 
[/LIST]

$ ln -sf /etc/network/if-up.d/mountnfs /etc/rcS.d/S34mountnfs 
[LIST]
[*]Edit /etc/network/interfaces and add a line to stop Network Manager from managing the nodes' Ethernet cards, as this can cause issues with NFS. Ours looks like the following: 
[/LIST]

# ...
# The loopback interface:
auto lo
iface lo inet loopback

# The primary network interface, manually configured to protect NFS:
iface eth0 inet manual
[LIST]
[*]Create a user for the bootable system. Replace <username> with whatever you want to call her. adduser will ask you for her real name and other details, so play along. 
[/LIST]

# adduser <username>
[LIST]
[*]Ensure that the new user is in the /etc/sudoers file so she can run root commands on the cluster: 
[/LIST]

# /etc/sudoers #
#User privilege specification
root ALL=(ALL) ALL
<username> ALL=(ALL) ALL
[LIST]
[*]Exit the root shell, and then exit from the chrooted bootable filesystem. You're done configuring the bootable FS and can now test it with your common-or-garden kernel. 
[/LIST]

# exit
# exit

---

### Post by jetsam on 2010-05-20
Looks like it's coming along.  Wow.

---

### Post by pengin80 on 2010-05-21
Hello all,

I'm a new Ubuntu user (on Server 10.04 64bit), who's found himself in possession of 7 Dell Optiplex 755s.  My goal is to evaluate a number of options to see how we can most effectively harness all their power.  

On the short list is Condor, GridGain, Hadoop and more recently Kerrighed.  Reading BigJimJams excellent [guide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide") has opened my eyes to the possibility of network booting all the machines, for all the clustering options listed above, it seems so much easier than having to install/maintain each node.  Thanks to Jedi453s [post]("http://ubuntuforums.org/showpost.php?p=6922286&postcount=86") I've just managed to fix boot errors and get an Ubuntu 10.04 image to start (not moved on to Kerrighed kernal yet).  

I have a few noob questions which I hope you may be able to help with.

1) I can't find the package nfsbooted in lucid.  As a result I carried on without it and everything seems OK so far; the lucid net boot seems to work.  Someone pointed out to that I can get the package from [here]("http://packages.debian.org/lenny/nfsbooted"), but do I really need to?  What does this package do?

2) All the booted nodes seem to take on the same hostname.  They are able to ping each other by the proper hostname (presumably because of the /etc/hosts file), but it's doesn't seem right that they all have the same name on the command line.  How do other people address this?

3) Related to (2),  is it really viable to have each node booting from the same image at /nfsroot/kerrighed?  E.g. when one node runs a bit of software are create a lock file will this cause problems for all the other nodes?

Thanks for your help and thoughts.

---

### Post by joeinbend on 2010-06-09
Hey Penguin,
I'm in a very similar situation with wanting to build a PXE boot cluster. Have you made any further progress on this? Hopefully we can jumpstart this conversation!

---

### Post by ductiletoaster on 2010-06-16
ok so i was goin to use this [guide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide") to setup a cluster.

Available Computers:
```

AMD Athlon 64 3700 2.2 ghz (This one i was thinking about making a Gui workstation)
2gb DDR 400 RAM
200 gb HDD

AMD Athlon 64 3200 2.0 ghz
512mb DDR 400 RAM (might be 1gb don't remb)
160gb HDD

Pentium 4 1.7 ghz
256mb RAM
NO! HDD

Pentium 4 1.7 ghz
256mb RAM
NO! HDD

Celeron 667 mhz
192mb (might be 128mb)
15gb HDD

```

My Questions:
1) Does it matter that some of the CPU's are 32bit an others are 64bit? Keep in mind its a Diskless-boot Kerrighed Ubuntu Cluster...
2) And what would be the best way to partition the main servers hard drive(s)?

---

### Post by D3ATH-D3AL3R on 2010-06-17
Hi gys...
I am trying to set up a ubuntu cluster using kerrighed in virtual box. But i am stuck at the NFS part. When i boot my machines they are stuck in (initramfs) after showing the following error:

Gave up waiting for root devices.Common problems:
- Boot args (cat /proc/cmdline)
 - Check root delay (did the system wait long enough)
 - Check root (did the system wait for right devices)
- Missing modules (cat /proc/modules; ls dev)
ALERT! /dev/nfs does not exist. Dropping to a shell.

---

### Post by nerdopolis on 2010-06-17
/dev/null! Kerrighed 3.0.0 was released on Monday (6/14/2010)! 

**ductiletoaster:** If you use a 32 bit image, it should not matter as most 64 bit processors can emulate a 32 bit.

---

### Post by lrilling on 2010-06-18
> **D3ATH-D3AL3R said:**
> Hi gys...
I am trying to set up a ubuntu cluster using kerrighed in virtual box. But i am stuck at the NFS part. When i boot my machines they are stuck in (initramfs) after showing the following error:

Gave up waiting for root devices.Common problems:
- Boot args (cat /proc/cmdline)
 - Check root delay (did the system wait long enough)
 - Check root (did the system wait for right devices)
- Missing modules (cat /proc/modules; ls dev)
ALERT! /dev/nfs does not exist. Dropping to a shell.

Your initramfs was probably not configured for NFS root. With Debian's initramfs-tools, you can enable it in /etc/initramfs-tools/initramfs.conf.

Thanks,

Louis

---

### Post by lrilling on 2010-06-18
> **nerdopolis said:**
> **ductiletoaster:** If you use a 32 bit image, it should not matter as most 64 bit processors can emulate a 32 bit.

Except that Kerrighed 2.4's support for 32 bits is buggy, and Kerrighed 3.0 does not even compile on 32 bits.

Thanks,

Louis

---

### Post by nerdopolis on 2010-06-18
Is support for 32 bit processors completley dropped, or will it get 32 bit support back some time?

---

### Post by faisalmehmood on 2010-06-19
I'm still running openMosix (linux-2.4.26-om1), but I'm planning to upgrade to Kerrighed. I tried out openSSI under Ubuntu 6.06 and 8.04, but had a lot of problems just trying to get it to run. There was some discussion about SSI recently on the beowulf list.           ):P

---

### Post by lrilling on 2010-06-21
> **nerdopolis said:**
> Is support for 32 bit processors completley dropped, or will it get 32 bit support back some time?

It is not planned to get it back. Contributions are welcome though.

Thanks,

Louis

---

### Post by D3ATH-D3AL3R on 2010-06-22
> **lrilling said:**
> Your initramfs was probably not configured for NFS root. With Debian's initramfs-tools, you can enable it in /etc/initramfs-tools/initramfs.conf.

Thanks,

Louis

I did what you said. But still cant boot my nodes.BTW i am using ubuntu 9.04. Will it works??? (the guide is for ubuntu 8.04)

---

### Post by lrilling on 2010-06-23
> **D3ATH-D3AL3R said:**
> I did what you said. But still cant boot my nodes.BTW i am using ubuntu 9.04. Will it works??? (the guide is for ubuntu 8.04)

You may have to specify BOOT=nfs in kernel command line. Also make sure that your NIC driver is either built in the kernel, or is put in the initramfs. Again, this is how Debian's initramfs-tools works. I don't know if Ubuntu changes initramfs-tools.

Thanks,

Louis

---

### Post by D3ATH-D3AL3R on 2010-06-23
[SOLVED]
I read thread 155 (thanx to nerdopolis) and everything went fine.

Thnx again:)

---

### Post by a.kazemi on 2010-06-25
Hi dears
I want to run a sample MPI C or C++ program for example hello word on two computers running Ubuntu,Eclipse and MPI. I can run MPI on each of these two PC and define virtual nodes with this command: 
-np "number of nodes" ${workspace_loc:"project name"}/Debug/"project name" 
in the program arguments. it works fine :lolflag: and now I want to run distributed computing on two PCs connected to each other through ethernet P2P network. can anybody help me how to configure Eclipse and network connection to do this?
Maybe I have to mention that each of these PCs have just one core!

---

### Post by D3ATH-D3AL3R on 2010-06-27
Hi gys....
I am stuck in part 2 of the guide. I have compiled the kernel 3 times but every time i cant find the file /etc/kerrighed_nodes file. I have checked these files:

/boot/vmlinuz-2.6.20-krg (Kerrighed kernel)
/boot/System.map (Kernel symbol table)
/lib/modules/2.6.20-krg (Kerrighed kernel module)
/etc/init.d/kerrighed (Kerrighed service script)
/etc/default/kerrighed (Kerrighed service configuration file)
/usr/local/share/man/* (Look inside these subdirectories for Kerrighed man pages)
/usr/local/bin/krgadm (The cluster administration tool)
/usr/local/bin/krgcapset (Tool for setting capabilities of processes on the cluster)
/usr/local/bin/krgcr-run (Tool for checkpointing processes)
/usr/local/bin/migrate (Tool for migrating processes)
/usr/local/lib/libkerrighed-* (Libraries needed by Kerrighed)
/usr/local/include/kerrighed (Headers for Kerrighed libraries)

They are there but i dont know where i m going wrong. Moreover i dont have the grub folder in /boot. BTW i m using ubuntu 8.04.4 and i have gcc3.3 and gcc4.2 , g++3.3 and g++4.2. And my nodes are booting fine with the new kernel. But without the /etc/kerrighed_nodes file it is useless.

Thnx in advance....

---

### Post by lrilling on 2010-06-28
> **D3ATH-D3AL3R said:**
> And my nodes are booting fine with the new kernel. But without the /etc/kerrighed_nodes file it is useless.

You are supposed to write this file if you want to use it.
```
$ man 5 kerrighed_nodes
```details the contents of this file.

However, you should node that the use of /etc/kerrighed_nodes has been deprecated for a long time.  The related documentation has even been removed in Kerrighed 3.0.0.

Thanks,

Louis

---

### Post by D3ATH-D3AL3R on 2010-07-02
Hi gys... I have succesfully implemented kerrighed 2.4.1 in ubuntu 8.04. Now i m trying to set up a cluster with kerrighed 3.0 and ubuntu 9.04. I keep getting this error during kernel compilation.
CC      arch/x86/vdso/vdso32-setup.o
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:In function 'import_vdso_context': 
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:321: error: 'compat' undeclared (first use in this function) 
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:321: error: (Each undeclared identifier is reported only once 
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:321: error: for each function it appears in.)
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:322: error: 'vdso_pages' undeclared (first use in this function) 
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:324: warning: comparison between pointer and integer    
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:325: error: 'vdso_size' undeclared (first use in this function)
make[3]: *** [arch/x86/vdso/vdso32-setup.o] Error 1            make[2]: *** [arch/x86/vdso] Error 2     
make[1]: *** [sub-make] Error 2  
make: *** [all] Error 2

This error occurs during make command.

---

### Post by lrilling on 2010-07-05
> **D3ATH-D3AL3R said:**
> Hi gys... I have succesfully implemented kerrighed 2.4.1 in ubuntu 8.04. Now i m trying to set up a cluster with kerrighed 3.0 and ubuntu 9.04. I keep getting this error during kernel compilation.
CC      arch/x86/vdso/vdso32-setup.o
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:In function 'import_vdso_context': 
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:321: error: 'compat' undeclared (first use in this function) 
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:321: error: (Each undeclared identifier is reported only once 
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:321: error: for each function it appears in.)
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:322: error: 'vdso_pages' undeclared (first use in this function) 
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:324: warning: comparison between pointer and integer    
/usr/src/kerrighed-3.0.0/_kernel/arch/x86/vdso/vdso32-setup.c:325: error: 'vdso_size' undeclared (first use in this function)
make[3]: *** [arch/x86/vdso/vdso32-setup.o] Error 1            make[2]: *** [arch/x86/vdso] Error 2     
make[1]: *** [sub-make] Error 2  
make: *** [all] Error 2

This error occurs during make command.

You must disable IA32 emulation (see 
[http://www.kerrighed.org/wiki/index.php/FAQ#Which_kernel_options_should_I_enable.2Fdisable_.3F](http://www.kerrighed.org/wiki/index.php/FAQ#Which_kernel_options_should_I_enable.2Fdisable_.3F)).

I could swear I made this impossible to build a Kerrighed kernel with this option enabled. How did you configure the kernel?

Thanks,

Louis

---

### Post by Hereticq2 on 2010-07-06
> **lrilling said:**
> You must disable IA32 emulation (see 
[http://www.kerrighed.org/wiki/index.php/FAQ#Which_kernel_options_should_I_enable.2Fdisable_.3F](http://www.kerrighed.org/wiki/index.php/FAQ#Which_kernel_options_should_I_enable.2Fdisable_.3F)).

I could swear I made this impossible to build a Kerrighed kernel with this option enabled. How did you configure the kernel?

Thanks,

Louis

Hello. I have same problem.
I built a kernel in an automatic mode using the command build Kerrighed from the manual. [http://www.kerrighed.org/docs/releases/3.0/INSTALL](http://www.kerrighed.org/docs/releases/3.0/INSTALL)

After I got this error I tried to compile a kernel manually.
But menu&#1089;onfig haven't this option I'm build kernel with GCC-4.4. May be problem in GCC?

I'm use Ubuntu 10.04.

Other ideas? :) Thank you.

---

### Post by Erwanenharma on 2010-07-07
Hi Everyone!

I'm trying to set up a kerrighed cluster with this howto:
[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)

I have this problem:
root@kerrighedserver:/usr/src/kerrighed-2.4.1/kernel# make kernel-install

make -C /usr/src/kerrighed-2.4.1/_kernel O=/usr/src/kerrighed-2.4.1/kernel kernel-install
make[2]: *** No rule to make target `kernel-install'.  Stop.
make[1]: *** [kernel-install] Error 2
make: *** [kernel-install] Error 2


if anyone has answer please let me know... I'm stuck here.

Best regards.

---

### Post by lrilling on 2010-07-07
> **Hereticq2 said:**
> Hello. I have same problem.
I built a kernel in an automatic mode using the command build Kerrighed from the manual. [http://www.kerrighed.org/docs/releases/3.0/INSTALL](http://www.kerrighed.org/docs/releases/3.0/INSTALL)

After I got this error I tried to compile a kernel manually.
But menu&#1089;onfig haven't this option

Or are you trying to build for 32 bits? This is not supported and (my fault) not checked for in menuconfig.

Thanks,

Louis

---

### Post by Hereticq2 on 2010-07-07
> **lrilling said:**
> Or are you trying to build for 32 bits? This is not supported and (my fault) not checked for in menuconfig.

Thanks,

Louis
Ok, I understand.
Yes, I'm build in 32 bits.

---

### Post by D3ATH-D3AL3R on 2010-07-07
OK i get it.
I think i just have compile my kerrighed on 64 bit machine.
Thanks....:popcorn:

---

### Post by D3ATH-D3AL3R on 2010-07-07
> **Erwanenharma said:**
> Hi Everyone!

I'm trying to set up a kerrighed cluster with this howto:
[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)

I have this problem:
root@kerrighedserver:/usr/src/kerrighed-2.4.1/kernel# make kernel-install

make -C /usr/src/kerrighed-2.4.1/_kernel O=/usr/src/kerrighed-2.4.1/kernel kernel-install
make[2]: *** No rule to make target `kernel-install'.  Stop.
make[1]: *** [kernel-install] Error 2
make: *** [kernel-install] Error 2


if anyone has answer please let me know... I'm stuck here.

Best regards.

Hi [Erwanenharma]("http://ubuntuforums.org/member.php?u=1108434"),
I think i got the same error so i used kerrighed svn. It is listed in post #109 of this thread. After that everything went fine.

I hope it helps.:p

---

### Post by Hereticq2 on 2010-07-09
Hello,all.

I have cluster with 3 nodes in Intel Xeon CPU 2.40GHz. 
In /proc/cpuinfo i see 12 cpu, but if i run linpack banchmarks test, work only 4 cpu. 
Why? Or all cpus can work only with mpi? 

Legacy scheduler behaviour is running.
And sheduler i configure:
# krgcapset -d +CAN_MIGRATE
# krgcapset -k $$ -d +CAN_MIGRATE

Me intrested run virtualisation(virtualbox, vmware or other who can work) in my cluster. Can I do it with Kerrighed? And,can work virtualisation with all cpu in cluster?

Thanks

---

### Post by lrilling on 2010-07-09
> **Hereticq2 said:**
> Hello,all.

I have cluster with 3 nodes in Intel Xeon CPU 2.40GHz. 
In /proc/cpuinfo i see 12 cpu, but if i run linpack banchmarks test, work only 4 cpu. 
Why? Or all cpus can work only with mpi? 

Legacy scheduler behaviour is running.
And sheduler i configure:
# krgcapset -d +CAN_MIGRATE
# krgcapset -k $$ -d +CAN_MIGRATE

Note that the two lines above are equivalent, and will only do what you want if you launch the benchmark from the same shell.

> **Hereticq2 said:**
>  Me intrested run virtualisation(virtualbox, vmware or other who can work) in my cluster. Can I do it with Kerrighed? And,can work virtualisation with all cpu in cluster?

No known virtualization technology (VMware, Xen, VirtualBox, Qemu, KVM, Linux vservers, Linux containers) can benefit from Kerrighed right now. The most promising one is currently Linux containers (which should supersede Linux vservers some day). Qemu, and maybe later KVM could benefit from Kerrighed's migration in some future, but not from resource aggregation (especially CPUs).

Thanks,

Louis

---

### Post by Hereticq2 on 2010-07-09
> **lrilling said:**
> Note that the two lines above are equivalent, and will only do what you want if you launch the benchmark from the same shell.
Louis

Sorry, don't understand. Where I need launch benchmark?
I'm login in first kerrighed node and launch benchmark there.

---

### Post by D3ATH-D3AL3R on 2010-07-10
Hi gys....
I had set up a kerrighed cluster as a project for my college. Can anyone list some applications in which thread migration or process migration is shown in graphical or textual form.

---

### Post by ajt on 2010-07-11
> **D3ATH-D3AL3R said:**
> Hi gys....
I had set up a kerrighed cluster as a project for my college. Can anyone list some applications in which thread migration or process migration is shown in graphical or textual form.

Hello, D3ATH-D3AL3R.

There was a graphical tool to show migration in openMosix:

[http://www.openmosixview.com/](http://www.openmosixview.com/)

However this, like openMosix itself, is now unsupported...

I've been thinking about porting "mosmon" from openMosix to Kerrighed, but I've not done it yet. Might be nice if someone ports openMosix view :-)

Bye,

  Tony.

---

### Post by ajt on 2010-07-11
> **lrilling said:**
> You may have to specify BOOT=nfs in kernel command line. Also make sure that your NIC driver is either built in the kernel, or is put in the initramfs. Again, this is how Debian's initramfs-tools works. I don't know if Ubuntu changes initramfs-tools.


Hello, Louis.

AFAIK Ubuntu works the same way as Debian, but I find it a lot easier to build the NIC driver into the kernel and PXE-boot without an initrd :-)

Bye,

  Tony.

---

### Post by ajt on 2010-07-11
I'm going to try booting nodes on our Kerrighed Beowulf using Perceus:

[http://www.perceus.org](http://www.perceus.org)

I mentioned Perceus some time ago on this thread - has anyone succeeded in setting up Perceus for node provisioning in a Kerrighed Beowulf cluster?

At present, I'm using a home-brew system based on UNFS3 with 'clusterNFS' extensions enabled. Interestingly, Oracle use similar 'context' dependent symbolic links in OCFS (Oracle Cluster File System):

[http://www.dba-oracle.com/real_application_clusters_rac_grid/cdsl.html](http://www.dba-oracle.com/real_application_clusters_rac_grid/cdsl.html)

Although OCFS was designed to support Oracle databases, they have recently added POSIX compatibility to OCFS so it can be used as a general purpose filesystem. Perceus does things quite differently...

Bye,

  Tony.

---

### Post by daniele.fetoni on 2010-07-19
Hi guys

I have already build a kerrighed 2.4 cluster, but now I am struggling with kerrighed 3.0.0.
I have build (several times)  with no errors the kernel over a debian lenny distro AMD64.
Machines can net boot without problem, but after loading vmlinuz-2.6.30-krg3.0.0, they crash and then reboot, then crash and reboot again and again...
I know that dhcp, tftp, nfs server works fine, so I think that there must be some troubles in the kernel. Maybe I should tick some options in menuconfig, or something similar.
My question is simple. Could anyone who managed to build a working kerrighed cluster tell me how he/she makes kernel?
Please, I need to use kerrighed 3.0.0 because of nodes hotplug improvement. 
Thanks a lot
Daniele

---

### Post by lrilling on 2010-07-20
> **ajt said:**
> AFAIK Ubuntu works the same way as Debian, but I find it a lot easier to build the NIC driver into the kernel and PXE-boot without an initrd :-)


I agree with you.

However, who knows what essential thing distros might put in their initramfs? So I don't try to convince people of not using an initramfs, because I could get far more questions for which I would have no answer ;)

Thanks,

Louis

---

### Post by lrilling on 2010-07-20
> **Hereticq2 said:**
> Sorry, don't understand. Where I need launch benchmark?
I'm login in first kerrighed node and launch benchmark there.

You need to launch the benchmark from the very same shell in which you entered the krgcapset commands that you mentioned. You might already do it correctly, but having not seen any definite evidence of it, I recall this rule.

Thanks,

Louis

---

### Post by lrilling on 2010-07-20
> **D3ATH-D3AL3R said:**
> Hi gys....
I had set up a kerrighed cluster as a project for my college. Can anyone list some applications in which thread migration or process migration is shown in graphical or textual form.

There is some project about this at Polytech'Tours (a french college). You could have a look at this video (in french, sorry): [http://www.youtube.com/user/mistergom](http://www.youtube.com/user/mistergom).
Alexandre Lissy is the guy leading this project. You can get his email from kerrighed.users mailing list or its partial mirroring in gmane [http://news.gmane.org/gmane.linux.cluster.kerrighed.user](http://news.gmane.org/gmane.linux.cluster.kerrighed.user)

Thanks,

Louis

---

### Post by mrrstrat on 2010-07-22
OK: now I am chiming in.
 
I do have a 'cookbook' list of instructions I created for setting up an Ubuntu-based high performance computing cluster (based on a Beowulf design).
 
The topology is:
* One main computer
* several diskless/monitorless PCs that TFTP recieve a linux kernal and boot up
* 100BT connected with a switch for fastest messaging
* a common landing zone (directory) for the cluster all PCs use
* Uses SSH to pass messages with OpenMPI
* Supports Open MPI C++/Fortran
 
How it works is it allows one computer to have all the dev tools and hosts the other computers that upon being turned on Netboot into the host machine. Then, you simply create programs using the OpenMPI compier and mpirun the jobs.
 
I am getting about 20x power over a single processesor computer with a couple of AM2 and several 400FSB XP3000 machines. The satellite computers have their MAC addresses manually setup, and this made implementation MUCH easier.
 
I just upgraded to 10.04 LTS, and am going to resetup everything (it takes under an hour). I made the instructions as such I could resetup everything quickly without having to remember how I did it each time.
 
I WILL post this PDF this weekend after I setup the cluster again.
 
I had to creat this set of instructions because I could not find a set of instructions that was easy to setup a HPC cluster. I based it on MANY different sources and in stages perfected a simple way to do it. The posts I have read here pushed me to figure it out: lots of fragmented advice, but NO EASY BRAINLESS way to do it.
 
And: I did not settle for anything less than a true HPC cluster that supports the latest OpenMPI downloads.

---

### Post by danmc on 2010-07-26
> **mrrstrat said:**
> OK: now I am chiming in.
 
I do have a 'cookbook' list of instructions I created for setting up an Ubuntu-based high performance computing cluster (based on a Beowulf design).
 
The topology is:
* One main computer
* several diskless/monitorless PCs that TFTP recieve a linux kernal and boot up
* 100BT connected with a switch for fastest messaging
* a common landing zone (directory) for the cluster all PCs use
* Uses SSH to pass messages with OpenMPI
* Supports Open MPI C++/Fortran
 
How it works is it allows one computer to have all the dev tools and hosts the other computers that upon being turned on Netboot into the host machine. Then, you simply create programs using the OpenMPI compier and mpirun the jobs.
 
I am getting about 20x power over a single processesor computer with a couple of AM2 and several 400FSB XP3000 machines. The satellite computers have their MAC addresses manually setup, and this made implementation MUCH easier.
 
I just upgraded to 10.04 LTS, and am going to resetup everything (it takes under an hour). I made the instructions as such I could resetup everything quickly without having to remember how I did it each time.
 
I WILL post this PDF this weekend after I setup the cluster again.
 
I had to creat this set of instructions because I could not find a set of instructions that was easy to setup a HPC cluster. I based it on MANY different sources and in stages perfected a simple way to do it. The posts I have read here pushed me to figure it out: lots of fragmented advice, but NO EASY BRAINLESS way to do it.
 
And: I did not settle for anything less than a true HPC cluster that supports the latest OpenMPI downloads.

I would love a look at that I'm looking into using a parallel cluster for a remote rendering project and a lot of the guides I have been looking at are either outdated or just don't quite work.

---

### Post by singing accordionist on 2010-07-26
Is the recipe download file still available somewhere?

---

### Post by mrrstrat on 2010-07-26
Here is the version that sets up my cluster:

This is setup for a 32/64 bit master node and the kernels for each node can be 32/64 bit.:popcorn:

**Be warned: you have to have a clue about Linux and basic computer network topology**. In this guide (if you can call it that) I setup my M5 computing cluster. This is basically a collective document from many other sources with my changes in how I setup my HPC.

For me, this is what I needed: just a list of things to do, files to edit, and things to look for to be sure its working. I actually paste in the blue text into the files referred to in the guide. I did not write this for mass-consumption (meaning other people), but this may be a welcomed help for others just trying to get a HPC going and not wanting to have an army of PCs with booting CDs (which works for some, but not me).

I just wanted something I could drop in cheap motherboards into with the most minimum of hardware (no disks, video cards if possible, no CDs).

---

### Post by mrrstrat on 2010-07-26
I just want to add in that while I 'hijacked' other recipes for setting up a Linux HPC, I had to have a solution that used a 'standard' installation, as I use my computer for many different things as well as a HPC.
 
* Again: this guide was never supposed to get posted, but I have had a few people ask about it. So if you can overlook the 'edgy' writing style, you can use it now *
 
I am using the standard Linux kernals that have the small change to boot from NFS: I list how I got it to work in the text. I did not want a bunch of custom kernals to download and maintain that might clash with my host system. After all: I wanted to program for a HPC and not spend time debugging why its not working.
 
I had to have something I could replicate with whatever version of Ubuntu I had. And this 'guide' assumes Ubuntu. I also am assuming that a user wants a 'main node' that writes software to be launched on the connected nodes using MPI (with ssh).
 
The NFS directory created in the guide was a 32-bit installation that my 64-bit host would remote compile code for. This was a pain, so now I have everything 32-bit: so I compile on the host and launch from the host.
 
If you are wanting to setup a mixed kernal system with 32 and 64 bit, I can tell you it is no advantage (I have found). The pain of keeping 32-bit extensions in 64-bit environment and the lack of support in 64-bit for some 32-bit activities made the benefit of having 32/64 operation non-existant.
 
I was able to easily maintain the constant stream of kernal updates with the method in the guide I made, and it was STABLE and I never had to work on it.
 
I manually would start the cluster (three services needed to start DHCP, FTP, SSH). I had some simple checks to make sure things were working including a simple MPI program that would run on all of the nodes to make sure everthing was working. I never had problems and basically followed the guide I wrote.
 
The guide uses DHCP 3x, and used JAUNTY as the NFS OS the nodes used. Both of these should be able to be changed as needed (as I will verify this weekend to support my 32-bit Ubuntu 10.04 LTS main node).

---

### Post by ductiletoaster on 2010-07-27
> except that Kerrighed 2.4's support for 32 bits is buggy, and Kerrighed 3.0 does not even compile on 32 bits.

Ok so even though it cant be compiled on a 32bit system can i still use a 32bit diskless node. My main node would be 64bit?

---

### Post by lrilling on 2010-07-27
> **ductiletoaster said:**
> Ok so even though it cant be compiled on a 32bit system can i still use a 32bit diskless node. My main node would be 64bit?

No. Kerrighed kernels only run on 64 bits hardware. If your "main" node is the NFS server and is not part of the SSI cluster, yes you should be able to use a 32 bit machine for it.

Thanks,

Louis

---

### Post by ductiletoaster on 2010-07-28
Ok so to clarify... Kerrighed wont run on 32bit (GOT that) but you said i can still use the 32bit hardware if the main node is not part of a ssi cluster?

---

### Post by lrilling on 2010-07-28
> **ductiletoaster said:**
> Ok so to clarify... Kerrighed wont run on 32bit (GOT that) but you said i can still use the 32bit hardware if the main node is not part of a ssi cluster?

You can use 32 bit hardware, but only for the main node, and only if it is not part of the SSI cluster.

Hope it's clearer...

Thanks,

Louis

---

### Post by ductiletoaster on 2010-07-29
Yes thank you that helped. Us there any particular guides that are geared toward clusters running 32bit hardware. My issue is that I have several computers (listed below)
```

AMD Athlon 64 3700 2.2 ghz (64bit *was planning on using as the "main node")
2gb DDR 400 RAM
200 gb HDD

AMD Athlon 64 3200 2.0 ghz (64bit)
512mb DDR 400 RAM (might be 1gb don't remb)
160gb HDD

Pentium 4 1.7 ghz (32bit)
256mb RAM
NO! HDD

Pentium 4 1.7 ghz (32bit)
256mb RAM
NO! HDD

Celeron 667 mhz (32bit)
192mb (might be 128mb)
15gb HDD

```

As you can see three of the machines are 32 and 2 are 64. Im trying to figure out how could I run them together as a cluster. Also keep in mind i wanted to setup the system so that all but the first machine would be disk less (I have to make sure this is possible with all the machines). How ever I am open to any suggestions

---

### Post by danmc on 2010-08-01
> **mrrstrat said:**
> Here is the version that sets up my cluster:

This is setup for a 32/64 bit master node and the kernels for each node can be 32/64 bit.:popcorn:

**Be warned: you have to have a clue about Linux and basic computer network topology**. In this guide (if you can call it that) I setup my M5 computing cluster. This is basically a collective document from many other sources with my changes in how I setup my HPC.

For me, this is what I needed: just a list of things to do, files to edit, and things to look for to be sure its working. I actually paste in the blue text into the files referred to in the guide. I did not write this for mass-consumption (meaning other people), but this may be a welcomed help for others just trying to get a HPC going and not wanting to have an army of PCs with booting CDs (which works for some, but not me).

I just wanted something I could drop in cheap motherboards into with the most minimum of hardware (no disks, video cards if possible, no CDs).

Thanks for the guide it works great in 8.04 with a couple of slight modifications, but for the life of me I can't get this to work with 9.04 which unfortunately is the version I need due to blender disliking 8.04.:(

---

### Post by ductiletoaster on 2010-08-02
I had blender running fine on 8.04LTS. You could also try 10.04.

I personally have found that .10 releases are usually unreliable! If your doing development work and need reliability use .04...

---

### Post by danmc on 2010-08-03
> **ductiletoaster said:**
> I had blender running fine on 8.04LTS. You could also try 10.04.

I personally have found that .10 releases are usually unreliable! If your doing development work and need reliability use .04...

The latest version won't it has dependencies that aren't in 8.04's repos, it's a catch22 situation. 

I can get 8.04 pxe booting no problem but 9.04 jut hangs and go's to an ALERT! /dev/nfs does not exist error even though I have used the exact same techniques:(?.

---

### Post by gabrielaca on 2010-08-06
> **danmc said:**
> The latest version won't it has dependencies that aren't in 8.04's repos, it's a catch22 situation. 

I can get 8.04 pxe booting no problem but 9.04 jut hangs and go's to an ALERT! /dev/nfs does not exist error even though I have used the exact same techniques:(?.

 hello danmc, by latest version you mean Blender 2.5(BETAs), i havent got my cluster yet but want to run some 3D Blender and Lux in it, so as of now only Blender 2.49 can run on the HPC.

---

### Post by nerdopolis on 2010-08-06
Kerrighed seems to have virtual images on their site. [http://www.kerrighed.org/forum/viewtopic.php?p=615#615](http://www.kerrighed.org/forum/viewtopic.php?p=615#615)

---

### Post by phydiux on 2010-08-07
> **lrilling said:**
> Or are you trying to build for 32 bits? This is not supported and (my fault) not checked for in menuconfig.

Thanks,

Louis

Can anyone chime in and tell me what the last version that worked with 32-bit processors was? I'm trying to install Kerrighed 2.4.4, but am getting:

"make[2]: *** No rule to make target `kernel-install'.  Stop."

when issuing "make kernel-install" - I don't have the option on the computers that I want to cluster to run 64-bit Linux, so I'm kind of stuck. I also tried with Kerrighed version 2.4.1 and get the same error.

Thanks in advance...

---

### Post by phydiux on 2010-08-08
> **phydiux said:**
> Can anyone chime in and tell me what the last version that worked with 32-bit processors was?

An update: I've been able to compile 2.4.4 by not making any changes under the /usr/src/kerrighed-2.4.4/kernel/ directory and doing a make and then make install from the kerrighed-2.4.4 directory (basically, skipping the following from the guide)

```

# cd kernel
# make defconfig
# make menuconfig
# make kernel
# make kernel-install

```

and instead, from /use/src/kerrighed-2.4.4/, simply doing this:

```

# make
# make install

```

My kerrighed compiled properly and I was able to follow the rest of the guide through to completion.

I now have an 18 node cluster running - here's my top:

```

top - 09:31:57 up 29 min,  1 user,  load average: 1.07, 4.41, 6.03
Tasks: 319 total,   1 running, 318 sleeping,   0 stopped,   0 zombie
Cpu352:  0.7%us,  0.7%sy,  0.0%ni, 94.8%id,  0.0%wa,  0.2%hi,  3.5%si,  0.0%st
Cpu384:  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  1.0%si,  0.0%st
Cpu416:  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  1.0%si,  0.0%st
Cpu448:  0.0%us,  0.0%sy,  0.0%ni, 98.2%id,  0.0%wa,  0.2%hi,  1.5%si,  0.0%st
Cpu480:  0.0%us,  0.2%sy,  0.0%ni, 98.0%id,  0.0%wa,  0.2%hi,  1.5%si,  0.0%st
Cpu512:  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Cpu544:  0.0%us,  0.3%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Cpu576:  0.0%us,  0.0%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  1.3%si,  0.0%st
Cpu608:  0.0%us,  0.2%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.2%hi,  1.2%si,  0.0%st
Cpu640:  0.0%us,  0.2%sy,  0.0%ni, 98.5%id,  0.0%wa,  0.2%hi,  1.0%si,  0.0%st
Cpu672:  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Cpu704:  0.0%us,  0.2%sy,  0.0%ni, 98.5%id,  0.0%wa,  0.0%hi,  1.2%si,  0.0%st
Cpu736:  0.0%us,  0.2%sy,  0.0%ni, 98.8%id,  0.0%wa,  0.2%hi,  0.7%si,  0.0%st
Cpu768:  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  1.0%si,  0.0%st
Cpu800:  0.0%us,  0.0%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.7%si,  0.0%st
Cpu832:  0.0%us,  0.2%sy,  0.0%ni, 98.2%id,  0.0%wa,  0.2%hi,  1.2%si,  0.0%st
Cpu864:  0.0%us,  0.0%sy,  0.0%ni, 98.5%id,  0.0%wa,  0.0%hi,  1.5%si,  0.0%st
Cpu896:  0.0%us,  0.0%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  1.3%si,  0.0%st
Mem:  11569408k total,   503476k used, 11065932k free,        0k buffers
Swap:        0k total,        0k used,        0k free,   232412k cached

```

18 processors, with 11.5 Gigs of RAM - I'm happy with that. I have room for two more machines in my rack, so I will probably bump the cluster up to 20 computers. It's now time to do some testing :) Thanks for the wonderful amount of information in this thread - it's been a great help on getting my cluster up and running.

---

### Post by ajt on 2010-08-16
I decided to replace our UNFS3+ClusterNFS stateless node provisioning with Perceus. We've got Perceus 1.6 installed from the deb:

[http://http://altruistic.infiscale.org/deb/perceus16.deb]("http://http://altruistic.infiscale.org/deb/perceus16.deb")

And we can boot nodes from the "gravityos-base" VNFS:

[http://http://altruistic.infiscale.org/~ian/gravityos-base.vnfs]("http://http://altruistic.infiscale.org/~ian/gravityos-base.vnfs")

So far, I've only been able to find a VNFS generation script for 32-bit Ubuntu 8.04:

[http://http://www.cs.indiana.edu/~adkulkar/perceus-ubuntu/]("http://http://www.cs.indiana.edu/~adkulkar/perceus-ubuntu/")

Does anyone know of a script to create a 64-bit Ubuntu 10.04 VNFS?

Thanks,

  Tony.

---

### Post by ajt on 2010-08-16
> **phydiux said:**
> An update: I've been able to compile 2.4.4 by not making any changes under the /usr/src/kerrighed-2.4.4/kernel/ directory and doing a make and then make install from the kerrighed-2.4.4 directory (basically, skipping the following from the guide)

[...]

18 processors, with 11.5 Gigs of RAM - I'm happy with that. I have room for two more machines in my rack, so I will probably bump the cluster up to 20 computers. It's now time to do some testing :) Thanks for the wonderful amount of information in this thread - it's been a great help on getting my cluster up and running.

Hello, phydiux.

We got this far, but found the cluster very fragile and have gone back to 2.3.0 which is more stable in our hands. Have you done much testing?

Bye,

  Tony.

---

### Post by ductiletoaster on 2010-08-25
To phydiux:
So are u saying u have 32bit only CPU's in your system by using your method? or are all of you computers have 64bit processors?

as i have mentioned in a previous post i have 5 machines and only two of which are 64 bit machines. Now the 32bit machines are older but they would add about 4.067ghz processing and 704mbs ram

---

### Post by phydiux on 2010-08-27
> **ajt said:**
> We got this far, but found the cluster very fragile and have gone back to 2.3.0 which is more stable in our hands. Have you done much testing?

Actually, I haven't had a chance to play with the cluster in the last week, but it did seem to be fragile when I was working on it. I was running distributed.net to test the cluster, and it seemed like processes would show that they were working but hang on the cluster in no specific manner or for no specific reason. This happened regardless of whether or not I was using memory sharing on the cluster. If I issued a "dnetc -shutdown", the processes would not shut down, and I would have to shutdown the cluster to get the processes to actually shut down. I thought there was some quirk with dnetc, so I assumed that I would look for another piece of software to test with - I just had not had the time to do that yet. So, I can say that the stability was questionable. Now that you mention that, I think I will compile kerrighed 2.3.0 and see if that works better for me. I hope it does.

> **ductiletoaster said:**
> So are u saying u have 32bit only CPU's in your system by using your method? or are all of you computers have 64bit processors?

All of the machines in my cluster are 32-bit machines. The are not capable of running a 64-bit OS - they're all PentiumIII class processors.

> **ductiletoaster said:**
> as i have mentioned in a previous post i have 5 machines and only two of which are 64 bit machines. Now the 32bit machines are older but they would add about 4.067ghz processing and 704mbs ram

Well, you could compile Kerrighed as a 32-bit cluster (your 64-bit machines don't *have* to run 64-bit - they are still capable of running 32-bit) - the downside to this is that you can't run Kerrighed 3.x, you need to run the 2.x version of Kerrighed.

Does anyone know why they dropped 32-bit support in 3.x?

I'm at a crossroads right now - it's hard to stick with the 32-bit Kerrighed since they're no longer targeting/allowing 32-bit systems in the new versions, but at the same time I have 18Ghz worth of 32-bit processors along with over 11 gigs of RAM  available if I stay 32-bit, and that whole setup is just sitting there doing nothing. If I use more current hardware, I'm probably in a better spot long-term, but at more expense, and I would have to purchase that stuff, since I don't have it sitting around.

---

### Post by lrilling on 2010-08-31
> **phydiux said:**
> Does anyone know why they dropped 32-bit support in 3.x?

Hello phydiux,

To be fair 32 bit support was already dropped with Kerrighed 2.4. The difference in Kerrighed 3.0 is that it does not build anymore for 32 bit.

The big reason for dropping 32 bit is the restricted manpower that we have. We prefer to focus on stability/features/performance for today's and tomorrow's machine, rather than investing time in keeping yesterday's machine alive.

Another reason is that no customer seems interested in paying for 32 bit support. In other words, nobody seems willing to fund developers for 32 bit.

Thanks,

Louis

---

### Post by amiller2k10 on 2010-09-12
> **phydiux said:**
> An update: I've been able to compile 2.4.4 by not making any changes under the /usr/src/kerrighed-2.4.4/kernel/ directory and doing a make and then make install from the kerrighed-2.4.4 directory (basically, skipping the following from the guide)

```

# cd kernel
# make defconfig
# make menuconfig
# make kernel
# make kernel-install

```

and instead, from /use/src/kerrighed-2.4.4/, simply doing this:

```

# make
# make install

```

My kerrighed compiled properly and I was able to follow the rest of the guide through to completion.

I now have an 18 node cluster running - here's my top:

```

top - 09:31:57 up 29 min,  1 user,  load average: 1.07, 4.41, 6.03
Tasks: 319 total,   1 running, 318 sleeping,   0 stopped,   0 zombie
Cpu352:  0.7%us,  0.7%sy,  0.0%ni, 94.8%id,  0.0%wa,  0.2%hi,  3.5%si,  0.0%st
Cpu384:  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  1.0%si,  0.0%st
Cpu416:  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  1.0%si,  0.0%st
Cpu448:  0.0%us,  0.0%sy,  0.0%ni, 98.2%id,  0.0%wa,  0.2%hi,  1.5%si,  0.0%st
Cpu480:  0.0%us,  0.2%sy,  0.0%ni, 98.0%id,  0.0%wa,  0.2%hi,  1.5%si,  0.0%st
Cpu512:  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Cpu544:  0.0%us,  0.3%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Cpu576:  0.0%us,  0.0%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  1.3%si,  0.0%st
Cpu608:  0.0%us,  0.2%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.2%hi,  1.2%si,  0.0%st
Cpu640:  0.0%us,  0.2%sy,  0.0%ni, 98.5%id,  0.0%wa,  0.2%hi,  1.0%si,  0.0%st
Cpu672:  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Cpu704:  0.0%us,  0.2%sy,  0.0%ni, 98.5%id,  0.0%wa,  0.0%hi,  1.2%si,  0.0%st
Cpu736:  0.0%us,  0.2%sy,  0.0%ni, 98.8%id,  0.0%wa,  0.2%hi,  0.7%si,  0.0%st
Cpu768:  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  1.0%si,  0.0%st
Cpu800:  0.0%us,  0.0%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.7%si,  0.0%st
Cpu832:  0.0%us,  0.2%sy,  0.0%ni, 98.2%id,  0.0%wa,  0.2%hi,  1.2%si,  0.0%st
Cpu864:  0.0%us,  0.0%sy,  0.0%ni, 98.5%id,  0.0%wa,  0.0%hi,  1.5%si,  0.0%st
Cpu896:  0.0%us,  0.0%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  1.3%si,  0.0%st
Mem:  11569408k total,   503476k used, 11065932k free,        0k buffers
Swap:        0k total,        0k used,        0k free,   232412k cached

```

18 processors, with 11.5 Gigs of RAM - I'm happy with that. I have room for two more machines in my rack, so I will probably bump the cluster up to 20 computers. It's now time to do some testing :) Thanks for the wonderful amount of information in this thread - it's been a great help on getting my cluster up and running.


I managed to get the Kernel to compile and installed on a local hard drive.  It boots up.  Kerrighed starts, etc.  I tried setting it up on a NFS now.  I can boot from the NFS using a non-KRG kernel.  However, when I use the KRG kernel; it will not boot.  It downloads the kernel.  Even gets as far as showing me kerrighed information on the boot screen.  But, then it says the NFS is not responding.  I assume this is when the kernel tries to mount the root file system.  Note, I have root file system on (not a module) in the kernel as well as nfs file system and nfs server support.  I also found another NFS tutorial that said to turn on bootp and rarp under networking options but that didn't help..  It seems like I've tried the things mentioned on this thread, any ideas??

I ultimately like to get this running on Ubuntu 10.04 but I installed 8.04 just to try and rule out some upgrade issues.  I am trying the 2.4.1 version of kerrighed.  Any ideas??

Thanks.

---

### Post by ajt on 2010-09-13
> **amiller2k10 said:**
> 
[...]
It seems like I've tried the things mentioned on this thread, any ideas??

I ultimately like to get this running on Ubuntu 10.04 but I installed 8.04 just to try and rule out some upgrade issues.  I am trying the 2.4.1 version of kerrighed.  Any ideas??

Thanks.

Hello, amiller2k10.

It's possible that you've not compiled the Kerrighed kernel with support for your network card built-in, if the NFSROOT filesystem is inaccessible.

HTH,

  Tony.

---

### Post by amiller2k10 on 2010-09-13
> **ajt said:**
> Hello, amiller2k10.

It's possible that you've not compiled the Kerrighed kernel with support for your network card built-in, if the NFSROOT filesystem is inaccessible.

HTH,

  Tony.


Hey Tony, 

Good thought but unless I am looking at this the wrong way, it appears to be built-in.  I am using an NVIDIA network card.  From what I understand, they use the forcedeth driver.  In my .config, I have CONFIG_FORCEDETH=y (asterisk in menuconfig).  

Unless I am missing something, shouldn't that cover it?

Thanks, 
Tony

---

### Post by amiller2k10 on 2010-09-14
Well it isn't the kernel.  I finally got it booting.  It appears there is something going on with the NFS server.  Time to troubleshoot it!!

---

### Post by anshumax on 2010-10-06
Hello everyone,
I'm a newbie to cluster systems and just wanted to make a basic cluster system of with my PC and the laptops I have at home. For the time being, my aim is to setup a simple 1 headnode(ie. my laptop) and 1 node(ie. my PC) cluster. I've followed the Easy Ubuntu Clustering guide and followed the steps in it. I had trouble at many steps but I managed to troubleshoot them by reading the posts in this thread. I first managed to boot into a a basic ubuntu hardy system as described by in the guide by making changes to the initrd.img by changing it to BOOT=nfs. The minimal hardy I installed using debootstrap works fine. I'm able to view to the NFS filesystem as well. It prompts for a login at the starting and I login and I'm at the console of the node. IS works because when I do something like 'cd /usr/var/' and then 'ls' it shows me the kerrighed and linux tarballs and the extracted folders. 
But when I build a kerrighed kernel and boot into it, the same setup gives me an error:
> Looking up port of RPC 100005/1 on 192.168.1.1
Portmap: server 191.168.1.1 not responding, timedout
Root-NFS: unable to get mountd port number from server, using default mount: Server 192.168.1.1 not responding, timed out
Root-NFS: Server returned error-5 while mounting /nfsroot/kerrighed
VFS: unable to mount root fs via NFS, tyring floppy.
VFS: Insert root floppy and press ENTER

My headnode ie. kerrighedserver is 192.168.1.1 and kerrighednode1 is 192.168.1.101
Now the funny thing is that when I modify the /var/lib/tftpboot/pxelinux.cfg/default file and change it to 'KERNEL vmlinuz-2.6.32-25-generic' and 'initrd=initrd.img-2.6.32-25-generic', the system boots into the minimal hardy system (Yes, I know I'm using the 2.6.32-25 kernel for minimal hardy installation because I have ubuntu 10.04 installed on my laptop but I've installed hardy using debootstrap to /nfsroot/kerrighed)

The kerrighed kernel built easily upon following the steps in the guide.
 
Why does NFS work with the linux kernel(ie. vmlinuz-2.6.32-25-generic and initrd.img-2.6.32-25-generic) but not with the Kerrighed kernel(vmlinuz-2.6.20-krg)?

---

### Post by anshumax on 2010-10-06
OK here's the contents of all the files mentioned in the guide.
/etc/default/dhcp3-server :
> 
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp

INTERFACES="eth0";


/etc/dhcp3/dhcpd.conf :
> 

# /etc/dhcp3/dhcpd.conf #
# General options
option dhcp-max-message-size 2048;
use-host-decl-names on;
deny unknown-clients; # This will stop any non-node machines from appearing on the cluster network.
deny bootp;

# DNS settings
option domain-name "kerrighed";          # Just an example name - call it whatever you want.
option domain-name-servers 192.168.1.1;  # The server's IP address, manually configured earlier.

# Information about the network setup
subnet 192.168.1.0 netmask 255.255.255.0 {
  option routers 192.168.1.1;              # Server IP as above.
  option broadcast-address 192.168.1.255;  # Broadcast address for your network.
}

# Declaring IP addresses for nodes and PXE info
group {
  filename "pxelinux.0";                 # PXE bootloader. Path is relative to /var/lib/tftpboot
  option root-path "192.168.1.1:/nfsroot/kerrighed";  # Location of the bootable filesystem on NFS server

  host kerrighednode1 {
        fixed-address 192.168.1.101;          # IP address for the first node, kerrighednode1 for example.
        hardware ethernet 00:1C:C0:02:FB:74;  # MAC address of the node's ethernet adapter
  }



  server-name "kerrighedserver"; # Name of the server. Call it whatever you like.
  next-server 192.168.1.1;       # Server IP, as above.
}



/etc/default/tftpd-hpa :
> 

# /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure"
RUN_DAEMON="YES"
OPTIONS="-l -s /var/lib/tftpboot"


/var/lib/pxelinux.cfg/default :
> 
LABEL linux  
KERNEL vmlinuz-2.6.20-krg
APPEND root=/dev/nfs noinitrd nfsroot=192.168.1.1:/nfsroot/kerrighed ip=dhcp rw  boot=nfs


/etc/exports :
> 

/nfsroot *(rw,async,no_root_squash,no_subtree_check)
/nfsroot/kerrighed *(rw,async,no_root_squash,no_subtree_check)


/nfsroot/kerrighed/etc/fstab :
> 

# <file system> <mount point> <type> <options> <dump> <pass>
proc            /proc         proc   defaults       0      0
/dev/nfs        /             nfs    defaults       0      0
configfs        /config         configfs        defaults        0 0


/nfsroot/kerrighed/etc/fstab :
> 

127.0.0.1 localhost

192.168.1.1    kerrighedserver
192.168.1.101  kerrighednode1


/nfsroot/kerrighed/etc/network/interfaces :
> 

# The loopback interface:
auto lo
iface lo inet loopback

# The primary network interface, manually configured to protect NFS:
iface eth0 inet manual


I'll be happy to post the contents of any other file that might help in solving this problem. 
Cheers and thanks!

---

### Post by ajt on 2010-10-06
> **anshumax said:**
> Hello everyone,
[...]
Why does NFS work with the linux kernel(ie. vmlinuz-2.6.32-25-generic and initrd.img-2.6.32-25-generic) but not with the Kerrighed kernel(vmlinuz-2.6.20-krg)?

Hello, anshumax.

The default kerrighed kernel does not use an initrd, so you have to compile the correct ethernet driver into the kernel in order to access the NFSROOT.

HTH,

  Tony.

---

### Post by anshumax on 2010-10-06
> **ajt said:**
> Hello, anshumax.

The default kerrighed kernel does not use an initrd, so you have to compile the correct ethernet driver into the kernel in order to access the NFSROOT.

HTH,

  Tony.

Hi Tony,
Yes I know that by default the Kerrighed kernel does not require an initrd. I removed the line 'initrd=initrd.img-2.6.-32-25-generic' from the pxelinux.cfg/default file.

anshumax

---

### Post by mazimi on 2010-11-29
Hi,

This thread along with the Wiki article was very helpful in setting up my Kerrighed cluster.  I currently have a system consisting of 20 nodes.  The head node is running Ubuntu 10.04 x64, DHCP, TFTP and NFS.  The remaining 19 compute nodes are running Ubuntu 8.04 x64 with Kerrighed 2.4.1.  I have access to the head node via SSH as it is connected to the network.  The 19 compute nodes are not directly connected to the network and to access any one of them I first have to SSH to the head node and from there SSH to any compute node.  I can run jobs from the compute nodes and can have the application use memory from the entire cluster.

My question is how can I make it so that users can simply login to the head node and submit their jobs there without having to access the kerrighed cluster?  Is this even possible?  If not, should I connect one of the compute nodes to the network and have my users SSH to that and submit jobs from there?  Any help/advice would be appreciated.

---

### Post by lrilling on 2010-11-30
> **mazimi said:**
> Hi,

This thread along with the Wiki article was very helpful in setting up my Kerrighed cluster.  I currently have a system consisting of 20 nodes.  The head node is running Ubuntu 10.04 x64, DHCP, TFTP and NFS.  The remaining 19 compute nodes are running Ubuntu 8.04 x64 with Kerrighed 2.4.1.  I have access to the head node via SSH as it is connected to the network.  The 19 compute nodes are not directly connected to the network and to access any one of them I first have to SSH to the head node and from there SSH to any compute node.  I can run jobs from the compute nodes and can have the application use memory from the entire cluster.

My question is how can I make it so that users can simply login to the head node and submit their jobs there without having to access the kerrighed cluster?  Is this even possible?  If not, should I connect one of the compute nodes to the network and have my users SSH to that and submit jobs from there?  Any help/advice would be appreciated.

Hi,

You have three options:
1. make your head node part of the SSI cluster (you should ask ajt/Tony about this),
2. connect one of the nodes to the external network. In this latter case, your head node need not appearing as a front-end.
3. (variant of 2.) port forward the ssh service from your head node to one of the cluster nodes. This way you need not connecting any cluster node to the external network: they will only be reachable through the SSH service.

Hope this helps.
Thanks,

Louis

---

### Post by mazimi on 2010-11-30
> **lrilling said:**
> 
3. (variant of 2.) port forward the ssh service from your head node to one of the cluster nodes. This way you need not connecting any cluster node to the external network: they will only be reachable through the SSH service.

I really like this idea, thanks a lot Louis!

I have some other general questions about the performance of my Kerrighed cluster which are not as critical but I would appreciate any insight you or others could give on this.

1. It's my understanding that Kerrighed is seen as an SMP system by applications.  Subsequently a multi-threaded application (lets say 16 threads) can be started on a quad core compute node but the threads will be distributed to other compute nodes efficiently.  This would be my guess for how Kerrighed's scheduler works for SMP applications.  However, when you have an MPI application and you launch your application via 'mpirun' on the kerrighed cluster, the MPI scheduler connects to the other compute nodes via SSH and distributes the jobs among your 'hosts'.  Is this the best method for handling MPI applications on kerrighed?

2. I imagine that running an MPI application on Kerrighed won't be as efficient as running it on an MPI system, is this correct?

3. In general, for applications such as molecular dynamics and finite element, will PVM or MPI systems show better performance?  I've scanned a few published articles but many of them seem to be over a decade old.

---

### Post by lrilling on 2010-12-01
> **mazimi said:**
> 1. It's my understanding that Kerrighed is seen as an SMP system by applications.  Subsequently a multi-threaded application (lets say 16 threads) can be started on a quad core compute node but the threads will be distributed to other compute nodes efficiently.  This would be my guess for how Kerrighed's scheduler works for SMP applications.

Please note that threads cannot be distributed yet. IOW, single-threaded processes can migrate, but threads of multi-threaded processes cannot. Similarly, a process cannot create another thread remotely.

> **mazimi said:**
> However, when you have an MPI application and you launch your application via 'mpirun' on the kerrighed cluster, the MPI scheduler connects to the other compute nodes via SSH and distributes the jobs among your 'hosts'.  Is this the best method for handling MPI applications on kerrighed?

Currently yes. There are still  issues with MPI applications when they are distributed by remote fork/migration.

> **mazimi said:**
> 2. I imagine that running an MPI application on Kerrighed won't be as efficient as running it on an MPI system, is this correct?

I'm not sure to understand what you call an "MPI system", but you're assumption sounds correct. The gains that Kerrighed could bring are to transparently migrate MPI workers out of nodes so that they can be removed, or to  re-balance the load.

> **mazimi said:**
> 3. In general, for applications such as molecular dynamics and finite element, will PVM or MPI systems show better performance?  I've scanned a few published articles but many of them seem to be over a decade old.

Native MPI support will probably show the best performance. However Kerrighed can definitely help when MPI support is not coded in  the application. It is then enough to program the application for multi-core architectures.

Thanks,

Louis

---

### Post by Trongersoll on 2010-12-13
Ok, I can see that [Kerrighed]("http://www.kerrighed.org/") has moved on to the 64-bit world. One of the main advantages of the Beowulf concept was the use of Commodity computers. It is going to be years before 32-bit machines are relics rather than abundantly available at affordable prices. Since [Kerrighed]("http://www.kerrighed.org/") is no longer an option for us 32-bit people, what is available that will do something similar?
 
Also, since the Server in a [Kerrighed]("http://www.kerrighed.org/") cluster is a server and not really a head. Is it relatively easy for the nodes to use more than one hard drive in the server? can extra drives in the server be added easily?

---

### Post by togueter on 2010-12-16
Hi, I try1 install kerrighed. I follow all step of guide. but my head node don't boot with kernel kerrighed. I try to install kerrighed in head node (out of /nfsroot) but when i boot may systhem , this say me: try to boot vnfs (why?, i want to boot head node, no client node), tray booting to diskette. eig? I press enter key and... kernel panic!!!

I think I do not understand the guidelines, because I assumed to be
Kerrighed install twice, once in the directory (as chroot)
/Nfsroot/Kerrighed/ nodes to boot with that kernel, and other
install at the ./ of the Master-Node (fronted) to communicate with
nodes.

thanks

---

### Post by ajt on 2010-12-16
> **togueter said:**
> Hi, I try1 install kerrighed. I follow all step of guide. but my head node don't boot with kernel kerrighed. I try to install kerrighed in head node (out of /nfsroot) but when i boot may systhem , this say me: try to boot vnfs (why?, i want to boot head node, no client node), tray booting to diskette. eig? I press enter key and... kernel panic!!!

I think I do not understand the guidelines, because I assumed to be
Kerrighed install twice, once in the directory (as chroot)
/Nfsroot/Kerrighed/ nodes to boot with that kernel, and other
install at the ./ of the Master-Node (fronted) to communicate with
nodes.

thanks

Hi, togueter.

The default Kerrighed install builds an NFSROOT kernel, and the head node does NOT run the Kerrighed kernel. If you want to run a Kerrighed kernel on the head node, you need to disable NFSROOT in the Kerrighed kernel configuration, then rebuild and install a stand-alone kernel on the head node.

HTH,

  Tony.

---

### Post by togueter on 2010-12-16
ok tony, thanks. but the kerrighed binaries have to installed in fronted, or not?

---

### Post by ajt on 2010-12-16
> **Trongersoll said:**
> Ok, I can see that [Kerrighed]("http://www.kerrighed.org/") has moved on to the 64-bit world. One of the main advantages of the Beowulf concept was the use of Commodity computers. It is going to be years before 32-bit machines are relics rather than abundantly available at affordable prices. Since [Kerrighed]("http://www.kerrighed.org/") is no longer an option for us 32-bit people, what is available that will do something similar?
 
Also, since the Server in a [Kerrighed]("http://www.kerrighed.org/") cluster is a server and not really a head. Is it relatively easy for the nodes to use more than one hard drive in the server? can extra drives in the server be added easily?

Hi, Trongersoll.

Re: alternatives - It depends what you want to do: The main feature of Kerrighed is SSI (Single System Image). I used to use 32-bit openMosix, but this project has now closed:

  [http://openmosix.sourceforge.net/](http://openmosix.sourceforge.net/)

This is still a viable system for 32-bit computers, but is no longer being developed and, critically, is limited to the 2.4 kernel and has very limited support for SATA drives.

Before deciding to switch to kerrighed, I also had a look at openSSI:

  [http://openssi.org/](http://openssi.org/)

There is a 32-bit version for Debian Lenny (i386) updated 2010/02/18, but the openSSI project seems dormant and I decided to try Kerrighed instead.

I have to say that the 32-bit version of Kerrighed 2.3.0 does work, and if you want to learn about SSI then this is an option. However, as Louis has said before the developers don't have the resources to devote to the 32-bit version. Remember, this is FLOSS and we are free to develop the 32-bit version of Kerrighed if we want to. However, look on eBay and you will see *many* very cheap COTS 64-bit server motherboards available!

It's a different matter if you want to use SSI for your work. In particular, if you want to use the aggregate memory of a Kerrighed Beowulf cluster you are limited to ~3GiB and the Kerrighed kernel does not support PAE. In that respect, you can only use 32-bit Kerrighed for transparent process migration - That's quite useful, though :-)

Bye,

  Tony.

---

### Post by nandugopan on 2010-12-16
Guys,

 I am completely new to clustering and after reading this thread, felt I should try setting up a small cluster for our lab. We have 4  HP Z 800 workstations (4x2 processors with 6 cores each) with Gigabit Ethernet Card. Our lab runs domain decomposition type of molecular dynamics simulations on the institute cluster. It uses gcc + gfortran +FFTW2+ MPICH.I just wanted to estimate how much of an improvement in computational power can be brought about by an in-house clustering of workstations.

Would there be a considerable improvement of computational power by setting up a cluster with just 4 machines? (most of the posts here seem to refer to 20 + machines)

Is there a 'how-to' or manual (wishful thinking) on how to go about setting up a cluster? I remember seeing something on how to set up an Ubuntu cluster somewhere. Cant quite find the link

Hoping to hear your inputs 

Thanks.:p

---

### Post by ajt on 2010-12-16
> **nandugopan said:**
> Guys,

[...]
It uses gcc + gfortran +FFTW2+ MPICH.I just wanted to estimate how much of an improvement in computational power can be brought about by an in-house clustering of workstations.
[...]

Thanks.:p

Hi, nandugopan.

You don't need Kerrighed SSI to run MPICH programs, which use the MPICH library under a standard linux kernel. However, one strategy I've used is to configure my MPI hostfile to use only one node of a cluster and allow automatic openMosix/Kerrighed load-balancing to distribute MPI processes between nodes by overloading the number of slots on that node (i.e. more slots than cores). In deciding how much of an advantage this might be, I recommend reading up about Amdah's law:

[http://en.wikipedia.org/wiki/Amdahl%27s_law](http://en.wikipedia.org/wiki/Amdahl%27s_law)

HTH,

  Tony.

---

### Post by Trongersoll on 2010-12-16
Hi Tony,
 
Thanks for your response. I started to play with OpenMosix about 5 years ago, but got busy with life and lost interest. I've accumulated a number of 32-bit machines over the years. The server can be 32 bit so i don't have a problem there, but if i go 32 bit i have 5 nodes at hand. If i go 64 bit, I have one node. Generally, when i upgrade my computers the old hardware would become a new node. 
 
Right now I'm wondering how much of a problem i would have reverse engineering the 64 bit updates to 32 bit. I need to think about this some.

---

### Post by vak on 2011-01-08
[GUYS, I need SSI badly in Ubuntu! ]("http://ubuntuforums.org/showthread.php?t=1662580")

---

### Post by cellstorm on 2011-02-05
here are debian packages:
[http://www.kerrighed.org/debian/](http://www.kerrighed.org/debian/)  
well hidden....

here how to use that:
[http://www.estrellateyarde.org/discover/cluster-kerrighed-en-linux](http://www.estrellateyarde.org/discover/cluster-kerrighed-en-linux)
at least I think so.

this guide is probably well known here, but anyways, could be helpful:
[http://www.debianadmin.com/how-to-set-up-a-high-performance-cluster-hpc-using-debian-lenny-and-kerrighed.html](http://www.debianadmin.com/how-to-set-up-a-high-performance-cluster-hpc-using-debian-lenny-and-kerrighed.html)

---

### Post by vak on 2011-02-05
@cellstorm, hey, thanks for sharing this info! I am going to try it

Did you tried both OpenSSI and Kerrighed? 

How good is Kerrighed in comparison to OpenSSI ?
 
I saw the [feature comparison table]("http://en.wikipedia.org/wiki/Single-system_image"), so in particular it would be interesting to know how is it now in Kerrighed with 

* Single I/O space and 
* Cluster IP

---

### Post by cellstorm on 2011-02-05
nope. Did not try anything. I was just researching. anyways, things seem to be more complicated as I thought. 

I was looking for a simple replacement of openmosix. A kernel which can be put on a livecd, and then can be used for distributed computing for mulitmedia apps.

As I understand it, the kernel used by kerrighed does needs to be compiled by hand, because it won't boot without compiling the driver of your network card into it.

Also,  multithreaded applications do not benefit from it (yet), hope this returns soon. 

the server, which holds all the applications the slaves are using, cannot be used for computing. Which is a bit strange, how would I work in e.g blender then?

---

### Post by vak on 2011-02-05
@cellstorm, well, those guides are too far from debian packages available by your first link :)

The packages have been installed by me OK using dpkg -i
However boot without any configuration failed (kernel panic) :)

Also, I didn't find any guide that explains how to install and configure Kerrighed from the .deb

I'll try tomorrow.

---

### Post by lrilling on 2011-02-07
> **cellstorm said:**
> here are debian packages:
[http://www.kerrighed.org/debian/](http://www.kerrighed.org/debian/)  
well hidden....

Guys, there is a good reason for not telling the world about those debs: they are part of XtreemOS 3.0, and as such include advanced features that are not so well documented nor stabilized.

> **cellstorm said:**
>  here how to use that:
[http://www.estrellateyarde.org/discover/cluster-kerrighed-en-linux](http://www.estrellateyarde.org/discover/cluster-kerrighed-en-linux)
at least I think so.

Typically, I doubt (cannot read spanish well enough) that this guide explains how to use the debs above, since they require some specific network configuration which is absolutely not required with Kerrighed 3.0.0...

If you still want to use those debs, the network configuration is explained in some README.Net file (to be found under /usr/share/doc/kerrighed in package kerrighed).

Thanks,

Louis

---

### Post by lrilling on 2011-02-07
> **cellstorm said:**
> the server, which holds all the applications the slaves are using, cannot be used for computing. Which is a bit strange, how would I work in e.g blender then?

The server only serves DHCP, PXE requests (to ship their kernel to the nodes) and files (through NFS). Applications must be launched from regular cluster nodes.

Btw, there is no real notion of slave in Kerrighed. All nodes participate the same to the cluster. The server itself is not part of the cluster in the recommended configurations.

Thanks,

Louis

---

### Post by vak on 2011-02-07
@lrilling, I have a following kernel panic problem during the boot with those debs: [http://article.gmane.org/gmane.linux.cluster.kerrighed.user/1084](http://article.gmane.org/gmane.linux.cluster.kerrighed.user/1084)

---

### Post by lrilling on 2011-02-07
> **vak said:**
> @cellstorm, well, those guides are too far from debian packages available by your first link :)

The packages have been installed by me OK using dpkg -i
However boot without any configuration failed (kernel panic) :)

Also, I didn't find any guide that explains how to install and configure Kerrighed from the .deb

Indeed, no guide covers those debs. However, you should succeed if you combine the usual guide(s) for Kerrighed 3.0.0 (see the official one [http://www.kerrighed.org/wiki/index.php/UserDoc](http://www.kerrighed.org/wiki/index.php/UserDoc) for instance) and file README.Net (to be found under /usr/share/doc/kerrighed). You should also be aware that two flavors of the kernel (packages kerrighed-image-2.6.30-krg and kerrighed-headers-2.6.30-krg) are shipped:

- version 3.0.0-1 includes support for a cluster-wide IP address, and requires network namespace isolation between the host system and the Kerrighed container.

- version 3.0.0+nonet-1 does not include support for cluster-wide IP address, and does not require network namespace isolation.

Thanks,

Louis

---

### Post by lrilling on 2011-02-07
> **vak said:**
> @lrilling, I have a following kernel panic problem during the boot with those debs: [http://article.gmane.org/gmane.linux.cluster.kerrighed.user/1084](http://article.gmane.org/gmane.linux.cluster.kerrighed.user/1084)

@vak: See my (coming) reply on kerrighed.users.

Thanks,

Louis

---

### Post by vak on 2011-02-07
> **lrilling said:**
> 
You should also be aware that two flavors of the kernel (packages kerrighed-image-2.6.30-krg and kerrighed-headers-2.6.30-krg) are shipped:
...

@lrilling, many thanks for the hint about the difference. It will save me a day. 

Now I have to boot somehow in the system first :)
So, I am curious and am looking for your reply on kerrighed maillist.

---

### Post by ajithabraham.m on 2011-02-08
hi
i done every thing as u said in the tutorial but when i start kerrighed 
  root@cluster:/home/kerrighed-src# /etc/init.d/kerrighed start
  modinfo: could not find module kerrighed
 * Starting Kerrighed:                                                   [ OK ]   

and i check the status 
root@cluster:/home/kerrighed-src# /etc/init.d/kerrighed status 
modinfo: could not find module kerrighed
 * Kerrighed status:                                                            not loaded                                                               [ OK ]

thanks

---

### Post by lrilling on 2011-02-10
> **ajithabraham.m said:**
> hi
i done every thing as u said in the tutorial but when i start kerrighed 
  root@cluster:/home/kerrighed-src# /etc/init.d/kerrighed start
  modinfo: could not find module kerrighed
 * Starting Kerrighed:                                                   [ OK ]   

and i check the status 
root@cluster:/home/kerrighed-src# /etc/init.d/kerrighed status 
modinfo: could not find module kerrighed
 * Kerrighed status:                                                            not loaded                                                               [ OK ]

thanks

Does kerrighed appear in lsmod?
# lsmod | grep kerrighed

If not, try (on any cluster node):
# depmod -a
and then retry:
# /etc/init.d/kerrighed start

Thanks,

Louis

---

### Post by abu_nawas on 2011-02-16
my system freeze when migrating. anyone know how to solve this problem?

---

### Post by lrilling on 2011-02-17
> **abu_nawas said:**
> my system freeze when migrating. anyone know how to solve this problem?

Please give kernel logs (both source and target machine), stack backtraces of blocked tasks if possible (you can have them with SysRq-w, or echo w > /proc/sysrq-trigger), and of course detail a bit what you did: which process, how launched, how migrated.

And Kerrighed version of course :)

Thanks,
Louis

---

### Post by awannabeee on 2011-03-06
forgive me if i am posting in the wrong thred!
can someone direct me to tutorials for single node set up of clustering, tried the hadoop tutorial and got confused at the configuation stage
 
**Configuration**

Use the following: 

conf/core-site.xml:
<configuration>     <property>         <name>fs.default.name</name>         <value>hdfs://localhost:9000</value>     </property></configuration>[http://hadoop.apache.org/common/docs/current/single_node_setup.html](http://hadoop.apache.org/common/docs/current/single_node_setup.html), is where the above comes from,can someone explain the above to me or tell me where to get the explanation of tha above?

---

### Post by baggzy on 2011-06-27
Hi all!  I'm attempting to install kerrighed 3.0.0 via NFSBOOT.  There have been some changes to kerrighed and debian which aren't reflected in the online docs, so I thought I'd share my experiences in case it assists others.  In this post I'll be covering the NFSBOOT part of the process.  I'll compile and run kerrighed later.  I'm booting off a machine running Ubuntu 10.10, for anyone who's interested.

The basic process is described in [_the official guide_]("http://www.kerrighed.org/wiki/index.php/Kerrighed_on_NFSROOT") and also [_this contributed doc_]("http://www.kerrighed.org/wiki/index.php/Kerrighed_on_NFSROOT_%28contrib%29") but I had to change some of the details.  Follow the official guide but refer to the points below as you go.

1) The format for [FONT="Courier New"]/etc/default/tftpd-hpa[/FONT] has changed.  Using [FONT="Courier New"]RUN_DAEMON = "yes"[/FONT] and [FONT="Courier New"]OPTIONS = "-l -s /srv/tftp"[/FONT] doesn't seem to work any more.  Instead I used what's shown below.  The default file has [FONT="Courier New"]TFTP_OPTIONS="--secure"[/FONT] but I couldn't get that to work.  tftpd-hpa runs as a daemon by default now, so no need for the -l flag.  (And no need for xinetd either.)
```

# /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/srv/tftp"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS=""
```

2) The official guide doesn't mention which file to edit to  "Configure the DHCP server".  The file in question is [FONT="Courier New"]/etc/dhcp3/dhcp.conf[/FONT].  The machine I'm booting off (the "server") has IP address 192.168.0.1 on network card eth0, but is connected to the cluster via a second network card with IP 192.168.1.1 called eth1.  The nodes will have IP's starting at 192.168.1.101 and be called node101, node102, etc.  My [FONT="Courier New"]dhcp.conf[/FONT] therefore looks like this:
```

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

### PART 1
# General options
option dhcp-max-message-size 2048;
use-host-decl-names on;
deny bootp;

### PART 2
option domain-name "kerrighed";
option domain-name-servers 192.168.1.1;
option ntp-servers ntp.network.net;

### PART 3
subnet 192.168.1.0 netmask 255.255.255.0 {
 option routers 192.168.1.1;
 option broadcast-address 192.168.1.255;
 # Define the first and last IP address to be authorized
 range 192.168.1.101 192.168.1.199;
 # This set up the node name to « nodeXX » with XX the id of the node (ip-address based).
 send host-name = concat("node", binary-to-ascii(10, 8, ".", substring(leased-address, 3, 1)));
 # If you want to limit which boxes are using kerrighed, use something like this :
 # host ssi1 { fixed-address 192.168.0.101; hardware ethernet xx:xx:xx:xx:xx:xx; 
 filename "/srv/tftp/pxelinux.0";
}

### PART 4 
group {
 server-name "server";
 option root-path "192.168.1.1:/NFSROOT/kerrighed";
}
```

3) As far as I recall, I didn't change anything in the standard file, I just added the stuff at the bottom.  But I left all the default gumph in there just in case.  A few things to note:

i) Since the server is on 192.168.1.1, starting the range at 192.168.1.2 would mean that the node names start with node2...  So I started the range at 101 so the first node is node101.  I suppose I could reconfigure eth1 on the server to be 192.168.1.254 or something, but I didn't.

ii) I moved the [FONT="Courier New"]filename "/srv/tftp/pxelinux.0";[/FONT] from the group block to the subnet block.  It didn't seem to work in the group block - I'd get a the following error on the node:
```
PXE-E53: No boot filename received
```

4) I added the following to [FONT="Courier New"]/etc/default/dhcp3-server[/FONT]:
```
INTERFACES="eth1"
```

5) I added the following to [FONT="Courier New"]/etc/network/interfaces[/FONT]:
```

auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
```

6) I added the following to [FONT="Courier New"]/etc/hosts.allow[/FONT] because without it I'd get a TFTP timeout error:
```
ALL: 192.168.1.*
```

7) If you make changes to the dhcp or tftp config files you need to restart various services.  As Steve Kelly suggesting in [his guide]("http://www.stevekelly.eu/cluster.shtml"), I set up a script to do this, called "restart-dhcp".  You'll need to [FONT="Courier New"]chmod 755[/FONT] it, then put it somewhere in your [FONT="Courier New"]$PATH[/FONT] (I put it in [FONT="Courier New"]~/bin[/FONT] and add that to my [FONT="Courier New"]PATH[/FONT] in my [FONT="Courier New"].bashrc[/FONT]).  Note that "restart" doesn't seem to work with tftpd-hpa so you have to "stop" it, then "start" it.
```

#
# tftpd-hpa restart is broken, so don't use it!
#
sudo restart portmap
sudo service dhcp3-server restart
sudo stop tftpd-hpa
sudo start tftpd-hpa
sudo service nfs-kernel-server restart
sudo exportfs -ra
```

8) The output from this script should look like the code below.  If any of the process id's are missing the daemon probably didn't actually start.  But a "status" check will say it did.  There's obviously a bug somewhere and the only solution I found was to reboot the server.
```

portmap start/running, process 844
 * Stopping DHCP server dhcpd3                       [ OK ] 
 * Starting DHCP server dhcpd3                       [ OK ] 
tftpd-hpa stop/waiting
tftpd-hpa start/running, process 23714
 * Stopping NFS kernel daemon                        [ OK ] 
 * Unexporting directories for NFS kernel daemon...  [ OK ] 
 * Exporting directories for NFS kernel daemon...    [ OK ] 
 * Starting NFS kernel daemon                        [ OK ]
```

9) The official guide doesn't mention it, but after you've done "[FONT="Courier New"]sudo mkdir /srv/tftp[/FONT]" you have to do the following.  The first thing your node will do when it tries to NFSBOOT is look for a file called [FONT="Courier New"]pxelinux.0[/FONT] in [FONT="Courier New"]/srv/tftp[/FONT].  Obviously if it's not there it won't boot.  Next it will fire up TFTP and try to transfer the boot files specified in the [FONT="Courier New"]/srv/tftp/pxlinux.cfg/default[/FONT] file.  If it fails it's either because TFTP isn't running, isn't set up correctly, doesn't have the required permissions, or your node isn't listed in [FONT="Courier New"]/etc/hosts.allow[/FONT].  The [FONT="Courier New"]chown[/FONT] may not be necessary, but if you have problems at the TFTP stage give it a try.
```

sudo cp /usr/lib/syslinux/pxelinux.0 /srv/tftp/
sudo chown -R tftp:tftp /srv/tftp
```

10) After you've [FONT="Courier New"]debootstrapp[/FONT]ed lenny and [FONT="Courier New"]chroot[/FONT]'d into [FONT="Courier New"]/NFSROOT/kerrighed[/FONT], in addition to mounting [FONT="Courier New"]/proc[/FONT] I also had to do the following to avoid errors while using "[FONT="Courier New"]apt-get install[/FONT]":
```

mount -t devpts none /dev/pts
```

11) To avoid warnings about your [FONT="Courier New"]LOCALE[/FONT] the first thing you need to install is [FONT="Courier New"]locales[/FONT], then configure it and select "[FONT="Courier New"]en_GB.UTF-8[/FONT]":
```

apt-get install locales
dpkg-reconfigure locales
```

12) After you've installed [FONT="Courier New"]nfs-common[/FONT], to avoid [FONT="Courier New"]statd[/FONT] failing during boot, and holding things up about 5 minutes each time, edit [FONT="Courier New"]/etc/default/nfs-common[/FONT] and change [FONT="Courier New"]NEED_STATD[/FONT] to no:
```

NEED_STATD=no
```

13) After installing [FONT="Courier New"]initramfs-tools[/FONT] edit [FONT="Courier New"]/etc/initramfs-tools/initramfs.conf[/FONT] and change [FONT="Courier New"]BOOT=local[/FONT] to:
```

BOOT=nfs
```

14) If you want to boot your node into debian to see if everything has worked so far...

i) Do the following.  (Answer "No" to creating a link, and "No" to aborting.)
```

apt-get install linux-image-2.6.26-2-amd64
```

ii) [FONT="Courier New"]exit[/FONT] (i.e. leave chroot)

iii) Copy the boot files:
```

sudo cp /NFSROOT/kerrighed/boot/vmlinuz-2.6.26-2-amd64 /srv/tftp/
sudo cp /NFSROOT/kerrighed/boot/initrd.img-2.6.26-2-amd64 /srv/tftp/
```

iv) Create or edit /srv/tftp/pxelinux.cfg/default to:
```

DEFAULT debian

LABEL debian
    kernel vmlinuz-2.6.26-2-amd64
    append ip=dhcp root=/dev/nfs initrd=initrd.img-2.6.26-2-amd64 nfsroot=192.168.1.1:/NFSROOT/kerrighed,rw rw
    initrd initrd.img-2.6.26-2-amd64
```

15) That's it!  You should be able to NFSBOOT your node(s)...

---

### Post by lrilling on 2011-06-28
> **baggzy said:**
> Hi all!  I'm attempting to install kerrighed 3.0.0 via NFSBOOT.  There have been some changes to kerrighed and debian which aren't reflected in the online docs, so I thought I'd share my experiences in case it assists others.  In this post I'll be covering the NFSBOOT part of the process.  I'll compile and run kerrighed later.  I'm booting off a machine running Ubuntu 10.10, for anyone who's interested.

The basic process is described in [_the official guide_]("http://www.kerrighed.org/wiki/index.php/Kerrighed_on_NFSROOT") and also [_this contributed doc_]("http://www.kerrighed.org/wiki/index.php/Kerrighed_on_NFSROOT_%28contrib%29") but I had to change some of the details.  Follow the official guide but refer to the points below as you go.


Hi baggzy,

First of all thanks for sharing your notes. If you don't mind, I'm going to comment some of the items, and with your permission I could also improve the official Kerrighed wiki :)

> **baggzy said:**
> 1) The format for [FONT="Courier New"]/etc/default/tftpd-hpa[/FONT] has changed.  Using [FONT="Courier New"]RUN_DAEMON = "yes"[/FONT] and [FONT="Courier New"]OPTIONS = "-l -s /srv/tftp"[/FONT] doesn't seem to work any more.  Instead I used what's shown below.  The default file has [FONT="Courier New"]TFTP_OPTIONS="--secure"[/FONT] but I couldn't get that to work.


According to tfptd-hpa's documentation, when using [FONT="Courier New"]--secure[/FONT], option [FONT="Courier New"]filename[/FONT] in the DHCP server configuration should not contain any path (eg. [FONT="Courier New"]pxelinux.0[/FONT], not [FONT="Courier New"]/srv/tftp/pxelinux.0[/FONT]), and the file should of course live exactly in the daemon's directory (ie [FONT="Courier New"]/srv/tftp[/FONT]). Have you tried setting up tftpd-hpa+dhcpd.conf this way?

> **baggzy said:**
> tftpd-hpa runs as a daemon by default now, so no need for the -l flag.  (And no need for xinetd either.)
```

# /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/srv/tftp"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS=""
```


Good candidate for improving the wiki.

> **baggzy said:**
> 2) The official guide doesn't mention which file to edit to  "Configure the DHCP server".  The file in question is [FONT="Courier New"]/etc/dhcp3/dhcp.conf[/FONT].


I guess that you meant [FONT="Courier New"]/etc/dhcp3/dhcpd.conf[/FONT], right? Note that on newer distros (eg Debian Squeeze), it has even moved to [FONT="Courier New"]/etc/dhcp/dhcpd.conf[/FONT]. The package has also been renamed isc-dhcp-server.

> **baggzy said:**
> The machine I'm booting off (the "server") has IP address 192.168.0.1 on network card eth0, but is connected to the cluster via a second network card with IP 192.168.1.1 called eth1.  The nodes will have IP's starting at 192.168.1.101 and be called node101, node102, etc.  My [FONT="Courier New"]dhcp.conf[/FONT] therefore looks like this:
```

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

### PART 1
# General options
option dhcp-max-message-size 2048;
use-host-decl-names on;
deny bootp;

### PART 2
option domain-name "kerrighed";
option domain-name-servers 192.168.1.1;
option ntp-servers ntp.network.net;

### PART 3
subnet 192.168.1.0 netmask 255.255.255.0 {
 option routers 192.168.1.1;
 option broadcast-address 192.168.1.255;
 # Define the first and last IP address to be authorized
 range 192.168.1.101 192.168.1.199;
 # This set up the node name to « nodeXX » with XX the id of the node (ip-address based).
 send host-name = concat("node", binary-to-ascii(10, 8, ".", substring(leased-address, 3, 1)));
 # If you want to limit which boxes are using kerrighed, use something like this :
 # host ssi1 { fixed-address 192.168.0.101; hardware ethernet xx:xx:xx:xx:xx:xx; 
 filename "/srv/tftp/pxelinux.0";
}

### PART 4 
group {
 server-name "server";
 option root-path "192.168.1.1:/NFSROOT/kerrighed";
}
```

3) As far as I recall, I didn't change anything in the standard file, I just added the stuff at the bottom.  But I left all the default gumph in there just in case.  A few things to note:

i) Since the server is on 192.168.1.1, starting the range at 192.168.1.2 would mean that the node names start with node2...  So I started the range at 101 so the first node is node101.  I suppose I could reconfigure eth1 on the server to be 192.168.1.254 or something, but I didn't.

ii) I moved the [FONT="Courier New"]filename "/srv/tftp/pxelinux.0";[/FONT] from the group block to the subnet block.  It didn't seem to work in the group block - I'd get a the following error on the node:
```
PXE-E53: No boot filename received
```


I have to admit that I don't understand the reason for this group declaration, since it contains no host declarations. I was told that it was working as it is written in the wiki, but I'm very much inclined to believe you :) To me the contents of this group declaration should be simply put in the subnet statement above. People needing more complex DHCP configurations will probably know how to create appropriate group or class declarations. Do you believe that there is some interest for this group declaration?

> **baggzy said:**
> 4) I added the following to [FONT="Courier New"]/etc/default/dhcp3-server[/FONT]:
```
INTERFACES="eth1"
```


Good candidate for the wiki too.

> **baggzy said:**
> 5) I added the following to [FONT="Courier New"]/etc/network/interfaces[/FONT]:
```

auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
```


Good candidate for the wiki.

> **baggzy said:**
> 6) I added the following to [FONT="Courier New"]/etc/hosts.allow[/FONT] because without it I'd get a TFTP timeout error:
```
ALL: 192.168.1.*
```


Good catch! I don't remember anybody mentioning it (which does not say that nobody ever told me about it, I just don't remember:)). As far as I can see, you must have something in /etc/hosts.deny that match your nodes and tftp. Otherwise, leaving /etc/hosts.allow empty should be enough to have tftpd-hpa working.

> **baggzy said:**
> 7) If you make changes to the dhcp or tftp config files you need to restart various services.  As Steve Kelly suggesting in [his guide]("http://www.stevekelly.eu/cluster.shtml"), I set up a script to do this, called "restart-dhcp".  You'll need to [FONT="Courier New"]chmod 755[/FONT] it, then put it somewhere in your [FONT="Courier New"]$PATH[/FONT] (I put it in [FONT="Courier New"]~/bin[/FONT] and add that to my [FONT="Courier New"]PATH[/FONT] in my [FONT="Courier New"].bashrc[/FONT]).  Note that "restart" doesn't seem to work with tftpd-hpa so you have to "stop" it, then "start" it.
```

#
# tftpd-hpa restart is broken, so don't use it!
#
sudo restart portmap
sudo service dhcp3-server restart
sudo stop tftpd-hpa
sudo start tftpd-hpa
sudo service nfs-kernel-server restart
sudo exportfs -ra
```


I would not include this in the wiki, but maybe add some link to your post.

> **baggzy said:**
> 8) The output from this script should look like the code below.  If any of the process id's are missing the daemon probably didn't actually start.  But a "status" check will say it did.  There's obviously a bug somewhere and the only solution I found was to reboot the server.
```

portmap start/running, process 844
 * Stopping DHCP server dhcpd3                       [ OK ] 
 * Starting DHCP server dhcpd3                       [ OK ] 
tftpd-hpa stop/waiting
tftpd-hpa start/running, process 23714
 * Stopping NFS kernel daemon                        [ OK ] 
 * Unexporting directories for NFS kernel daemon...  [ OK ] 
 * Exporting directories for NFS kernel daemon...    [ OK ] 
 * Starting NFS kernel daemon                        [ OK ]
```

9) The official guide doesn't mention it, but after you've done "[FONT="Courier New"]sudo mkdir /srv/tftp[/FONT]" you have to do the following.  The first thing your node will do when it tries to NFSBOOT is look for a file called [FONT="Courier New"]pxelinux.0[/FONT] in [FONT="Courier New"]/srv/tftp[/FONT].  Obviously if it's not there it won't boot.  Next it will fire up TFTP and try to transfer the boot files specified in the [FONT="Courier New"]/srv/tftp/pxlinux.cfg/default[/FONT] file.  If it fails it's either because TFTP isn't running, isn't set up correctly, doesn't have the required permissions, or your node isn't listed in [FONT="Courier New"]/etc/hosts.allow[/FONT].  The [FONT="Courier New"]chown[/FONT] may not be necessary, but if you have problems at the TFTP stage give it a try.
```

sudo cp /usr/lib/syslinux/pxelinux.0 /srv/tftp/
sudo chown -R tftp:tftp /srv/tftp
```


Good candidate for the wiki.

> **baggzy said:**
> 10) After you've [FONT="Courier New"]debootstrapp[/FONT]ed lenny and [FONT="Courier New"]chroot[/FONT]'d into [FONT="Courier New"]/NFSROOT/kerrighed[/FONT], in addition to mounting [FONT="Courier New"]/proc[/FONT] I also had to do the following to avoid errors while using "[FONT="Courier New"]apt-get install[/FONT]":
```

mount -t devpts none /dev/pts
```


I think that the errors you mention are dpkg complaining that it is not able to log. This however does not prevent dpkg from correctly installing packages, so I personally don't mount /dev/pts. I can add this to the wiki though, if people can feel more comfortable this way.

> **baggzy said:**
> 11) To avoid warnings about your [FONT="Courier New"]LOCALE[/FONT] the first thing you need to install is [FONT="Courier New"]locales[/FONT], then configure it and select "[FONT="Courier New"]en_GB.UTF-8[/FONT]":
```

apt-get install locales
dpkg-reconfigure locales
```


Same category as the previous item, IMHO.

> **baggzy said:**
> 12) After you've installed [FONT="Courier New"]nfs-common[/FONT], to avoid [FONT="Courier New"]statd[/FONT] failing during boot, and holding things up about 5 minutes each time, edit [FONT="Courier New"]/etc/default/nfs-common[/FONT] and change [FONT="Courier New"]NEED_STATD[/FONT] to no:
```

NEED_STATD=no
```


I wouldn't recommend disabling statd, especially when you mount NFS trees with file locking support (IIRC this is the default for mounts done from [FONT="Courier New"]/etc/fstab[/FONT]). You might have issues because either [FONT="Courier New"]/var/run[/FONT] or [FONT="Courier New"]/var/lib/nfs[/FONT] is shared (each node must have its own ones, for instance using tmpfs mounts). [FONT="Courier New"]/var/lib/nfs[/FONT] should be added to the [FONT="Courier New"]/etc/fstab[/FONT] sample of the wiki, however it requires a bit of initialization. I don't know if nfsbooted have some helpers for this.

> **baggzy said:**
> 13) After installing [FONT="Courier New"]initramfs-tools[/FONT] edit [FONT="Courier New"]/etc/initramfs-tools/initramfs.conf[/FONT] and change [FONT="Courier New"]BOOT=local[/FONT] to:
```

BOOT=nfs
```


Good candidate too.

> **baggzy said:**
> 14) If you want to boot your node into debian to see if everything has worked so far...

i) Do the following.  (Answer "No" to creating a link, and "No" to aborting.)
```

apt-get install linux-image-2.6.26-2-amd64
```

ii) [FONT="Courier New"]exit[/FONT] (i.e. leave chroot)

iii) Copy the boot files:
```

sudo cp /NFSROOT/kerrighed/boot/vmlinuz-2.6.26-2-amd64 /srv/tftp/
sudo cp /NFSROOT/kerrighed/boot/initrd.img-2.6.26-2-amd64 /srv/tftp/
```

iv) Create or edit /srv/tftp/pxelinux.cfg/default to:
```

DEFAULT debian

LABEL debian
    kernel vmlinuz-2.6.26-2-amd64
    append ip=dhcp root=/dev/nfs initrd=initrd.img-2.6.26-2-amd64 nfsroot=192.168.1.1:/NFSROOT/kerrighed,rw rw
    initrd initrd.img-2.6.26-2-amd64
```

15) That's it!  You should be able to NFSBOOT your node(s)...

Thanks again for your notes!

Louis

---

### Post by baggzy on 2011-07-01
> **lrilling said:**
> 
First of all thanks for sharing your notes. If you don't mind, I'm going to comment some of the items, and with your permission I could also improve the official Kerrighed wiki :)


Of course! :)

> **lrilling said:**
> 
I guess that you meant [FONT="Courier New"]/etc/dhcp3/dhcpd.conf[/FONT], right? Note that on newer distros (eg Debian Squeeze), it has even moved to [FONT="Courier New"]/etc/dhcp/dhcpd.conf[/FONT]. The package has also been renamed isc-dhcp-server.


Doh!  Yes, that's what I meant.  (And new location noted.)

> **lrilling said:**
> 
I have to admit that I don't understand the reason for this group declaration, since it contains no host declarations. I was told that it was working as it is written in the wiki, but I'm very much inclined to believe you :) To me the contents of this group declaration should be simply put in the subnet statement above. People needing more complex DHCP configurations will probably know how to create appropriate group or class declarations. Do you believe that there is some interest for this group declaration?


I don't know if the group declaration actually does anything either, now you mention it...  My nodes boot fine without it (I just tried).  On the other hand, moving the remaining two lines up to the subnet section doesn't appear to change anything, so maybe those lines do nothing.

> **lrilling said:**
> 
You must have something in /etc/hosts.deny that match your nodes and tftp. Otherwise, leaving /etc/hosts.allow empty should be enough to have tftpd-hpa working.


No my hosts.deny is empty.  Odd.

> **lrilling said:**
> 
I think that the errors you mention are dpkg complaining that it is not able to log. This however does not prevent dpkg from correctly installing packages, so I personally don't mount /dev/pts. I can add this to the wiki though, if people can feel more comfortable this way.


That's true, it just gets rid of all those warnings.  As does the LOCALES thing.

> **lrilling said:**
> 
I wouldn't recommend disabling statd, especially when you mount NFS trees with file locking support (IIRC this is the default for mounts done from [FONT="Courier New"]/etc/fstab[/FONT]). You might have issues because either [FONT="Courier New"]/var/run[/FONT] or [FONT="Courier New"]/var/lib/nfs[/FONT] is shared (each node must have its own ones, for instance using tmpfs mounts). [FONT="Courier New"]/var/lib/nfs[/FONT] should be added to the [FONT="Courier New"]/etc/fstab[/FONT] sample of the wiki, however it requires a bit of initialization. I don't know if nfsbooted have some helpers for this.


From what I read there's a bug in statd which means it ends up in a race with portmapper.  As a result statd won't start and takes ages to time out.  That happens three times during boot, which means it took my nodes around 18 minutes to boot, instead of 1.  If it causes problems I'll put it back, or find some other work-around.  I'll let you know.

Cheers!

---

### Post by baggzy on 2011-07-01
Hi all!  I was going to share my experiences with the compilation process for kerrighed 3.0.0, but it went without a hitch so there isn't really anything to say. :)

Sadly when I tried to boot I was hit with the same problem that a few others have had - an immediate crash where the screen fills with multi-coloured flashing text.  This happens so fast I had to make a movie with my digital camera to see what happened.  Basically the last message is "Trying to load: pxelinux.cfg/default ... ok" then it crashes.  Presumably the crash happens as soon as it executes vmlinuz-2.6.30-krg3.0.0...  See below for a couple of images from the movie.  These are two consecutive frames, so it happens in less than 1/30th of a second.

This leaves us with little information on which to base an investigation.  The only other threads I found on this ([_here_]("http://comments.gmane.org/gmane.linux.cluster.kerrighed.user/1216") and [_here_]("https://bbs.archlinux.org/viewtopic.php?id=110758")) offered no solution.  Anyone know what the problem is?  Or, even better, how to solve it?

The only clue I have to offer is that I successfully built and booted linux-2.6.30 from the same tarball that kerrighed is patching.  So the problem isn't with debian, it's with the kerrighed patches...

---

### Post by baggzy on 2011-07-02
> **lrilling said:**
> 
According to tfptd-hpa's documentation, when using [FONT="Courier New"]--secure[/FONT], option [FONT="Courier New"]filename[/FONT] in the DHCP server configuration should not contain any path (eg. [FONT="Courier New"]pxelinux.0[/FONT], not [FONT="Courier New"]/srv/tftp/pxelinux.0[/FONT]), and the file should of course live exactly in the daemon's directory (ie [FONT="Courier New"]/srv/tftp[/FONT]). Have you tried setting up tftpd-hpa+dhcpd.conf this way?

Sorry, I forgot to reply to this one...  I just tried it and yes that seems to work. :)  Still getting the multicoloured screen of death though...  :(

---

### Post by lrilling on 2011-07-04
Hi baggzy,

> **baggzy said:**
> Hi all!  I was going to share my experiences with the compilation process for kerrighed 3.0.0, but it went without a hitch so there isn't really anything to say. :)

Sadly when I tried to boot I was hit with the same problem that a few others have had - an immediate crash where the screen fills with multi-coloured flashing text.  This happens so fast I had to make a movie with my digital camera to see what happened.  Basically the last message is "Trying to load: pxelinux.cfg/default ... ok" then it crashes.  Presumably the crash happens as soon as it executes vmlinuz-2.6.30-krg3.0.0...  See below for a couple of images from the movie.  These are two consecutive frames, so it happens in less than 1/30th of a second.

This leaves us with little information on which to base an investigation.  The only other threads I found on this ([_here_]("http://comments.gmane.org/gmane.linux.cluster.kerrighed.user/1216") and [_here_]("https://bbs.archlinux.org/viewtopic.php?id=110758")) offered no solution.  Anyone know what the problem is?  Or, even better, how to solve it?

The only clue I have to offer is that I successfully built and booted linux-2.6.30 from the same tarball that kerrighed is patching.  So the problem isn't with debian, it's with the kerrighed patches...

The only "solution" found so far for this issue is to build Kerrighed from the git repository. As far as I know, it's no less stable than Kerrighed 3.0.0, so it's not risky. The big problem with this screen of death is that I couldn't reproduce it myself. Others tried with some debugging options enabled, but could not obtain consistent results :/ Anyway, it looks "solved" in git!

Thanks,

Louis

---

### Post by Cluster Penguin on 2011-07-10
Never mind.

---

### Post by Bocho on 2011-08-01
Hi All, and thanks for your posts and replies!

I hope this information will be useful for some people with "multicoloured screen" (I [COLOR=Black]**was**[/COLOR] also among them). "Therapy":
after you create your kernel and got "multicoloured screen", change its name from "vmlinuz-2.6.30-krg3.0.0" for something else e.g. "vmlinuz" (do not forget about "default" in /srv/tftp/pxelinux.cfg/) ... and your kernel is alive.
And vice versa: if you want :) to see "multicoloured screen" - change the name of your working kernel to something else.

Works for me, has been tested several times.
-----------------------------------------------------

Slightly of another: since dhcpd package has been renamed to isc-dhcp-server for restart services I use this script:

```
sudo restart portmap
sudo service isc-dhcp-server restart
sudo stop tftpd-hpa
sudo start tftpd-hpa
sudo service nfs-kernel-server restart
sudo exportfs -ra
```Thank you **baggzy** for:> **baggzy said:**
> I moved the filename "/srv/tftp/pxelinux.0"; from the group block to the subnet block.this is saves my neurons :)

Best regards!

---

### Post by lrilling on 2011-08-06
> **Bocho said:**
> I hope this information will be useful for some people with "multicoloured screen" (I [COLOR=Black]**was**[/COLOR] also among them). "Therapy":
after you create your kernel and got "multicoloured screen", change its name from "vmlinuz-2.6.30-krg3.0.0" for something else e.g. "vmlinuz" (do not forget about "default" in /srv/tftp/pxelinux.cfg/) ... and your kernel is alive.
And vice versa: if you want :) to see "multicoloured screen" - change the name of your working kernel to something else.

Works for me, has been tested several times.


Hi Bocho, this is an interesting point. I must mention that I almost never use "vmlinuz" as filename, more something like "2.6.20-SMP-64". But your observation makes me think that the multi-colored screen effect may be a bug around pxelinux. Maybe just a filename length issue...

Thanks,

Louis

---

### Post by Retrogamer95 on 2011-08-14
Lots of good information here. Once I get a few more workstations from the trash, I think I will try to make a cluster.

---

### Post by wbw on 2011-08-29
I'm interested in making a Beowulf cluster and this thread looks dead on it.

However, I don't have a dedicated switch to use. All machines here are connected on a switch with a fixed IP, therefore if I install dhcp-server on one machine, it shouldn't harm the current network, right? Basically, what I want to know is if it's possible to perform the instructions from the guide the same way without breaking the current LAN?

Any help is appreciated. Thanks in advance.

---

### Post by ajt on 2011-08-29
> **wbw said:**
> I'm interested in making a Beowulf cluster and this thread looks dead on it.

However, I don't have a dedicated switch to use. All machines here are connected on a switch with a fixed IP, therefore if I install dhcp-server on one machine, it shouldn't harm the current network, right? Basically, what I want to know is if it's possible to perform the instructions from the guide the same way without breaking the current LAN?

Any help is appreciated. Thanks in advance.

Hi, wbw.

Your network administrator (if that's not you) will not be happy about you putting another DHCP server on the LAN if one is running already. It's likely that one of your switches is the DHCP server if no other machine is doing it. However, this is like NOTHING in comparision to the deeply anti-social aspect of running a Beowulf on your LAN because it's really easy to saturate the network with traffic between Beowulf nodes.

That's why a Beowulf normally has a private LAN...

You can get a second-hand switch inexpensively off eBay ;-)

HTH,

  Tony.

---

### Post by wbw on 2011-08-29
> **ajt said:**
> Hi, wbw.

Your network administrator (if that's not you) will not be happy about you putting another DHCP server on the LAN if one is running already. It's likely that one of your switches is the DHCP server if no other machine is doing it. However, this is like NOTHING in comparision to the deeply anti-social aspect of running a Beowulf on your LAN because it's really easy to saturate the network with traffic between Beowulf nodes.

That's why a Beowulf normally has a private LAN...

You can get a second-hand switch inexpensively off eBay ;-)

HTH,

  Tony.


Thanks for the fast answer!

Well, I'm not sure if there is a DHCP server already running, since all connections here are only with static IP. I understand point of saturating the LAN, but I was planning on using only two machines for testing purposes. If it works, we will probably be allowed to get a shiny new gigabit switch with some boxes. However, we will only get new "toys" if we prove it will work without any extra expense (oh, and probably without causing an incident on the LAN). =p

Considering the nature of this experiment (really few nodes, computation tasks only to test the process distribution), do you think it can still be problematic for the local LAN?

Thanks again, regards.

EDIT: Is it possible to do it with a router or it has to be a switch? With a router I could test at home with a desktop and a laptop, avoiding possible conflicts.

---

### Post by quequotion on 2011-10-02
> **wbw said:**
> 
EDIT: Is it possible to do it with a router or it has to be a switch? With a router I could test at home with a desktop and a laptop, avoiding possible conflicts.

If your machines have multiple (at least two on the main node, one on a single client node works, two on client nodes if there are 2+) ethernet ports, you can create a private LAN without a separate router or switch. Static IPs would be the way to go in this case.

---

### Post by lrilling on 2011-10-03
> **quequotion said:**
> If your machines have multiple (at least two on the main node, one on a single client node works, two on client nodes if there are 2+) ethernet ports, you can create a private LAN without a separate router or switch. Static IPs would be the way to go in this case.

The basic configuration of TIPC (on which Kerrighed's kernel-to-kernel communications and node discovery rely) requires broadcast ethernet for node discovery though. It's probably possible to tune TIPC to use a router instead, but this is becoming tricky :)

Thanks,

Louis

---

### Post by quequotion on 2011-10-09
> **lrilling said:**
> The basic configuration of TIPC (on which Kerrighed's kernel-to-kernel communications and node discovery rely) requires broadcast ethernet for node discovery though. It's probably possible to tune TIPC to use a router instead, but this is becoming tricky :)

Thanks,

Louis

LOL, I misread. I thought wbw wanted to do it *without* a router....

---

### Post by liangrx06 on 2011-10-17
> **Bocho said:**
> Hi All, and thanks for your posts and replies!

I hope this information will be useful for some people with "multicoloured screen" (I [COLOR=Black]**was**[/COLOR] also among them). "Therapy":
after you create your kernel and got "multicoloured screen", change its name from "vmlinuz-2.6.30-krg3.0.0" for something else e.g. "vmlinuz" (do not forget about "default" in /srv/tftp/pxelinux.cfg/) ... and your kernel is alive.
And vice versa: if you want :) to see "multicoloured screen" - change the name of your working kernel to something else.

Works for me, has been tested several times.
-----------------------------------------------------

Slightly of another: since dhcpd package has been renamed to isc-dhcp-server for restart services I use this script:

```
sudo restart portmap
sudo service isc-dhcp-server restart
sudo stop tftpd-hpa
sudo start tftpd-hpa
sudo service nfs-kernel-server restart
sudo exportfs -ra
```Thank you **baggzy** for:this is saves my neurons :)

Best regards!
   Hello!
    I'm having trouble in building kerrighed 3.0.0 cluster.
    I know from this page that you have successfully building it.
    Can you help me? I mean can you send me a detailed installtion guide?
    Thank you very much!

---

### Post by lrilling on 2011-10-19
> **liangrx06 said:**
> Hello!
    I'm having trouble in building kerrighed 3.0.0 cluster.
    I know from this page that you have successfully building it.
    Can you help me? I mean can you send me a detailed installtion guide?
    Thank you very much!

Hello,

(Just curious) if you are following the [official guide]("http://kerrighed.sourceforge.net/wiki/index.php/UserDoc") from kerrighed.org, which step is failing?

Thanks,

Louis

---

### Post by DB1177 on 2011-12-07
Is this possible with ubuntu 11.1?  I'm new to all of this so I apologize if this is a silly question.

---

### Post by magn0x on 2012-04-18
DB1177, there is no reason, in principle, why clustering will not work with Ubuntu 11.10. However, I'm currently running into difficulties getting it to work. I'm basing my set up on BigJimJams - UbuntuKerrighedClusterGuide created on 26/02/2009. The DHCP server appears to work but, it now appears to be called isc-dhcp-server rather than dhcp3-server. I appear to have set up the TFTP server, but, I'm not confident the bootable filesystem is correctly setup. I get some error messages when using:
# debootstrap --arch i386 oneiric /nfsroot/kerrighed [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
Even so, the file system appears to be created in the /nfsroot/kerrighed directory. But, the node1 is not booting over the LAN from the filesystem on the head node.

---

### Post by ajt on 2012-04-18
> **magn0x said:**
> DB1177, there is no reason, in principle, why clustering will not work with Ubuntu 11.10. However, I'm currently running into difficulties getting it to work. I'm basing my set up on BigJimJams - UbuntuKerrighedClusterGuide created on 26/02/2009. The DHCP server appears to work but, it now appears to be called isc-dhcp-server rather than dhcp3-server. I appear to have set up the TFTP server, but, I'm not confident the bootable filesystem is correctly setup. I get some error messages when using:
# debootstrap --arch i386 oneiric /nfsroot/kerrighed [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
Even so, the file system appears to be created in the /nfsroot/kerrighed directory. But, the node1 is not booting over the LAN from the filesystem on the head node.

Hi, magn0x.

Have you monitored the DHCP server to see it it is responding?

```

tail -f /var/log/daemon.log | fgrep DHCP

```

HTH,

  Tony.

---

### Post by magn0x on 2012-04-18
Hi ajt,
Thanks and Nice one; Even though ifconfig indicates there has been correct ip address allocation to eth0 node1 , I find 'No such file exists', so its back to the beginning for me. I need to think about this.
kind regards,
magn0x

---

### Post by ajt on 2012-04-18
> **magn0x said:**
> Hi ajt,
Thanks and Nice one; Even though ifconfig indicates there has been correct ip address allocation to eth0 node1 , I find 'No such file exists', so its back to the beginning for me. I need to think about this.
kind regards,
magn0x

Hi, magn0x.

The 'No such file exists' error suggests that you've not set up TFTP properly. Bear in mind that pxelinux.0 should be in:

```

/var/lib/tftpboot/

```

And your DHCP server config should be something like:

```
subnet 192.168.0.0 netmask 255.255.255.0 {
	option routers 192.168.0.254;
	filename "pxelinux.0";
	option root-path "192.168.0.254:/var/lib/kerrighed/image";
}

```


HTH,

  Tony.

---

### Post by magn0x on 2012-04-18
Hi Tony,

Yes the first error was LABEL in pxelinux.cfg/default was spelt LABLE. :mad:

     Code:
     /var/lib/tftpboot/pxelinux.0      OK :p


But, I need to review DHCP server config which is more like;  #-o

     Code:
     subnet 192.168.2.0 netmask 255.255.255.0 {
    option routers 192.168.2.1;
        option broadcast-address 192.168.2.255;
}

group {
    filename "pxelinux.0";
    option root-path "192.168.2.1:/nfsroot/kerrighed";
host magn0x1 {
        hardware ethernet nn:nn:nn:nn:nn:nn;
        fixed-address 192.168.2.101;
        }
host magn0x2 {
        hardware ethernet yy:yy:yy:yy:yy:yy;
        fixed-address 192.168.2.102;
        }
server-name "kerrighedserver";
next-server 192.168.2.1;

}



-------------------------------

First node on booting reports:
       Trying to load: pxelinux.cfg/default                                        OK
No DEFAULT or UI configuration directive found!
boot:


Steve

---

### Post by tehowe on 2012-04-19
Since this is the 'easy' thread :)

Has anyone tried a kerrighed node on Precise yet? This looks like it would be fun/frustrating to learn about, even between say a notebook and a desktop as an exercise. That's assuming you can use a commercial router (DD-WRT?) as the go-between. It'll be interesting to read back through the thread and see how it's done...

---

### Post by magn0x on 2012-04-19
I've discovered that to set up the Ubuntu 11.10 image to be booted from the nfs server I require nfsbooted. This is not available in the Ubuntu repositories. It appears to have been in the Debian repositories at version (0.0.15) unstable, but, has since been removed. While it can still be found it appears to be a nightmare to run; requiring various prerequisites.

Has anyone any alternative suggestions to prepare the image for booting from the nfs server   :?:

NB The latest version of Kerrighed is 3.0.0 see [http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page).
Since this is based on Linux 2.6.30 it may prove difficult to run on Ubuntu 11.10 (Linux 3.0.0-17-generic)

---

### Post by Cluster Penguin on 2012-07-13
Hey everyone,

I have been working on a project to get this cluster working on a virtual box. I have successfully completed a  32 bit version (ubuntu 8,04) of the project  (see photo) and have moved onto a 64 bit version (ubuntu 9.04). For some reason however when I use the 64 bit kernel make from kerriged 3.0.0 all I get is a bunch of brightly colored pixels on screen (see photo). At first I thought It might have been caused by sloppy kernel patching on my part so I remade the kernel being careful to note any errors and such. But the problem still remains.    Do any of you have an idea?
I know that the server end is working because the node is receiving the kernel. I just don't know what's wrong with the kernel. 
server os = ubuntu 9.10
node os (given by the server) = 9.04 with kerriged kernel

If the 64 bit works out I might put both up on [sourceforge]("http://sourceforge.net/") so people can finally have a ready out of the box cluster! :shock:\\:D/

Pixaled 64 bit 9.04
                      [ATTACH]221218[/ATTACH] 
 working 32bit 8.04 
                      [ATTACH]221223[/ATTACH]

---

### Post by Cluster Penguin on 2012-07-29
Really? No one has any idea what's wrong with my 64 bit setup? 

Bump.

---

### Post by navic on 2012-09-13
I'm looking for an update on the Easy Ubuntu Clustering project - is anyone working on it anymore??

I am very interested in getting a working SSI with an updated Ubuntu distro... I played with some SSI live distro (can't recall the name at the moment) but it was from 2005 so NIC drivers on new hardware was a nightmare.

On a side note, I have no issue getting basic HPC cluster tech like MPI working on a base Ubuntu system but SSI being a kernel module I get lost quickly.

Thanks!

---

### Post by cisprakash on 2012-09-13
Well this is really great to know about Clustering, i am using Ubuntu from past 6 months and well i am enjoying lot and very curious to learn more about Ubuntu.

---

### Post by NewAmercnClasic on 2012-11-13
I'm also following this thread, I hope to see more updates soon, this is exciting software that can reduce development cost and time especially when clusters are needed to compile large projects; it would be so great to not have to create application specific software again and again.

---

### Post by vak on 2012-11-13
unfortunately Linux clustering is not that active as we might want it.

OpenSSI -- is almost inactive
Kerrighed is "rather a bit alive". 

The interest to the subject is not growing:

[http://www.google.com/trends/explore#q=Kerrighed%2C%20openssi&date=1%2F2006%2073m&cmpt=q](http://www.google.com/trends/explore#q=Kerrighed%2C%20openssi&date=1%2F2006%2073m&cmpt=q)
(you may add "linux clustering" or "ubuntu clustering" there)

Patching the kernel all these years were not that easy as life shows it. It is a pity that Linus Torvalds doesn't look towards clustering. 

Things like global Process IDs, global file descriptors, global socket references, etc are not even discussed at kernel.org

---

### Post by ajtravis on 2013-09-17
> **navic said:**
> I'm looking for an update on the Easy Ubuntu Clustering project - is anyone working on it anymore??

I am very interested in getting a working SSI with an updated Ubuntu distro... I played with some SSI live distro (can't recall the name at the moment) but it was from 2005 so NIC drivers on new hardware was a nightmare.

On a side note, I have no issue getting basic HPC cluster tech like MPI working on a base Ubuntu system but SSI being a kernel module I get lost quickly.

Thanks!

Hi, navic.

I started this thread a while ago, but the project I was working on is now over and my student has left. however, I'm still very interested in Ubuntu clustering. In fact, I'm building a Beowulf in my garage ;-)

Bye,

  Tony.

---

### Post by NickJohn on 2013-11-26
Hi All,
From a quick skim looks like there is no package that you can download and just yet or have I missed something?
Nick

---

### Post by ajtravis on 2013-11-26
> **NickJohn said:**
> Hi All,
From a quick skim looks like there is no package that you can download and just yet or have I missed something?
Nick

Hi, Nick.

Check out Jason Coomb's port of Kerrighed to Ubuntu 12.04 LTS:

  [http://www.kerlabs.com/](http://www.kerlabs.com/)
  [email]Jason.Coombs@kerlabs.com[/email]

HTH,

  Tony.

---

### Post by NickJohn on 2013-11-26
[http://www.stevekelly.eu/cluster.shtml](http://www.stevekelly.eu/cluster.shtml)
in my search today I found the baove site that looks like it is easy scaling after the initial setup

---

### Post by clusterpenguin on 2014-04-15
Kerrighed on Ubuntu 12.04! 0.o That's the best news I'v heard in a long time! I spent all summer (about two years ago) getting this thing running in a VB using ubuntu 8.XX and even though I got it working, none of the soffwere I wanted to run on it would work in Ubuntu 8.XX This is truly fantastic news! I'll see what I can cook up using the sweet 12.04. :D

---

