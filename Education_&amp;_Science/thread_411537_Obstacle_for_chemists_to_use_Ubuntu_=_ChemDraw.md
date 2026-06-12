---
title: "Obstacle for chemists to use Ubuntu = ChemDraw"
date: 2007-04-17
forum: Education &amp; Science
---

### Post by tak1150 on 2007-04-17
There is ONE thing that stands in the way of chemists who'd like to completely migrate from Windows to Linux...

It is the 2D Drawing software (or lack thereof)!
In Windows and Mac, we all use ChemDraw (I should be specific, for all of us who are organic chemists).

Xdrawchem is really getting there and I'm grateful for the developers, But it is not quite satisfactory (bugs, resolution, stability).

Some people might be aware that when one tries to install ChemDraw via Wine, it (v. 9, at least) installs but there is a major bug; atoms appear as black boxes.

I'd like to call on the bright ones who're reading this to help get ChemDraw to work with Wine. For a simpleton like me, all I can do is shuffle around native DLLs to no avail. They got IE6 to work with wine and made IE4Linux package. I'm confident somebody can!

May God bless you a bunch.

Tak

---

### Post by tak1150 on 2007-04-17
Thought I'd post the screenshot of what I was talking about and the output in the terminal.

```
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:ole:OleUIAddVerbMenuA ((nil), (null), 0x280, 16, 65, 66, 0, 0, 0x33fd28): stub
fixme:ole:OleUIAddVerbMenuA ((nil), (null), 0x280, 16, 65, 66, 0, 0, 0x33df08): stub
fixme:ole:OleUIAddVerbMenuA ((nil), (null), 0x280, 16, 65, 66, 0, 0, 0x33df08): stub
fixme:ole:OleUIAddVerbMenuA ((nil), (null), 0x280, 16, 65, 66, 0, 0, 0x33e43c): stub

```

[ATTACH]29915[/ATTACH]

---

