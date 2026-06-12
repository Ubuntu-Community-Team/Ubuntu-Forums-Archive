---
title: "Vmware in new Ubuntu Install with existing Vista partition"
date: 2007-10-04
forum: Desktop Environments
---

### Post by phargarten on 2007-10-04
Just as a preface, I am fairly new to linux but very tech savy with everything Windows. I am trying to make the switch but I want to find a way to virtualize my existing vista partition in Ubuntu. 

Right now I have Ubuntu installed on an external hard drive and that is running great. Vista is installed on an internal SATA drive in my HP dv2000t notebook. 

I am wondering if people reccomend this [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html) guide and if not if there are any ways to run my existing install in Ubuntu. 

I do not have install disks for Vista, only stupid recovery disks from HP that use a version of Ghost I think to reimage the drives. Any suggestions?

---

### Post by bubbalouie on 2007-10-04
Yes, and No....

You could try making and ISO file of the recovery disks and use them to set up a VM. You can configure a VM file here:

[http://www.easyvmx.com/](http://www.easyvmx.com/)

Once you have  VM setup you will be able to point it at you ISO file (open the .vmx file in gedit, kate, nano or some other text editor) to see what I mean. You should be able to restore the image to you virtual hard drive and start playing.

However, I would be skeptical of how well that'd work, for one it'd have no VMWare tools installed which vastly improve the speed of your VM. Also, I seem to recall the standard Vista EULA states somewhere that you may not use it in a VM (not totally sure of this).

My recommendation is to get your hands on a ISO copy of XP (preferably legitimately) and use that instead. Install it on a VM, install VMWare tools on the guest XP (VERY IMPORTANT) and strip out any unwanted services (not as important). By doing this the VM on my 1.83ghz Core Duo is faster than the real install of XP on my old work 1.83ghz Core 2 Duo (admittedly this is in part because the IT guy at my work was unconcerned with making systems run right and filled them with all sorts of nasties like bad network drivers which crashed and chomped up CPU cycles even though the delivered drivers worked fine).

---

### Post by eagledrc on 2007-12-20
if you have vista and it fails, i would just dl windows xp illegally.  if microsoft is making you pay for this junk, just get their old OS.  you bought vista, stop using it and get XP.  its still a microsoft product...

---

