---
title: "Medical imaging and fat area calculating"
date: 2016-10-03
forum: Education &amp; Science
---

### Post by Niklas Baastrup on 2016-10-03
Hi

I am curently working on a project concerning postoperative complications in relation to viscereal fat volume/area measured on CT scans. Therefore i'm in need of a piece of software there can calculate an area of pixels according to a predefined range of hounsfield units. The image will be in DOCOM format

Does anyone have knowledge of a suitable program that runs on Ubuntu?

Sincerely

Niklas Baastrup

---

### Post by steeldriver on 2016-10-03
Hello and welcome to the forums

Although you refer to "area" I'm assuming your end goal is to process 3d CT images (i.e. volume models made up from vertical slices) - if that's the case, I'd suggest starting by seeing if one of the existing 3d segmentation packages will do what you need e.g.

[https://www.slicer.org/slicerWiki/index.php/Documentation/4.5/Announcements#What_is_3D_Slicer](https://www.slicer.org/slicerWiki/index.php/Documentation/4.5/Announcements#What_is_3D_Slicer)

[https://www.slicer.org/slicerWiki/index.php/Documentation/4.1/Modules/GrayscaleModelMaker](https://www.slicer.org/slicerWiki/index.php/Documentation/4.1/Modules/GrayscaleModelMaker)

(I have no direct experience with 3dslicer - but was impressed when I saw it demoed)

---

### Post by Niklas Baastrup on 2016-10-06
Thank you very much for your answer.

I have now tried 3D slicer, and it solves some of my problems.
I am actualle looking for software that can give me areas of different tissue at certain levels as well as automated volume calculation software. 
I have been able to build a model from a single slice in 3D Slicer only marking fatty tissue. My problem here is that i get a volume instead of an area. I assume that it is the volume of a single layer of voxels and therefore i can devide it by height (slice thickness) and hereby calculate the area. But i have no way to test if it actually give me the right result.

---

### Post by steeldriver on 2016-10-06
Sorry I don't know enough to help further - iirc the 3dslicer community is quite active, so you will probably find better help there

OTOH maybe a 3d solution is inappropriate for your application - there are possibly simpler 2d options, even MATLAB might be worth a look

[https://www.mathworks.com/help/images/image-segmentation-using-the-image-segmenter-app.html](https://www.mathworks.com/help/images/image-segmentation-using-the-image-segmenter-app.html)

---

