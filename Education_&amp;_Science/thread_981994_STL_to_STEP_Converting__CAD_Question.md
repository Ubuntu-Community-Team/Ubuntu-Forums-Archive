---
title: "STL to STEP Converting  CAD Question"
date: 2008-11-14
forum: Education &amp; Science
---

### Post by basilwatson on 2008-11-14
Hi all 

I am using Ubuntu 8.04 , with CAE LINUX on a virtual machine , As well as ACAD..  I have been downloading Varicad as they release new versions ,,,

The reason , well I design small parts, not industry leading or F1 but there you go ,,  I use cad to draw the parts in 3d , Blender to give the parts life, in order to show customers , and Calculix  to analyse the parts , ( Gmesh as well as Netgen to mesh the STL files ) 

Now My problem is Cad will import STEP and DXF files but everyone else uses STL or VRML etc files ,,Everything except STEP! 

So I cant keep the same file throughout the process!  ie , Export the file in STL , into blender , make a few changes , oops back to cad in STL then off to Calculix via Netgen ! 

What is the Difference between STEP and STL , any converters out there . and why so many file extension types ..why not ,,,filename.sameaseveryone:confused:


Kind Regards and open to all suggestions 


Stephen

---

### Post by alan34 on 2008-11-14
Hi, see this for a definition of STEP

[http://en.wikipedia.org/wiki/ISO_10303](http://en.wikipedia.org/wiki/ISO_10303)

As you see STEP is a data exchange format for CAD models to ease the transfer between different CAD programs. It will transfer 3D data, dimensions, text etc normally to say 8 or so decimal places.

IGES is another similar data exchange format and DXF for CAD drawings usually to Autocad or similar.

STL or Sterio Lithography stores a CAD model as a series of 3D facets depending on the tolerance in effect when you saved the modal. So in effect it is an approximation of the original CAD model and as such when you load a STL file it will only ever be the series of 3D facets that you saved originally - you cannot exchange exact CAD data with it so no lines, circles, surfaces etc.

So I guess, no there is no exact way of converting STEP to STL or vice versa.

Hope this helps. It is how I understand it anyway.



The reason there are so many different formats is that usually CAD software is proprietary so each vendor will save the files in a unreadable file format, so you need the converters to transfer data - just another way of making more money from their customers.

---

### Post by basilwatson on 2008-11-14
Thank for that good reply
, . would be nice to have a converter , or maybe I will review my process  I know you can render in cad but its not as powerful;l as Blender I think ..

Once again thank you taking the time 

Stephen

---

