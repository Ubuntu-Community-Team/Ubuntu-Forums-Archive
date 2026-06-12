---
title: "Commercial Engineering Applications For Linux"
date: 2009-07-24
forum: Education &amp; Science
---

### Post by cb951303 on 2009-07-24
This is a list of industrial-grade (known/accepted by companies) commercial engineering applications for linux.
These are the ones that I know that they work in Linux. If I'm missing something please tell me so that I can add.

**Data Acquisition / Analyse**
[LIST]
[*][LabVIEW]("http://www.ni.com/labview/")
[/LIST]
**Numerical Analysis**
[LIST]
[*][Maple]("http://www.maplesoft.com/products/Maple/professional/index.aspx")
[*][Matlab]("http://www.mathworks.com/products/matlab/")
[*][Mathematica]("http://www.wolfram.com/products/mathematica/index.html")
[/LIST]
[B]
CAD[/B]
[LIST]
[*][Unigraphics NX]("http://www.plm.automation.siemens.com/en_us/products/nx/index.shtml")
[*][Eagle]("http://www.cadsoft.de/")
[*][PTC Pro/Engineer]("http://www.ptc.com/products/proengineer/") (Discontinued)
[/LIST]
[B]
Simulation / Engineering Analysis[/B]
[LIST]
[*][Abaqus]("http://www.simulia.com/")
[*][Star-CD]("http://www.cd-adapco.com/products/STAR-CD/index.html")
[*][Comsol Multiphysics]("http://www.comsol.com/")
[*]MSC Software
[Nastran]("http://www.mscsoftware.com/products/msc_nastran.cfm?Q=131&Z=396&Y=422")
[Adams]("http://www.mscsoftware.com/products/adams.cfm?Q=131&Z=396&Y=397")
[Patran]("http://www.mscsoftware.com/products/patran.cfm?Q=131&Z=396&Y=402")
[*]Ansys Workbench
[Multiphysics]("http://www.ansys.com/products/multiphysics/default.asp")
[Structural Mechanics]("http://www.ansys.com/products/structural-mechanics/default.asp")
[Fluid Dynamics]("http://www.ansys.com/products/fluid-dynamics/default.asp")
[Explicit Dynamics]("http://www.ansys.com/products/explicit-dynamics/default.asp")
[Electromagnetics]("http://www.ansys.com/products/electromagnetics/default.asp")
[/LIST]
**Less Known / Good Quality Products**
[LIST]
[*][Varicad:]("http://www.varicad.com/en/home/") This is a cheap mechanical CAD application with 2D/3D capabilities that supports STEP, STL, IGES, DWG and DXF formats. It's very stable, small in size and works really fast compared to the big brothers such as SolidWorks, UGS NX etc. Perfect for small-to-medium sized companies.
[/LIST]

---

### Post by XCan on 2009-07-24
Simulation (FEM): Comsol Multiphysics, previously known as FEMLAB as a plugin fro Matlab.

---

### Post by cb951303 on 2009-07-24
updated.

---

### Post by hambone79 on 2009-07-25
PTC Pro/Engineer Wildfire 2 and 3 are still available for Linux. I'm currently using Wildfire 2 on my Ubuntu box for contract work.

---

### Post by cb951303 on 2009-07-25
> **hambone79 said:**
> PTC Pro/Engineer Wildfire 2 and 3 are still available for Linux. I'm currently using Wildfire 2 on my Ubuntu box for contract work.

added. it's a shame they stopped supporting linux. I would prefer it over UGS NX.

---

### Post by Chronon on 2009-07-28
LabVIEW.

---

### Post by cb951303 on 2009-07-28
Updated. I once used it back in school for MSA (Measurement Systems Analysis) course. It's a great product.

---

### Post by XCan on 2009-07-28
> **cb951303 said:**
> Updated. I once used it back in school for MSA (Measurement Systems Analysis) course. It's a great product.

Yeah... Except the 'code' always becomes a total mess if you write a larger project. :p

---

### Post by in_flu_ence on 2009-07-28
How about Star-cd?
[http://www.cd-adapco.com/press_room/dynamics/23/linux.html](http://www.cd-adapco.com/press_room/dynamics/23/linux.html)

---

### Post by cb951303 on 2009-07-28
> **in_flu_ence said:**
> How about Star-cd?
[http://www.cd-adapco.com/press_room/dynamics/23/linux.html](http://www.cd-adapco.com/press_room/dynamics/23/linux.html)

Added, to the "well known" list but I actually don't know this product. Do any big companies use this CFD?

---

### Post by thelaughingbuddha on 2009-07-28
**SCILAB** is a MATLAB like program for numeric computations. It is free software and the leaflet from their site states that it has 250,000 plus installed seats worldwide. It is said to be very powerful.

[http://www.scilab.org/platform/](http://www.scilab.org/platform/)

Personally, I don't know whether it is commercially used or not since I am not into that field. :)

---

### Post by cb951303 on 2009-07-28
> **thelaughingbuddha said:**
> **SCILAB** is a MATLAB like program for numeric computations. It is free software and the leaflet from their site states that it has 250,000 plus installed seats worldwide. It is said to be very powerful.

[http://www.scilab.org/platform/](http://www.scilab.org/platform/)

Personally, I don't know whether it is commercially used or not since I am not into that field. :)

Yeah I know about open source alternatives. But this list is about mass acceptance rather than quality of the products (although most of them are really great products.) Think of it this way, this is the list of applications that would matter, if their name was written on your CV.

---

### Post by in_flu_ence on 2009-07-28
> **cb951303 said:**
> Added, to the "well known" list but I actually don't know this product. Do any big companies use this CFD?

It is actually used in some big companies. Some academic insitutions use them as well.

[http://www.redhat.com/videos/customers_cdadapco.html](http://www.redhat.com/videos/customers_cdadapco.html)

I guess they are fairly into Linux.

---

### Post by Xnst on 2009-08-03
For FE-simulations:

ABAQUS works very well on linux.  I currently use it myself.

---

### Post by Chronon on 2009-08-03
> **XCan said:**
> Yeah... Except the 'code' always becomes a total mess if you write a larger project. :p

I admit I have only used LabVIEW for modest sized applications (i.e. managing tabletop experiments involving communication with handfuls of instruments).  I could see how streamlining communication with hundreds or thousands of devices could become troublesome (especially if this needs to be done synchronously).  On the other hand, I have never found an easier method to initiate communication with instruments using so many different protocols.

---

### Post by cb951303 on 2009-08-03
> **Xnst said:**
> For FE-simulations:

ABAQUS works very well on linux.  I currently use it myself.

How did I missed that :) added.

---

### Post by abloxom on 2009-09-03
We run CD-Adapco's STAR-CCM+ on Scientific in my office at Virginia Tech. I just talked with one of the developers at a conference in LA this week and he's going to give me instructions for an install on Ubuntu 8.04.

---

### Post by mikgol on 2010-10-20
If your after estimating software you could use web browser based software such as [http://www.UltraBOQ.com.au](http://www.UltraBOQ.com.au).

Cheers,
Michael

---

### Post by Silentvoice on 2010-10-21
Mathematica and maple I think should go under CAS (computer algebra system). Their focus is not numerical computations. While they can do them, it's not the goal of those products.

---

