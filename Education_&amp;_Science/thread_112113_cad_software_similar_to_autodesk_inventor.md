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

### Post by shreko on 2006-01-03
There is an IntelliCAD from bricscad.com, which is fully compatible AutoCAD software recently ported or maybe run under wine to linux. I was not able to get it running. I think they focus on redhat and suse compatibility.

I also know of varicad from varicad.com, 2d/3d mechanical design software. I think they even have .deb as download which I tried to install, but failed. I think there was dependency on some Qt libraries in my case.

---

### Post by Peter76 on 2006-01-03
I don't know inventor, but for my cad needs I use qcad. Install it through synaptic or
sudo apt-get install qcad.
Good luck

---

### Post by pk_volt on 2006-01-03
sorry for the double post.

But yea, all of the mentioned cad softwares are 2d.  I want a 3d cad software that can simulate motion and assemble parts.

thanks!

---

### Post by Kjell on 2006-01-06
Hej,

I did install KDE and tried installing both varicad & bricscad.

bricscad appears not to work on a debian based system.

Varicad still are missing the *libqt3c102-mt*

I've been googlin for libqt3c102-mt and apparently it is not compatible with KDE 3.4 
There is a simular package, libqt3-mt, but this does not work with Varicad

Any other ideas how to get Varicad working ?

//Kjell

---

### Post by Peter76 on 2006-01-06
did you try linking libqtr-mt to libqt3c102-mt? This is often a problem..
good luck

---

### Post by Kjell on 2006-01-06
Hej,

How do I link libqtr-mt to libqt3c102-mt ? 

//Kjell

---

### Post by Peter76 on 2006-01-07
[QUOTE=Kjell]Hej,

How do I link libqtr-mt to libqt3c102-mt ? 

//Kjell[/QUOTE]

From the directory where is your libqt:

sudo ln -s libqt3-mt libqt3c102-mt

The name is probably libqt3-mt.so, so you have to add the .so in the above command to bovth libs

---

### Post by Jammy_Stuff on 2006-01-07
[QUOTE=Peter76]I don't know inventor, but for my cad needs I use qcad. Install it through synaptic or
sudo apt-get install qcad.
Good luck[/QUOTE]

Is it in the Universe?

---

### Post by Peter76 on 2006-01-07
[QUOTE=Jammy_Stuff]Is it in the Universe?[/QUOTE]

Yes, or maybe multiverse

---

### Post by Hatchetfish on 2006-02-06
No idea about your budget, but [Pro Engineer]("http://www.ptc.com/appserver/mkt/products/home.jsp?k=403") blows Inventor away.  Then there's [CATIA]("http://www.3ds.com/products-solutions/plm-solutions/catia/overview/") if you're Boeing.

---

### Post by robertrej on 2007-02-06
I downloaded varicad   debian version to ubuntu  gnome and it works very well ,I tried
to  install on ubuntu KDE and varicad would not work at all.I have tried to install Bricscad
linux on many different linux Distros and had no success  well actually last time I created
a debian format from RPM using alien but after install was complete I could not start
the program so I will continue to search for a way !    keep ya posted.


                                                                                           Good day
                                                                                             Bob










> **Kjell said:**
> Hej,

I did install KDE and tried installing both varicad & bricscad.

bricscad appears not to work on a debian based system.

Varicad still are missing the *libqt3c102-mt*

I've been googlin for libqt3c102-mt and apparently it is not compatible with KDE 3.4 
There is a simular package, libqt3-mt, but this does not work with Varicad

Any other ideas how to get Varicad working ?

//Kjell

---

### Post by francisco.colaco on 2007-02-09
Pleas install libqt3-mt.

Varicad works well here.  It is just a pity is has no python scripting, or I would reactivate my subscription at the moment.

---

### Post by Gimikk on 2007-06-09
I want to ask, is VariCAD free (as beer) on Ubuntu Linux?

---

