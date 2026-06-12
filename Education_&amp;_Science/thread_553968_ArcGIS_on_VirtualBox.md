---
title: "ArcGIS on VirtualBox"
date: 2007-09-18
forum: Education &amp; Science
---

### Post by Go_Bucks on 2007-09-18
I have found numerous discussions of Mac users running ArcGIS software in a virtual pc environment but have not found the same anywhere for Linux. Does anyone know if you can run ArcGIS on a Linux PC running Windows XP in VirtualBox? Even better, would that same virtual environment run Microsoft Access (for the purpose of integration with personal geodatabases in ArcGIS)? 

My employer is really digging the whole Linux thing after I badgered him into letting me install it on one of our office workstations, and I am replacing the Windows server with a Linux one. Our only current problem in fully switching to Linux on desktops is the need to run ArcGIS (though GRASS is outstanding, it does not easily do [or we don't know how to easily do] many things we do regularly in ArcGIS), Access, and a couple of environmental consulting-related government agency software tools that only run in a Windows environment (but those are simple enough I would have to assume they will run on VirtualBox).

---

### Post by Soybean on 2007-09-18
If it works on Macs, it ought to work on Linux. Once you're inside VirtualBox, you're essentially in the same "place" regardless of the outer operating system. That's the theory, anyway. As long as nobody comes in here and says, "I've tried it, it doesn't work," I think you should probably at least test it (and let us know!).

One consideration, though: if your people are pushing ArcGIS to its limits on their current Windows PCs, you could have a problem. You'll essentially be downgrading their computers and expecting them to do the same things they were doing before (VirtualBox effectively simulates a Windows PC with lower specs than the PC it's running on). I'm told that a lot of people use ArcGIS with relatively small maps, so it'd be fine... I'm just saying, the GIS guys where I work would NOT be happy about having to run ArcGIS on a system with less RAM. ;)

---

### Post by Go_Bucks on 2007-09-18
Thanks for the response. Unless someone said no, I was intending to try it out, but there is no way that I can try every ArcGIS function we use, Spatial Analyst, various ArcInfo modules, etc in a relatively short timeframe. Then again, if we get basic ArcMap functionality and can generate maps and basic GIS layers, we could use ArcMap on VirtualBox and maintain a Windows PC with remote access capability for more resource-intensive uses. 

I am still hoping for a GRASS/qgis solution but the problem is final product (e.g., cartography). GMT, though it makes outstanding maps, is too difficult to expect everyone to use for final products (not to mention the time-intensiveness of exporting everything from GRASS to GMT), qgis right now has VERY limited ability on the final mapping front (and NO ability to make maps in our standard format), and GRASS simply has no ability to do anything other than stick a limited-edit scalebar, north arrow, and legend on your image.

There are also issues with ease of managing data tables in the Linux GIS workflow, least cost corridor analysis in GRASS (which we use for wildlife movement corridor analysis... GRASS only allows point features for the start and end and we really need the polygon start and end ability of ArcGIS), and the fact that GRASS doesn't allow you to overlap polygons (which is good in many situations, but we require overlapping polygons in certain development project land use impact over time tracking applications). 

Anyway, I am blabbing. I will try to get an install on the office Linux box when I get the time (I am only at the office one day a week) and report what happens. I know there are number of other GIS people on this board who may be interested.

---

### Post by Go_Bucks on 2007-09-18
I should also state that we are going down this road because my employer agrees with me (after discussion with a professional tech guy) that we do NOT want to put Vista on our computers and with frequent new hardware purchases, we can't run XP forever. Though my role is primarily as a biologist/project manager, I am good with computers and software and I make all the determinations in our company of how resource data gets from biologists in the field to a final CEQA/NEPA/FESA document with maps years later.

---

### Post by hzambran on 2007-09-19
I have installed Innotek Virtual Box in my Ubuntu Feisty 7.04 and it runs without any problems,a nd the reason why I installed this virtual machine is because i still need some functions from ArcView 3.2 (do you remember it ?). Everything works fine and there is a little penalty in the shapefiles load time, but I think it could be improved with more RAM, but up to now, the penalty is small enough.

But, I'm trying to move to GRASS and is it true that the final map is still a little bit far form those coming from ESRI world, but now is it also possible to put a grid in the image, with the corresponding UTM (in my case) coordinates. Furthermore, for working with the information within the maps (more than for presenting the maps) I think GRASS is faster and more powerful than ArcGIS.

---

### Post by Nikos.Alexandris on 2007-10-21
I am trying to do the same... ! To migrate to GRASS.

I use ESRI software under VirtualBox.

---

### Post by cohoking on 2007-10-24
I am also attempting to break my long-standing association with ESRI and move to GRASS/QGIS.  One quick thought on map production, I have found that once you have the components squared away it is almost always better to produce the final map with an external program like Corel Draw (in windows). I would be interested to hear opinions on a good Corel/Adobe illustrator replacement in Linux which can edit postscript fluidly (GIMP??).

---

### Post by Nikos.Alexandris on 2007-11-06
Did you try GRASS6.3

Its really powerful!

*New GUI called wxgrass and many addons in the official GRASS page.

---

### Post by standingfire on 2007-11-17
Yes you can, there is no problem what so ever that I have found to date. I loaded a student version on my laptop in a Virtual box VM running windows on Xubuntu 7.04, I upgraded to 7.10 with nary a hiccup.[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

All that you need to ensure is that you have enough memory allocated for the VM, ramp up the video card settings to something realistic, ensure that the network in the VM can connect outside the machine, then you should be on your way.

---

### Post by sasquatch74 on 2007-11-19
> **standingfire said:**
> Yes you can, there is no problem what so ever that I have found to date. I loaded a student version on my laptop in a Virtual box VM running windows on Xubuntu 7.04, I upgraded to 7.10 with nary a hiccup.[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

All that you need to ensure is that you have enough memory allocated for the VM, ramp up the video card settings to something realistic, ensure that the network in the VM can connect outside the machine, then you should be on your way.

Which version of ArcGIS did you install? 
Did you install it through XP or Vista?

---

### Post by kolibri on 2008-01-31
I'm considering doing this- wondering which would be the best set-up to get ArcGis (Arcmap-scene etc) running on an Ubuntu laptop.  It would be a standalone license.  Does anyone else have any experience?  I'm wondering if dual booting windows and Ubuntu, running Arcmap in VIrtualBox, or trying to run it under Wine would work the best.
 I don't have the computer I'd be running it on yet, so I can't play with it myself.

---

### Post by Nick Lake on 2008-08-03
Does anyone have any performance metrics for ArcGIS on VirtualBox? Our usage at work is quite heavy and I would be interested to see what the performance hit would be.

I've not used VirtualBox so how would something like pass-through authentication to our ArcSDE instance work?

Appreciate any feedback (good or bad).

- Nick

---

### Post by dstath on 2009-05-03
I was also able to run ArcGIS 9.3 on Ubuntu 9.04 using virtual box. It runs without any errors whatsoever. Never crashed up to now. The speed is excellent. I would say 90% for most of the tasks. I 've tried geoprocessing, layout and also python scripts. 

I am able to work on data saved on ubuntu disks via the shared folders of virtualbox. No need to duplicate the data. I can simply open a .mxd that is stored in ubuntu, work with it and save back again. 

I tried WINE and lin4win also. It can not run with WINE. With lin4win it
installs and opens but crashes even when you add a single simple layer.

I didn't try VWmare but vitrualbox is definitely the solution to running arcgis on ubuntu.

---

### Post by OldDirtyTurtle on 2009-05-26
I'm utterly ashamed that I've not found this thread until now.  :oops:

I'm putting ArcGIS on my Sys76 laptop this week.  I'll be sure to give a blow-by-blow once I get it running and start working with my data.

---

### Post by adolfo158 on 2009-06-04
[FONT="Arial"][SIZE="4"][COLOR="Navy"]Hi all:
 I am just beginning to figure out how to post.

I will be installing ArcGis 9.2 on a Virtual Windows XP running in Ubintu 9.04. I will be working on various GIS topics since I am an old Geographer that is updating its GIS skills.

I am not sure if I understood correctly but "dstath" post did not say that virtualized windows XP and run ArcGis from there. He said that run ArcGis from Virtual Box, is that possible? or is understood that it should be run from within the virtualized XP?

Adolfo
[/COLOR][/SIZE][/FONT]

---

### Post by machoo02 on 2009-06-05
Programs cannot be run "from VirtualBox".  VirtualBox is virtual machine software that will allow you to install a guest operating system within VBox...a 'system within a system' if you will.

For any Windows program to run, you will need to install Windows XP (or whatever flavor of Windows you want) on the virtual machine.  Once XP is installed within VBox, any Windows progam installed within the virtual machine will run as if XP was installed on bare metal (with the exception of programs with heavy 3D graphics, but that's changing as well).

BTW...I have ArcGIS 9.2 installed on my virtual instance of XP, and it works just fine.  A little slower than if XP was native...but that's to be expected.

---

### Post by adolfo158 on 2009-06-05
[SIZE="4"][COLOR="Navy"]OK Understood. Thank you "macho02" 
:D[/COLOR][/SIZE]

---

### Post by carlo S on 2011-01-11
hello

i yust can't get virtualbox (win xp) to load the cd of arcmap 9.3.1, every time i insert the cd in the drive it gives me an error.

Im running uubuntu-10.10-desktop-i386
and in virtualbox i have installed xp 

hope you guys and girls can help me 
cause i need this prog for school exams.

thanks

carlo

---

### Post by rs87424 on 2011-02-25
[QUOTE=machoo02]Programs cannot be run "from VirtualBox". VirtualBox is virtual machine software that will allow you to install a guest operating system within VBox...a 'system within a system' if you will.

For any Windows program to run, you will need to install Windows XP (or whatever flavor of Windows you want) on the virtual machine. Once XP is installed within VBox, any Windows progam installed within the virtual machine will run as if XP was installed on bare metal (with the exception of programs with heavy 3D graphics, but that's changing as well).

BTW...I have ArcGIS 9.2 installed on my virtual instance of XP, and it works just fine. A little slower than if XP was native...but that's to be expected.[/QUOTE]

I have already installed arc map 9.2 on vista just recently using a single use student edition of the software from my university. I was wondering if there was any way for me to install it on ubuntu 10.10 using virtualbox even after I have registered the product on Vista?

---

### Post by sffvba[e0rt on 2011-09-30
Seeing as this thread is pretty old, and varies attempts at bumping it and asking for assistance on similar issues in the last year or so has proven futile at getting support I am going to close it.


404

---

