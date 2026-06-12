---
title: "Vmware -the focus is shifting"
date: 2007-04-29
forum: Desktop Environments
---

### Post by StoneySS on 2007-04-29
I know that this might be the wrong place to post this but i can't find the right place, so i apologize for that :)

Now, i'm using windowsXP with vmware for ubuntu 6.10 (i think thats edgy)
I press the full screen button and after like 10 seconds, it goes back to the program window.
I can still use it but i have to switch between the two OS's so i can scroll to the top/bottom.

On both OS's i use 1024x1050 res with a 60Hz refresh rate.

Again, i apologize if this is the wrong forum, but i'm really stuck and i love ubuntu so far :)

---

### Post by veloce on 2007-05-01
I can't quite understand what you mean but, if you are running a virtual xp under vmware server running on ubuntu, then I suggest you stop using the vmware server console for running the xp vm.

I've had much better usability from using gnome rdp over host only network to the virtual machine.  It's much more responsive and just works.

---

### Post by galileux on 2007-05-08
> **veloce said:**
> I if you are running a virtual xp under vmware server running on ubuntu, then I suggest you stop using the vmware server console for running the xp vm.

I've had much better usability from using gnome rdp over host only network to the virtual machine.  It's much more responsive and just works.

Hi Veloce.
I just had massive performance problems with VMware WS 6 Beta on Feisty on a Core2Duo and 4 GB RAM.
The problem was solved by following your advice on the number of processors, in another thread. I had them set to 2 on all guests.

If you're interested, the thread where I published the problem is
[http://ubuntuforums.org/showthread.php?t=437353](http://ubuntuforums.org/showthread.php?t=437353)

At VMWare they weren't much helpful: here's the thread on their site:
[http://www.vmware.com/community/thread.jspa?threadID=83605&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=83605&tstart=0)

Now I would like to ask you more details about your other suggestion: "using gnome rdp over host only network".

Where could I find detailed instructions to accomplish that on feisty_amd64?

Thanks!

---

### Post by veloce on 2007-05-10
> **galileux said:**
> Hi Veloce.
Now I would like to ask you more details about your other suggestion: "using gnome rdp over host only network".

Where could I find detailed instructions to accomplish that on feisty_amd64?

Thanks!

Unfortunately, I don't know of any detailed instructions anywhere.  I'll check my notes to see if I can write them up as a howto.  Here's a better description of how I have it set up:

Ubuntu Feisty running vmware server 1.02 (should upgrade to 1.03 but I haven't).
VMware Server has two virtual networks - Bridged and Host Only. Turned off inbuilt DHCP server.

Virtual machines:
Virtual Firewall - IPCop + BlockOutTraffic - has two virtual network cards - one to the bridged network one to the host only.  I use this to control the access from the virtual machines to my work network and the internet.  Is the DHCP server for the host only network.

Win XP machines - have virtual network card connected to the host only network.  Have "allow remote connections" turned on.

Under ubuntu i run gnome rdp.  I connect to a running vm via it's ip address on the host only network.

---

