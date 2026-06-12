---
title: "My Ubuntu CAD station"
date: 2006-03-08
forum: Education &amp; Science
---

### Post by dalani on 2006-03-08
AS long time autocad user, I am evaluating CAD 3D apps on Linux for Architectural visualizations: Contrary to what one might think, it is possible to find killer apps for LInux. For hth e longuest time autocad was king app for Win32. I know this has been discussed before.  But now after some search I found a few LINUX Cad 3d apps that run on native UNix (no wine required).  Here are a few links I found that are quite good.

[CYCAS]("www.cycas.de") and Aryam
CyCAS is classified as commercial software but makes a public version aviable for Deb. I installed this on my Hoary 5.04 easily and it runs as expected. Frequent Autocad users be prepeared to spend a brief time to familiariaze yourself with the welcome simplicity  of its interface. It draws in 2d AND 3d with built-in archtecturals like openings for doors, windows and curtain walls complete with sizable mullions. 
Its approach is a blessing after successive versions of feature bloated autodesk software. It exports to the renderer [POVray]("http://www.povray.org/") and the reasonably priced 68euro BASIC version will exprot in DXF format.  Nitpicks is that it does not yet output to [RADIANCE]("http://http://www.cs.wisc.edu/~schenney/sced/dining.rad.jpg") (the phenomenal physics based radiosity-raytracer). The closest thing is this source code [POV-RAD translator]("http://www.cs.gsu.edu/mathcsc/research/hvl/radiance/pov2rad.c") I found.  If any programmer can make a decent LINUX front end to the RADIANCE or POVRAY app it would be much appreciated. (These OSS linux renderers  can put apps costing thousands to shame).

Other 3d modelers are SCED and Ayam. Both of these are new to me but have been around a while. SCED is a constraint baed modeler that can export in RENDERMAN, POV and RADIANCE.  If anyone have actualy used these or others post them here.

I am especially interested in hearing about real world applications in  modeling and simulation FEA, lighting design etc...

---

### Post by verbalshadow on 2006-03-08
I haven't tried most of this apps but there is a list at [Gnome Files Graphic/Design section]("http://gnomefiles.org/category.php?cat_id=4") and you might also look at Blender it exports to DXF and many other formats as well.  It also Exports to [URL="http://mywebpages.comcast.net/rayae1/tutorial.html"] 	
RADIANCE[/URL]

---

### Post by halfvolle melk on 2006-03-09
Solid Edge is also available for Linux (according to Google).

---

### Post by eMuNiX on 2006-03-09
I’d like to more of the proper full-blown 3D CAD modelling systems move to Linux.  I use Unigraphics, CATIA and Autodesk Inventor (plus a little ProE) and would love for these to move over to linux.  Certainly UG, CATIA and ProE started life on Unix workstations and may even still be supported so the transition would not be so great.  I believe that there is a version of ProE available for linux already.  Obviously none of these products would be available for free.

---

### Post by LKRaider on 2006-03-09
The CAD area is one that I miss in Linux, specially on the Architectural side.

Software like Autocad and SketchUp that are of daily use on my WinXP install just don't have up-to-par alternatives on the Linux world. And I blame the same companies that make them. Autodesk latest releases could be considered as simple bloatware. If they would spend half the time they do in developing new annoying popups in a cross-platform application we could be using Autocad on Linux for years now. Instead they seem to drive further away from this at every release they make.
And I am not even going to mention the dreaded DWG closed-format market dominance...

Can't Mark Shuttleworth just buy these companies and OpenSource them? :P


Note: here is a Novell poll for software that you must use and would like to see on the Linux platform: [Take Novell Linux Apps Survey]("http://www.novell.com/coolsolutions/tip/16646.html")

---

### Post by dalani on 2006-03-09
For good work flow and immediacy for Architectural projects I think CyCAS comes closest to Sketch-up ease of use and consise tools. Ive tried sketch-up but I like CYCAS on linux (very stable).  CYCAS uses another approach to 3d drawing than simple extrude and booleans. Walls are drawn and completed with openings in seconds.