### Post by LaserJock on 2007-04-18
I know what you mean. I'm a Physical Chemist, so I don't do much *wet* chemistry but it seems we have a lot of 2D molecular editors but none that quite stand up to ChemDraw. One you might look at is a Java app called JChemPaint ([http://almost.cubic.uni-koeln.de/cdk/jcp)](http://almost.cubic.uni-koeln.de/cdk/jcp)). It seems nice. 

This is also why I'm trying to help out as much as I can on a really cool project called gchemutils ([http://www.nongnu.org/gchemutils/](http://www.nongnu.org/gchemutils/)) that is becoming a whole Chemistry suite (crystal viewer, 3d molecule viewer, periodic table, molecule calculator) and will soon be incorporating GChemPaint ([http://www.nongnu.org/gchempaint/](http://www.nongnu.org/gchempaint/)) another good 2D molecular editor.

-LaserJock

---

### Post by tak1150 on 2007-04-18
Thanks for your tip.
Does JChemPaint or GChemPaint copy and paste into, say OpenOffice?

Because for us researchers, the most important use of these softwares is for presentation / publication.

So if I can't copy / paste into OO Impress or OO Writer, it's not much use (though I know I can save them as pics, etc). I noticed that no other Linux programs I've tried (Chemtool, BK..., a couple others I forgot) does that except for Xdrawchem.

---

### Post by briansers on 2007-04-18
Hi there!  As yet another physical chemist (and a spectroscopist as you might imagine) I don't need chemical drawing programs as much as some.  However, I too, still need them.  I was poking around the internets one day and found the following review:

[http://groundstate.ca/chemdraw]("http://groundstate.ca/chemdraw")

It is fairly old (2004), but the reviewer does specifically address importing drawings into Open Office.  Hope it helps some.

---

### Post by tweedledee on 2007-04-18
> **tak1150 said:**
> Thanks for your tip.
Does JChemPaint or GChemPaint copy and paste into, say OpenOffice?

Because for us researchers, the most important use of these softwares is for presentation / publication.

So if I can't copy / paste into OO Impress or OO Writer, it's not much use (though I know I can save them as pics, etc). I noticed that no other Linux programs I've tried (Chemtool, BK..., a couple others I forgot) does that except for Xdrawchem.

While it's not "copy and paste," you can export from BKChem to an OO Draw file, which then integrates just fine into the rest of OO (as well as allowing for some advanced editing, once the structure is in place).  I find "copy and paste" solutions to be unreliable anyway when forced to convert a file to an MS format (especially presentations for Powerpoint), as the images often lose a great deal if they were not properly imported.  (Incidentally, that is true in Windows as well for OO -> Powerpoint, as well as Powerpoint -> Powerpoint if the version changes from 2000/XP to anything higher or vice versa.)

Personally I've found BKChem to be better for my purposes than ChemDraw (the recent versions spend too much time trying to change my structures for me!), but I only need it occasionally.  It also seems more reliable (stable) than most of the other tools (though I've not tried the Java-based ones).  I have hope for GChemPaint, but I don't think it's quite there yet.  Of course, I'm also partial to Python solutions, as I regularly use the language.

---

### Post by lbyrd33 on 2007-05-11
> **tak1150 said:**
> There is ONE thing that stands in the way of chemists who'd like to completely migrate from Windows to Linux...

It is the 2D Drawing software (or lack thereof)!
In Windows and Mac, we all use ChemDraw (I should be specific, for all of us who are organic chemists).

Xdrawchem is really getting there and I'm grateful for the developers, But it is not quite satisfactory (bugs, resolution, stability).

Some people might be aware that when one tries to install ChemDraw via Wine, it (v. 9, at least) installs but there is a major bug; atoms appear as black boxes.

I'd like to call on the bright ones who're reading this to help get ChemDraw to work with Wine. For a simpleton like me, all I can do is shuffle around native DLLs to no avail. They got IE6 to work with wine and made IE4Linux package. I'm confident somebody can!

May God bless you a bunch.

Tak

I have a similar problem with installing Chemoffice 9 using crossover office. I dont have the black box problems as I can see all carbon-carbon bonds; however, when you want to put in a heteroatom I am left with just a blank white box where the atom should be. Everything else seems to work fine. Even though I cannot see the atom, the program does notice it as I can see the change in the mass.

---

### Post by tak1150 on 2007-05-12
> **lbyrd33 said:**
> I dont have the black box problems as I can see all carbon-carbon bonds; however, when you want to put in a heteroatom I am left with just a blank white box where the atom should be. 

I meant to say that I only have problems with the heteroatoms as well. Also any text that you type in will be all black boxes!

[This person]("http://appdb.winehq.org/appview.php?iVersionId=5524") claims on WINE App DB that s/he got it to work after installing "gdiplus.dll" I have tried that and it didn't work...

I don't have crossover (yet) but maybe if you put gdiplud.dll in your ~/.wine/drive_c/windows/system32 folder, w/ all the Crossover stuff it might work...?

---

### Post by lbyrd33 on 2007-05-12
> **tak1150 said:**
> I meant to say that I only have problems with the heteroatoms as well. Also any text that you type in will be all black boxes!

[This person]("http://appdb.winehq.org/appview.php?iVersionId=5524") claims on WINE App DB that s/he got it to work after installing "gdiplus.dll" I have tried that and it didn't work...

I don't have crossover (yet) but maybe if you put gdiplud.dll in your ~/.wine/drive_c/windows/system32 folder, w/ all the Crossover stuff it might work...?

Thanks, Ill give it a try later.

---

### Post by Enverex on 2007-05-12
If it currently doesn't work in Wine even without tweaking then you could speak to Codeweavers about it and see how much they'd charge to get it fully working and supported. If you all chipped in then it may be affordable, just depends how much effort it would take and how many people want it.

One sidenote though, DO NOT use native DLLs unless you know it specifically needs them. Feeding Wine/CO native DLLs will normally break it unless there is good reason to use them.

---

### Post by Iridos on 2007-06-01
> **lbyrd33 said:**
> I have a similar problem with installing Chemoffice 9 using crossover office. I dont have the black box problems as I can see all carbon-carbon bonds; however, when you want to put in a heteroatom I am left with just a blank white box where the atom should be. Everything else seems to work fine. Even though I cannot see the atom, the program does notice it as I can see the change in the mass.

Black box or white box - AFAIK, this is the same problem. I think I have seen both over the time, but cannot remember anymore what I changed (I thought it was colordepth of the Xserver, but when I try to reproduce it now, wine only runs in a 24/32 bit truecolor mode).

One thing, that seems to cause it is the wine-version (or the version of one of the libraries it uses). The problem appeared several years ago - before that, displaying characters worked fine (although there were other gliches - but not as dramatic ones as these boxes which render ChemDraw nearly useles).

I.

---

### Post by Iridos on 2007-06-01
PS. I should probably mention that I use Debian, not Ubuntu - the problem still is exactly the same, but I might have been using wine/chemdraw for longer than Ubuntu actually exists. In regard of this, it is possible that Ubuntu never had a version of wine+libs that did not have the problem

---

### Post by tak1150 on 2007-06-01
> PS. I should probably mention that I use Debian, not Ubuntu - the problem still is exactly the same, but I might have been using wine/chemdraw for longer than Ubuntu actually exists. In regard of this, it is possible that Ubuntu never had a version of wine+libs that did not have the problem

I have only tried Ubuntu / wine /chemdraw since Ubuntu Edgy (2006 Oct), but for that period what you said about ubuntu is true.

> 
If it currently doesn't work in Wine even without tweaking then you could speak to Codeweavers about it and see how much they'd charge to get it fully working and supported. If you all chipped in then it may be affordable, just depends how much effort it would take and how many people want it.

I have emailed CambridgeSoft directly, but have not received any replies (no surprise); I told them that it'd be good for them if they got it working in Linux so that Linux chemists would use their product as well, but oh well.

---

### Post by Iridos on 2007-06-07
> **tak1150 said:**
> (quoting tak1150): I have only tried Ubuntu / wine /chemdraw since Ubuntu Edgy (2006 Oct), but for that period what you said about ubuntu is true.

Hm, perhaps it depended on Chemdraw version? It definitely exists in Chemdraw 6.0.
This is a very long time period, we're discussing and I switched universities etc. 
I think the problem appeared when updating some packages, but it is so long ago, I cannot be sure.
I

---

### Post by Iridos on 2007-06-07
I did some research on this.  (Had already typed it, but got logged out and it was all lost)
ColorDepth was mentioned here:[http://appdb.winehq.org/appview.php?iVersionId=1336&iTestingId=869](http://appdb.winehq.org/appview.php?iVersionId=1336&iTestingId=869)
- but that seems to have no effect on ChemDraw. 

This seems to be a similar problem:
[http://www.winehq.org/pipermail/wine-devel/2005-December/043616.html](http://www.winehq.org/pipermail/wine-devel/2005-December/043616.html)

connected with this bug report:
[http://bugs.winehq.org/show_bug.cgi?id=2737](http://bugs.winehq.org/show_bug.cgi?id=2737)
this bug was fixed in 2006,  though. 

Seeing  all these debug flags in the bug report,  I tried to get some useful output myself.

The way I got this output was by starting wine with the debug flags shown below, then adding a bond, then typing a character on the end of the bond, which creates a label and only look at the lines appearing during that action.

WINEDEBUG=+x11drv wine chemdraw.exe gives this output
trace:x11drv:X11DRV_CreateBitmap (0x910) 14x20 1 bpp
trace:x11drv:X11DRV_CreateBitmap (0x914) 1x1 1 bpp
trace:x11drv:X11DRV_CreateBitmap (0x938) 14x20 1 bpp
trace:x11drv:X11DRV_CreateBitmap (0x93c) 1x1 1 bpp
trace:x11drv:X11DRV_CreateBitmap (0x94c) 14x20 1 bpp
trace:x11drv:X11DRV_CreateBitmap (0x95c) 14x20 24 bpp
trace:x11drv:X11DRV_CreateBitmap (0x990) 14x20 1 bpp
trace:x11drv:X11DRV_CreateBitmap (0x994) 1x1 1 bpp
trace:x11drv:X11DRV_CreateBitmap (0x9a4) 14x20 1 bpp
trace:x11drv:X11DRV_CreateBitmap (0x9b4) 14x20 24 bpp
trace:x11drv:X11DRV_SetWindowPos win 0x10026 window (294,10)-(1221,910) client (298,52)-(1217,906) style 16cf0000
trace:x11drv:X11DRV_SetWindowPos win 0x1002c window (1,1)-(922,31) client (2,4)-(921,30) style 50800101
trace:x11drv:X11DRV_SetWindowPos win 0x1002a window (0,835)-(919,854) client (0,835)-(919,854) style 50000000
trace:x11drv:X11DRV_CreateBitmap (0xb2c) 16x16 24 bpp

I also tried WINEDEBUG=+font as well as the options +gdi,+bitmap,+seh,+text
+gdi gave too much output to tell anything useful
+font shows ever-repeating fontchanges
+bitmap showed nothing really new compared to x11drv
and +seh did not create output on adding a character
+text only creates for the menues, but not for typed text (to test that, I wrote some text instead of the single lable using to get output from the other options)

I.



Now I forgot to mention it - these 1 bpp (bits per pixel) entries seem strange - although they are followed by a 24 bpp entry. 
It seems x11 first tries to clear the area, using 1 bit color depth, then overwrite this with the real image. Seems we are somehow stuck with the 2-color version (?)
Also creating 1x1 bitmaps seems strange. If these were scaled, they'd definitely be black or white boxes (or perhaps better rectangles) :)

---

### Post by mortenkjeldgaard on 2007-06-10
Another GPL chemistry drawing program is BKchem, written in Python. I haven't used it, but it looks very nice.
Check it out! ([http://freshmeat.net/projects/bkchem/](http://freshmeat.net/projects/bkchem/))

Cheers,
Morten

---

### Post by eZtaR on 2007-06-10
I just came across this totally at random and thought you might find it interesting:
[http://code.google.com/soc/kde/appinfo.html?csaid=3EBDFAAF85EFFA00](http://code.google.com/soc/kde/appinfo.html?csaid=3EBDFAAF85EFFA00)

It's a student named Marcus Hanwell who's gonna devote his summer to writing a 3d molecular editor. In his article he also mentions various other apps that might help you in your journey of finding a 2d chemical drawer.


*Oh btw*: Have you guys checked out if [ChemSketch](http://www.acdlabs.com/products/chem_dsn_lab/chemsketch/) works with wine? Seems to me that it does practically the same as chemdraw :)

---

### Post by tak1150 on 2007-06-10
> *Oh btw*: Have you guys checked out if [ChemSketch](http://www.acdlabs.com/products/chem_dsn_lab/chemsketch/) works with wine? Seems to me that it does practically the same as chemdraw :)

Yes, I have tried Chemsketch and it does work under wine :p
Drawing features of it are not as good (in my opinion) as Chemdraw and the files are not very portable to other linux applications. That's why I've abandoned it.

**Biggest reason why I need ChemDraw:**
Most communications between collaborators are done in ChemDraw files (windows or mac) and therefore, I really need ChemDraw and nothing else to work in my Ubuntu computer.

-I am aware that Xdrawchem is supposed to support chemdraw files, but I've never been able to read any Chemdraw files in xdrawchem.


Software I've tried: (well either way, I still need chemdraw, but had to try these for my curiosity)
[LIST=1]
[*]BKChem - great portability, but bad resolution, somewhat unstable, ok drawability
[*]GChempaint - so so portability, ok resolution, good drawability, but bad when it comes to heteroatoms
[*]EasyChem - too weird :-s
[*]XDrawchem - excellent portability, bad resolution, unstable, good drawability, but unacceptable because the development seems to have ceased
[*]JChempaint - can't remember ... but there must have been some reason why I'm not using it :o
[/LIST]

Again, I'm very grateful for these developers, but I'm in a situation where I'm forced to be picky! And I admit I'm picky in general.

Hope this list is somewhat useful...
My favorite is GChempaint even though it's not very usable for the reasons stated. GUI is excellent. BKChem is nice and probably most promising in my eyes.

---

### Post by tak1150 on 2007-06-10
Oh, I have tried ISISDraw with Wine as well. But it has the same problems as ChemSketch.

My philosophy is that if a software has all of the needed features, I don't mind running it under Wine. But if there is one feature missing, it's not really worth it for me to have to resort to Wine (because of the inherent instability from having another layer). Whereas a Linux native software may be tolerated with one missing feature or so.

---

### Post by LaserJock on 2007-06-12
> **tak1150 said:**
> 
<snip>
Softwares I've tried: (well either way, I still need chemdraw, but had to try these for my curiosity)
[LIST=1]
[*]BKChem - great portability, but bad resolution, somewhat unstable, ok drawability
[*]GChempaint - so so portability, ok resolution, good drawability, but bad when it comes to heteroatoms
[*]EasyChem - too weird :-s
[*]XDrawchem - excellent portability, bad resolution, unstable, good drawability, but unacceptable because the development seems to have ceased
[*]JChempaint - can't remember ... but there must have been some reason why I'm not using it :o
[/LIST]

Again, I'm very grateful for these developers, but I'm in a situation where I'm forced to be picky! And I admit I'm picky in general.

Hope this list is somewhat useful...
My favorite is GChempaint even though it's not very usable for the reasons stated. GUI is excellent. BKChem is nice and probably most promising in my eyes.

Thanks for the review, I'm often amazed at how many apps we have for essentially the same task, and yet many just seem to fall short of the "standard". I'm curious, what version of gchempaint did you try? I'm a contributor to gchemutils (which has now incorporated gchempaint) and an Ubuntu developer so I'm especially interested in getting gchempaint in better shape in Ubuntu. 

The latest release of gchempaint, 0.8, has quite a few improvements and I think the 0.10 release will be a significant leap forward. In the CVS branch we are working on more/better templates, better reaction rendering, OpenOffice.org copy-n-paste support, Wikipedia image integration, similar structure searches and CAS lookup for starters. As you can imagine right now all of this is a bit unstable do I don't recommend using gchempaint from CVS for production work, but testers are always welcome and the lead developer is quite responsive.

Anyway, my $0.02

-LaserJock

---

### Post by tak1150 on 2007-06-12
> I'm a contributor to gchemutils (which has now incorporated gchempaint) and an Ubuntu developer so I'm especially interested in getting gchempaint in better shape in Ubuntu.

Wow, thank you so much for what you do. You guys are very much appreciated.

> Thanks for the review, I'm often amazed at how many apps we have for essentially the same task, and yet many just seem to fall short of the "standard". 

Yes. And it seems to a simpleton like me that each app has slightly different strengths and if they pool the resources together they could make something that would challenge ChemDraw?

> I'm curious, what version of gchempaint did you try? 

currently ver 0.7.91

Since I'm so happy to have a real developer in the audience, allow me to continue my selfish review :o

As somebody who has draw chemical structures everyday for living, I would really love to see compatibility with ChemDraw files (i've said this before, but b/c everybody else sends me ChemDraw files and I need to send C-D files to them). The moment that feature appears in either Gchmpaint or BKChem, I will erase my Windows partition forever!

> OpenOffice.org copy-n-paste support
That'd be awesome!

BTW, what I meant by "resolution" in the last post is how it looks when it's pasted (or inserted) into PowerPoint or Impress and shown on a big screen.

Also what I meant by
> bad when it comes to heteroatoms
is that the way you draw in heteroatoms is too much of a hassle for me. In ChemDraw (and I think in XDrawchem) you just place the mouse cursor on the atom and type the atom. Without this feature I cannot draw structures as fast as I need to.

Thanks for reading!
Tak

---

### Post by Enverex on 2007-06-12
Just out of interest, have all bugs for ChemDraw been logged in Wine's Bugsite with all relevant data?

---

### Post by Iridos on 2007-07-11
Hi,

after my attempt to get some info on the bug, I looked some further - this problem here looks similar:
[http://bugs.winehq.org/show_bug.cgi?id=4529](http://bugs.winehq.org/show_bug.cgi?id=4529)

An bad mask for characters could also rather well explain the phenomenon...

Also - they are not necessarily "black boxes", but also yellow, blue or green boxes - according to the current text color. 

Debugging suggests that it's not one of the 1bpp drawings, that is erasing the letter. 
I.

---

### Post by Iridos on 2007-07-11
And about your question if the bug has been entered at wineHQ - I cannot find any bugreports regarding this issue... might even not be so hard to fix. Volunteers?
Problem is, that Chemdraw is proprietary... so someone might have to donate a version to them before they fix it. I.

---

### Post by modestmelody on 2007-09-09
This thread is worth bumping.  It's just so much hassel to use Chemsketch in Wine which runs horribly slow and does have some issues (templates appear with strange boxes).

GChem is so close, but totally misses the mark with heteroatoms as stated.  There is no way I should have to open up a seperate window to access heteroatoms.  It should be easy to add things like R groups etc.  It should be easy to draw reaction mechanism arrows, etc.

I need to be able to read/write in Chemdraw format as well as export into a high quality, transparent (preferably), vector format which can be scaled easily and beautifully (for presentations or for varying size within papers), etc.  There just isn't a great chemical structure drawing program on Linux, yet.

Oh yeah, and perhaps most important-- structure correction.  Sometimes it's a pain in the ***, but it's a great thing to be able to quickly draw something without attention to angle and length and then letting the program standardize it.

---

### Post by tak1150 on 2007-09-09
> **modestmelody said:**
> 
GChem is so close, but totally misses the mark with heteroatoms as stated.  There is no way I should have to open up a seperate window to access heteroatoms.  It should be easy to add things like R groups etc.  It should be easy to draw reaction mechanism arrows, etc.

I need to be able to read/write in Chemdraw format as well as export into a high quality, transparent (preferably), vector format which can be scaled easily and beautifully (for presentations or for varying size within papers), etc.  There just isn't a great chemical structure drawing program on Linux, yet.


Hi modestmelody,

Since I started this thread, I have made quite a few contacts with the developer of Gchempaint. He/she (I don't know) has been extremely helpful and responsive (often s/he replies back in a couple of minutes by email!!). Gchempaint 0.8.2 now does the hassle-free heteroatom drawing by keyboard keys! Thanks to Jean (the developer from France).

And yes, s/he has been working on the ChemDraw compatibility issues as well. I think now that it's possible that gchempaint will get to a real production level product within 6 mo to 1 year.

Jean also mentioned that 0.8.3 will come out any day now. I suggest that you give this latest version a try. It's much different than say, 0.8.0.

Blessings,
Tak

---

### Post by glotz on 2007-09-09
A chemist-to-be here. Interesting thread. I use Ubuntu all the way.

---

### Post by chemicalscum on 2007-09-19
I don't think that Chemdraw is the standard for organic chemists, some use MDL ISIS others use Chemwindows/Knowitall as well as those that use Chemsketch.

In my personal view the best 2D chemical drawing program is Chemaxon's Msketch.  It is proprietary but is free as in beer.  Chemaxon is to Hungary what ACD is to Canada.  Chemaxon's bioinformatics and chemoinformatcs software is widely used in the EU by the pharmaceutical industry and they use Msketch as a free loss leader.  Similarily ACD's physical porperties, spectroscopy and chromatography products are widely used in North America with Chemsketch as their free loss leader.

Msketch is a Java program that will run on any platform with a recent Sun Java.  It is available from:

[http://www.chemaxon.com/products.html](http://www.chemaxon.com/products.html)

You can register for free downloads or you can try it out using Java webstart (if you have Sun Java installed on Feisty then Firefox is Webstart enabled):

[http://www.chemaxon.com/marvin/jnlp/msketch.jnlp](http://www.chemaxon.com/marvin/jnlp/msketch.jnlp)

At work over the past 10 years we have been through the Chemwindows/Knowitall stream with some use of Chemsketch but we have now dropped Knowitall (Chemwindows went downhill when it became Knowitall) and I have got pretty much everyone on board with Msketch.

It is nice because I can use it at home on Ubuntu and at work on XP.  It doesn't cut and paste to OOo but it does cut and paste to Abiword and it is quite convenient to create a page or so of structures in Abiword  then export them to OOo as  an .odt or.doc. You can  then cut and paste them internally in OOo.  Now the bad news for tak1150, it doesn't support Chemdraw file formats.  So you would have to rely on Openbabel (what Xdrawchem uses) to convert the files, the latest Openbabel claims it will export to .cdxml how good it is I don't know.  You can also use Chemsketch in Wine to do file conversion.

Of the FOSS 2D drawing applications gchempaint seems to be coming along really well (though Bkchem is a nice tool too).  What I like is that I can download a SDF file from Pubchem and Firefox offers to open it in gchempaint.  Hey presto you have the full structures even from a multi part SDF displayed in gchempaint.  You then right click on a molecule and it offers to transfer it to ghemical, It transfers the structure to the excellent ghemical quantum chemistry OpenGL based graphical front end, and you can start doing quantum chemistry 3D visualizations using the MOPAC semi-empirical and the MPQC ab initio packages.  This makes an Ubuntu desktop a powerful quantum chemistry workstation.

A last word, from way back when I was a grad student 18 years ago the MDL molfile format was the standard for exchanging molecular structures (both 2D and 3D) and it still is. Now you also have  the SDF multipart format to extend its capabilities.  If you want to exchange structures the MDL formats are the best supported between a large number of different chemistry applications.  On this basis the Chemdraw formats should be deprecated.  We now have the CML fully open standard for molecular structures but unfortunately I find the structures created in one applicatiion in CML will often not open in another application.  I don't know if this is a weakness in the standard or the implementations.

---

### Post by qwen71n on 2007-09-20
> **chemicalscum said:**
> 
In my personal view the best 2D chemical drawing program is Chemaxon's Msketch.  

After trying many programs, all of them already discussed above, I also stick to Marvin Sketch, at least for now. It has a number of nice features, but also lacks many things I need, such as drawing simple orbital shapes. I don't have control how the lone pairs and charges look like and I can not move them the way I like. So, I have to draw a reaction scheme then save as an SVG image, and edit it in Inkscape, which is not too easy since Marvin's SVGs are not too edit-friendly. 

The result looks very good, but it takes lots of time! There are many, many things I didn't like about ChemDraw, and sometimes I had to use post-editing in CorelDraw, but still it took less time to get exactly what I want. 

I'll try to install the latest GChemPaint now, its early versions seemed promising. By the way, does anybody know if there is a BkChem deb package available? I generally don't like to have too many programs hand-compiled.

---

### Post by tak1150 on 2007-09-20
> **qwen71n said:**
> 
I'll try to install the latest GChemPaint now, its early versions seemed promising. By the way, does anybody know if there is a BkChem deb package available? I generally don't like to have too many programs hand-compiled.

Last time I tried BKChem, it is a binary python package that you download and you don't compile it. You just run "python bkchem.py" or something like that.

As for GChempaint, it is somewhat tricky to get all the dependencies; you have to compile most of them yourself since you need the latest of everything to get the latest gchempaint. If you have trouble, post here. I did take notes of what I did to install it that I could post.

---

### Post by LaserJock on 2007-09-21
> **tak1150 said:**
> As for GChempaint, it is somewhat tricky to get all the dependencies; you have to compile most of them yourself since you need the latest of everything to get the latest gchempaint. If you have trouble, post here. I did take notes of what I did to install it that I could post.

I've been thinking about this lately. Would people be interested if I were to maintain a repo with updated gchempaint/gchemutils and required dependencies? It'd be some work so I don't want to do it if nobody is interested, but if it's useful I'd like to see what I can do.

-LaserJock

---

### Post by glotz on 2007-09-21
Would that mean I could run them on Dapper? If yes I certainly would be overjoyed.

Sorries if the question is daft. ;) (LTS FTW!)

---

### Post by LaserJock on 2007-09-21
> **glotz said:**
> Would that mean I could run them on Dapper? If yes I certainly would be overjoyed.

Sorries if the question is daft. ;) (LTS FTW!)

Yes, I would try anyway :-) Sometimes dapper can be a bit difficult to backport to.

-LaserJock

---

### Post by glotz on 2007-09-21
A resounding YES PLEASE it is then!

---

### Post by qwen71n on 2007-09-21
> **LaserJock said:**
> I've been thinking about this lately. Would people be interested if I were to maintain a repo with updated gchempaint/gchemutils and required dependencies? It'd be some work so I don't want to do it if nobody is interested, but if it's useful I'd like to see what I can do.

-LaserJock

Yes, please!

---

### Post by chemicalscum on 2007-09-22
> **LaserJock said:**
> I've been thinking about this lately. Would people be interested if I were to maintain a repo with updated gchempaint/gchemutils and required dependencies? It'd be some work so I don't want to do it if nobody is interested, but if it's useful I'd like to see what I can do.


I have been thinking about uninstalling gchempaint 0.6.6 from Feisty and trying to build 0.8.3 and came to the conclusion it would be easier to wait for Gutsy, but now I see that 0.6.6 is still listed in the package listing for Gutsy. 

So yes I would really appreciate it it if you were to maintain a repo with updated  chempaint/gchemutils and the required dependencies.  I would certainly install and use them.

While we are talking about gchempaint.  I don't see what the heteroatom problem with gchempaint that people are complaining about really is.  You can keep the periodic table window open all the time and switch between heteroatoms to paste easy enough.

---

### Post by tak1150 on 2007-09-22
I have been using 0.8.3 of Gchempaint for a few days now. It is great!
Please check out the [official announcement page]("https://savannah.nongnu.org/news/?group=gchempaint").

> While we are talking about gchempaint. I don't see what the heteroatom problem with gchempaint that people are complaining about really is. You can keep the periodic table window open all the time and switch between heteroatoms to paste easy enough.

chemicalscum, you are probably more patient a person than I. Once I got the taste of ChemDraw (such as version 6-9, of which I sometimes use v.9 at  work), and tasted how easy and fast it is draw structures with key strokes rather than moving the mouse to point to an element in the table, I just cannot be satisfied with any other method.

So 0.8.3 does the keystroke to heteroatom thing perfectly like ChemDraw. It now comes with a theme that has the right bond length, etc, for ACS publicaitons. And the chain tool does the thing I really like (check out the announcement above). It rocks!

Now as for ChemDraw file compatibility, it does not open them correctly especially if there are texts. As I'm writing this, I have forgotten to test to see if ChemDraw can open Gchempaint's files (it can save it as CDXML). Currently that bug has been confirmed and is being worked on though it may take some time b/c the problem comes from Openbabel (which is like the engine that Gchempaint runs on, if I understand it correctly).

I am going to give Jean another wish list for some small features (such as I'd like the molecular weight calculator to calculate up to 3rd decimal point, etc), but except for the "ChemDraw Compatibility Issue", Gchempaint, IMO, is practically a production level product.
If you're in France and reading this, please bake cookies or something for Jean for me :)

---

### Post by darmot7 on 2007-09-29
> **LaserJock said:**
> I've been thinking about this lately. Would people be interested if I were to maintain a repo with updated gchempaint/gchemutils and required dependencies? It'd be some work so I don't want to do it if nobody is interested, but if it's useful I'd like to see what I can do.

-LaserJock

interested! without a doubt, no question, would love it, yes please. all my attempts at building gchempaint from source have failed, if its to much work to maintain a repo could you (or anyone for that matter) write a how to? :)

thanks for the offer/thought!
:)

---

### Post by huggies15 on 2007-10-21
hey, i would like to use this too. if it as good as u say it is then i will be doze free in no time. i dont get how to compile the software myself, and i dont see the point in using old stuff. anyone got any advice on how to install it?

---

### Post by tak1150 on 2007-10-21
> hey, i would like to use this too. if it as good as u say it is then i will be doze free in no time. i dont get how to compile the software myself, and i dont see the point in using old stuff. anyone got any advice on how to install it?

Are you using Gutsy?
I started writing a how-to for installing Gchempaint in Feisty, but before I finished it Gutsy came out! I'm thinking I'll write it for Gutsy.

---

### Post by huggies15 on 2007-10-23
> **tak1150 said:**
> Are you using Gutsy?
I started writing a how-to for installing Gchempaint in Feisty, but before I finished it Gutsy came out! I'm thinking I'll write it for Gutsy.

i use gutsy on my laptop and feisty on the pc... so either/both would be good!
is it stupid to ask why they dont come as deb files, seen as the older versions do... is it just a case of it takes too long for the makers, or cant they be bothered? - meant in the nicest way possible!

---

### Post by tak1150 on 2007-10-23
I was going to work on the how-to article for installing Gchempaint for Gutsy this week, but we may have to evacuate! We live in San Diego.

To answer your question, my guess is that it's pretty difficult. There is a dependency that has to do with MIME and it sort of messes up things in the system (have to re-install essential packages). Maybe incorporating this dependency in a deb file is difficult. Also up until Gutsy, libgoffice-0.4 was not available. It was pretty tricky to compile that package for Feisty. It will be easier for Gutsy for sure, but still some MIME problems.

---

### Post by huggies15 on 2007-10-23
cool, i assumed it owuld be difficult :)
will installing gchempaint inlcude the chemutil package as well, or do u not reccomend that?

hope ur house stays safe!

---

### Post by tak1150 on 2007-10-23
> cool, i assumed it owuld be difficult
will installing gchempaint inlcude the chemutil package as well, or do u not reccomend that?

hope ur house stays safe!

Thanks.

We've been just glued to the radio and the internet all day (we don't have a tv).

chemutil is a dependency for gchempaint. Chemical-mime-data and libgoffice-0.4 and others are requirements for chemutils.

---

### Post by LaserJock on 2007-10-24
I've been working a little bit on getting gchemutils and gchempaint 0.8 .debs going. It is indeed a decent amount of work. The problem is in the dependencies (goffice and openbabel). As I'm trying to write my dissertation and finish research and am also an Ubuntu/Edubuntu developer my time seems in short supply sadly. I am working on it however.

-LaserJock

---

### Post by tak1150 on 2007-10-27
I hope LazerJock can put together the deb file soon, but in the meanwhile, you can install GChemPaint using [this guide]("http://taksuyama.com/?p=34"). It is not the ideal method of installing programs, b/c the package manager will not recognize it. But I also included a way to uninstall these packages in the guide. Enjoy!

---

### Post by huggies15 on 2007-10-29
Hey, thanks for the guide it worked perfectly! im now getting used to gchempaint, and when happy that it does what i need will remove windows once and for all :)

i was wondering what other software ppl used, like for viewing nmr data (mainly buker), i use winnuts in windows but that doesnt seem to like wine much either...

---

### Post by tak1150 on 2007-10-31
> **huggies15 said:**
> Hey, thanks for the guide it worked perfectly! im now getting used to gchempaint, and when happy that it does what i need will remove windows once and for all :)

i was wondering what other software ppl used, like for viewing nmr data (mainly buker), i use winnuts in windows but that doesnt seem to like wine much either...

Hi huggies15,

Are you a synthetic org chemist? It sounds like it. I am one too.
Anyhow, there is NMRPipe, which is maintained by NIH.
There are other ones you can find at [Linux4Chemistry]("http://www.redbrick.dcu.ie/~noel/linux4chemistry/")

Hope this help.

[SIZE="5"]BTW, GChemPaint 0.8.4 just came out![/SIZE]

I must try it out! I'll update my how-to article for the newest version ASAP.

---

### Post by LaserJock on 2007-11-02
OK, here we go:

```

deb http://ppa.launchpad.net/laserjock/ubuntu gutsy main
deb-src http://ppa.launchpad.net/laserjock/ubuntu gutsy main
```

This repo will give you gchemutils and gchempaint 0.8.4 for Ubuntu 7.10 (Gutsy). :)

**Disclaimer:** these are just testing packages. Use at your own risk. 

I'm still working on these packages making sure that everything works correctly. So far all the apps seem to work with the exception that gcrystal doesn't seem to recognize .gcrystal files.

I'm close to getting everything ready to go into the official Hardy repos and will look more into farther backporting if people are interested. Does anybody want Feisty packages?

Have fun and let me know how they work.

-LaserJock

---

### Post by LaserJock on 2007-11-08
*bump* Anybody try my packages yet? :popcorn:

---

### Post by tak1150 on 2007-11-08
> **LaserJock said:**
> *bump* Anybody try my packages yet? :popcorn:

Hey Laserjock,

Would you expect any problems if I have 0.8.3 installed from source and I just do "sudo make uninstall" from the directories and then install your packages? I'm kind of concerned about MIME stuff (maybe irrational concern...). Thank you so much for making these packages!
I will definitely try it on my desktop as soon as I upgrade it to Gutsy. My laptop is my workhorse (already gutsy) and I try not to experiment on it.

Tak

---

### Post by LaserJock on 2007-11-08
> **tak1150 said:**
> Hey Laserjock,

Would you expect any problems if I have 0.8.3 installed from source and I just do "sudo make uninstall" from the directories and then install your packages? I'm kind of concerned about MIME stuff (maybe irrational concern...). Thank you so much for making these packages!
I will definitely try it on my desktop as soon as I upgrade it to Gutsy. My laptop is my workhorse (already gutsy) and I try not to experiment on it.

Tak

It should all work fine. What you can do is **not** uninstall 0.8.3 you've got locally (I'm assuming you installed to /usr/local/ which is default when building from source) and install my packages. It should run my 0.8.4 in preference to your 0.8.3 (you can run "which gchempaint" in a terminal to see the path it's going to). If you then have problems with my packages just uninstall them and you should be set.

-LaserJock

---

### Post by huggies15 on 2007-11-10
Im about to wipe my laptop and install gutsy a fresh, then ill use ur repos :) thanks so much for doin them!!
will let you know if it works :)

steve

---

### Post by evillan on 2007-11-10
I tried gchempaint 0.6.6 (installed with aptitude) and preferred this program to xdrawchem because the output in xdrawchem i awfully pixelated. 

So, now I want to try the newest (stable?) version of gchempaint, 0.8.3. How do I install it? I've added the debs to /etc/apt/sources.list, what do I do next? tak1150's howto looks appalling as I am a linux newbie.

---

### Post by LaserJock on 2007-11-11
> **evillan said:**
> I tried gchempaint 0.6.6 (installed with aptitude) and preferred this program to xdrawchem because the output in xdrawchem i awfully pixelated. 

So, now I want to try the newest (stable?) version of gchempaint, 0.8.3. How do I install it? I've added the debs to /etc/apt/sources.list, what do I do next? tak1150's howto looks appalling as I am a linux newbie.

I've you've added:

deb [http://ppa.launchpad.net/laserjock/ubuntu](http://ppa.launchpad.net/laserjock/ubuntu) gutsy main

to your sources.list. Then, if you've already got gchempaint installed from Ubuntu you can:

sudo apt-get update
sudo apt-get dist-upgrade

or you can substitute aptitude for apt-get if you like. Alternatively you can run System->Administration->Synaptic Package Manager and look for gchempaint.

-LaserJock

---

### Post by evillan on 2007-11-11
> **LaserJock said:**
> I've you've added:

deb [http://ppa.launchpad.net/laserjock/ubuntu](http://ppa.launchpad.net/laserjock/ubuntu) gutsy main

to your sources.list. Then, if you've already got gchempaint installed from Ubuntu you can:

sudo apt-get update
sudo apt-get dist-upgrade

or you can substitute aptitude for apt-get if you like. Alternatively you can run System->Administration->Synaptic Package Manager and look for gchempaint.

-LaserJock

Got it, thanks! I'm trying it out now.

---

### Post by huggies15 on 2007-11-17
i have now reinstalled gutsy and downloaded the gchempaint software package from your repo, working brill, thanks so much :)

---

### Post by tak1150 on 2007-11-17
Hey LaserJock,

I had to uninstall 0.8.3 because the command "gchempaint" preferentially used 0.8.3 rather than 0.8.4, but now your package is working! Thank you so much!

Tak

---

### Post by achianese on 2007-11-21
I'm an inorganic chemist trying to switch from WinXP to Ubuntu, and Tak is right.. it's hard because there's so much I do with commercial programs in Windows, exp. Chemdraw.

Laserjock: I just installed Gchempaint using your repository, and it works like a charm. Thanks for your effort.

Huggies: I've had good luck so far with NUTS in Wine. What were your problems? I'm running NUTS 2D version 20001128 using Wine 0.9.49.

---

### Post by huggies15 on 2007-11-22
it keeps crashing, and not letting my copy and paste into open office. i havent had to use it in a while tho, so it might be working now with the newer versions of wine/nuts. i also only had the demo version of nuts, so that might be the problem... got nmr pipe to try out now tho... looks good.

im an organometallics guy atm, so using mostly the same stuff as u organic guys :)

EDIT: just thought id add... can anyone else open chemdraw files with gchempaint... i cant. i saved one as a cdxml file, then tried opening it straight after and said it couldnt recognise the file?! v. strange, so atm im using the native file type.... any ideas?

---

### Post by tak1150 on 2007-11-22
> **huggies15 said:**
> it keeps crashing, and not letting my copy and paste into open office. i havent had to use it in a while tho, so it might be working now with the newer versions of wine/nuts. i also only had the demo version of nuts, so that might be the problem... got nmr pipe to try out now tho... looks good.


What program is crashing on you? GChemPaint?


> im an organometallics guy atm, so using mostly the same stuff as u organic guys :)

Cool. What kind of research do you do? I have a few very different projects, but my main one is to synthesize a natural product. Just curious :)

Tak

---

### Post by huggies15 on 2007-11-22
no i mean that nuts keeps crashing on me, gchempaint has worked fine with the exception of not opening chemdraw files, but i just use my windows pc for that :)
im doin my final (undergrade) yr project on phosphine macrocycles, its quite interesting and means i get to do quite a bit of straight organic then wack it on a metal :) hoping to carry it on for a phd next yr, but that depends on how this all goes. last yr i had a yr out in germany and did acetylenedithiolate chemistry on cobalt, and that was really good. proper nice colours!

