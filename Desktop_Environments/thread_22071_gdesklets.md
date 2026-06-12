---
title: "gdesklets"
date: 2005-03-25
forum: Desktop Environments
---

### Post by danip on 2005-03-25
Am I the only one having problems with gdesklets?  When I started my computer up this morning the starter bar was almost microscopic and I could not click on anything.  I closed gdesklets so I could restart it and now it just won't even start.  Anyone else having problems like this?

---

### Post by cdhotfire on 2005-03-25
well my starter bar doesnt want to work, shows up as a little black dot.  Trying to figure out whats going on.;)

edit: mine starts.  try to open gdesklets in terminal and tell me what it says.

---

### Post by danip on 2005-03-25
```
steve@blackbetty:~$ gdesklets
Starting gdesklets-daemon...


```

Mine is the same thing..a little black dot.  Something must have happened with an update.

edit: I hit control c because it was not doing anything and then gdesklets decided to start up.  I started the starterbar and it started up normal size but when i try to add things I can't.

---

### Post by cdhotfire on 2005-03-25
this is the same thing, must of been update.  Guess we must wait for another update for them to fix.:-k

---

### Post by bobmitch on 2005-03-25
Same problem here - it`s the second time in about 3 weeks it's happened.
Small price to pay for living on the cutting edge I say. :D

---

### Post by rickwood on 2005-03-25
Same problem here after updating.

---

### Post by danip on 2005-03-26
I got the latest updates for hoary.  I can now start up gdesklets and the starterbar but I still cannot add anything to it.

---

### Post by MetalMusicAddict on 2005-03-26
This is great to hear. Im not the only one. :) Will be glad when a update comes. ;)

---

### Post by lordmyth on 2005-03-27
You can allways, as I'm currently doing now (dependencies), go through the hell of building the latest version yourself...

---

### Post by cdhotfire on 2005-03-27
[QUOTE=lordmyth]You can allways, as I'm currently doing now (dependencies), go through the hell of building the latest version yourself...[/QUOTE]

as you said we woudl have to go through that dam hell.8-[

---

### Post by danip on 2005-03-28
has anyone filed a bug report on this since it still is not working?

---

### Post by Leebobs on 2005-03-28
I guess I won't download the latest updates... Let us know when it gets fixed please?

Leebobs

---

### Post by yusufk on 2005-03-29
The problem seems to be with the StarterBar Desklet, my other ones seem fine. I lost all my launchers and cant add any new ones. 

Weird!

---

### Post by mike998 on 2005-03-29
I can start the starterbar and it I get the home icon in full size.
If I add any more icons, it doesn't show.  If I restart the starterbar it goes microscopic.
If nobody has reported this as a bug, I am willing to. (I'm at work so it would have to wait till I get home.)

---

### Post by nico1278 on 2005-03-29
Just upgraded to hoary from warty and gdesklets are definitly not working right. I can't get working most of the desklets... The one I use most of the time hopefully works fine ( plain clock ), but I have to manualy start the demon very time... When I log out with saving the current session, the demon is not started the next time. Does any one have the same problem ?

---

### Post by danip on 2005-03-29
go to system>preferences>sessions from there you can have gdesklets start up every time you log in.

---

### Post by yusufk on 2005-03-29
[QUOTE=mike998]I can start the starterbar and it I get the home icon in full size.
If I add any more icons, it doesn't show.  If I restart the starterbar it goes microscopic.
If nobody has reported this as a bug, I am willing to. (I'm at work so it would have to wait till I get home.)[/QUOTE]
Please report it, I dont think anyone here has and I dont have time at the moment!

Thanks

---

### Post by Dracontopes on 2005-03-29
[QUOTE=danip]go to system>preferences>sessions from there you can have gdesklets start up every time you log in.[/QUOTE]
 Thank you thank you thank you ;)

---

### Post by mike998 on 2005-03-29
Bug report logged : bug number is 8367.

--EDIT--

"gdesklets is an universe component, we don't use this bugzilla for universe
packages. You can mail the ubuntu-users list or contact the MOTU team about it."

Okay.. Guess that's not the right way to go about it.  I will check out the gdesklets forums later on today if I get time.

---

### Post by Steel3 on 2005-03-30
Offhand, this doesn't work for me either.  I'm encountering the same difficulties.

---

### Post by danip on 2005-04-02
Does anyone know of any sarge repositories that would have gdesklets in it?  Perhaps that might fix the problem.

---

### Post by tigger on 2005-04-10
There is a new version of StarterBar available! You can download it from [here]("http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210"), it comes with PyXDG 0.8, so the problem with the newer PyXDG is 'solved'! It at least works here :D

some install notes:
 close gDesklets first (don't know if it is necessary)
 After downloading it to [path] (by example: ~/Desktop):
  ```
cd ~/Desktop
 tar zxf starterbar-desklet-0.31.3.tar.gz
 cd starterbar-desklet-0.31.3.tar.gz
 python Install*.bin