As for autodesk, I think if they would just had stopped at A2004 it would have been fine-but there's word now  about encrypted file headers in the latest dwg version and a subscription model for new releases. Open standards are a must when interchanging files. At work, all dwg  files are saved in A2000 to insure our engineers can open the files( some are still using A14). When will autodesk  learn that proprietory file formats are hindrance to business.

Blender's interface is overwhelming and counter-intuitive - it seems more suited for wasting time on a steep learning curve.  I would not recommend that one for general 3d design work. A word of advice to Linux cad-3d developers out there: make your keyboard shortcuts remappable so autocad users like myself can make the transition. (all pros use the keyboard to activate functions-cross screen mouse clicks are too slow). 

> I&#8217;d like to more of the proper full-blown 3D CAD modelling systems move to Linux. 

Maya, THE pro 3d broadcast quality app, has been available for Unix for years. It's been used for everything from architectural stills to TV ad animations. It doesn't get more full blown than that.

RADIANCE can max out any cpu. Anyone use Rendercity.com render farm (all 64bit linux clusters) for speed?? For that matter can anyone tell where one can find cut-paste IES photometric data that can inserted into a scene without requiring a phd in computer science???

---

### Post by dudus on 2006-04-09
I'll give a try for Qcad and CYCAS. 
Are these stable on Dapper?

---

### Post by dalani on 2006-04-15
[QUOTE=dudus]I'll give a try for Qcad and CYCAS. 
Are these stable on Dapper?[/QUOTE]

I used CYCAS and Qcad both on Hoary so I can't tell you how these fare on Dapper. But im sure they must work fine because they run on Gtk libs.

---

### Post by curuxz on 2006-04-15
Out of intrest are you guys Archs then? Im studing Arch tech (much more on the CAD side than standard Arch). I have been looking for ages for a good arch-cad program but cant get anything working, im highly tempted to just say sod it and sit down and learn blender.

---