naturals products must take forever to make, due to the many steps, doesnt it get frustrating?

---

### Post by LaserJock on 2007-11-24
> **huggies15 said:**
> it keeps crashing, and not letting my copy and paste into open office. i havent had to use it in a while tho, so it might be working now with the newer versions of wine/nuts. i also only had the demo version of nuts, so that might be the problem... got nmr pipe to try out now tho... looks good.

im an organometallics guy atm, so using mostly the same stuff as u organic guys :)

EDIT: just thought id add... can anyone else open chemdraw files with gchempaint... i cant. i saved one as a cdxml file, then tried opening it straight after and said it couldnt recognise the file?! v. strange, so atm im using the native file type.... any ideas?

I talked to the gchempaint author about your chemdraw problem and he suggested you file a bug report and attach your cdxml. Here is a link for submitting a bug report:
[http://savannah.nongnu.org/bugs/?func=additem&group=gchempaint](http://savannah.nongnu.org/bugs/?func=additem&group=gchempaint)

Gchempaint *should* be able to open many ChemDraw files and I think it should open any cdxml that it created. It uses OpenBabel for file conversion so it should be able to open anything supported by OpenBabel.

-LaserJock

---

### Post by tak1150 on 2007-11-24
> **huggies15 said:**
> no i mean that nuts keeps crashing on me, gchempaint has worked fine with the exception of not opening chemdraw files, but i just use my windows pc for that :)
im doin my final (undergrade) yr project on phosphine macrocycles, its quite interesting and means i get to do quite a bit of straight organic then wack it on a metal :) hoping to carry it on for a phd next yr, but that depends on how this all goes. last yr i had a yr out in germany and did acetylenedithiolate chemistry on cobalt, and that was really good. proper nice colours!

