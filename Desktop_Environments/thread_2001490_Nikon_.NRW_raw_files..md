---
title: "Nikon .NRW raw files."
date: 2012-06-11
forum: Desktop Environments
---

### Post by jtappin on 2012-06-11
Under Kubuntu (12.04), Nikon raw format (*.NRW) files are recognized as TIFF files (amd the file header certainly does match that of a TIFF), however most of the default programs to open TIFFs fail (Gwenview, Krita, Kolourpaint...). Gimp opens the files succesfully using the UFraw plugin, which it recognizes that it needs.

My guess is that the file is a non-standard extension of TIFF that causes a normal TIFF reader to fail. However I've not been able to persuade Konqueror that this isn't a normal TIFF by defining a new image type image/x-nikon-nrw with extensions .nrw and .NRW and specifying Gimp as the only program to open them.

Any suggestions? Or is there really  a bug in the display tools (libtiff?) that is preventing the files from opening?

[As the camera will only generate raw files at full resolution, and the resulting files are about 15Mb I'll not attach a specimen unless someone really thinks they need one.]

---

### Post by rag2 on 2012-06-11
1. Nikon, bless them, have made life difficult for us users by inventing _yet another file format that the world does not need_™

1A. The following observations all relate to **Ubuntu 12.04**.

2. **Raw Studio** will** open** **.NRW** files, but there is a **green cast** to the images (and some information on this in the blogs at rawstudio.org).

3. **RawTherapee** will **not open .NRW** files.

4. **DigiKam**, my otherwise favourite picture editor, seems to be **unable to cope** with **.NRW** files, other than to read the embedded JPG image.

5. **Shotwell**, the default photo management system in Ubuntu 12.04 (presumably **not** in Kubuntu) **will** read **.NRW** files, and understands the concept of saving an image as simultaneous RAW & JPG. Alleluia! **However**, it used to have the nasty habit of making an enormous thumbnail repository if one has a sizeable photo library—this issue seems now to be fixed. [COLOR=Blue]**Shotwell**** may well be what one is looking for** (even if it has no k)**.**[/COLOR]

6. **DNG Converter** (part of **kipi-plugins**) will produce **DNG files** from .NRW files that digiKam, Gimp, Raw Studio & RawTherapee can read and process:

[LIST]
[*]This has only been checked with ISO 100 files: there may be colour cast problems at higher ISO ratings
[*]The checks have not been very thorough
[*]The camera specified white balance is probably not getting through DNG Converter—not sure on this
[/LIST]
7. AFAIK everything uses **DCRAW** (a very fine piece of work) to import the NRW files. The default colour matrix for the P7000 used is fine for ISO 100 pictures, but gives a **colour cast** at **higher ISO settings** (certainly did in the past, not been checked recently). This can be corrected, and in principle one could generate a suitable colour matrix to avoid the issue, but that would take a certain amount of time and understanding.

8. The **libgphoto2** version in 12.04 (2.4.13-1ubuntu1) **should** have support for Nikon P7000 & P7100 (from 2.4.12). But note that this is for picture capture, camera control &c. Understanding .NRW file format is not required by libgphoto.

9. **Bibble** (now known as Corel AfterShot Pro) is paid-for software that many photographers have found useful, but I personally have no direct experience of it.

Nothing mentioned so far has any serious problem with Nikon .NEF files, needless to say!

Hope this helps, and thanks for asking the question. Your Q has helped this P7000 owner to get a better handle on his own P7000 raw file workflow!

---

### Post by jtappin on 2012-06-11
Thanks for that list of what does what. I'll try a few and see what works best -- hitherto I've always used the UFraw plugin (which does handle .NRW but is quite tricky as much of the automatic stuff that works with Canon files has to be done by hand) as I was using a Canon DSLR, but recently got a Coolpix P7100 for times when the DSLR is too bulky.

---

### Post by jtappin on 2012-06-11
BTW: It seems that Ubuntu ships with a relatively old dcraw (8.99, current is 9.12).

---

### Post by rag2 on 2012-06-11
> **jtappin said:**
> BTW: It seems that Ubuntu ships with a relatively old dcraw (8.99, current is 9.12).

If you visit [https://bugs.launchpad.net/ubuntu/+source/dcraw/+bug/913833](https://bugs.launchpad.net/ubuntu/+source/dcraw/+bug/913833) and add your name to those of us affected by it, it will be some small help in accreting pressure to get it fixed, and similarly for anyone else reading this (you'll need to register if you've not already done so).

---

### Post by jtappin on 2012-06-11
> **rag2 said:**
> If you visit [https://bugs.launchpad.net/ubuntu/+source/dcraw/+bug/913833](https://bugs.launchpad.net/ubuntu/+source/dcraw/+bug/913833) and add your name to those of us affected by it, 

Done.

I think that Gimp+UFRaw looks like the best option for most purposes, with Shotwell for "quick look". (Now to find some time to collect the White Balance parameters and send them to Udi Fuchs).

---

### Post by eric-yorba on 2012-06-11
> **rag2 said:**
> 1. Nikon, bless them, have made life difficult for us users by inventing _yet another file format that the world does not need_™

You can't really blame Nikon for this.  The one and only standard format for RAW images is called DNG, which stands for "Digital NeGative."  Nobody uses it.

Even if there was a standard RAW format that everyone used, it would need to have a bunch of extensions for camera-specific features, making the benefits of standardization somewhat negligible

---

### Post by rag2 on 2012-06-12
> **eric-yorba said:**
> You can't really blame Nikon for this.  The one and only standard format for RAW images is called DNG, which stands for "Digital NeGative."  Nobody uses it.

Even if there was a standard RAW format that everyone used, it would need to have a bunch of extensions for camera-specific features, making the benefits of standardization somewhat negligible

Could have made 1. a little clearer. There was an existing Nikon raw file format called .NEF format, to which .NRW was added, to make **two** Nikon raw file formats that need to be supported by software supporting raw workflow. (Latest Nikon D800 uses .NEF not .NRW BTW.)

As to the rights & wrongs of DNG *vs* proprietary raw formats, that would be **way** off topic! Leica support DNG (sometimes), Nikon never—so far. The Wikipedia article [http://en.wikipedia.org/wiki/Digital_Negative](http://en.wikipedia.org/wiki/Digital_Negative) seems quite balanced. YMMV, and probably will!

---

