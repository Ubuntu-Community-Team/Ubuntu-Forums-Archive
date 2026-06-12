---
title: "Xsane tiff format bad"
date: 2009-02-26
forum: General Help
---

### Post by 73ckn797 on 2009-02-26
[SIZE=3]**Solved the problem. Changed save format to JPG. Same size and compatible across platforms.**[/SIZE]

Today I discovered that all of the documents I have been scanning via Xsane and saving in the "tiff" format can only be viewed within Ubuntu using "Eye of Gnome" or GIMP. I had to send several pages I scanned to someone else. They could not open them. When I went to my Windows XP and tried to view them there was no program that would read them. They displayed a message as an unknown format. I can save them as a PDF and no problem but the file size is almost double than the tiff format. I have scanned from Windows using the HP scan program and they save as "tif" and can be viewed using any program that is available and supports the "tif" format.

Is there any other scanning program that will save in the "tif" and not "tiff"? If not then I will have to go back to WIndows to do my work. I really do not desire to do that. I prefer to do all of my computing on one platform. Would this be my farewell to Ubuntu? Maybe not but I need cross platform compatibility to share work documents.

I will be looking around the repos. Suggestions welcome.

I tried another scanning program from the repos called "Flegita". It works but file size is very large also. I found that if I use a different compression for the scanned file that it will open in Windows. but the file size is 3.6mb. I figure that I will scan in PDF format and take a file size approx. double (650kb for PDF) and maintain cross compatibility.

Anyone else had to deal with a similar issue with scanned documents?

---

### Post by kaibob on 2009-02-27
I'm not an expert on this, but no one else has responded, so I thought I would pass along what I know.

The TIFF image format, which is the same as the TIF format, has many variations and compatibility issues are common. This is commented on by a knowledgeable individual as follows:

> TIFF. This is the Image interchange format that was developed to transfer high quality images between programs before any serious image formats were available. Unfortunately, because of this beginning, the format has been modified with a haphazard array of features and compression styles and no programs understands them all. 

[http://www.imagemagick.org/Usage/formats/](http://www.imagemagick.org/Usage/formats/)

The following link includes some modifications that could be implemented with the Imagemagick convert utility, and these may make your TIFF files readable by other applications. However, looking forward, this may be more trouble than it's worth.

[http://www.imagemagick.org/Usage/formats/#tiff](http://www.imagemagick.org/Usage/formats/#tiff)

I primarily scan documents, and PDF format works great for this. To scan graphics, I would use PNG format. It has almost all of the benefits of TIFF, achieves the same degree of compressions, and in my experience is very compatible.

BTW, after writing the above, I noticed that you decided to use the JPG file format and had marked this thread as solved. I'll go ahead and post rather than delete this message for whatever it's worth.

---

### Post by 73ckn797 on 2009-02-27
Hey thanks for the input. After playing around the JPG would work and not be a large file size. I was using the Xsane defaults for their image format choices. Changing the compression did allow compatibility but, as mentioned, made for a very large file size.

If anything, someone reading this may benefit from this information.

---

