---
title: "Any way to get Compiz-like effects under VMware, w/o 3D acceleration?"
date: 2008-03-07
forum: Desktop Effects &amp; Customization
---

### Post by dnquark on 2008-03-07
I am running Ubuntu under VMWare.  I would very much like to have the Compiz Scale and Desktop Wall plug-ins (essentially, same as OS X's Expose and Spaces).  I know that Compiz can't run on virtual hardware, but are there any other window managers or applications that might provide the Scale / Desktop Wall functionality?  Seems that it wouldn't be so resource-heavy so as to not run on VMware.

---

### Post by boeing777 on 2008-03-07
i don't think it's possible.

---

### Post by BooBooNTZU on 2008-03-07
> **dnquark said:**
> I am running Ubuntu under VMWare.  I would very much like to have the Compiz Scale and Desktop Wall plug-ins (essentially, same as OS X's Expose and Spaces).  I know that Compiz can't run on virtual hardware, but are there any other window managers or applications that might provide the Scale / Desktop Wall functionality?  Seems that it wouldn't be so resource-heavy so as to not run on VMware.


I'm not 100% sure on this but , i think Compiz is running 100% on the processor .... If you install the file xserver-xgl you can probably run it even in the virtual machine. The reason i'm saying that it runs on the processor only is because everytime i rotate that cube you can see the CPU being used 100%.

UPDATE:

Yes , Compiz it's working in a virtual machine. You just need to configure it properly. I've tried it in a virtual machine but , it was the Innotek VirtualBox , not the vmware thing. You have to install the virtual machine additions which installs the accelerated video driver. Then install all the packages related to Compiz , GLdesktop , xserver-xgl , xgl .... That's about it .... You'll probably end up with keyboard shortcut conflicts if you have Compiz running on the Host machine and the Guest machine simultaneously  .... You can select different keyboard shortcuts for each or turn off Compiz on the host . I'll post some screenshots soon. Thanks for the idea.

UPDATE: 

Here you have a few screenshots.
I'm pretty sure it's gotta work with other virtual machines too but you have to install the VM additions to get the accelerated drivers working properly.
By the way , the innotek VirtualBox is free and you can download it from their website while the VMware thing is not. 

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by dnquark on 2008-03-09
I just tried installing Hardy Alpha 6 under VirtualBox (Windows host) and I can't get compiz to work.  I installed the vboxadditions (Devices->Install guest additions), and installed xserver-xgl in synaptic.  However, when I try compiz --replace, it fails: 
```
leoa@leoa-vbox:~$ compiz --replace&
Checking for Xgl: [1] 6292
leoa@leoa-vbox:~$ not present. 
No whitelisted driver found
```

Any idea on what might be going wrong?  

I hope to get this working.  I'm kind of surprised that (judging by the responses in this thread) there are no tools other than compiz (or maybe other fancy 3d WM's) that provide the basic scale/desktop grid effects...

---

### Post by dnquark on 2008-03-09
Never mind, got this to work after a few tries -- vboxadditions were finicky.

One problem that took a while to resolve was that Virtualbox was not detecting the LCD panel of my laptop correctly and would only run in low-res mode, however I followed the instructions from [http://ubuntuforums.org/showthread.php?t=610407](http://ubuntuforums.org/showthread.php?t=610407) and everything works fine -- I believe the key was to set the correct horizontal sync / vertical refresh settings.

All seems to work now, although my hardware is a bit too weak for virtualized compiz.  I allocated a gig of RAM and 128 megs of video RAM in virtualbox to the guest OS, but things are laggy.  I bet it would work fine on a fast machine, though.

---

