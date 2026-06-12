---
title: "SigmaPlot with wine (or vmware)?"
date: 2007-05-09
forum: Education &amp; Science
---

### Post by Toufik on 2007-05-09
Hi,

I tried to install SigmaPlot with wine but, even if the installation seemed ok, the program doesn't work after: nothing happens when executing.

Does someone manage to make SigmaPlot work with wine ? Is there some useful tips to know for wine

I've read it should be possible with vmware. But i've no clue of how to do it!

Thanks

Toufik

---

### Post by bernied on 2007-05-09
Vmware-server is now free (as in beer) to use. It may even be in one of the repositories (try 'aptitude install vmware-server'). If it's not, go to the vmware site and download vmware-server.

In vmware, you create a virtual machine (VM), which is like a PC inside your PC. This virtual machine has virtual disks (files in your ubuntu file system), and access to your mouse, keyboard, etc. To run sigma-plot, you would want to install windows on this VM, and this is going to be your biggest problem, not because it's difficult to do, but because Windows wants a licence. You can use the activation key on an existing install but this might cause you problems, because even if it's on the same computer, it will look to Windows like it's on a different computer. This can give you grief on both the VM install and on your original install, if you still use it. There is much about this on the web - google 'windows vmware activation'.

So, once you've installed windows in your VM, you can install sigma plot in the VM, then it will run as it would normally. I haven't run sigma plot, but apart from games that need accelerated graphics, I haven't yet found anything that won't run in a Windows VM that runs in Windows on a normal machine.

---

### Post by bernied on 2007-05-09
I should also say that windows runs quite a bit slower in a VM than on the same machine independently. So, for sustained use, you want a fast machine to do this, unless you have great patience.

---

### Post by NikoC on 2007-05-10
Perhaps Rlplot is a nice substitute for Sigmaplot, though it has not all the options (yet) that Sigma has...
No harm done in giving it a try... 
Just startup synaptic and search for Rlplot.

Cheers.

---

### Post by Toufik on 2007-05-10
Thanks for your advices

I haven't googled yet but on my laptop, the Windows "CD" is on the first partition, moreover it's Vista. I already get trouble installing Ubuntu on dual boot...  If I understand the spirit of VM, you have to install a second version of windows on your Ubuntu partition?

For Rlplot, I don't want to redo all the job done during the last two years :)

---

### Post by NikoC on 2007-05-10
A colleague at work advised me to try Virtualbox as an OS 'emulator'...
Going to try it out myself soon... it can be found at [http://www.virtualbox.org/]("http://www.virtualbox.org/").

.deb files are available for ubuntu!

---

### Post by fjf on 2007-05-12
Search for vmware server in the synaptic list and let it install it.  Then start it and create a new virtual machine.  Use NAT network if you want access to internet right away.  Install windows 2000 if you have 1 GB of total ram because it works well with 512 mB of ram, and the rest is for linux.  If you have more, you can go with XP.  Then install the vmware tools (I think they are in the VM menu) as they will allow for better graphics (you can go full screen if you want) and better mouse play.  then install sigmaplot in windows, and it will work fine.

The only problem then is that both machines you have dont see eachother, and you have to figure out the way of communicating both.  I haven't gotten that far.  One way is installing samba in linux and sharing folders in a virtual network.  There are a couple of tutorials about that here, in the tutorials and tips forum.  It involves a lot of command line use in the terminal and I did not try that (yet), but it appears to be the best solution because you can share folders between the hardrives and direcltly copy files from both machines to them.  The second way is to install a program in windows called winscp ([http://winscp.net](http://winscp.net)) and something called SSH in linux (from synaptic) and do file transfers between both hard drives doing a virtual FTP kind of simulated thing.  More primitive perhaps, but it seems easier to do if you are (like me) a linux newbie.  Play and report.  At least, this is fun!.

---

### Post by Bio Leo on 2007-05-13
I don't have experience with VMware server, but I've used VMware Workstation (not a free program) to run SigmaPlot on Kubuntu via Win2k and it worked fine.  I didn't notice any slowdown on a somewhat older laptop, but SigmaPlot isn't a resource hog (at least for what I use it for).

---

### Post by raja on 2007-05-14
If you really want to use sigmaplot only, vmware or virtualbox should be great solutions to run a virtual windows machine. Running windows xp on a host with more than 500 MB RAM, you should not notice any speed difference.
But it really is worth looking at gnumeric and rlplot as alternatives.

---

### Post by leogagliardi on 2011-11-08
Ubuntu is running relatively fast in any not-sooo-old machine. Then, SP will run at normal speed in both, wine or VMs. Opening a Wine software could me more practic. But I must confess I could never run well in wine programs heavier than simple and single small *.exe files. Then, I'm having SP in a Virtualbox WinXP insulated Machine excepting the shared folder. Obviously, when I want to use it I have to wait the init losing my time. The "best" replacement or alternative to Sigma Plot I've found is SciDAVis. It is not similar to SP because it is based on (the more powerful but different) QTIplot, copy of Origin. But in SciDAVis is more easy to handle and customize the plots which is what we-scientifics need to edit our publications!. Forget about the nonlinear regressions tool. Until now I didn't find any nice replacement  (with "nice" I don't mean powerful but simple).

---

### Post by overdrank on 2011-11-08
Back to sleep thread. Thread closed.

---