naturals products must take forever to make, due to the many steps, doesnt it get frustrating?

Yes, natural product synthesis can be frustrating, but I don't imagine it'd be any more frustrating than methodology studies, etc. For the last 7-8 months, I've been working on ONE step of the synthesis (and it's the very last step in the total synthesis!).

If you have undergraduate research under your belt, I'm sure you will get accepted into a good graduate school. God bless your career.

BTW, I have already filed a bug report about the Chemdraw problem at the place LaserJock mentioned. The developer has been working on this issue for a while. One limiting factor is s/he doesn't have a copy of ChemDraw. So if we provide him/her with chemdraw files, that'd help the process.

Tak

---

### Post by huggies15 on 2007-11-25
OK, cool. how do i send them some cdxml/normal chemdraw files to help? i wish i understood programming in the slightest then i would offer to help, but i have no clue :(

ive got 2 yrs research under my belt by the time i graduate, but hoping to stay in cardiff to do the phd there. one step for helf a year is crazy! is it not working at all or just poor yields?

---

### Post by LaserJock on 2007-11-26
> **huggies15 said:**
> OK, cool. how do i send them some cdxml/normal chemdraw files to help? i wish i understood programming in the slightest then i would offer to help, but i have no clue :(

ive got 2 yrs research under my belt by the time i graduate, but hoping to stay in cardiff to do the phd there. one step for helf a year is crazy! is it not working at all or just poor yields?

Attaching them to the bug report (I think it's [https://savannah.nongnu.org/bugs/?21112](https://savannah.nongnu.org/bugs/?21112))  or just via email ( the developer is jean.brefort AT normalesup.org) works.

I'm going to try to upload some new gchempaint/gchemutils packages today that fix some issues so watch for updates from my repo ;-)

-LaserJock

---

### Post by chemicalscum on 2007-11-26
> **LaserJock said:**
> *bump* Anybody try my packages yet? :popcorn:

I have just upgraded to Gutsy and installed your 0.8.4 gchempaint and gcu packages and they work great.  0.8.4 is a great improvement over 0.6.6.  

As someone who does a lot of mass spec interpretation the ability to export a structure to the gcu calculator and get a monoisotopic mass makes gchempaint a practical tool for mass spec interpretation.

---

### Post by jbrefort on 2007-11-28
I feel it's time for me to say something in this thread.

First, let me introduce myself. I'm a man (for those who did not know) and a 53 years old chemistry teacher living in western France. I started writing gchempaint and other programs around 6 years ago (gcrystal has its origins in a 11 years old windows program) in the hope I might not need any windows program one day. Even if many features are still missing, I mostly reached my initial goal.

I have a lot of projects for the future. Just speaking of the 0.10 version, reading what has been written here and elsewhere, I understand that a much better support for cdx(ml) format is a much wanted feature. Using OpenBabel for that needs changes in that library that will not even be in 2.2, and, more problematic, this library is GPLv2 only, so that if any other dependency changes its license to a v3 version, it will just become unusable, so I'm considering writing a new famework for import/export chemdraw files (and possibly others later).
Another goal for gchempaint-0.10 is to not use anymore gnome-canvas and gnome-print which are either deprecated or almost deprecated, and not acitively maintained. As I don't want to have a new dependency, this means that I have to wait until there is a canvas widget in gtk+ (which was planed for 2.12, then 2.14, and now for later), or I write a simple one from scatch, which is more work.

About the other new features we'll have in 0.10 are a spectrum viewer (started, but not really usable yet), and various enhancements for the other existing utilities.

Tak, you wrote you asked me for a better precision in the calculator, please, open a bug report against gchemutils so that I don't forget.

Now, the bad side of things: I'm still working mostly alone on these projects, which  makes their future quite uncertain. Although I don't intend to stop the development at least until I retire (I have no idea when this will occur), I might have a life accident (or worse), and the project would become orphan. If anyone reading this thread is able to help or knows somebody who might, it would be a great thing. There are several ways where people can help, not only programming, but UI design and documentation writing, and probably others I don't think of at the moment, are also needed.

---

### Post by tak1150 on 2007-11-28
> **jbrefort said:**
> I feel it's time for me to say something in this thread.

First, let me introduce myself. I'm a man (for those who did not know) and a 53 years old chemistry teacher living in western France. I started writing gchempaint and other programs around 6 years ago (gcrystal has its origins in a 11 years old windows program) in the hope I might not need any windows program one day. Even if many features are still missing, I mostly reached my initial goal.

I have a lot of projects for the future. Just speaking of the 0.10 version, reading what has been written here and elsewhere, I understand that a much better support for cdx(ml) format is a much wanted feature. Using OpenBabel for that needs changes in that library that will not even be in 2.2, and, more problematic, this library is GPLv2 only, so that if any other dependency changes its license to a v3 version, it will just become unusable, so I'm considering writing a new famework for import/export chemdraw files (and possibly others later).
Another goal for gchempaint-0.10 is to not use anymore gnome-canvas and gnome-print which are either deprecated or almost deprecated, and not acitively maintained. As I don't want to have a new dependency, this means that I have to wait until there is a canvas widget in gtk+ (which was planed for 2.12, then 2.14, and now for later), or I write a simple one from scatch, which is more work.

About the other new features we'll have in 0.10 are a spectrum viewer (started, but not really usable yet), and various enhancements for the other existing utilities.

Tak, you wrote you asked me for a better precision in the calculator, please, open a bug report against gchemutils so that I don't forget.

Now, the bad side of things: I'm still working mostly alone on these projects, which  makes their future quite uncertain. Although I don't intend to stop the development at least until I retire (I have no idea when this will occur), I might have a life accident (or worse), and the project would become orphan. If anyone reading this thread is able to help or knows somebody who might, it would be a great thing. There are several ways where people can help, not only programming, but UI design and documentation writing, and probably others I don't think of at the moment, are also needed.

Welcome aboard on Ubuntuforums.org! I'm sure I'm speaking for many others when I say your presence here is much appreciated.

I'll open that bug report ASAP.
Thank you very much for your work!

Tak

---

### Post by tak1150 on 2007-11-28
> **huggies15 said:**
> ive got 2 yrs research under my belt by the time i graduate, but hoping to stay in cardiff to do the phd there. one step for helf a year is crazy! is it not working at all or just poor yields?

2 years of research in undergraduate is VERY good.
As for my bad last step, I've gotten a trace (<5% yield) amount of the product before, but that's it. Right now, I am scaling up the synthesis so that I'll have more material to do experiments with (I was working with a few milligrams). I have to go back ~10-11 steps. I'm now 2 steps in with ~100g material! Thanks for asking :)

---

### Post by huggies15 on 2007-11-28
I'd just like to say thanks so much for doing all this work to jbrefort. it is most appriciated!! I'm not the world most artist man, but if i come up with any ideas on layout/UI then ill have a go at making something and seeing what you think, at the moment i have nothing to complain about :) was also considering writing a basic how-to for ppl at uni to use this program, but i dont have time at the moment, project work seems to be getttin more demanding :( if/when i write something, i will also post info here, as any help it gives ppl makes it all worth while.

Anyway, thanks once again,
Steve

---

### Post by huggies15 on 2007-12-05
ok ive got a problem... i will add a bug report unless im being stupid in this:
i open a file i created with gchempaint, saved as a gchempaint file... and i get the follwing message
sorry, format application/octet stream not supported! failed to load file....
now i havent done anything except create a file and save it, which is rather annoying as it took ages to make it, and i opened it on the day, so it seems to not like opening after creation date...

do i need to add a bug repport, or is this all my own fault?

---

### Post by tak1150 on 2007-12-05
[https://savannah.nongnu.org/bugs/index.php?21665](https://savannah.nongnu.org/bugs/index.php?21665)

That is a known bug. I've reported it already. It may be fixed if you install it from the source using the newest OpenBabel package, but maybe not :(

Tak

---

### Post by jbrefort on 2007-12-05
Use goffice instead of goffice-gtk, and files will be correctly loaded.

---

### Post by huggies15 on 2007-12-05
that fixed it for me :)
yay! thanks for working that out so quickly, can do the rest of my talk now!!!

---

### Post by tweedledee on 2007-12-10
> **LaserJock said:**
> *bump* Anybody try my packages yet? :popcorn:

Thanks!  I finally upgraded to Gutsy (well, one computer of four in the house so far), and your package installed perfectly.

---

### Post by lbthrice on 2007-12-14
did someone already mention BioClipse??  Because it is phenomenal and is java platform independent!

---

### Post by tak1150 on 2007-12-21
This thread is almost turning into a Gchempaint support thread, but...

Version 0.8.5 came out! (yesterday)
LaserJock-
Are you going to make a deb package for us? Thanks.

Merry Christmas to you all Chembuntuers

tak

---

### Post by jbrefort on 2007-12-21
Tak, how did you know, I did not annouce it yet !

---

### Post by tak1150 on 2007-12-21
> **jbrefort said:**
> Tak, how did you know, I did not annouce it yet !

Once in a while I check the "Download" page on the Gchempaint website. Version 0.8.5 was postmarked 12-20-07. That's my secret :)

---

### Post by evillan on 2007-12-25
Did anybody try [MarvinSketch]("http://www.chemaxon.com/product/msketch.html")?

I really like the output and it is quite simple to use. Go ahead and try the online tryout (Java required). Unfortunately, it doesn't appear to be open source, but it is completely free (as in beer :p).

Other than that, I returned to ChemSketch (via wine) since it is the only lab kit drawing program I've been able to find. I'm using a template from schropps.dk - really nice output :)

---

### Post by jbrefort on 2007-12-27
I agree we also need a lab kit drawer. If time was available I'd add one to gchemutils, but I can't do everything I would like. May be if somebody provided the templates... the code itself is not so difficult.

---

### Post by chemicalscum on 2008-01-03
> **evillan said:**
> Did anybody try [MarvinSketch]("http://www.chemaxon.com/product/msketch.html")?

I really like the output and it is quite simple to use. Go ahead and try the online tryout (Java required). Unfortunately, it doesn't appear to be open source, but it is completely free (as in beer :p).



I use it a lot as being cross platform I can use the same program at work on XP and at home on Gutsy.

I find it very useful for modeling Mass Spec fragmentation pathways as it has a nice  selection tool for copy/cut which allows for box or free form selection (Unfortunately this is currently not present in Gchempaint).

I also find its pKa tool (with microspecies distribution plots) useful for designing HPLC mobile phases from scratch and in general getting an idea of what is happening in solution chemistry.

I have persuaded people at work(the managers are happy as they don't have to spend money to purchase software) to use it as our default chemistry drawing software.  We use it in general for preparing structure drawings and reaction schemes for submission to regulatory agencies.  It has taken a bit of a learning curve to shift people from Chemwindows/Knowitall to Marvinsketch but now most people seem happy with it.

You can also use it to draw 3D (OpenGL) charge distribution models using the Mulliken orbital electronegativity approach.  This is a bit of a crude approximation compared to using the Gchempaint - Ghemical combination in Linux to prioduce similar 3D charge distributions using the integration of the electrostatic surface potential (ESP) calculated using  semi-empirical quantum mechanical Hamiltonians (MNDO, MINDO/3, AM1 and PM3 or even do ab intio instead). This approach gives large differences in partial charges compared to the orbital electronegativity approach but the overall patterns are similar.  The Marvinsketch models are OK for a quick approximation.

I would like to thank Jean for Gchempaint which I use a lot in Linux especially for its excellent integration with Ghemical.

---

### Post by LaserJock on 2008-01-06
> **tak1150 said:**
> This thread is almost turning into a Gchempaint support thread, but...

Version 0.8.5 came out! (yesterday)
LaserJock-
Are you going to make a deb package for us? Thanks.

Merry Christmas to you all Chembuntuers

tak

Yes, a little late but I've got them up. They should be in 8.04 very soon as well.

-LaserJock

---

### Post by sombrero on 2008-01-09
Hi everyone,

thanks a lot to jbrefort for doing such a nice work and to laserjock for making it available easily.

I am afraid there is a known problem with the last version 0.8.5 (the atoms are not corrected added). A patch has apparently been published ([http://savannah.nongnu.org/bugs/?21964](http://savannah.nongnu.org/bugs/?21964)) so I am wondering if the package could be recompiled.

I am aware that it's a lot of work so I am wondering if anyone knows how I could replace my 0.8.5 by 0.8.4 since I really need this software right now.

Thanks for your help and happy new year to everyone

---

### Post by LaserJock on 2008-01-10
> **sombrero said:**
> Hi everyone,

thanks a lot for jbrefort for doing such a nice work and for laserjock for making it available easily.

I am afraid there is a known problem with the last version 0.8.5 (the atoms are not corrected added). A patch has apparently been published ([http://savannah.nongnu.org/bugs/?21964](http://savannah.nongnu.org/bugs/?21964)) so I am wondering if the package could be recompiled.

I am aware that it's a lot of work so I am wondering if anyone knows how I could replace my 0.8.5 by 0.8.4 since I really need this software right now.

Thanks for your help and happy new year to everyone 

I was going to wait until Debian had the fix published but I just went ahead and uploaded it anyway. It's currently waiting to be built on i386 (amd64 is done) and should be available shortly.

Once I'm confident that our 0.8.5 packages are good I think I'll file a backport request (we got 0.8.5 in Hardy a few days ago) so that we can have more official packages for Gutsy.

-LaserJock

---

### Post by sombrero on 2008-01-10
I have just installed the amd package, it seems to be working great so far.

Thanks a lot for your help.

---

### Post by sombrero on 2008-01-10
Actually the 0.8.5 appears to be very unstable. It keeps crashing when I try to add a group not a single atom. Did you use the last patch since apparently the first one didn't work ?

I am going to post a bug report but is it possible to downgrade to the 0.8.4 ie does someone has the 0.8.4 (amd64) in his archive and could make it available.

Thanks a lot

---

### Post by sallyGR on 2008-01-11
i see , thanks  a lot.


--------------------------
[business directory]("http://www.bizearch.com")

---

### Post by Nigggo on 2008-01-20
I tried to install gchempain manually but it didnt realy work... then i found laserjocks package and installed this... now it starts but as i want to ad an atom it crashes... do you have any hints?

---

### Post by jbrefort on 2008-01-21
Which version? 0.8.5 was accidentally very unstable (apologies). I intend to release 0.8.6 later this month after some more testing.

---

### Post by Nigggo on 2008-01-21
yes 0.8.5 out of the posted  package

---

### Post by LaserJock on 2008-01-21
> **Nigggo said:**
> yes 0.8.5 out of the posted  package

What does the following command give you:

```
which gchempaint
```

I had similar problems but I found that it was because I previously had built 0.8.5 from the source tarball and that was interfering (I was actually running gchempaint from /usr/local/bin/ rather than /usr/bin). I'm fairly sure my packages should be working ok.

-LaserJock

---

### Post by Nigggo on 2008-01-21
the command line gives mw
```
/usr/bin/gchempaint
```
i can add an atom without any problems but as soon as i choose "add group of atoms" it crashes. i made the mistake and tried to install the programm manually on my second pc to before i found your package... mayby i installed some wron packages or there are any configuration of previous trys to manually install it making problems....
without the add group funkction i am not able to add "O" without getting "H2O"... so a cannot add hydroxy groups :/

---

### Post by jbrefort on 2008-01-22
The atom group tool has also been fixed since 0.8.5, but I confirm it was broken. You can add hydroxy groups with the atom tool if you add a bond to the oxygen atom. Hydrogens number is evaluated automatically after each change.

---

### Post by sombrero on 2008-01-22
Hi Laserjock,

I have installed your package on both a xeon (amd64) and on my old laptop (i386). Both crash in the circumstances described by Niggo. I filed a bug to jbrefort as I said and apparently it has been fixed by a patch.

I guess the best thing is to wait for the next version while using the old 0.6 .

Thanks to both of you for this great work.

Here is what I get when it crashes

```

(gchempaint:19482): Pango-CRITICAL **: pango_attr_list_ref: assertion `list != NULL' failed

(gchempaint:19482): Pango-CRITICAL **: pango_layout_get_text: assertion `PANGO_IS_LAYOUT (layout)' failed

(gchempaint:19482): Pango-CRITICAL **: pango_layout_get_attributes: assertion `PANGO_IS_LAYOUT (layout)' failed

(gchempaint:19482): Pango-CRITICAL **: pango_attr_list_filter: assertion `list != NULL' failed

(gchempaint:19482): Pango-CRITICAL **: pango_attr_list_splice: assertion `list != NULL' failed

(gchempaint:19482): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gchempaint:19482): Pango-CRITICAL **: pango_layout_get_text: assertion `PANGO_IS_LAYOUT (layout)' failed

(gchempaint:19482): GLib-CRITICAL **: g_string_insert: assertion `pos <= string->len' failed

(gchempaint:19482): Pango-CRITICAL **: pango_layout_get_attributes: assertion `PANGO_IS_LAYOUT (layout)' failed

(gchempaint:19482): Pango-CRITICAL **: pango_attr_list_filter: assertion `list != NULL' failed

(gchempaint:19482): Pango-CRITICAL **: pango_attr_list_splice: assertion `list != NULL' failed

(gchempaint:19482): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gchempaint:19482): Pango-CRITICAL **: pango_layout_get_text: assertion `PANGO_IS_LAYOUT (layout)' failed
Erreur de segmentation (core dumped)

```

---

### Post by tweedledee on 2008-03-17
Before I posted a bug report, I was wondering if anyone else has observed that Gchempaint 0.8.5 (Laserjock's build) can't handle spaces in the path name when opening files?  I have no trouble opening the files in question once I remove the spaces from the path or move the files.

---

### Post by jbrefort on 2008-03-17
Do you try opening from the file dialog or from the command line? If you di it from the command line you must add backslashes before every space.

---

### Post by tweedledee on 2008-03-18
> **jbrefort said:**
> Do you try opening from the file dialog or from the command line? If you di it from the command line you must add backslashes before every space.

Actually, from the command line I have no problem.  Opening the file by executing gchempaint either in the directory with the space or from elsewhere but enclosing the path+filename in quotes works just fine.  It's only from the file dialog that I have the problem: it uses %20 for the space, which perhaps is getting interpreted literally after the substitution and so no longer represents a valid path?  I'm not sure when the conversion occurs, but the error message that is displayed includes it.

---

### Post by jbrefort on 2008-03-18
Might be a Gtk+ issue. I don't get that on debian sid, so it is hard to track what's going on.

---

### Post by tweedledee on 2008-03-19
> **jbrefort said:**
> Might be a Gtk+ issue. I don't get that on debian sid, so it is hard to track what's going on.

I suspected the same, but I can't find any other Gtk+ programs with the same issue.  That's why I posted here first - if this is unique to me, then perhaps I just have an odd Gtk+ setup somehow, or there is some subtle difference between my system and Laserjock's that's triggering this?  So if anyone using Laserjock's build on Gutsy could please respond either way....

---

### Post by jbrefort on 2008-03-22
There is an issue. When I type a path with sapces for an inexistant file, gchempaint crashes.  You might file a bug report. I'll manage to make a patch during the week-end if my current grading work allows.

---

### Post by jbrefort on 2008-03-22
The crash was not related with the spaces in the path, but to the fact that the file did not exist. I filed the bug report and attached a patch: [https://savannah.nongnu.org/bugs/?22686](https://savannah.nongnu.org/bugs/?22686)

The "%20" which replace the spaces are normal because the file name is converted to an uri, so this is not harmful.
Thanks for reporting, and don't hesitate to tell me if it does not fix the issue for you.

---

### Post by tweedledee on 2008-03-22
Unfortunately, the issue I'm seeing is not the same, as the patch did not solve my problem.  I went ahead and filed a bug report, along with the major dependency versions I used to compile, in the event that's where the problem is.

---

### Post by jbrefort on 2008-03-23
Fixed, a patch has been published: [https://savannah.nongnu.org/bugs/download.php?file_id=15314](https://savannah.nongnu.org/bugs/download.php?file_id=15314)

---

### Post by Iridos on 2008-09-28
Yeah!
Hooray, fixed after 8 years or so :)

It's also in the repositories now - read somewhere else it was fixed, updated, worked.

Cheers and toodles,
I

PS. it doesn't matter so much now, because it's fixed and hopefully for good, but in general you might want to keep unrelated discussions like the one about gchempaint out of an existing thread and open a new thread. That helps people who google for a problem and come upon a thread dealing with their problem to just see relevant things and not have to wade through 20 pages of unrelated things (although in this case the topic was a bit broader anyways - if it's addressing distinctly different problem it's better off in a different thread - which makes finding both problems/solutions easier)

---

### Post by tak1150 on 2008-09-29
Fellow Chembunters,

Thumbs up to GChempaint and others!

BTW, did you guys know that ChemDraw 9 now works under Wine near perfectly?
Even NMR predictions + Chem3D work! Those of you who have legit licenses should try it. My campus has ChemOffice 9, 10, 11 licenses.
I also own my own ChemDraw6 license and it works under the newest wine too!
And the latest GChempaint is very impressive as well; you can copy and paste into OO Writer, etc.

So I declare this year the year of Independence from Windows for Chemists!

Tak

---

### Post by mister_pink on 2008-09-30
Forgive me if this has been mentioned, but I was wondering if anyone has used chemdraw 10 or 11 in wine? We have a site licence for it so I was thinking of giving it a try soon. Otherwise I'll just use it in my VM but its a bit of a pain.

---

### Post by manij on 2008-12-30
Wine 1.0.0.1

chemdraw ultra 7.0 : no problems : a breeze!

---

### Post by canakas on 2009-01-27
mister_pink and everyone,

 CD10/11 do not really work under wine, as they require .NET 2.0 (which can be installed separately).
I installed .NET 2.0 using winetricks and CD11, and I have come as far as seeing the program window, but the first problem at hand is not being able to register.

It is like the registration scripts cannot access the internet. It just sits there, and then it gives you an error. If I remember correctly, I monitored the network for activity while trying to authenticate the software, and there was none.

If anyone cracks this open, please let us know =)

Now for my two cents on the other suites:

GChem is good, but needs more tools(ms fragmenter, NMR prediction(couple with quantum calculations), hotkey bond sprouting, more journal templates). But it is truly best with a native app, so many thanks to the developers - please continue your excellent work :D

Marvin 5.1.2 is positively more complex but it doesn't have NMR prediction, and I cant find anywhere to choose journal template for the document. And how do I turn off the implicit hydrogens, and why doesn't it allow me to select one molecule on the screen for elemental analysis in stead of returning the mass for all of them? 

And this one goes out to all makers of chemistry software; Cleaning a structure should not cause the rotation of the structure - only the adjustment of the bond angles. One develops a favourite view of compounds one works with and so a carbonyl doesn't always need to have the oxygen upwards =)

Please forgive me and correct me if any of the above complaints are wrong, and I just haven't found the right option.

I am sad to say though, that I think CD11 is still ahead in terms of satisfying the needs of an organic chemist.

-canakas

---

### Post by tak1150 on 2009-01-28
> **canakas said:**
> mister_pink and everyone,

 CD10/11 do not really work under wine, as they require .NET 2.0 (which can be installed separately).
I installed .NET and CD11, and I have come as far as seeing the program window, but the real problem is not being able to register.

It is like the registration scripts cannot access the internet. It just sits there, and then it gives you an error. If I remember correctly, I monitored the network for activity while trying to authenticate the software, and there was none.

If anyone cracks this open, please let us know =)

I have had the same problem with ChemOffice 9 and I contacted CambridgeSoft. I gave them my serial number and they gave me an activation code that you can type in so that you don't have to register it over the Internet. As long as you have a legitimate license, you should be able to do so.

So it sounds like if you just do the above, you will be the first one to use CD 11 under Linux! Please let us know how it turns out.

> **canakas said:**
> 
And this one goes out to all makers of chemistry software; Cleaning a structure should not cause the rotation of the structure - only the adjustment of the bond angles. One develops a favourite view of compounds one works with, and, say, a carbonyl doesnt always need to have the oxygen upwards =)

Please forgive me and correct me if any of the above complaints are wrong, and I just havent found the right option.


It's a small but good point. I agree with you about the "clean up structure" feature.

---

### Post by richardmandle on 2009-02-05
Hello

 I am new here, and to linux. I have been trying to get ChemBio Office Ultra 11 to work also, and have *almost* succeded. ChemDraw loads although i cant actually draw anything or do anything, but it loads and thats something! I registered it by badgering cambridgesoft for an activation code, after installing a few dll's it happily loads but crashes if i try to access preferences or load previous chemdraw files. if i get it to run propperly i'll let you know

Richard

---

### Post by canakas on 2009-02-14
> **tak1150 said:**
> 
So it sounds like if you just do the above, you will be the first one to use CD 11 under Linux! Please let us know how it turns out.


I will indeed try this, but tell me how did you get the verification code program to work under Wine? ([this]("ftp://ftp.camsoft.com/support/outgoing/win/verification_code.exe")).

Last I tried it gave me a tiny window saying: "Verification code=0-38" 
I'll post back when I have results.

By the way Richard, did you install NET 2.0 through winetricks?

-canakas

---

### Post by canakas on 2009-02-21
Hello, 

I am trying the CD11 again. After installing .NET 2.0 with no errors. Also installed mono-2.0-devel to be up to date on the gdiplus side.
Wine is 1.1.15 from the repos. Windows version is set to Win2k during install of .NET 2.0 and back XP afterwards.

Also I had to get the VB6 library MSVBVM60.dll and put it in \windows\system32 to make the installer run. 

I am prompted with request of serial and such, and this time internet activation worked like a charm!!! Must be some Wine-update.

The first part of the installer crashes with the following messages in terminal;

```
~/.wine/drive_c/CSTEMP$ wine install.exe
fixme:ole:OleLoadPictureEx (0xb4eb14,7910,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fa2c), partially implemented.
fixme:ole:OleLoadPictureEx (0xb4eb14,7910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fa2c), partially implemented.
fixme:ole:OleLoadPictureEx (0xb4eb14,159296,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OLEPictureImpl_get_hPal unimplemented for type 3. Returning 0 palette.
fixme:ole:OLEPictureImpl_SaveAsFile (0x131670)->(0x15f6a8, 0, (nil)), hacked stub.
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
err:ole:CoGetClassObject class {100202c1-e260-11cf-ae68-00aa004a34d5} not registered
err:ole:create_server class {100202c1-e260-11cf-ae68-00aa004a34d5} not registered
err:ole:CoGetClassObject no class object {100202c1-e260-11cf-ae68-00aa004a34d5} could be created for context 0x5
fixme:advapi:LookupAccountNameW (null) L"manny" (nil) 0x33f77c (nil) 0x33f780 0x33f774 - stub
fixme:advapi:LookupAccountNameW (null) L"manny" 0x1330a8 0x33f77c 0x132718 0x33f780 0x33f774 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 6 ignored L"MsiAssembly" table values
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1b4698 0x7e1b467c (nil) (nil)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\CSTEMP\\Cambridgesoft\\Activation\\ActivateProduct.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\CSTEMP\\Cambridgesoft\\Activation\\ActivateProduct.exe" failed, status c0000135
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OleLoadPictureEx (0xb4f0b4,7910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fa2c), partially implemented.
fixme:ole:OleLoadPictureEx (0xb4f0b4,97564,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x133f80)->(0x150af8, 0, (nil)), hacked stub.
fixme:ole:OleLoadPictureEx (0xb5176c,502,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fa2c), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,7910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fa2c), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,159296,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,504,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OleLoadPictureEx (0xb5176c,1264,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9fc), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x1613f8)->(0x197cc8, 0, (nil)), hacked stub.

```

Then I click begin installation and I am requested to repair .NET 2.0 which I accept. This leads to the lines below and a crash in setup.exe;

```
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:LsaOpenPolicy ((null),0x33f3c0,0x00000001,0x33f3e8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"manny" (nil) 0x7de4a4f8 (nil) 0x7de4a4fc 0x7de4a4f0 - stub
fixme:advapi:LookupAccountNameW (null) L"manny" 0x14d0f8 0x7de4a4f8 0x14d668 0x7de4a4fc 0x7de4a4f0 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
fixme:msi:msi_unimplemented_action_stub DeleteServices -> 4 ignored L"ServiceControl" table values
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 4 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveDuplicateFiles -> 7 ignored L"DuplicateFile" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 16 ignored L"CreateFolder" table values
fixme:msi:msi_unimplemented_action_stub BindImage -> 8 ignored L"BindImage" table values
fixme:ntdll:server_ioctl_file Unsupported ioctl 900a4 (device=9 access=0 func=29 method=0)
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
fixme:imm:ImmDisableIME (-1): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
err:ole:CoUninitialize Mismatched CoUninitialize
err:ole:CoUninitialize Mismatched CoUninitialize

```




The second part of the installer installs CD and C3D with quite a few errors in terminal.
When launching the program it appears, then backs out with the following lines;

```
~/.wine/drive_c/Program Files/CambridgeSoft/ChemOffice2008/ChemDraw$ wine ChemDraw.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\CambridgeSoft\\ChemOffice2008\\Common\\Extensions\\Online\\Online11.dll") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\Program Files\\CambridgeSoft\\ChemOffice2008\\Common\\Extensions\\Online\\Online11.dll"
err:ole:create_server class {10bc9a49-4c78-4f4f-9f9a-3dd69162ed4b} not registered
err:ole:CoGetClassObject no class object {10bc9a49-4c78-4f4f-9f9a-3dd69162ed4b} could be created for context 0x7
fixme:gdiplus:GdipCreateBitmapFromGraphics hacked stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x32fdbc): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebe8820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:commdlg:PrintDlgExA (0x32fac0) stub
wine: Call from 0x7b844fc0 to unimplemented function gdiplus.dll.GdipGetVisibleClipBounds, aborting
wine: Unimplemented function gdiplus.dll.GdipGetVisibleClipBounds called at address 0x7b844fc0 (thread 0009), starting debugger...
Unhandled exception: unimplemented function gdiplus.dll.GdipGetVisibleClipBounds called in 32-bit code (0x7b845036).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b845036 ESP:0032f2a8 EBP:0032f30c EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82eed5 EBX:7b8b4df8 ECX:00000000 EDX:0032f330
 ESI:0032f330 EDI:02f66948
Stack dump:
0x0032f2a8:  0032f330 00000008 00000002 7eb109f4
0x0032f2b8:  80000100 00000001 00000000 7b844fc0
0x0032f2c8:  00000002 7e1d7da0 7e1d85d7 0032f314
0x0032f2d8:  7eaba6fd 0032f300 00000000 7e1b77b8
0x0032f2e8:  00000000 0032f308 f710689a 02f653a0
0x0032f2f8:  401f1b7f 00000000 00000000 00ffffff
Backtrace:
=>0 0x7b845036 in kernel32 (+0x25036) (0x0032f30c)
  1 0x7e1d7d26 in gdiplus (+0x27d26) (0x0032f33c)
  2 0x7e1b2678 in gdiplus (+0x2678) (0x0032f40c)
  3 0x0059be4d in chemdraw (+0x19be4d) (0x0032f4b0)
  4 0x0058dbea in chemdraw (+0x18dbea) (0x0032f644)
  5 0x7ebf42da WINPROC_wrapper+0x1a() in user32 (0x0032f674)
  6 0x7ebf49be WINPROC_wrapper+0x6fe() in user32 (0x0032f6b4)
  7 0x7ebf9215 in user32 (+0xb9215) (0x0032fb84)
  8 0x7ebf9e0a in user32 (+0xb9e0a) (0x0032fbc4)
  9 0x7ebbade1 in user32 (+0x7ade1) (0x0032fc24)
  10 0x7ebbeefd in user32 (+0x7eefd) (0x0032fc84)
  11 0x7ebbf36a SendMessageW+0x4a() in user32 (0x0032fcc4)
  12 0x7ebcbf8b RedrawWindow+0x1db() in user32 (0x0032fd24)
  13 0x7ebcd435 UpdateWindow+0x35() in user32 (0x0032fd44)
  14 0x007ebe3b in chemdraw (+0x3ebe3b) (0x0032fd64)
  15 0x00610d17 in chemdraw (+0x210d17) (0x0032fe30)
  16 0x007f6f73 in chemdraw (+0x3f6f73) (0x0032fe78)
  17 0x00d36c2b in chemdraw (+0x936c2b) (0x0032ff08)
  18 0x7b877c87 in kernel32 (+0x57c87) (0x0032ffe8)
0x7b845036: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (103 modules)
PE	  400000- 1307000	Export          chemdraw
PE	 1970000- 1a1e000	Deferred        cawprop
PE	 1b20000- 1c04000	Deferred        regcodecom11
PE	78000000-78044000	Deferred        msvcrt
PE	78130000-781cb000	Deferred        msvcr80
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bcad000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c420000-7c4a7000	Deferred        msvcp80
ELF	7da43000-7da70000	Deferred        ws2_32<elf>
  \-PE	7da50000-7da70000	\               ws2_32
ELF	7db2e000-7db4a000	Deferred        localspl<elf>
  \-PE	7db30000-7db4a000	\               localspl
ELF	7db4a000-7db7d000	Deferred        libxslt.so.1
ELF	7db7d000-7dbbc000	Deferred        urlmon<elf>
  \-PE	7db80000-7dbbc000	\               urlmon
ELF	7dbbc000-7dcdc000	Deferred        libxml2.so.2
ELF	7dcdc000-7dd2c000	Deferred        msxml3<elf>
  \-PE	7dce0000-7dd2c000	\               msxml3
ELF	7df4e000-7df52000	Deferred        libgpg-error.so.0
ELF	7df52000-7df9f000	Deferred        libgcrypt.so.11
ELF	7df9f000-7dfaf000	Deferred        libtasn1.so.3
ELF	7dfaf000-7dfc2000	Deferred        libresolv.so.2
ELF	7dfc2000-7dfca000	Deferred        libkrb5support.so.0
ELF	7dfca000-7dffc000	Deferred        libcrypt.so.1
ELF	7dffc000-7e072000	Deferred        libgnutls.so.13
ELF	7e072000-7e095000	Deferred        libk5crypto.so.3
ELF	7e095000-7e122000	Deferred        libkrb5.so.3
ELF	7e122000-7e14b000	Deferred        libgssapi_krb5.so.2
ELF	7e14b000-7e17e000	Deferred        libcups.so.2
ELF	7e180000-7e198000	Deferred        spoolss<elf>
  \-PE	7e190000-7e198000	\               spoolss
ELF	7e198000-7e1e7000	Export          gdiplus<elf>
  \-PE	7e1b0000-7e1e7000	\               gdiplus
ELF	7e1e7000-7e2cd000	Deferred        oleaut32<elf>
  \-PE	7e200000-7e2cd000	\               oleaut32
ELF	7e2cd000-7e302000	Deferred        winspool<elf>
  \-PE	7e2d0000-7e302000	\               winspool
ELF	7e302000-7e3ae000	Deferred        comdlg32<elf>
  \-PE	7e310000-7e3ae000	\               comdlg32
ELF	7e3ae000-7e3d6000	Deferred        oledlg<elf>
  \-PE	7e3b0000-7e3d6000	\               oledlg
ELF	7e3d6000-7e3f8000	Deferred        mpr<elf>
  \-PE	7e3e0000-7e3f8000	\               mpr
ELF	7e3f8000-7e449000	Deferred        wininet<elf>
  \-PE	7e400000-7e449000	\               wininet
ELF	7e476000-7e4db000	Deferred        rpcrt4<elf>
  \-PE	7e480000-7e4db000	\               rpcrt4
ELF	7e4db000-7e5e8000	Deferred        ole32<elf>
  \-PE	7e500000-7e5e8000	\               ole32
ELF	7e5e9000-7e5ec000	Deferred        libkeyutils.so.1
ELF	7e5ff000-7e632000	Deferred        uxtheme<elf>
  \-PE	7e610000-7e632000	\               uxtheme
ELF	7e632000-7e63b000	Deferred        libxcursor.so.1
ELF	7e63b000-7e640000	Deferred        libxfixes.so.3
ELF	7e640000-7e643000	Deferred        libxcomposite.so.1
ELF	7e643000-7e649000	Deferred        libxrandr.so.2
ELF	7e649000-7e651000	Deferred        libxrender.so.1
ELF	7e651000-7e656000	Deferred        libxxf86vm.so.1
ELF	7e656000-7e659000	Deferred        libxinerama.so.1
ELF	7e659000-7e679000	Deferred        imm32<elf>
  \-PE	7e660000-7e679000	\               imm32
ELF	7e679000-7e67e000	Deferred        libxdmcp.so.6
ELF	7e67e000-7e696000	Deferred        libxcb.so.1
ELF	7e696000-7e699000	Deferred        libxau.so.6
ELF	7e699000-7e780000	Deferred        libx11.so.6
ELF	7e780000-7e78e000	Deferred        libxext.so.6
ELF	7e78e000-7e7a6000	Deferred        libice.so.6
ELF	7e7a6000-7e7ae000	Deferred        libsm.so.6
ELF	7e7ae000-7e7b1000	Deferred        libcom_err.so.2
ELF	7e7c8000-7e860000	Deferred        winex11<elf>
  \-PE	7e7e0000-7e860000	\               winex11
ELF	7e88b000-7e8ac000	Deferred        libexpat.so.1
ELF	7e8ac000-7e8d6000	Deferred        libfontconfig.so.1
ELF	7e8f0000-7e95d000	Deferred        libfreetype.so.6
ELF	7e95d000-7e95f000	Deferred        libxcb-xlib.so.0
ELF	7e977000-7ea38000	Deferred        comctl32<elf>
  \-PE	7e980000-7ea38000	\               comctl32
ELF	7ea38000-7ea8c000	Deferred        advapi32<elf>
  \-PE	7ea40000-7ea8c000	\               advapi32
ELF	7ea8c000-7eb2a000	Deferred        gdi32<elf>
  \-PE	7eaa0000-7eb2a000	\               gdi32
ELF	7eb2a000-7ec74000	Export          user32<elf>
  \-PE	7eb40000-7ec74000	\               user32
ELF	7ec74000-7eccf000	Deferred        shlwapi<elf>
  \-PE	7ec80000-7eccf000	\               shlwapi
ELF	7eccf000-7ee58000	Deferred        shell32<elf>
  \-PE	7ece0000-7ee58000	\               shell32
ELF	7ee58000-7ee6b000	Deferred        shfolder<elf>
  \-PE	7ee60000-7ee6b000	\               shfolder
ELF	7ef8b000-7ef96000	Deferred        libnss_files.so.2
ELF	7ef96000-7efa0000	Deferred        libnss_nis.so.2
ELF	7efa0000-7efb8000	Deferred        libnsl.so.1
ELF	7efb8000-7efc1000	Deferred        libnss_compat.so.2
ELF	7efc1000-7efe6000	Deferred        libm.so.6
ELF	7efe6000-7effb000	Deferred        libz.so.1
ELF	b7d13000-b7d17000	Deferred        libdl.so.2
ELF	b7d17000-b7e66000	Deferred        libc.so.6
ELF	b7e66000-b7e7e000	Deferred        libpthread.so.0
ELF	b7e98000-b7fd3000	Deferred        libwine.so.1
ELF	b7fd5000-b7ff1000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\CambridgeSoft\ChemOffice2008\ChemDraw\ChemDraw.exe
	00000021    0
	00000020    0
	00000019    0
	00000018    0
	00000009    0 <==
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
0000001a 
	0000001f    0
	0000001e    0
	0000001d    0
	0000001c    0
	0000001b    0
Backtrace:
=>0 0x7b845036 in kernel32 (+0x25036) (0x0032f30c)
  1 0x7e1d7d26 in gdiplus (+0x27d26) (0x0032f33c)
  2 0x7e1b2678 in gdiplus (+0x2678) (0x0032f40c)
  3 0x0059be4d in chemdraw (+0x19be4d) (0x0032f4b0)
  4 0x0058dbea in chemdraw (+0x18dbea) (0x0032f644)
  5 0x7ebf42da WINPROC_wrapper+0x1a() in user32 (0x0032f674)
  6 0x7ebf49be WINPROC_wrapper+0x6fe() in user32 (0x0032f6b4)
  7 0x7ebf9215 in user32 (+0xb9215) (0x0032fb84)
  8 0x7ebf9e0a in user32 (+0xb9e0a) (0x0032fbc4)
  9 0x7ebbade1 in user32 (+0x7ade1) (0x0032fc24)
  10 0x7ebbeefd in user32 (+0x7eefd) (0x0032fc84)
  11 0x7ebbf36a SendMessageW+0x4a() in user32 (0x0032fcc4)
  12 0x7ebcbf8b RedrawWindow+0x1db() in user32 (0x0032fd24)
  13 0x7ebcd435 UpdateWindow+0x35() in user32 (0x0032fd44)
  14 0x007ebe3b in chemdraw (+0x3ebe3b) (0x0032fd64)
  15 0x00610d17 in chemdraw (+0x210d17) (0x0032fe30)
  16 0x007f6f73 in chemdraw (+0x3f6f73) (0x0032fe78)
  17 0x00d36c2b in chemdraw (+0x936c2b) (0x0032ff08)
  18 0x7b877c87 in kernel32 (+0x57c87) (0x0032ffe8)
wine: Call from 0x7b844fc0 to unimplemented function gdiplus.dll.GdipGetVisibleClipBounds, aborting
wine: Call from 0x7b844fc0 to unimplemented function gdiplus.dll.GdipGetVisibleClipBounds, aborting

```

As you can see it is quite nasty. I believe it is a lack of support for some of the graphics portion of CD11 through GDI+, but I am only guessing.

Hope the right people see this, and can make more sense of it than me.

best regards
-canakas

---

### Post by mister_pink on 2009-02-22
I'm trying this now.

I installed .net as you said, and chemoffice. Couldn't get the registration to work so I'm trying by email. What mono thing did you install? I get the same as you got though, if I choose activate later then the program opens and instantly disappears.

Looks like the same error as yours, something to do with GDI+. Don't know what to do about that really, might require more native dlls perhaps?

---

### Post by mister_pink on 2009-02-22
SUCCESS!!!

I copied gdiplus.dll from my windows install to wine and ChemDraw now runs!

Still can't activate, but hopefully I'll be able to get a code by email/telephone!

:D

I should add - its really choppy, and I haven't actually tried anything out properly yet.

But still, I can draw things!

---

### Post by tak1150 on 2009-02-22
You may want to start over in a new wine bottle.
I used the .NET that comes with ChemOffice (you don't need to install anything but the ChemOffice exe package). What version of ChemOffice are you using? If 9, it comes with .NET. If older than 7 (i think), you don't even need .Net.

---

### Post by canakas on 2009-02-23
OK I stuck the gdiplus.dll in system32, with Chemdraw.exe and in common/DLLs, I can now also avoid crash on startup! I got the DLL from DLL-files.com

Which of these folders where the right one to use?

Okey so heres the terminal output of me entering, setting document standard to ACS 1996(I have to do this to make the drawing area appear, as it starts out as grey) and drawing diethylether.

```
~/.wine/drive_c/Program Files/CambridgeSoft/ChemOffice2008/ChemDraw$ wine ChemDraw.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32f61c,0x00000000), stub!
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\CambridgeSoft\\ChemOffice2008\\Common\\Extensions\\Online\\Online11.dll") not found
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\Program Files\\CambridgeSoft\\ChemOffice2008\\Common\\Extensions\\Online\\Online11.dll"
err:ole:create_server class {10bc9a49-4c78-4f4f-9f9a-3dd69162ed4b} not registered
err:ole:CoGetClassObject no class object {10bc9a49-4c78-4f4f-9f9a-3dd69162ed4b} could be created for context 0x7
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x32fdbc): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:dciman:DCICreatePrimary 0x364 0x186129c
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x7ebfb820): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x110000): stub
fixme:commdlg:PrintDlgExA (0x32fac0) stub
fixme:ole:OleUIAddVerbMenuA ((nil), (null), 0x280, 16, 65, 66, 0, 0, 0x32fa4c): stub
fixme:ole:OleUIAddVerbMenuA ((nil), (null), 0x280, 16, 65, 66, 0, 0, 0x32dfac): stub

