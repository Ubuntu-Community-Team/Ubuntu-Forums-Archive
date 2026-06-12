---
title: "Rename photographs according to tag"
date: 2009-04-24
forum: General Help
---

### Post by GabrielWolff on 2009-04-24
My camera has lately had issues naming different pictures the same name, hence making it really difficult to save them on my HDD.

I would like to rename all pictures (a few thousands) to the following:

DATE-TIME.jpg.
or
DATE/DATE-TIME.jpg

The info is in the photos' tag.

Is there any good, simple way of doing this. I'm not afraid of command line solutions. In fact, I prefer them.

---

### Post by _Purple_ on 2009-04-24
You can try renrot. Its in the repos.

---

### Post by GabrielWolff on 2009-04-24
> **_Purple_ said:**
> You can try renrot. Its in the repos.

Worked perfectly.
Thanks :)

---

### Post by _Purple_ on 2009-04-24
> **GabrielWolff said:**
> Worked perfectly.
Thanks :)

Glad to know it helped. :)

---

### Post by GabrielWolff on 2009-05-05
I tried to refine the renaming. 
I want all the pictures be named according to the date and time in their tags, plus, I want them to be put in directories according to their date.

When I type in:```
renrot "%Y, %m"/%Y%m%d%H%M%S.jpg *.JPG
``` the files are renamed just OK, but no directories are created. 

How come?
I try to read the man pages ([http://linux.die.net/man/1/renrot](http://linux.die.net/man/1/renrot)), but the info there seems to be wrong. When I use the command suggested there, I get no directories neither...

Help?

Edit: OK, I'm confused. I crippled the command step by step until I was typing in ```
renrot *.JPG
``` only - and I still got the same results...?!??

---

### Post by _Purple_ on 2009-05-05
The syntax is 
```
renrot --aggr-mode template --aggr-template %Y%m  --extension jpg

```

This will create the folders %Y%m and save the pictures with .jpg extension as %Y%m%d%H%M%S.jpg in the folders.

---

### Post by GabrielWolff on 2009-05-10
> **_Purple_ said:**
> The syntax is 
```
renrot --aggr-mode template --aggr-template %Y%m  --extension jpg

```

This will create the folders %Y%m and save the pictures with .jpg extension as %Y%m%d%H%M%S.jpg in the folders.

Works like a charm.
Thanks!! :)
Only thing is: it doesn't rotate the images. I looked in the man pages and it seems like other than if you give a certain command, it should rotate the images according to the info in the EXIF.

However, my images don't get rotated.

Any clue why?

---

### Post by _Purple_ on 2009-05-10
Did you check if the Orientation EXIF tag is set properly?

---

### Post by GabrielWolff on 2009-05-11
> **_Purple_ said:**
> Did you check if the Orientation EXIF tag is set properly?

Seems so. Look at the "orientation line"

```
gabriel@gabriel-laptop:/media/disk/DCIM/118_FUJI$ exif DSCF8341.JPG 
EXIF tags in 'DSCF8341.JPG' ('Intel' byte order):
--------------------+----------------------------------------------------------
Tag                 |Value                                                     
--------------------+----------------------------------------------------------
Manufacturer        |FUJIFILM                                                  
Model               |FinePix S5700 S700                                        
Orientation         |top - left                                                
x-Resolution        |72.00                                                     
y-Resolution        |72.00                                                     
Resolution Unit     |Inch                                                      
Software            |Digital Camera FinePix S5700 S700 Ver1.00                 
Date and Time       |2009:05:11 09:52:30                                       
YCbCr Positioning   |co-sited                                                  
Copyright           |[None] (Photographer) -  (Editor)                         
Unknown             |                                                          
Compression         |JPEG compression                                          
Orientation         |top - left                                                
x-Resolution        |72.00                                                     
y-Resolution        |72.00                                                     
Resolution Unit     |Inch                                                      
YCbCr Positioning   |co-sited                                                  
Exposure Time       |1/51 sec.                                                 
FNumber             |f/3.5                                                     
ExposureProgram     |Normal program                                            
ISO Speed Ratings   |400                                                       
Exif Version        |Exif Version 2.2                                          
Date and Time (origi|2009:05:11 09:52:30                                       
Date and Time (digit|2009:05:11 09:52:30                                       
ComponentsConfigurat|Y Cb Cr -                                                 
Compressed Bits per |4.00                                                      
Shutter speed       |5.70 EV (APEX: 7, 1/51 sec.)                              
Aperture            |3.60 EV (f/3.5)                                           
Brightness          |2.30 EV (16.87 cd/m^2)                                    
Exposure Bias       |0.00 EV                                                   
MaxApertureValue    |3.60 EV (f/3.5)                                           
Metering Mode       |Pattern                                                   
Light Source        |0                                                         
Flash               |Flash did not fire, compulsory flash mode.                
Focal Length        |6.3 mm                                                    
Maker Note          |1854 bytes unknown data                                   
FlashPixVersion     |FlashPix Version 1.0                                      
Color Space         |sRGB                                                      
PixelXDimension     |3072                                                      
PixelYDimension     |2304                                                      
Focal Plane x-Resolu|5376.00                                                   
Focal Plane y-Resolu|5376.00                                                   
Focal Plane Resoluti|Centimeter                                                
Sensing Method      |One-chip color area sensor                                
File Source         |DSC                                                       
Scene Type          |1                                                         
Custom Rendered     |Custom process                                            
Exposure Mode       |Auto exposure                                             
White Balance       |Auto white balance                                        
Scene Capture Type  |Standard                                                  
Sharpness           |Normal                                                    
Subject Distance Ran|Unknown                                                   
InteroperabilityInde|R98                                                       
InteroperabilityVers|0100                                                      
--------------------+--------------------------------------------------------
```--

---

### Post by _Purple_ on 2009-05-11
I tried too and rotation does not work for me either. Yes, according to the man page, it rotates based on the EXIF orientation tag. I am not sure if I am missing something.

---

### Post by stani on 2009-06-27
The new version of Phatch can batch rename your pictures to tags  and rotate lossless (!) jpeg pictures with the "Lossless JPEG" action. Please try it first with a copy of one your pictures and let me know if it works for you. 

BTW Phatch has a nice graphical user interface.

See [http://ubuntuforums.org/showthread.php?t=1178224](http://ubuntuforums.org/showthread.php?t=1178224)

---

