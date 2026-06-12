---
title: "Starcraft - issues in a virtual machine"
date: 2007-06-04
forum: Gaming &amp; Leisure
---

### Post by Tyke91 on 2007-06-04
I recently got virtualbox to run windows from ubuntu so that i wouldn't have to restart.

When i first started using it, it worked great except for some resoultion issues. Starcraft would run, but only in a small 620x480 box.

now that I've updated with the VM additions, the resolution errors are gone, but now my SC gives me this error when i try to play

[[IMG]http://images7.pictiger.com/thumbs/98/7af4b43b7c08721350311105158d2698.th.png[/IMG]](http://server7.pictiger.com/img/237651/picture-hosting/-home-mykola-desktop-screenshot-1-.php)

---

### Post by dfreer on 2007-06-04
for one, you can't use 3D graphics within a virtual machine. so most 3D games are out. that being said, although starcraft's system requirements are pretty low I'm surprised you got it working at all.

dunno your default resolution but I'm gonna say 1280x1024 for kicks...
starcraft CANNOT run at any resolution other than 620x480. which means you will either see a 620x480 window on your 1280x1024 desktop, or starcraft is going to change the resolution of your desktop to fit 640x480. The first behaviour is typical, and I'm going to go out on a limb here and say that virtualbox cannot resize your default desktop resolution to fit it's window. Unless there is a fullscreen mode like there is in VMWare.

EDIT: looking at the error message, try doing what it says and changing your windows resolution down to it's requirements.

---

### Post by Tyke91 on 2007-06-04
whoa... hold on.

no 3D graphics in a virtual machine? 

why?

---

### Post by dfreer on 2007-06-04
Try doing a search on here about that, someone else has explained it far better than I can, but I think basically the virtual machines all run on virtual drivers. and no one (although I think vmware is beta testing some) has yet to come up with a virtual 3D capable driver. I think that's basically it.

Yeah it made me cry too once I realized the VMware server I setup wouldn't let me play F.E.A.R. :(

---

### Post by Tyke91 on 2007-06-04
lol... i guess i can still keep it for something... ish... no... not really

ah well... at least it made me happy for a minute or two

---

### Post by zerosystem on 2007-06-05
If you want to play Starcraft, it works perfectly in Wine.

---

### Post by elpichi on 2007-06-05
like zero said starcraft works perfect on wine if you want to change the screen resolution you can always go type winecfg and adjust it to your needs

---

### Post by Tyke91 on 2007-06-05
lol... yeah. i was just hoping to play everything else as well. (using SC as a test)


i've had it in wine for a while... the menus in battle.net bug me, but otherwise it's perfect :)

---

### Post by dfreer on 2007-06-05
Starcraft works pretty well, unless you have a widescreen laptop :(
[http://ubuntuforums.org/showthread.php?t=444565&highlight=starcraft](http://ubuntuforums.org/showthread.php?t=444565&highlight=starcraft)

---

### Post by aanderse on 2007-06-05
[QUOTE=dfreer]for one, you can't use 3D graphics within a virtual machine. so most 3D games are out./QUOTE]

hey while i agree this guy should try to run starcraft through wine i thought i would point out a few things for future reference.

i can't remember the link at the moment, but some guy from university of toronto got opengl to work through a virtual machine.  you can download the source from his site, he had a video of him playing unreal tournament through a virtual machine ... pretty cool stuff.  as well, something i do have a link for .... [http://www.macnn.com/articles/07/05/31/parallels.opengl.directx/](http://www.macnn.com/articles/07/05/31/parallels.opengl.directx/)
opengl and directx in parallels.  now this doesn't do anything for gnu/linux yet, but i'm sure the technology will eventually be reinvented here.  so just something to look forward to for you guys :)

---

### Post by dfreer on 2007-06-05
Hmm, interesting news! Although I'm still waiting for a windows machine to try the rdesktop to lauch applications from windows in linux (possibly games?):
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)
Also this link for vmware users:
[http://www.vmware.com/products/beta/fusion/faqs.html#games](http://www.vmware.com/products/beta/fusion/faqs.html#games)

---

### Post by edemark on 2007-06-05
Hi 
While i agree that it is better to use wine for starcraft as it work well, i would like to indicate that you can actually use some 3d games in an emulated windows. I just finish playing civilization 3 in a wirtually installed win. It can be done in vmwareplayer and there is a thread  on the vmware site explaining how to make it work.

---

### Post by dfreer on 2007-06-05
Link?

---

### Post by edemark on 2007-06-05
[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)
here is one but i remember that there is a thread here in ubuntuforums. If i was not mistaken it was a howto.

---

### Post by dfreer on 2007-06-06
[http://ubuntuforums.org/showthread.php?t=379489&highlight=3d+vmware](http://ubuntuforums.org/showthread.php?t=379489&highlight=3d+vmware)
I know I saw an how-to yesterday but now I can't seem to find it :(

---