```

I have limited knowledge about Microsoft products but I suppose we should look into "Microsoft.VF80.MFC" and "MFC80.DLL" wherever its contained...

tak1150: We(at least I am) using CD 11.
mister_pink: the mono-2.0-devel is just some newer GDI for linux I found, it didnt seem to make much of a difference though. Or maybe it was this that enabled activation for me??

It is easy to cause a crash(here is me trying to predict the carbon spectrum):
```
fixme:bitmap:CreateBitmapIndirect planes = 8
fixme:ole:OleUIAddVerbMenuA ((nil), (null), 0x280, 16, 65, 66, 0, 0, 0x32dfac): stub
fixme:commdlg:PrintDlgExA (0x32f168) stub
fixme:ole:OleUIAddVerbMenuA ((nil), (null), 0x280, 16, 65, 66, 0, 0, 0x32dfac): stub
Killed

```

I'll try more when I get home later.

-canakas

---

### Post by mister_pink on 2009-02-23
I found predicting spectra crashed it. I've activated now by email, so thats not too much of a worry. Can't understand why it didn't work normally - I could see it trying to connect to their server by https. 

I'll try playing around a bit more later to see if other native dlls help it or not. It's quite buggy, but a bit usable at least now! I could draw things and save them to disk fairly well.

Did you find it was really slow as well?

And btw, I only put the dll in system32 so I guess thats all you need!

---

### Post by canakas on 2009-02-23
Hello there,

Yes its a little bit choppy. I'll post back if I can wrap my head around what it needs..

-canakas

---

### Post by mister_pink on 2009-02-24
Well after a bit of a play around I haven't really got anywhere. There was an error about ntdll.dll which I copied across, the error went away but nothing improved.

I think there's an issue with fonts - try writing anything and it locks up temporarily and nothing appears. I tried putting font debug on and it gave tons of output, so I tried again with only font error output and didn't get anything I could work with.

I think we need someone who actually knows something about wine to look at this...

---

### Post by tak1150 on 2009-03-06
Canakas-

Due to the .NET 2 issue, you cannot use ChemDraw >9. The latest version you can use is 9 (v9 uses .NET 1).

---

### Post by mister_pink on 2009-03-06
> **tak1150 said:**
> Canakas-

Due to the .NET 2 issue, you cannot use ChemDraw >9. The latest version you can use is 9 (v9 uses .NET 1).

What do you mean by "the .NET 2 issue"? (emphasis on "the"!) We both have it installed and are now trying to fathom out how to make it work properly - it starts, and you can draw, save and edit molecules. You just can't do anything that requires text. I might try a newer version of wine to see if that helps. 

ChemScript, on the other hand, seems to be working perfectly, which is actually pretty helpful. Unfortunately you can't import the modules into native python, you have to use python in wine.

---

### Post by tak1150 on 2009-03-08
MR pink

Which version are you referring to?

---

### Post by mister_pink on 2009-03-09
> **tak1150 said:**
> MR pink

Which version are you referring to?

ChemOffice Ultra 11. Read the previous page of discussion on this thread - I posted how I managed it there.

---

### Post by tak1150 on 2009-03-10
> **mister_pink said:**
> What do you mean by "the .NET 2 issue"? (emphasis on "the"!) We both have it installed and are now trying to fathom out how to make it work properly - it starts, and you can draw, save and edit molecules. You just can't do anything that requires text. I might try a newer version of wine to see if that helps. 


Your text problem must be very similar to the problems I was having more than a year ago (see the very beginning part of the thread). I couldn't find the articles for it, but I remember I read that that problem was due to .NET 1 not playing nice with WINE. Then around the time WINE v.1.0 came out, that problem was solved. (thus I can now use ChemDraw 9 with wine)

While [this page]("http://appdb.winehq.org/appview.php?iVersionId=3754") labels .NET 2 support as gold, I read elsewhere that WINE still doesn't work well with .NET 2, which is also my experience.

---

### Post by canakas on 2009-03-16
Dear tak1150,

How are you attempting to install .NET 2.0 ?

I used winetricks...

best regards
-canakas

---

### Post by tak1150 on 2009-03-16
Oh, I didn't see that.
Thanks, canakas.

mister_pink,
Did you use winetricks and still get the problem where you can't type letters in ChemDraw?

Tak

---

### Post by mister_pink on 2009-03-17
I didn't use winetricks. I had a .net installer archived from when I used XP. I just ran it and it seemed to work.

I did find a bug report that seemed to explain the issue, can't remember where I found it though. I'll post it if I find it again

---

### Post by canakas on 2009-03-19
Hello colleagues,

I installed a fresh Intrepid (Ubuntu Studio flavour), and figured I would shortly sum up how I got ChemDraw 11 to work again:

-Add Wine to the sources (description in the [ubuntu download section]("http://www.winehq.org/download/deb") on winehq.org)
-Install Wine 1.1.17 from repos
-Get winetricks [as stated here]("http://wiki.winehq.org/winetricks")
-Install .NET 2.0 and some necessary libraries. I installed them one by one but you could presumably run
```
sh winetricks dotnet20 corefonts vb6run vcrun2005 mono22
```

-Start the ChemBioOffice11 installer and activate over internet (it worked again!)
-The .NET 2.0 repair/installer stops and I helped it along by ending the ngen.exe process in system monitor. This made the .NET installer say it installed successfully... The CBO-installer continues and proceeds to completion with no apparent errors.
-Start ChemDraw

***

New things:
-ChemDraw now starts with the first blank page open and active as it should and not with the page crumbled in a corner with a grey background. Maybe you guys got this one right the first time.

Please post stuff from terminal if it puts out something interesting that can point to what we are missing to get the GUI not to crash when doing more than drawing, like NMR-prediction and such...

-canakas

---

### Post by barbarosreis on 2009-08-30
hey;
I am very new to linux-almost 30 mins- and i first checked chem draw or any equivalent program at ubuntu. and read your posts but i couldt get what should i do.

as i understand we can use chemdraw but we should do something tricky.

if someone tell what should i do. i will be very close to uninstall win.

thanks

---

### Post by canakas on 2009-08-30
Hello there,

Wow 30min you are brave! =)
 it took me a year of much frustration to gain the knowledge I needed to be able to get ChemDraw11 to work...I also had help from mister_pink here on the forum.

I think a little searching around the ubuntu/wine guides should help you understand the recipe in a better way than I am able to explain...sorry about that.

but I would recommend that you go for something a little less unstable if you want to do some serious chemistry work in linux... :P

 Several nice softwares were mentioned earlier in this thread I believe
Maybe the Marvin-bundle suits your needs...

by the way 
CD 12 is out.. I will post back here when I do try it in Wine.

mister_pink: have you installed it yet?

cheers

---

### Post by barbarosreis on 2009-08-31
I even didnt know how diffucult to use chemdraw on ubuntu.

I checked bkchem and gchempaint. they are nice but i cant something i easy do in chemdraw.

in bkchem you cant rotate a part of molecule even if you select a part of molecule program rotate all of it.

sometimes bond angles not so correct i know chemdraw not a genius for that but it's much better especially when heteroatom is encounter.

and nmr predict is a good properties for chem draw sometimes help me to faster decisions.

converting molecule name to structure and structure to name also is very useful.

sure, one of the biggest problem is that these softwares cannot open or save cdx format  -chemdraw- 

are there any more option i can check

---

### Post by canakas on 2009-08-31
I completely agree with you. 
I don't know of any native linux chemistry application that can do what we can do in ChemBioDraw...:(

You can try MarvinSketch from the JChem-suite from ChemAxon... it is free you just have to register and a few things... It is not as good a GUI as CD, but it has some nice features like pKa-estimation. It also works pretty well with its brother MarvinSpace (like a simple Chem3D), although the structure optimization algorithms are not the strongest.

---

### Post by mister_pink on 2009-08-31
Unfortunately I no longer do chemistry, so I don't have access to chemdraw. Would be interested to know if anyone gets it working properly though.

---

### Post by rutulian on 2009-12-06
Just noticed this thread. My $0.02....

I'm writing my dissertation. The Marvin-suite is awesome!!!! Yes, ChemDraw is the standard, but I've been doing some cheminformatics work, and the Marvin tools are far better suited to the task then the Cambridgesoft stuff. ChemDraw itself is nice, but I've always hated everything else from them: Chem3D, ChemFinder, etc.... And the constant activation nagging really irks me. It's designed to be Windows-only software, so it has a lot of annoying Windows-isms. MarvinSketch is a bit different. If you're used to ChemDraw, it might be a bit frustrating at first. But when you get used to the flow, the interface is actually very efficient and nice. And the figures it generates are very nice (high resolution bitmaps or vector-based, your choice).

My current workflow:
1) Structures drawn in MarvinSketch  -->  Stored in an InstantJChem database
2) With the database I can easily sort and query for particular structures and add metadata like entry #'s and NMR data. If you process your NMRs with MestRec (yes, it works in Linux too!) and store them as a .png or whatever, you can link them to your records in InstantJChem so that you can quickly retrieve the NMR for any given compound in the database.
3) Use MarvinSketch again to assemble the reaction schemes
4) Use the included MolConverter program to export the .mrv files to .svg files, and then use Inkscape to convert those to .eps files
5) Use latex with the chemstyle package to automatically manage the compound numbering and referencing

There are some issues....
1) MarvinSketch doesn't have precision alignment tools, so the schemes can be a little painful. I guess it depends on how OCD you are. I was able to manage, but some more of the common vector illustration tools would be nice (keyboard positioning, alignment and distribution of groups, rulers, guides, snap to grid, etc). Maybe those will come in a future release.

2) Also, MarvinSketch doesn't export directly to EPS. It does export to PDF, but depending on what you are doing, that may not be good enough. The chemstyle package, for example, uses the PSFrag utility which, of course, only works on postscript files. The SVG route is a usable workaround, but then you have to add Inkscape processing to your workflow. Every additional step is more time....

3) InstantJChem doesn't support fields with rich text. In many cases this is just aesthetic, but it really helps when you are storing NMR data.

Anyhow, that's a bit longwinded, but I just thought I should put in a plug for ChemAxon. Running programs critical for my work under WINE is not particularly desirable to me. Of the available tools that run natively under Linux, ChemAxon's are definitely the best. Yes, I've tried them all. GChempaint is promising, but it needs a lot more work.

---

### Post by lastpook on 2009-12-06
Hello, everyone
Does anybody know if GChemPaint works with Karmic Koala? I have totally failed with installation (it seems like package 'gcu' is named 'gcu-bin' now and therefore ./configure returns error all the time)

As for Marvine. Really rocks after I have realized how to use shortcuts for radicals :)

---

### Post by jbrefort on 2009-12-07
Seems there is no gchempaint package in karmic. You might try one from debian (testing has 0.10.9 which is ways better than 0.8.6, but you will need to update gcu-bin at least to the same version).

Replying to the previous post, I'd say that I agree that gchempaint needs a lot more work. May be it will never reach a full-featured state just because it is a one man project. I failed to find other interested developers.

---

### Post by lastpook on 2009-12-08
> **jbrefort said:**
> Seems there is no gchempaint package in karmic. You might try one from debian (testing has 0.10.9 which is ways better than 0.8.6, but you will need to update gcu-bin at least to the same version).

I have installed [0.10.9]("http://mirror.lihnidos.org/GNU/savannah/gchemutils/0.10/gnome-chemistry-utils-0.10.9.tar.gz") and [0.10.8]("http://mirror.lihnidos.org/GNU/savannah/gchemutils/0.10/gnome-chemistry-utils-0.10.8.tar.bz2") in Karmic but unfortunatelly after installation none of the applications can be launched.
```
gchempaint-0.10: error while loading shared libraries: libgchempaint-0.10.so.0: cannot open shared object file: No such file or directory
gchem3d-0.10: error while loading shared libraries: libgcu-0.10.so.0: cannot open shared object file: No such file or directory
gchemcalc-0.10: error while loading shared libraries: libgcu-0.10.so.0: cannot open shared object file: No such file or directory
```Where one can get these libraries for Ubuntu 9.10?

After using Marvin for a while I've found that there is no way to draw multistep retrosynthetic schemes. [weird, isn't it? ]("http://www.chemaxon.com/forum/ftopic5037.html")

---

### Post by LaserJock on 2009-12-08
For people wanting GChemPaint for Ubuntu 9.10, I've just uploaded it to the [Debichem PPA]("https://launchpad.net/~debichem/+archive/ppa/"). If you're running Ubuntu go to the Software Sources and add ppa:debichem/ppa in the third party tab. Reload the repositories and install/upgrade gchempaint. For command line users you can use the following:

```

