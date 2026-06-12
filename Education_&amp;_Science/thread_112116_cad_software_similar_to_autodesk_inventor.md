---
title: "cad software similar to autodesk inventor?"
date: 2006-01-03
forum: Education &amp; Science
---

### Post by pk_volt on 2006-01-03
Anyone know of any?
I'm having a lot of trouble finding one.

Most are for architecture, but i want it for mechanical design stuff.

---

### Post by Kjell on 2006-01-03
Hej,

Dont know what inventor is for version of AutoCad 

But I gues the most comon Cad program, that is free, is qcad 
howwever qcad only handles dxf files, not dwg. You can install qcad directly with synaptic. 

There are some other profesional (comercial) cad versions.
Perhaps you find some suitable at [http://www.tech-edv.co.at/lunix/CADlinks.html](http://www.tech-edv.co.at/lunix/CADlinks.html)

//Kjell

---

### Post by Kjell on 2006-01-03
One that hadles DWG files is BricsCad, there is a demo version at their web site 
but I have not managed to get it working 
[http://www.bricscad.com/](http://www.bricscad.com/)
//Kjell

---

### Post by pk_volt on 2006-01-03
ok, I tried install varicad.

But i get these two errors when I do a dpkg -i varicad.deb or whatever

Unpacking varicad2005-en (from varicad2005-en_2.00-1_i386.deb) ...
dpkg: dependency problems prevent configuration of varicad2005-en:
 varicad2005-en depends on kdelibs4 (>= 4:3.3.2-6.3); however:
  Package kdelibs4 is not installed.
 varicad2005-en depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing varicad2005-en (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 varicad2005-en


But I already have libqt-mt and kdelibs4 installed.

and here are the lists of availabe linux platforms to download from. 

Fedora Core, RedHat EL, SUSE, Mandriva, Debian

---

### Post by Kjell on 2006-01-04
Hej,

It apears that Varicad is a Qt application (for the KDE desktop, not Gnome)

I have tried installing other program that are Qt applications on my Ubuntu 5.10
without sucess. I'm just trying to get some help for this at another forum threads.

I also need *libqt3c102-mt* but I dont now how to get it ! 

I prefer gnome (Ubuntu) and dont whish to switch to KDE (Kubuntu), but perhaps there is a way to have both systems installed - were you can make a choice  
at the log-in screen ?

//kjell

---

### Post by z_diver on 2006-01-04
You can just install the KDE desktop from Synaptic and then you will have all the libraries necessary to run KDE apps.  You are right that you will be able to log into KDE from the login screen but you don't really need to do this.  The program will run as long as it can find the KDE libraries.

---

### Post by Hitchhiker427 on 2006-01-05
I'm gonna bump this because I'm curious too.

Also, Autodesk Inventor is not a normal CAD program like the ones that are being suggested (tried out qcad, pretty nice).  Inventor is all 3D and relatively easy to use.  Another comparable Windows app is Solidworks.  

Are there any linux apps with similar functionality?  thanks.

---

### Post by F0CUS on 2006-06-12
Bump!

I am a 3rd year Mechanica Engineering Student and I am really interested in finding out if there are any SolidWorks comparible apps for Linux out there already?

---

### Post by thematrix on 2006-06-13
PTC pro/engineer, one of the market leaders in the medium-end to high-end solid modeling market (together with CATIA, UGS and SW) and my personal favorite, has a native linux port. It runs flawlessly on debian/ubuntu...
I did extensive testing but our management has a corporate policy to stay on win32 platform for the moment :-(

Cheers,

Frederic

---

### Post by mips on 2006-09-09
There is also BRL-CAD, [http://brlcad.org/](http://brlcad.org/)

---

### Post by hizaguchi on 2006-09-26
The really sad part of this is that even if there was a great open source 3D CAD package, it still wouldn't be compatible with the formats that the mainstream apps use.  The best you could hope for would be to convert everything to .step files, which loses all the construction history and assembly constraints.  That's why CAD is the ultimate in user lock in, because there is no standard format.  It's not like any 3D design software will do.  Your choice is almost always dictated by the file type you have to work with.

Anyhow, it is possible (but not practical) to make models in Blender and 2D drawings in QCAD.  And if you have a ton of money to throw around, Pro/E and CATIA supposedly work in Linux, but I've not had a chance to try myself.

Most Windows CAD apps don't work in Wine/Cedega, and even if they did I would think that managing links would be odd with Unixy directory structure... especially if you wanted to make assemblies that others would be able to view.  And VMWare doesn't have 3D acceleration, so even though you can run Windows in Linux just for CAD it doesn't work very well at all.

The only option I've found to really work is to keep a Windows installation around.  Then you can either dual boot or use coLinux to use Linux, depending on whether you'd prefer to be booting back and forth on a daily basis or just deal with the confusion of having 2 whole systems running at the same time and communicating with ssh and/or samba. ](*,)

---

### Post by Kjell on 2006-11-16
Or FreeShip a excellent ship hull program for boat design in 3D
Its free and must run under wine - without any problems

It can be used for other 3D modeling also 
  
Check it out at [http://www.freeship.org/](http://www.freeship.org/)

//Kjell

---

### Post by mips on 2006-11-17
[http://www.opencascade.org/](http://www.opencascade.org/)  &  [http://www.salome-platform.org/home/presentation/overview/](http://www.salome-platform.org/home/presentation/overview/)

QCad ?

Does CATIA & Solidworks not run on Linux ?

Here is a nice article about Audi's in house cad stuff running almost exclusively on linux,  [http://www.hoise.com/primeur/06/articles/live/LV-PL-06-06-28.html](http://www.hoise.com/primeur/06/articles/live/LV-PL-06-06-28.html)

---

### Post by dan_wrnr on 2007-01-15
Attn: PK_volt
may I recommend Medusa4.o complete mechanical design package for linux which by the way is being offered for linux free for personal use try [http://www.cad-schroer.de/index.php?land=de&ziel=Products-M4Personal&scr=1.3](http://www.cad-schroer.de/index.php?land=de&ziel=Products-M4Personal&scr=1.3)
I hope you can use it as it is very powerful cad package copareable to proengineer
Dan_wrnr

---

### Post by baslin6 on 2007-02-12
> **z_diver said:**
> You can just install the KDE desktop from Synaptic and then you will have all the libraries necessary to run KDE apps.  You are right that you will be able to log into KDE from the login screen but you don't really need to do this.  The program will run as long as it can find the KDE libraries.

This is absolutely correct.  I am a gnomester myself, but am also tied to AutoCAD, Inventor and XP in the office.  :-(

I installed Ubuntu 6.10 on a spare box with the specific intent of testing qcad & VariCAD to see if I can migrate to linux on my production box.  

I, too, couldn't get VariCAD to run "out of the box" (free trial download).  

I searched for answers and found that KDE is required for VariCAD. 

Well, like I said, I'm a gnomester, but I can live with KDE if it means being able to get shed of Windows. So after installing kubuntu-desktop via synaptic, VariCAD ran flawlessly.

I also installed qcad, which isn't bad for a 2d CAD app.  Like anything else, it takes a bit of acclimation, but I think I can live with it.  Anything to get out from under Microsoft and Autodesk! :-)

---

### Post by salariua on 2008-02-23
Right now I am testing ProE under Ubuntu 7.1 AMD64 and I can say I am having a lot of crashes.
Of course I am not a terminal user and I cannot do more than a simple copy/paste of solution found on the web posted by others.

I haven't tried Unigraphix but for the rest I can pretty much say that it's the best I have used till now and I have tried a couple of them (Inventor, SolidEdge, SolidWorks, Catia... and others). I guess it's a matter of personal preference and also a matter of inside needs (company needs). If you want good looks and small jobs then anyone will do but if you don't mind investing other resources (time, training ...) than ProE is well worthy. 

Every once in a while I go to old friends and colleagues and check the other software, but what I see makes me work harder and longer to stick with proe, because it's anyway less time used (and better spent) compared to what they have to pull to get to the same results.

---

### Post by zipperback on 2008-05-29
I use the gnome desktop and there is no problem using varicad. You just need to install the required qt files.

Also varicad and varicad viewer are available in .deb package format so installing it is really easy.

[http://www.varicad.com/en/home/](http://www.varicad.com/en/home/)

Hope this helps you.
- zipperback
:popcorn:

---