```
 And then you can start gDesklets again and use the StarterBar

---

### Post by emperor on 2005-04-10
[QUOTE=nico1278]Just upgraded to hoary from warty and gdesklets are definitly not working right. I can't get working most of the desklets... The one I use most of the time hopefully works fine ( plain clock )/QUOTE]

Same problem here, the LTCandy Weather Desklet quit working after a apt-get upgrade a couple days ago and as of yesterday, the Rhythmlet stop working. I remember seeing that gdesklets package was upgraded about a week ago.

The gdesklets package is at revison 0,34 and the gdesklets-data package is still at revison 0.32. I would bet that this is the problem!

---

### Post by artinla on 2005-04-10
My gdesklets starts up but I can't run any of the desklets.

---

### Post by somuchfortheafter on 2005-04-10
I just wanted to say that it is seriously screwed, i installed via synaptic, apt-get, compiled from source, tried different debs, compiled via apt-get source. Still nothing works ahhhhhhhhhhhhhhhhhhhhhhhhhhh.

---

### Post by darkaudit on 2005-04-10
Ok. Here's the deal. Many of the gdesklets in the gdesklets-data have been rendered obsolete by the new version of gdesklets proper. Some of these desklets have not been updated in years. In particular, the PSI series has been removed from the collection on the gdesklets home page because the maintainer is AWOL and the desklets no longer function.

I've switched from PSI and LTCandy desklets to the new SideCandy series. These are designed for the new implementation of gdesklets.

If there is a bug to be filed, it should be against gdesklets-data for holding onto those obsolete desklets.

---

### Post by danip on 2005-04-10
[QUOTE=tigger]There is a new version of StarterBar available! You can download it from [here]("http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210"), it comes with PyXDG 0.8, so the problem with the newer PyXDG is 'solved'! It at least works here :D

some install notes:
 close gDesklets first (don't know if it is necessary)
 After downloading it to [path] (by example: ~/Desktop):
  ```
cd ~/Desktop
 tar zxf starterbar-desklet-0.31.3.tar.gz
 cd starterbar-desklet-0.31.3.tar.gz
 python Install*.bin
```
 And then you can start gDesklets again and use the StarterBar[/QUOTE]


Awesome it works great for me

---

### Post by somuchfortheafter on 2005-04-10
I am using the lt ones an gdesklets is still broken :(

---

### Post by Xian on 2005-04-10
[QUOTE=darkaudit]I've switched from PSI and LTCandy desklets to the new SideCandy series. These are designed for the new implementation of gdesklets.

If there is a bug to be filed, it should be against gdesklets-data for holding onto those obsolete desklets.[/QUOTE]
Yeah, I not sure what happened in this regard. I know the developers went through and removed alot of the old sensor desklets, but there are still many that remain which won't work with the newer Gdesklet releases.

Just be sure to try and only use the recent desklets.

---

### Post by emperor on 2005-04-11
I un-installed the "gdesklets-data" package and then went to [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/) and downloaded some Side Candy "working" displays. 

Then open the "gDesklets Shell" (gDesklets in the Applications-Accessories) and from the "File" menu you can use the "Install package" option to load the package which will insert it in the category list for easy selection.

---

### Post by griefman on 2005-11-30
Hi
i'm having a few problems with the memory and disk gauges... i've tried all that are available on the site and there is still the problem that the gauge doesnt show how much of the disk is free and how much is used, i mean that this field where it has to be shown graphically the current condition of the space its somehow allways full and not only full it's even overfilled, as if i'm over my free space. But for instance the numeric value of the free space or memory is ok... i have ho idea why this could happen.... because of the fact that it happens on every applet with disk and memory stats, i think that the problem is somehow common for my system.
please help... i look really shitty... all other applets are working just fine.... only this little scratch....:)

thnx

---

### Post by emperor on 2005-11-30
[quote=griefman]Hi
i'm having a few problems with the memory and disk gauges... i've tried all that are available on the site and there is still the problem that the gauge doesnt show how much of the disk is free and how much is used, i mean that this field where it has to be shown graphically the current condition of the space its somehow allways full and not only full it's even overfilled, as if i'm over my free space. But for instance the numeric value of the free space or memory is ok... i have ho idea why this could happen.... because of the fact that it happens on every applet with disk and memory stats, i think that the problem is somehow common for my system.
please help... i look really shitty... all other applets are working just fine.... only this little scratch....:)

thnx[/quote]

type "df" in the terminal and see how it reports the mounted drive.

I have had similar problems with drives reporting wrong values before. Partion Magic 8 was not able to move or copy the partions either. The problem partions contained a Fedora Core 2 installation.

---

### Post by griefman on 2005-12-01
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3             13309348  12597232    712116  95% /
/dev/hda1             31117872  28939588   2178284  93% /media/hda1
/dev/hda5             33206320  29126988   4079332  88% /media/hda5



this is what i get... i as i said the numeric value in the applet is ok... it is showing the right amount of free space... but the graphic... that little bar that gets filled in and out when i use more space or less...that little stupid bar thinks somehow that i have used more space then i have... couse it is overfilled... i dont get it.... please help!!!
i'm getting crazy about this thing:)

---

