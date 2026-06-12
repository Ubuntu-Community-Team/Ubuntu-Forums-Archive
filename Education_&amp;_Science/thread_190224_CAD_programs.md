---
title: "CAD programs?"
date: 2006-06-06
forum: Education &amp; Science
---

### Post by slimdog360 on 2006-06-06
Im looking for a good CAD program for linux. Something simialar to Auto CAD, also Id rather it be free if possible. Can anyone suggest anything along these lines?
thanks

---

### Post by floflooo on 2006-06-06
I heard of qCAD... It's supposedly good.

---

### Post by dudus on 2006-06-06
I installed a bunch and QCad was the best IMHO. Even so it is not that good

---

### Post by cotcot on 2006-06-06
Indeed QCAD. You can save AutCAD drawing as DXF or convert DWG to DXF with dwg2dxf (lx-viewer) and work on them in QCAD. QCAD is only 2D.

---

### Post by M+J on 2006-06-07
LinuxCad is a replacement for autocad, so they say at linspire, It will cost $200:(

---

### Post by thematrix on 2006-06-07
Pro/Engineer runs great on Linux, even did some tests on Kubuntu and it flies. Far from free, but then again it _is_ the best cad package... 

Cheers,

Frederic

---

### Post by mihkel on 2006-06-08
Just curious. Has anyone managed to install medusa4??
[http://www.medusa4.com/index.php?screen=1.024&land=com&ziel=Products|MEDUSA]("http://www.medusa4.com/index.php?screen=1.024&land=com&ziel=Products|MEDUSA")

---

### Post by cosine7 on 2006-06-26
I have been a long term autocad user and have just converted to Ubuntu. I found qcad great and the closet to autocad of all the drawing packages i tested. :mrgreen:

---

### Post by g7kse on 2006-07-10
Cosine7, if you've used it quite a bit which version do you think its closest to? Is it up to mech desktop standards or dare I say it inventor or is it back at 98LT level?

Cheers

Alex

I only use 2002 at work but have 2004 for home projects. 2002 was fine for most things (3D stuff definetly not included!)

---

### Post by cosine7 on 2006-07-10
> **g7kse said:**
> Cosine7, if you've used it quite a bit which version do you think its closest to? Is it up to mech desktop standards or dare I say it inventor or is it back at 98LT level?

Cheers

Alex

I only use 2002 at work but have 2004 for home projects. 2002 was fine for most things (3D stuff definetly not included!)

I found it to be pretty close to ACAD 2000 (- 3d of course), probably one of the things that is majorly different is the printing aspects, which are a bit simpler. But i actually found (after about 5hours of use) it to be quite a bit more intuitive then ACAD... hope that helps.

---

### Post by Slingshot on 2007-11-15
Its not free, but I believe Bricscad is a version of Intellicad for Linux. I havent used it myself, but most Intellicad based packages are close to AutoCAD.

---

### Post by francisco.colaco on 2007-11-16
Since wine 0.9.46 I am able to install and run successfully ProgeSoft Intellicad out of the box.  There are still some small issues, like a lack of refreshment of the screen, and not functional shading, wireframe.  It loads, saves and edits without much hassle a CAD file, however big it might be.

Please confirm these results.

   Francisco Colaço

---

### Post by francisco.colaco on 2007-11-16
Just to add something:

  VARICAD has the easiest 3D I ever came up with.  It is more expensive than Progesoft Intellicad (which I now run under wine), but it's 2D is somewhat lacking.

  Worth a try.

    Francisco Colaço

---

### Post by hkgonra on 2007-12-18
A buddy of mine has a shop running Solidworks and Mastercam , is there anything that works in linux that is comporable to those programs ?

---

### Post by hambone79 on 2007-12-18
Here is a list of links to CAD programs for Linux:
[http://linux4engineering.org/index.php?option=com_weblinks&catid=14&Itemid=23]("CAD software for Linux")

I haven't tried most of these programs but I do know from personal experience that Pro/E and VariCAD both run extremely well in Linux.

---

### Post by Peter76 on 2007-12-20
Not open source; but here: [http://www.graytechsoftware.com/](http://www.graytechsoftware.com/) they have a free program witch runs fine under wine and looks promising

---

### Post by cmat on 2007-12-24
I need to use AutoCAD and unfortunately Windows because of the third party plug-ins that are designed for AutoCAD only. :/

---

### Post by bakketti on 2007-12-24
avoCADo is a new CAD development similar to Solidworks. It looks promising, however, development is going slowly. They definitely need help.

[http://avocado-cad.sourceforge.net/](http://avocado-cad.sourceforge.net/)

---

### Post by gilf on 2007-12-27
I am running **CollabCAD** right now on Ubuntu 7.10 and Kubuntu 7.04.

This is a very advanced**[COLOR="Red"] FREE [/COLOR]**(though not Open Source) 3D CAD program with tie- ins to CAM, Blender rendering, analysis software, ERP, and much else.

It is designed to allow multiple users in different locations to collaborate on a design. It does parts and assemblies, multiple on screen views, wireframe, and shading, solids, etc.

It is not well documented, and this is probably the problem faced by people trying to install it. In fact, I found the installation easy, though not what I had expected.

Looking at the downloadable files a .tgz file of over 100 megabytes, I assumed that it was a source file that would have to be compiled. In fact it does not need compilation,  it is merely unpacked. for use

Once unpacked into the collabcad folder it can be run directly from the collabcad.sh script. Be aware however that this is a C shell, not a bash script -- a fact it took awhile to figure out.  You will probably need to install the C shell (I did in Ubuntu 7.10) You can run the program by opening a terminal and changing to the collabcad directory. Issue the command ./collabcad to start. 

I built a shortcut with an icon to open the program from the desktop without using the terminal. Instructions for this are elsewhere on the forums in a thread I started.
 
In use, a big problem I had was trying to figure out how to change the color of an entity. There is no obvious path to controlling colors in CollabCAD.

After trying many menu drawing commands I finally stumbled upon the Edit, Modify, command which requires that you be in wireframe mode only, and the selection of an entity. There, finally I found you could alter an object's color.  There is no way to set a default drawing color initially however -- there are very limited options for saving preferences. These are rather a small price to pay for such a sophisticated program.

Despite some challenges, due mainly to a lack of good documentation, I found this to be a very good design tool, with great potential for sophisticated work. It will take some learning however. I'm sure that the user interface, particularly drawing preferences, will be improved as will the documentation.

I'd be interested in hearing from others who use this CAD system.

OTHER CADS TRIED: 
I have also run **TurboCAD LE** (free) under Wine -- and these days it works well without much tweaking of Wine. This is more of a drawing program than a 3D modeler. It is only 2D. It does support DWG and DXF but mainly in older versions of those formats. It will write a compatible file, but may not open newer drawings.

**CollabCAD**, above does not support DWG or DXF. It does support STEP and IGES, and VRML

---

### Post by mb125 on 2007-12-28
Ive been using Autocad 14 under wine with no problems at all, has anyone used 2004-2007 with any luck?

---

### Post by deepthought on 2007-12-30
Hello,

i made an overview of CAD programs working with Ubuntu: [http://wiki.ubuntuusers.de/CAD?highlight=%28cad%29](http://wiki.ubuntuusers.de/CAD?highlight=%28cad%29)
It's in german but maybe interresting to you too.

---

### Post by deepthought on 2008-01-01
CAD overview now in english available:
[https://help.ubuntu.com/community/UbuntuScience#head-3cdf7bb4c23423811354a77a7ebeaff72498b692](https://help.ubuntu.com/community/UbuntuScience#head-3cdf7bb4c23423811354a77a7ebeaff72498b692)

---

### Post by hkgonra on 2008-01-03
I need versions that will integrate with CNC machines.

---

### Post by deepthought on 2008-01-03
> **hkgonra said:**
> I need versions that will integrate with CNC machines.

[http://www.gcad3d.org](http://www.gcad3d.org)
[http://www.webersys.com](http://www.webersys.com)
[http://www.collabcad.com/](http://www.collabcad.com/)

---

### Post by jfl on 2008-01-05
> **slimdog360 said:**
> Im looking for a good CAD program for linux. Something simialar to Auto CAD, also Id rather it be free if possible. Can anyone suggest anything along these lines?
thanks
If you only need 2D, QCAD is good; I needed to do drawings to customize a trailer, didn't want to spend money.
I tried QCAD (it is in the repos); installed flawlessly on my Dapper machine.
One thing that got me confused at the beginning - I have NO experience of AUTOCAD or others - is that you first have to select an action then the object(s) to apply it to.
It's opposite to what I have been used to.
Other than that it is pretty intuitive, printing was no problem.

I liked it, it served my purpose.

Hope this helps.

---

### Post by decjedrek on 2008-02-01
I tried QCAD and it seems to be the closest to AutoCad.

I have also managed to install MEDUSA4 on my Ubuntu 7.10 It runs fine, but I'm still testing if this package can replace QCAD.

You could also try VARKON. I couldn't draw anything there but I've heard many good things about this soft, so you would have do dig some Varkon Wiki or some kind of tutorials ;)

Have fun,
Jedrek

---

### Post by simha on 2009-06-26
Yes collabCAD is Good Package

---

### Post by hsweet on 2009-06-29
Did you have a native port of Pro Engineer or run in in Wine?  We have the software and would love to run it in Linux.

> **thematrix said:**
> Pro/Engineer runs great on Linux, even did some tests on Kubuntu and it flies. Far from free, but then again it _is_ the best cad package... 

Cheers,

Frederic

---

### Post by lobo_blanco on 2009-10-04
> **decjedrek said:**
> I tried QCAD and it seems to be the closest to AutoCad.

I have also managed to install MEDUSA4 on my Ubuntu 7.10 It runs fine, but I'm still testing if this package can replace QCAD.

You could also try VARKON. I couldn't draw anything there but I've heard many good things about this soft, so you would have do dig some Varkon Wiki or some kind of tutorials ;)

Have fun,
Jedrek

I can't get VARKON to install properly, seems there are some missing files or something is not where it should be. Got a message about missing pid file etc.

I tried install through synaptic and from the Deb for Ubuntu 32 bit with no luck.
No launcher is created so I just typed varkon at the terminal ... tries to start but creates 3 windows that then lock up.

I sure would like to try it, I'm using Hardy ... anyone have any success there?

Thanks in advance.

Dave


UPDATE: I figured out how to get the program to open.
At the terminal I entered --help and saw that I could create the initial PID file by specifying it after the command.
example: varkon Testjob
From there it prompts you what is needed.
I didn't get far with the program yet but at least it's configured and works now.
Time to RTFMS!

UPDATE2: Didn't find this program to be useful

---