sudo add-apt-repository ppa:debichem/ppa
sudo apt-get update
sudo apt-get install gchempaint

```

That repository also has Avogadro, the awesome 3D molecular editor, that people might also find useful.

Hope that helps,

LaserJock

---

### Post by lastpook on 2009-12-10
Thanks!

---

### Post by Captain_Rage on 2010-03-04
Many thanks for posting the PPA address! Though I wonder why GChemPaint isn't in the official Ubuntu repositories...

---

### Post by LaserJock on 2010-03-05
> **Captain_Rage said:**
> Many thanks for posting the PPA address! Though I wonder why GChemPaint isn't in the official Ubuntu repositories...

It is in the official Ubuntu repositories (gchempaint) but we use the PPA to provide newer versions where we can for stable Ubuntu releases. Ubuntu's update policy is fairly strict and doesn't generally allow completely new software releases, only critical bug fixes.

---

### Post by repunante on 2010-10-19
For years and years I was using all the list of software available in Linux to draw structures of molecules, changing from one to another again and again. It was impossible to find a proper one: not enough features, annoying interfaces, poor quality of the results,...
So at the end I was using chemdraw for windows with wine, having good results but feeling a bit uncomfortable, you know, I don't like to run something from Windows in Linux, call it scrupulousness maybe.

Today I tried Bkchem, I think this it is the 4th time I tried it in several years. I always had problems with it, maybe because I run it with Gnome the lines are crap (the letters are nice though). The main problem was the stability, it always crashed for no apparent reason.
Today it didn't crash, it wash smooth and stable, I couldn't change the kde feeling but at least it was working. My surprise was that I could do everything I needed, write heteroatoms directly to the structure, scale some molecules leaving the others with the original size, put brackets, move the structures easily, rotate them ... in the chemdraw way: intuitive and easy.

The only bad thing was that I couldn't copy the scheme directly to openoffice but I save it to a svg file and I pasted it in the document with an excellent quality. It was strange for me, because the lines looked awful in Bkchem but in openoffice looked quite neat. I printed it out and now I have it in front of me: I cannot believe the result, just perfect.
Bkchem made my day.

PS. sorry about the possible mistakes in my narration, I'm learning slowly.

---

### Post by billyjmc on 2010-12-20
@repunante,

This is very similar to my experience. BKchem doesn't look too nice on-screen, but you can't argue with the results. I love that it natively saves the product in SVG. It makes it easy to process into something else, like PDF or PS for inclusion in a LaTeX document. (Also, the project has recently been taken over by a new programmer, so it's likely to see some more updates in the near future. Woo!)

I've found that MarvinSketch is too clever for its own good. Sometimes I want to simply write free-form labels instead of actual atoms or functional groups. And I don't like how the "atoms" are centered in their locations -- left-align, please. Finally, converting them to a reasonable vector graphic form that I'm satisfied with has been somewhat painful, but certainly not insurmountable.

With that all said, I have scripts and makefiles for doing the heavy lifting for all these conversions. Maybe someone will find them useful...

[http://people.tamu.edu/~bjmcculloch/]("http://people.tamu.edu/%7Ebjmcculloch/")

---

### Post by billyjmc on 2011-02-10
I'm now using ChemDraw on Linux. My version of Wine (1.1.42) works fine (if a but slow on startup) for CD7, which is sufficient for my purposes.

Perhaps more interestingly, though, for all those fans of TeX et al., is that I've managed to script the conversion from native CDX format to any filetype ChemDraw is capable of.

I've detailed the procedure at my website (URL below), but will give a summary here for archival purposes.

[http://people.tamu.edu/~bjmcculloch/]("http://people.tamu.edu/%7Ebjmcculloch/")

[B]cdx2eps.pl
[/B]```