### Post by John.Michael.Kane on 2006-04-15
curuxz these may help
[http://k3studio.sourceforge.net/](http://k3studio.sourceforge.net/)
[http://www.kpovmodeler.org/](http://www.kpovmodeler.org/)
[http://www.povray.org/](http://www.povray.org/) [http://megapov.inetart.net/](http://megapov.inetart.net/)
[http://www.k-3d.org/](http://www.k-3d.org/)
[http://www.wings3d.com/](http://www.wings3d.com/)
[http://kludge3d.sourceforge.net/](http://kludge3d.sourceforge.net/)
[http://www.linux.org/apps/all/Graphics/CAD/CAM.html](http://www.linux.org/apps/all/Graphics/CAD/CAM.html)
[http://www.ribbonsoft.com/](http://www.ribbonsoft.com/)
[http://www.bartels.de/bae/bae_en.htm](http://www.bartels.de/bae/bae_en.htm)
[http://www.bocad.com/home/en/index.htm](http://www.bocad.com/home/en/index.htm)
[http://www.cycas.de/](http://www.cycas.de/)
[http://diffractive.optics.free.fr/](http://diffractive.optics.free.fr/)
[http://www.gnome.org/projects/dia/](http://www.gnome.org/projects/dia/)
[http://www.soffernet.com/jaime/fandango/](http://www.soffernet.com/jaime/fandango/)
[http://askoh.com/freecad/](http://askoh.com/freecad/)
[http://www.cadcam.co.at/freiter/gCAD3D_en.htm](http://www.cadcam.co.at/freiter/gCAD3D_en.htm)
[http://www.graphiteone-cad.com/en/index.htm](http://www.graphiteone-cad.com/en/index.htm)
[http://lignumcad.sourceforge.net/doc/en/HTML/index.html](http://lignumcad.sourceforge.net/doc/en/HTML/index.html)
[http://www.nocrew.org/software/ocadis/?part=about](http://www.nocrew.org/software/ocadis/?part=about)

---

### Post by zubrug on 2006-04-15
I hope that they follow through on the Science / Math forum, it would be very usefull, this thread is great.

Thanks for the links all.

---

### Post by hizaguchi on 2006-04-15
[QUOTE=dalani]Blender's interface is overwhelming and counter-intuitive - it seems more suited for wasting time on a steep learning curve.  I would not recommend that one for general 3d design work. A word of advice to Linux cad-3d developers out there: make your keyboard shortcuts remappable so autocad users like myself can make the transition. (all pros use the keyboard to activate functions-cross screen mouse clicks are too slow).[/QUOTE]
Blender's interface is only counter-intuitive if you're not willing to put in the time to learn it.  Once you get used to it, it is more efficient than any other modeling program I've ever used.

> Maya, THE pro 3d broadcast quality app, has been available for Unix for years. It's been used for everything from architectural stills to TV ad animations. It doesn't get more full blown than that.
Depends on what you want to use it for.  That's why CATIA has been mentioned in this thread.  You can draw a really pretty model in Maya, but the one I draw in CATIA can be easily converted to design drawings for production, or evaluated for mass properties, or have its dimensions easily revised later, or have its history reviewed by another engineer, or integrate with a database manager like SmarTeam.  I don't know of any Linux CAD programs that really meet these needs.

---

### Post by curuxz on 2006-04-16
Thanks SD, im constantly trying these lists when I see them on the forums. ill have a look again since you have put a few up I have not tried yet :)

---

### Post by Efrain Valles on 2006-04-16
is there an app for viewing DWG files...???
I have installed qcad but id only works with dxf files... and I need to only view DWG

---

### Post by John.Michael.Kane on 2006-04-16
Efrain Valles this may help. [http://lx-viewer.sourceforge.net/](http://lx-viewer.sourceforge.net/)

---

### Post by hizaguchi on 2006-04-16
[QUOTE=Efrain Valles]is there an app for viewing DWG files...???
I have installed qcad but id only works with dxf files... and I need to only view DWG[/QUOTE]
Are they Autocad DWGs, or Personal Designer/4D DWGs?

For Autocad, the Open Design Alliance has some tools.  [http://www.opendesign.com/](http://www.opendesign.com/)

For Personal Designer, you can use DosBox to run the latest version of PD, but you have to jump through some flaming hoops to get it to work.  (Compile DosBox 0.65+, use a Windows computer (or maybe Wine) to setup PD, copy the PD directory to your Linux machine and run it under DosBox).

---

### Post by John.Michael.Kane on 2006-04-16
hizaguchi check the link i posted. (LX-Viewer is a program that will allow you to open, view, print and convert DWG or DXF files, typically used in AutoCAD related technical drafting.)

---

### Post by Efrain Valles on 2006-04-16
[QUOTE=SD-Plissken]hizaguchi check the link i posted. (LX-Viewer is a program that will allow you to open, view, print and convert DWG or DXF files, typically used in AutoCAD related technical drafting.)[/QUOTE]

I use Autocad... great stuff guys...:D

---

### Post by John.Michael.Kane on 2006-04-16
Efrain Valles that program should help you with reading DWG files outside of autocad.

---

### Post by hizaguchi on 2006-04-16
[QUOTE=SD-Plissken]hizaguchi check the link i posted. (LX-Viewer is a program that will allow you to open, view, print and convert DWG or DXF files, typically used in AutoCAD related technical drafting.)[/QUOTE]
Yeah, I saw that.  I just thought I'd mention another option.  Plus, there are 2 types of DWG files... one is made by Autocad and the other is the native format of a Dos-based 2d CAD package called Personal Designer, which some people still use.  Most DWG viewers won't open the PD DWGs because, despite having the same extension, they are totally different files.

---

### Post by Efrain Valles on 2006-04-18
[QUOTE=hizaguchi]Yeah, I saw that.  I just thought I'd mention another option.  Plus, there are 2 types of DWG files... one is made by Autocad and the other is the native format of a Dos-based 2d CAD package called Personal Designer, which some people still use.  Most DWG viewers won't open the PD DWGs because, despite having the same extension, they are totally different files.[/QUOTE]

again great things... 

I am trying them ... 

=Eff=

---

### Post by naught101 on 2006-08-05
nice thread. looking good. Archimedes looks like it has lots of promise, but I installed it using the .jar file, and now I can't figure out how to run it! damn...

Blender's interface IS cool, but takes a bit to get into. one of the things that it needs before it can be used for architectural stuff is multiple dimension inputs, and angle snapping, similar to Archicad, or autocad.

there was a CAD project in the blender dev, at [http://projects.blender.org/projects/blendercad/](http://projects.blender.org/projects/blendercad/) but it seems to be dead.

---

### Post by naught101 on 2006-08-05
oh, and sketchup does work in linux, to some extent. I have used the free windows version in dapper, and the modelling works. the only serious problem is that the 32bit cursors don't work, which makes it hard to use. there are other minor problems, but it's usable.

there's a winehq.org entry on it here [http://appdb.winehq.org/appview.php?appId=1815](http://appdb.winehq.org/appview.php?appId=1815) , if there's any coders interested.

---

### Post by nitao on 2006-08-11
> **LKRaider said:**
> The CAD area is one that I miss in Linux, specially on the Architectural side.

Software like Autocad and SketchUp that are of daily use on my WinXP install just don't have up-to-par alternatives on the Linux world. And I blame the same companies that make them. Autodesk latest releases could be considered as simple bloatware. If they would spend half the time they do in developing new annoying popups in a cross-platform application we could be using Autocad on Linux for years now. Instead they seem to drive further away from this at every release they make.
And I am not even going to mention the dreaded DWG closed-format market dominance...

Can't Mark Shuttleworth just buy these companies and OpenSource them? :P


Note: here is a Novell poll for software that you must use and would like to see on the Linux platform: [Take Novell Linux Apps Survey]("http://www.novell.com/coolsolutions/tip/16646.html")


I just found out about this discussion so I am a bit late.
Anyway, I just wanted to mention that we agree with you in the fact that CAD for Linux are hard to find and when you do, they never think about the architectural side. This is why we started [Archimedes]("http://archimedes.iv.fapesp.br") which is an open source CAD software for architects being developed with architects.
It is still very young and therefore uncomplete. Unstable versions are released weekly and stable ones about each month so check it out and please send us your feedback.

Thanks,
Hugo

---

### Post by Efrain Valles on 2006-08-11
YEah Marky... just Buy Adobe and Buy the rights to Autocad...

:)
Free at last free at last thank god almighty they will be Free software...

Ok... back to reality...

NEVER GONNA HAPPEN

:)

---

### Post by hizaguchi on 2006-08-11
> **eMuNiX said:**
> I’d like to more of the proper full-blown 3D CAD modelling systems move to Linux.  I use Unigraphics, CATIA and Autodesk Inventor (plus a little ProE) and would love for these to move over to linux.  Certainly UG, CATIA and ProE started life on Unix workstations and may even still be supported so the transition would not be so great.  I believe that there is a version of ProE available for linux already.  Obviously none of these products would be available for free.
Catia still runs on Unix, and I've heard it works on Linux too.  Wish I could say the same for SolidWorks. :(

---

### Post by Ijump2 on 2006-09-20
I'm curious, has anybody installed PTC ProE Wildfire 3 on Ubuntu and if so, how?

---

### Post by francisco.colaco on 2006-10-04
After trying in two very different computers with Ububtu to run Progesoft Intellicad Trials with WINE, I just hat to give up and keep a computer with Windows just for Machanical CAD work and printing with the Minolta M2300W laser.

Either with msvcrt.dll native or builtin, Progecad will not run.  I am quite bothered to keep a computer running windows for absolutely no reason, but that is what I can do to run a decent CAD software.  QCad, which I have tried, it is still quite basic for the work I do, and does not have 3D, though I think it has been improving quite well.  For the rest of us, there is VariCAD, which I bought several years ago, but gave it up two years later for the Autocad compatibility was flaky (and that is what I needed to interact with others.)

---

### Post by eMuNiX on 2006-10-05
> Maya, THE pro 3d broadcast quality app, has been available for Unix for years. It's been used for everything from architectural stills to TV ad animations. It doesn't get more full blown than that.Maya is a 3D modelling and animation package it is not a 3D CAD modelling package.  Maya is for visualisations, a 3D CAD modelling package such as Catia is for manufacturing.  They are 2 quite different animals.

This evening I might have a look at [http://www.webersys.com/](http://www.webersys.com/) this is a 3D CAD/CAM package that runs under Linux, I wonder how good it is compared to full blown commercial 3D CAD packages such as SolidEdge, SolidWorks and Inventor.  I doubt that it can hold a light to something like Unigraphics or CATIA though.

---

### Post by hollowhead on 2006-10-09
qcad works very well on dapper. I have used it to produce scaled drawings for simple planning applications (vertical drawings) and cycas for floorplans the local authority said they were good enough to submit.

---

### Post by dalani on 2006-10-27
Sad but true: nothing beats Sketchup for ease of use, flexibilty and price for 3d work. If sketchup was availab;e for linux, I would have delete my windows partition years ago. 

Qcad? I use AUtocad daily and most CAD software use the same concept and shorcuts. You can invent a car that steers with your feet and uses handoperated brakes but no one will buy it. HenriFord and Benz a century ago decided the basic car control layout. Dont tell me about motorbikes ; you can't do half the things a car does with a bike. It's the same with some software like autocad which established itself as leader in the field. 

All this to say I tried Qcad but dropped it because it wasn't possible at the time remap the keyboard shortcuts.

Now that googlesketchup is here, that's my package of choice for all around use. (I  use autocad and SUpro at work).

---

### Post by dalani on 2006-10-27
epilogue: for anyone still interested in Cycas it's the only linux cad  program I have on my computer. I've even done some decent renderings with POV with Cycas3. But since Sketchup5 and googles's free version of sketchup, it\s hard to stick with Cycas. Many have requested a linux version of SU and that might happen someday.

---

### Post by dalani on 2006-10-28
Here is test rendering of my kitchen done with Cycas demo and POV (which i've barely explored)  great renderings are possible and cycas integrates POV in situ. But for modeling, Cycas could use more intuitive tools. My model can be done in Sketchup in a matter of minutes without pre-amble. Cycas required more planning...

[IMG]http://dalani.com/StudioM_files/scene.jpg[/IMG]

---

### Post by DynaWerx on 2007-03-15
Great information here, folks.  Thanks a bunch!

Most of the CAD products referenced here are slanted more toward 3D... what I am looking for is CAD that I can use to create engineering and surveying maps.  That is, a subdivision plat or engineering design plans for, say, a roadway.

I haven't tried qcad yet, but I wanted to check here before I got too excited.  ;-)

Edit:  I should note that I currently use AutoCad 2006 in Windows XP, but I don't use all of the functions simply because all I need to create is a 2D map.

Thanks!

---

### Post by AnRa on 2007-03-17
What about [BRL-CAD](http://www.brlcad.org/)?

It has a deb package here: [http://sourceforge.net/project/showfiles.php?group_id=105292&package_id=113559](http://sourceforge.net/project/showfiles.php?group_id=105292&package_id=113559)

---

### Post by MontanaMax on 2007-05-21
> **LKRaider said:**
> Software like Autocad and SketchUp that are of daily use on my WinXP install just don't have up-to-par alternatives on the Linux world. ...
And I am not even going to mention the dreaded DWG closed-format market dominance...

Can't Mark Shuttleworth just buy these companies and OpenSource them? :P


That would be the coolest thing ever!!

AutoDesk is one of the largest and most influential companies behind groups like the Software Business Alliance who specialize in investigating and closing down companies for software license violations along with Micro$oft, so I don't think they will come over to the FOSS world on their own.  :(

---

### Post by sexybobo on 2007-05-23
I know this post is going to make me look stupid. But the only 3d design type work i have ever done is for game maps. what does say auto cad offer that [qeradiant]("http://www.qeradiant.com/top/") does not. or are they just 2 completely different program types.i have never used auto cad but from what i understand it lets you make 3d models of items with your pc which is also what qeradiant does. does it just have a much larger functionality. (like paint compared to photoshop) or is it more like the difference of gimp to photoshop (bad interface to good and photoshop has more function that i will never use) or is it like comparing apples to oranges?

---

### Post by LKRaider on 2007-06-02
Autocad is used for professional work, that is, architects, engineers, etc who need to correctly draw plans and schematics according to standards and rules, plot them in different paper sizes and so on.

The problem is Autocad is so integrated on the workflow of these professions it is almost impossible to replace it. Talk about company lock-in. Autodesk has a monopolistic lock-in of several of these projectual professional fields all over the world.

---

### Post by scott stanley on 2007-07-31
Hope this thread gets noticed, been dead a while. I saw a screenshot of NX4 running on ubuntu posted by one "whiprush". The guy's like a phantom; google hits up the wazoo but never a point of contact.

Anyway, does anyone know how to install NX4 on ubuntu?

---

### Post by LKRaider on 2007-08-02
There's a Linux version of NX4:

[http://worldcadaccess.typepad.com/blog/2006/04/ugs_we_heart_li.html](http://worldcadaccess.typepad.com/blog/2006/04/ugs_we_heart_li.html)
[http://www.evanyares.com/the-cad-industry/2006/4/11/cad-on-linux.html](http://www.evanyares.com/the-cad-industry/2006/4/11/cad-on-linux.html)

PTC Pro Engineer Wildfire 3.0 also runs on Linux:
[http://ubuntuforums.org/showthread.php?t=336942](http://ubuntuforums.org/showthread.php?t=336942)

---

### Post by LaserJock on 2007-08-05
> **scott stanley said:**
> Hope this thread gets noticed, been dead a while. I saw a screenshot of NX4 running on ubuntu posted by one "whiprush". The guy's like a phantom; google hits up the wazoo but never a point of contact.

Anyway, does anyone know how to install NX4 on ubuntu?

I know whiprush personally (awesome guy), if you need to contact him PM me and I'll give you his address.

-LaserJock

---

### Post by mechanicfox on 2007-12-31
Hi, I have installed with success Autocad R14 in Ubuntu 7.04-Feisty, 
with the Wine Emulator.
I have tried other variants, there are with "i"-from internet suffixes, but they didn't work at all.
I haven't a variant of Autocad 2k, not Autocad 2000i, to try.
It seems it works, too.
I have installed the DWG TrueConvert with Crossover and I am converting the drawings to R14...........
It the best I could do.
I wish you for you all the Ubuntu enthusiasts all my best wishes!!!

---

### Post by parhyang on 2008-07-09
> **Efrain Valles said:**
> is there an app for viewing DWG files...???
I have installed qcad but id only works with dxf files... and I need to only view DWG
Re : DWG Viewer
you should try this:
[http://ftp.varicad.com/pub/VariCAD/linux/varicad2008-view-en_2.03-1_i386.deb](http://ftp.varicad.com/pub/VariCAD/linux/varicad2008-view-en_2.03-1_i386.deb)
hope this help :)

---

### Post by Nothingbetter2do on 2008-07-15
actually it is possible to get Autocad R14 (it pre dates .net framework) to run on linux

[http://architectafrica.com/bin0/news200411111_wine.html](http://architectafrica.com/bin0/news200411111_wine.html)

R14 can do most of what the newer versions can without all the bloatware added

---

### Post by C.S.Cameron on 2008-07-15
R14 works fine in wine except it does not have orbit.
Recall there were some 2nd party orbit plugins available for it though

---

### Post by Nothingbetter2do on 2008-07-15
i tried autocad 2009 for windows.......man is it bloated... it takes ages even on a good rig to load... i got 
windows xp pro sp3(had mce 2005 but its useless in ireland - no decent DVB-T service yet)/ubuntu 8.04 amd64 dual boot,
AMD Athlon x2 6000+ @ 3.0ghz,
Asus M2N E -SLI motherboard
4gb Corsair XMS 2 DDR PC6400 ram (4x 1024mb)
512mb XFX nVidia geforce 8500gt pci-e x16 video
Hauppauge HVR 1300mce  Tv Tuner
500gb SATA2 Western Digital Hard drive
500gb USB2 Western Digital Hard drive
16x Toshiba Dual layer DVD/R/RW/RAM drive

(i had Vista Home Premium x64 SP1 but file transfers were so slow & unreliable [7-10 kb/s ***_YES_*** 7-10kb/s file transfer speeds on a SATA2 drive] i fdisked the pc and put back on xp sp3)

---

### Post by riggomatic on 2008-08-17
I'm running 8.04, and decided to install WINE today.  I have a copy of IntellicadCMS that installed fine, and works.  IntelliCADcms is not free, but it opens 98% of Autocad drawings.

[http://www.intellicadms.com](http://www.intellicadms.com)

---

### Post by longtom on 2009-02-18
Hi,

I was using an ancient version (1996/7) of TurboCad and TurboCad 3d in connection with FloorPlan 3D which I bought in those days.  It was still working fine in XP.

Anything you can recommend for furniture construction?  2D would be fine for the moment - if 3D as well I take it as a bonus.

Greetings

longtom

---

### Post by bigsexy on 2009-08-20
or you could just install WINE and run windows programs

---

### Post by acornbrain on 2009-08-30
I do architectural drafting for a manufactured housing company. At work, we use AutoCAD (Windows).

I'm thinking about switching my home OS over completely to Ubuntu.

I went from an office that used AutoCAD 2006 to one using 2009. (I can't tell any difference except the silly "ribbon" that we do not use anyway.) I would not want to return to pre-2006 autocad because I like the dynamic blocks feature.

Have not yet tried Wine (only been on Ubuntu for a few days) is it fairly straightforward to install and use?

If I were to use wine to run Autocad..what is the procedure? Install Wine and then pop in the AutoCad startup disk and see what happens?

Will macros I've written in VBA and LISP run normally?

---

### Post by czigor on 2009-09-16
> **acornbrain said:**
> I do architectural drafting for a manufactured housing company. At work, we use AutoCAD (Windows).

Have not yet tried Wine (only been on Ubuntu for a few days) is it fairly straightforward to install and use?

If I were to use wine to run Autocad..what is the procedure? Install Wine and then pop in the AutoCad startup disk and see what happens?


You can install wine in synaptic. Then upon right-clicking on setup.exe (or whatever) on your install cd you can choose Open with Wine. 

As far as I know the last version of AutoCAD that worked under wine was R14. If you want to have a later version you can either install a virtual machine or dual boot.

---

### Post by chayzer on 2009-09-16
> **acornbrain said:**
> I do architectural drafting for a manufactured housing company. At work, we use AutoCAD (Windows).

I'm thinking about switching my home OS over completely to Ubuntu.

I went from an office that used AutoCAD 2006 to one using 2009. (I can't tell any difference except the silly "ribbon" that we do not use anyway.) I would not want to return to pre-2006 autocad because I like the dynamic blocks feature.

Have not yet tried Wine (only been on Ubuntu for a few days) is it fairly straightforward to install and use?

If I were to use wine to run Autocad..what is the procedure? Install Wine and then pop in the AutoCad startup disk and see what happens?

Will macros I've written in VBA and LISP run normally?

According to [winehq appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11538") 2009 is "garbage" on wine. I did mess around with 2008 and it did run alright. Eventually dug up an old copy of XP and went back to a dual boot system (sigh) for the first time in 3 years after switching to Linux.

---

### Post by hsweet on 2009-09-19
I at first thougt qcad was too primtive.  Now I'm rather starting to like it for exactly that reason for teaching drafting.  The fact that you have to do most of the work helps students understand the basic principals.  Later on they will be more effective with more sophisticated CAD since they will know what the computer is doing for them.

That, and Google should get off their **s and port Sketchup.  Hopefully by the time they release their OS.

---

### Post by fmonson on 2010-10-16
> **verbalshadow said:**
> I haven't tried most of this apps but there is a list at [Gnome Files Graphic/Design section]("http://gnomefiles.org/category.php?cat_id=4") and you might also look at Blender it exports to DXF and many other formats as well.  It also Exports to [URL="http://mywebpages.comcast.net/rayae1/tutorial.html"] 	
RADIANCE[/URL]
Amen to your last, and Semper Fi.

---

### Post by LexingtonNC on 2012-04-06
> **verbalshadow said:**
> I haven't tried most of this apps but there is a list at [Gnome Files Graphic/Design section]("http://gnomefiles.org/category.php?cat_id=4") and you might also look at Blender it exports to DXF and many other formats as well.  It also Exports to [URL="http://mywebpages.comcast.net/rayae1/tutorial.html"] 	
RADIANCE[/URL]

The link is borked. [http://gnomefiles.org/index.php?xcontentmode=322x323x324](http://gnomefiles.org/index.php?xcontentmode=322x323x324) will get ya there, though.

---

### Post by Elfy on 2012-04-06
It is a 6 year old post.

 Old thread closed.

---

