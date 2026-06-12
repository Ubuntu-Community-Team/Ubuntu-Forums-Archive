---
title: "gcrystal ouput size"
date: 2010-09-19
forum: Education &amp; Science
---

### Post by engineer on 2010-09-19
I'm trying to create sideviews of crystal surfaces with different orientations. I.e. a projection of an (100) surface on to the (010) plane. But depending on the orientation, there is a different number of atoms in the image.

This however, seems to change the size of the output, like it would be some magic zoom parameter. I already looked at the files with a text editor, but I can't find anything that would specify the size. Also the atoms don't seem to be centered, depending on if I cleave planes from one end.

Is there a better way to do this? Maybe even some other program?
I would like to avoid exporting to svg and then doing the scaling with an image manipulation program. But obviously it can't be so simple.

I tried both the karmic stable version 0.10.? and the newest stable 0.12.?, which I compiled from the sources. That didn't change anything.

---

### Post by Lateralis on 2010-09-19
I use [VESTA]("http://www.geocities.jp/kmo_mma/crystal/en/vesta.html") for crystal visualisation.  You first begin by specifying the crystall symmetry and place atoms in inequivalent positions. Then you can select the cyrstal orientation, select boundaries (artifically cut the crystal down any given direction), rotate the crystal and finally export an xyz atomic list or images either as bitmaps or raster images (pdf or postscript - ideal for papers).  It can also do other things that I've never played with, but for instance I think it can calculate a powder diffraction spectrum.  

You could also try XCrysDen.  It is strictly a crystal viwer, unlike VESTA, so you will need an xyz list of atomic co-ordinates and species.  But you may prefer the look and feel of exported images.  I don't, but you might. :)

---

### Post by engineer on 2010-09-19
Thanks for the suggestion! I will look into Vesta. Looks a bit more powerfull/complicated though.

---

### Post by Lateralis on 2010-09-19
No worries! 

VESTA is certainly a very powerful program that might take a little while to get used to.  In particular, it seems a little strange at first specifying the atomic positions of atoms for a given crystal symmetry.  But once you know the space group and where inequivalent atoms are relative to the unit cell, you will be up and running in no time. 

As an example, GaAs - a material I am intimately familiar with! - has F-43m space group and has a two atom basis.  Specifiying Ga to be at (0, 0, 0) and As to be at (0.25, 0.25, 0.25) is all you need.  

Hope that helps.

---

### Post by jbrefort on 2010-09-20
In GCrystal, there is a check box at the bottom of the cleavages dialog to avoid the view size change. Hope this helps.

---

