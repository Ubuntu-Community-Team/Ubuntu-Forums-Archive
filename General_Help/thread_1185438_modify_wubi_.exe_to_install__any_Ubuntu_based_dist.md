---
title: "modify wubi .exe to install  any Ubuntu based distro !!!"
date: 2009-06-12
forum: General Help
---

### Post by paok4 on 2009-06-12
[CENTER]I have seen this [http://http://ubuntuforums.org/showthread.php?t=1062504&highlight=remastersys]("http://http//ubuntuforums.org/showthread.php?t=1062504&highlight=remastersys")

 but it looks very difficult for me !!! Is there any modified wubi .exe that allows you to install an ISO from your hard disk (ubuntu based / mostly 8.10 / created with remastersys or reconstructor) having just a browse tab where you can select the ISO you want to setup ? If there isn't an already modified wubi for this  , is there some easy way to make something like that ? Or probably directions how to compile wubi (8.10 or 9.04) to have this option ???[/CENTER]

---

### Post by paok4 on 2009-06-13
OK I did everything !!! 

Compiled Wubi OK
Modified Remastersys OK
Finally I created the live cd with custom isolist.ini and  wubi in it , burned it to a cd ...
Under windows vista the Wubi autoruns correctly and during the setup process is looking to connect to [http://something]("http://something/") !!! and the process stops after a few attempts ...
Why is not using the CD ??? Where is the problem ???

PS: the only thing that doesn't look correct to me is that the .DISK/info file in the generated ISO still says ''Ubuntu 8.10 "intrepid" - Release i386 (20090613)'' and not something like Custom CD bla bla bla ... Isn't that supossed to be generated differently from the modified remastersys ???

Any help ????

---

