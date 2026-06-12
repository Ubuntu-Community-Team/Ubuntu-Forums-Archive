---
title: "3D-Games on Windows in XEN"
date: 2006-08-14
forum: Gaming &amp; Leisure
---

### Post by KlausU on 2006-08-14
Hi,

having a VT processor I am wondering if it is possible to not have Dual boot for Windows Games but to run Windows inside XEN and giving it full access to the GFX card?

I would think of switching the GFX card access when starting the Guest-Windows and then somehow maybe starting a script running in the host by ssh from the guest to suspend the Guest and give the Host back control to the GFX Card.

Has anyone done this or an Idea, this would be really cool?

---

### Post by Epsilon on 2006-08-14
As far as I know, you can't run windows through zen without having a processor featuring virtualization :P
I might be wrong though, but last I checked Zen+windows was a no go.

---

### Post by KlausU on 2006-08-14
> **Epsilon said:**
> As far as I know, you can't run windows through zen without having a processor featuring virtualization :P

I do have one... Thats it.

---

### Post by Epsilon on 2006-08-14
Oh? which one would that be? i'm interrested in knowing this myself.

---

### Post by KlausU on 2006-08-14
Core 2 Duo

---

### Post by Epsilon on 2006-08-14
You need ot run Xen 3.0 or higher as thats when intels VT-x was added, supporting unmodified guest os's like windows xp, it should utilize your hardware just as a normal installation.

---

### Post by KlausU on 2006-08-14
> **Epsilon said:**
> You need ot run Xen 3.0 or higher as thats when intels VT-x was added, supporting unmodified guest os's like windows xp, it should utilize your hardware just as a normal installation.

Are you sure? Searching through the Web I found this: [http://wiki.xensource.com/xenwiki/XenFaq#head-d5a7a247a5168517291228a6f02fd74b419badeb](http://wiki.xensource.com/xenwiki/XenFaq#head-d5a7a247a5168517291228a6f02fd74b419badeb) , very sad :(? However elsewhere someone claimed to have run UT 2004 on two Monitors with two GFX Cards in two OSes with two mice/keyboards.

---

### Post by Silentheero on 2007-11-07
Sorry to dredge, but it has been almost a year and I haven't found much in searching. Has there been any changes and are we closer to gaming through Windows through Xen through Linux?

---

### Post by KhaaL on 2007-11-08
I know apple computers has vmware fusion to run 3d games and such... I don't know of anything yet for linux. Virtualbox team are intrested in it, but they need help in implementing it (it's a big task).

---

### Post by cogadh on 2007-11-08
The problem with gaming through VMs, other than the excessive RAM and processor requirements of essentially running two OSes simultaneously, is that they don't have sufficient access to the 3D hardware to pull off the graphics effectively. VMWare has done it with their Fusion product on Macs; VirtualBox is working on it, but still currently uses a "virtual graphics card" that only provides the minimum VESA and VGA support necessary to run a desktop; since Xen was bought up by Citrix, they seem to be focusing on business/server applications and don't really seem to be looking into gaming at all.

---

### Post by nixtux on 2008-07-08
Can Xen do 3D if you have a pair of Nvidia 8800GT cards?

For example, if you assigned 1 card to Ubuntu and the other to Windows?

I'm not looking to run games however I would like to run stuff
like google sketchup and various other OpenGL applications that run 
shabby in Vmware.  Although it would be ideal to be able to run a game from time to time. But certainly not a big concerns as I have a separate partition that never gets used as is.

System specs, Core2Quad, 4GB ram, Asus SLI board.  I'm thinking about upgrading to 8GB soon as I'm putting together another Quad box which will run the VC I currently have.

I have one Nvidia 8800 currently, but I'm debating getting a pair of 8800GT's for this purpose provided it would work with the goal of mutli-display for Ubuntu and a third screen for Windows.

I hope this makes sense and isn't a stupid question as I have search but with little real world information and I would hate to drop 300-400 into new Video cards/ram for no good reason.

Thanks.

---

### Post by KlausU on 2008-07-09
I don't think thats possible, because it would still require the guest-OS to have access to the PCIe bus. But I'm not really into it and I would be glad if someone tells otherwise.

---

### Post by frootloop on 2008-11-13
I've been doinf some research on this myself...specifically the idea of passing a second graphics card straight through to the VM. From the Xen FAQ's ( please correct me if I'm wrong) I understand that its not possible with 1 gfx card, as the host OS maps the gfx memory to a specific location, while the guesy OS assumes its running at location 0 and maps gfx memory accordingly. This doesnt really cover the scenario with two gfx cards. I'd like to try this, but I dont have a VT CPU (Core2 Duo e4300 :( ) Will post back with my experience if i can locate an appropriate CPU that I can afford ;)

---

### Post by frootloop on 2008-11-13
Hmm...looks like motherboard support for vt-d is required..

[http://www.heise.de/english/Xen-3-3-0-hypervisor-ready-for-download--/newsticker/news/114883](http://www.heise.de/english/Xen-3-3-0-hypervisor-ready-for-download--/newsticker/news/114883)

Drat...I'll keep looking..

---

### Post by frootloop on 2008-11-13
Maybe not ...

[http://wiki.xensource.com/xenwiki/CoolConfigurations](http://wiki.xensource.com/xenwiki/CoolConfigurations)

So pass through to a second card is possible...that would mean the memory mapping issue is not a problem on the seconf video card...interesting..

---

