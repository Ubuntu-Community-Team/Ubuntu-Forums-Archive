---
title: "Dell Optiplex 755 ( with Ubuntu 7.10 ) - Audio issues. Enterprise rollout to 138 empl"
date: 2008-03-25
forum: Dell  Ubuntu Support
---

### Post by SLK55_AMG on 2008-03-25
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R179548&SystemID=PLX_PNT_P4_755&servicetag=&os=WLH&osl=en&deviceid=15256&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=244447](http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R179548&SystemID=PLX_PNT_P4_755&servicetag=&os=WLH&osl=en&deviceid=15256&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=244447)

 

 

This is the bios update to go from A01 to A08.  Evidently the upgrade is turning out to be necessary to get Audio working on this system with Ubuntu 7.10 .

 

 

Something is adressed in the latest bios patch that enables the onboard generic sound to work with Ubuntu 7.10

 

the information listed at the URL here, has an interesting note on #4.

 

 

I would like dell to be more specific about what "linux improvements" there are for the optiplex 755 system.  This is to vague, to be of any use for corporate IT administrators who are looking for specifics.  Optiplexes are typically for an enterprise, and not the home user.

 

 

 

 

My main question is, I would like an ISO version of this BIOS revision, because executable will not run in Ubuntu, and it won't work in Wine.  If dell markets optiplex towards enterprise, at least give an option for linux users an option to burn an ISO so it does a boot envrionment bios upgrade.

---

### Post by john_hull-DELL on 2008-03-25
Try this utility I wrote a while back for flashing the BIOS on Dell systems: [http://linux.dell.com/projects.shtml#biosdisk](http://linux.dell.com/projects.shtml#biosdisk)

If you use the biosdisk install option, the utility will create the necessary disk image and modify your GRUB menu so that you can choose to flash the BIOS from the bootloader.

---

### Post by SLK55_AMG on 2008-03-27
Will see how it works.


John_Hull, can dell possibly think about giving every bios upgrade an ISO option besides executable?  There is variability I have noticed.  Some url's have ISO as the only option, some only have exe as the only option, it varies among different computer models..  Would be cool to have a pre-made A08 iso instead of having to use your utility, which I am sure is an excellent utility.  Will let you know how things go. 


John, do you know if A08 is required to get sound coming out of the t internal speakers on the optiplex 755's?  out of the box, after I do the 204 upgrade packages, sound doesn't work.  There's literally 25+ tutorials out there how to get sound working w/ the onboard audio that comes w/ the optiplex 755, with variance being off the chart(method to have audio success)     If dell is going to start making linux more and more of an option, it would be great I think to have as much out of the box success w/ the Ubuntu integrations as there is with Vista/XP.  




----

well I see you guys are working hard John, at achieving some of the uknowns presented in my questions.

good interview with you I read here:

[http://theciscocommunity.com/index.php?topic=42.0](http://theciscocommunity.com/index.php?topic=42.0)

Ryan.

---

