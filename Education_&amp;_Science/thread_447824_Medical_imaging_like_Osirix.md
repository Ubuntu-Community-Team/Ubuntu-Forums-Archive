---
title: "Medical imaging like Osirix"
date: 2007-05-18
forum: Education &amp; Science
---

### Post by Domie on 2007-05-18
Hello,


This is probably a long shot, but I wondered if someone knows a tool in Linux that can do medical imaging in Linux? I found something on the Mac, Osirix: [http://homepage.mac.com/rossetantoine/osirix/Index2.html](http://homepage.mac.com/rossetantoine/osirix/Index2.html)

This seems open source, but there's no Linux adaptation.

For reasons not worth stating here (you all know them), I'd prefer to run medical software on Linux in stead of Windows. After a long search I finally found Linux administrative tools for the branch I'm in, but the imaging is a cornerstone of my profession...

Oh, and in case if your wondering, I'm prepared to pay for it, it hasn't to be "free" ;-)

---

### Post by Domie on 2007-05-19
For instance...

Can I compile this Mac open source project myself in Linux? That would a good start...

---

### Post by diceratops on 2007-05-21
I use 3D Slicer - [www.slicer.org](www.slicer.org). It has readily-available Linux binaries (for free), is under active development, and has quite a few very nice features. I'm not sure exactly what you need to do with your images, but I've found Slicer to be a great program for visualization, segmentation, measurement, and 3D reconstruction.

For simple viewing of DICOM files, I recommend ImageJ (with its associated DICOM reader plug-ins).

Good luck,

Andy

---

### Post by UbuWu on 2007-05-23
None of them as good as osirix, but some DICOM image viewers good enough for viewing e.g. simple x-ray images:

* [Aeskulap]("http://www.nongnu.org/aeskulap/")
* [Kradview]("http://www.orcero.org/irbis/kradview/")
* [openDICOM.NET]("http://opendicom.sourceforge.net/")

---

### Post by Domie on 2007-05-25
Thanks for the links...

Silly question perhaps, but do these programs provide hardware support for medical imaging devices like this:

[http://www.jmorita-mfg.com/download/en/Veraview_IC5.pdf](http://www.jmorita-mfg.com/download/en/Veraview_IC5.pdf)

---

### Post by UbuWu on 2007-05-27
> **Domie said:**
> 
Silly question perhaps, but do these programs provide hardware support for medical imaging devices like this:


They don''t support any hardware directly, but medical imaging hardware and software is pretty much standardized on the DICOM format, so it probably should work if you can connect the two somehow.

---

### Post by Domie on 2008-05-10
> **UbuWu said:**
> They don''t support any hardware directly, but medical imaging hardware and software is pretty much standardized on the DICOM format, so it probably should work if you can connect the two somehow.


That's a shame...

Meanwhile, I have called and emailed to different suppliers (Kodak, J. Morita,...), but none gave a positive response.

Now, I am considering installing two PC's in my practice room: one for the records of my patients and one for the image database (including drivers).

That's a shame, because I still need Windows and two PC's.

What do you think of this idea?

---

### Post by orion114 on 2008-05-15
Our Kodak Panorex uses a .pano extension on the file names, but they are actually DICOM files that have been renamed.
You could probably use something like Conquest Dicom server to store your medical images. 
The problem with dental equipment is that they appear to come without any DICOM send/recieve facilities built in, so what you can do is write an script to copy the files to a shared folder on the conquest server and then just get conquest to re-initialise its image database every now and then.

I know conquest runs on Linux, but I have no experience in setting it up on linux but there is source available: [www.xs4all.nl/~ingenium/dicom.html](www.xs4all.nl/~ingenium/dicom.html)

Otherwise you can look at something like clearcanvas or k-pacs on windows. They however don't have 3D functionality, but for panorex images its not important.

---

### Post by Domie on 2008-05-15
> **orion114 said:**
> Our Kodak Panorex uses a .pano extension on the file names, but they are actually DICOM files that have been renamed.
You could probably use something like Conquest Dicom server to store your medical images. 
The problem with dental equipment is that they appear to come without any DICOM send/recieve facilities built in, so what you can do is write an script to copy the files to a shared folder on the conquest server and then just get conquest to re-initialise its image database every now and then.

I know conquest runs on Linux, but I have no experience in setting it up on linux but there is source available: [www.xs4all.nl/~ingenium/dicom.html](www.xs4all.nl/~ingenium/dicom.html)

Otherwise you can look at something like clearcanvas or k-pacs on windows. They however don't have 3D functionality, but for panorex images its not important.

Thanks, I'll check it out!!!

---

### Post by Oscar Pradilla on 2008-07-13
can anyone please compile this to run in ubuntu... i have no idea how to do it, but we need it...best DICOM and PACS software for clinical practice ever...

[http://www.osirix-viewer.com/]("http://www.osirix-viewer.com/")


Thanks...

---

### Post by hanzj on 2008-07-19
Gimp opens my DICOM images (xray).
I love GIMP!!!

---

### Post by raddoc on 2008-08-09
There might be something useful here.

[http://www.sim.hcuge.ch/uin/01_Presentation_EN.htm](http://www.sim.hcuge.ch/uin/01_Presentation_EN.htm)

---

### Post by blecha on 2012-02-07
You can download MeVisLab2.2.1 (1.3 Gb). It reads most of the formats (I am using it with DICOM format data pre-processed by Osirix). Easy to use, though you must spend some time to understand the modular philosophy. It's free for private usage.

[http://www.mevislab.de/](http://www.mevislab.de/)

Good luck

---

### Post by nothingspecial on 2012-02-07
Please don't bump old threads to the top.

Closed.

---