#!/path/to/windows/version/of/ActivePerl/perl.exe
# Usage: cdx2eps.pl <input document 1> [input document 2] [...]

use strict;
use warnings;

use Win32::OLE;
use File::Basename;
use Cwd 'abs_path';

my $ChemDraw = Win32::OLE->new('ChemDraw.Application', 'Quit');

foreach ( @ARGV ) {
    my $absolute = abs_path($_);
    my ($filename, $directory, $suffix) = fileparse($absolute, ".cdx");
    my $input = $directory . $filename . $suffix;
    my $output = $directory . $filename . ".eps";
    $ChemDraw->Application->Documents->Open($input)->SaveAs($output);
}

```One caveat here is that even though I've given the "Quit" command to Chemdraw, it never does (Wine has a few bugs when working with COM Automation, apparently). You can kill it of course, but that's a pain. You also can't, as far as I can tell, specify options for the save process, e.g. resolution of a PNG. Otherwise, this works great. ChemDraw is smart enough to output the proper filetype based on the output filename.

---

### Post by mfomich on 2011-10-14
Hi!
My problem is that the window of ChemDraw 7 under Wine is almost totally invisible. It means I see only a kind of refraction.:) Any suggestions please?

Ubuntu 11.04
Wine 1.2.2
ChemDraw 7.0

UPD. Sorry. I had to wait more. The start was quite sluggish. Finally, it worked fine.

---

### Post by repunante on 2011-10-14
> **billyjmc said:**
> @repunante,

This is very similar to my experience. BKchem doesn't look too nice on-screen, but you can't argue with the results. I love that it natively saves the product in SVG. It makes it easy to process into something else, like PDF or PS for inclusion in a LaTeX document. (Also, the project has recently been taken over by a new programmer, so it's likely to see some more updates in the near future. Woo!)

I've found that MarvinSketch is too clever for its own good. Sometimes I want to simply write free-form labels instead of actual atoms or functional groups. And I don't like how the "atoms" are centered in their locations -- left-align, please. Finally, converting them to a reasonable vector graphic form that I'm satisfied with has been somewhat painful, but certainly not insurmountable.

With that all said, I have scripts and makefiles for doing the heavy lifting for all these conversions. Maybe someone will find them useful...

[http://people.tamu.edu/~bjmcculloch/]("http://people.tamu.edu/%7Ebjmcculloch/")


I tried ChemDoodle for Linux and it is awesome. Not free but very very cheap.

---

### Post by yeayea on 2012-08-29
Hey All,

For those of you who are still interested in running ChemDraw in Ubuntu, I have ChemDraw 12 up and running with Wine 1.4 in Ubuntu 12.04!

Check out the WineHQ page on [_ChemDraw 12_]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=24320&iTestingId=71516")

I followed the instructions and installed from the .msi file and everything is working fine! The anti-aliasing was not working at first, but after installing .NET 2.0 with winetricks the structures look pretty good.

---

