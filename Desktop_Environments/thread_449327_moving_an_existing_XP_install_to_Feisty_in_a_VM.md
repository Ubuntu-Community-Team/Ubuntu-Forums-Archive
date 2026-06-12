---
title: "moving an existing XP install to Feisty in a VM"
date: 2007-05-20
forum: Desktop Environments
---

### Post by neill on 2007-05-20
hi

i have a fully fledged and tweaked XP install sitting on C: on one of my PCs - all my data is on an ubuntu server

what i want to do is move that XP install such that it runs on a virtual machine in Feisty - i'm assuming virtualbox but not necessarily (note though i don't have a VM enabled CPU but its fast enough for waht i want and there's plenty of RAM)

i want to avoid - if at all possible - having to start again from scratch

anyone any pointers or ideas ??

there is a brief note of a few things that need to be done on the virtualbox site, but it's very much the 'other' bits you need to do

i'm still lacking the basics !!! 

thanks

neill

---

### Post by thelinuxguy on 2007-05-20
This link may help you run the existing Windows installation from VMWare: [http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)
It doesn't create a VM out of the existing installation. Just runs it. I don't have personal experience with this but I guess one needs to be careful. Let me know if you get it running.

EDIT: You said "one of my PCs". In that case, this may not be useful but nevertheless.

---

### Post by neill on 2007-05-20
at first glance this looks very helpful

i'll play around a bit and report back - and i **will **report back although it might well take sometime !!

thanks

---

### Post by veloce on 2007-05-21
VMWare have a tool for converting a physical machine to a virtual one.  However, a colleague could not get it to work on his machine, so YMMV.

---

### Post by rjcc81 on 2007-05-21
Hi!

My console shows this error!

renato@renato-desktop:~$ sudo parted /dev/hdc1
GNU Parted 1.7.1
Using /dev/hdc1
Bem vindo ao GNU Parted! Digite 'help' para visualizar uma lista de comandos.
(parted) unit s                                                           
(parted) print                                                            
Erro: Não pode ter uma partição fora do disco!.                           
(parted)

---

### Post by veloce on 2007-05-21
> **rjcc81 said:**
> Hi!

My console shows this error!

renato@renato-desktop:~$ sudo parted /dev/hdc1
GNU Parted 1.7.1
Using /dev/hdc1
Bem vindo ao GNU Parted! Digite 'help' para visualizar uma lista de comandos.
(parted) unit s                                                           
(parted) print                                                            
Erro: Não pode ter uma partição fora do disco!.                           
(parted)

Cool!  What language is that?

(Or, if you want help, you might want to describe what you are trying to do.  I can't immediately see why you posted under this thread.)

---

### Post by thelinuxguy on 2007-05-22
> **veloce said:**
> VMWare have a tool for converting a physical machine to a virtual one.  However, a colleague could not get it to work on his machine, so YMMV.

Are you referring to the P2V Assistant that used to come with VMware workstation? A lot of users seem to have used it successfully. Could be an option here.

---

### Post by veloce on 2007-05-22
> **thelinuxguy said:**
> Are you referring to the P2V Assistant that used to come with VMware workstation? A lot of users seem to have used it successfully. Could be an option here.

I mean this:
[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)
(One of the free products from vmware).

It should be ideal here, but I have no direct experience.

---

### Post by thelinuxguy on 2007-05-22
Seems to be very good. Looks like the advanced version of P2V assistant because when you download it, it says that "If you are an existing VirtualCenter or P2V Assistant customer and you have a current subscription contract, you are entitled to VMware Converter Enterprise Edition". Does much more than P2V Assistant though.

---

### Post by thelinuxguy on 2007-05-22
Edit: Posted the above twice by mistake.

---

### Post by Sunflower1970 on 2007-05-22
> **veloce said:**
> I mean this:
[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)
(One of the free products from vmware).

It should be ideal here, but I have no direct experience.

How does this work...I install it over on the Windows side to create an image, then point VMWare at it on the LInux side...?

---

### Post by veloce on 2007-05-22
> **Sunflower1970 said:**
> How does this work...I install it over on the Windows side to create an image, then point VMWare at it on the LInux side...?

As I said, I haven't used it, but I would expect that you would 
[LIST=1]
[*]install it on the linux side, 
[*]point it at the windows install 
[*]run the resulting vm on vmware under linux
[/LIST]

This is only based on it potentially having an issue creating a virtual copy of the system it's running on.  You should check the website for more details.

EDIT: Looks like I was all wrong.  This is a windows tool and it can apparently create a vm of the system it is installed on.

---

### Post by jnorth on 2007-05-22
> **veloce said:**
> As I said, I haven't used it, but I would expect that you would 
[LIST=1]
[*]install it on the linux side, 
[*]point it at the windows install 
[*]run the resulting vm on vmware under linux
[/LIST]

This is only based on it potentially having an issue creating a virtual copy of the system it's running on.  You should check the website for more details.

Only problem with installing it on the linux side is that the download is an exe only - no option to dl other formats (tar.gz/rpm/deb, whatever)

I'm attempting a wine-based install of it now on one of my boxes in an attempt to convert a different linux physical disk to an image... not quite what the OP is doing but similar.

EDIT: from the FAQ on VMWare's site:
What Operating Systems are compatible with VMware Converter?
    VMware Converter can run on Windows XP, Windows Server 2003, Windows 2000, Windows NT 4 (SP4 +) and 64-bit versions of Windows XP and Windows Server 2003.
    NOTE: Experimental support only is available for Linux-based physical to virtual machine conversions using the Vmware Converter BootCD (cold cloning) if the source physical machine has SCSI disks.

So - I'm in luck because I'm converting from a physical machine with a SCSI array - YMMV though depending on your setup.

I'm afraid my input isn;'t going to help any more than the others in this case.

---

### Post by marguz on 2007-05-22
Hello,
 You install Converter on the WIndows side and "point" the new VM to your VMware Server running on Linux. 

I've done this.....

---

### Post by veloce on 2007-05-22
> **marguz said:**
> Hello,
 You install Converter on the WIndows side and "point" the new VM to your VMware Server running on Linux. 

I've done this.....

Looks like I was wrong.  Use the windows version.

---

