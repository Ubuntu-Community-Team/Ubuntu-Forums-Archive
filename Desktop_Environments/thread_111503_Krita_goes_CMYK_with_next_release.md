---
title: "Krita goes CMYK with next release"
date: 2006-01-02
forum: Desktop Environments
---

### Post by branco on 2006-01-02
Here's a quote from the Changelog:

> * I created a klik image of a Krita developer snapshot you can try. This snapshot includes 16 bit/channel and cmyk, among other things.
 
 * Krita is now part of the regular KOffice releases with the 1.4 release coming up. The binary snapshot I formerly linked to is very obsolete by now.
 
 * This is the second binary snapshot. We've added image restauration using CImg and Greycstoration, polygon and polyline tools, profile loading and more stuff that I've forgotten...
 
 * This is the first binary release. This version should run on most Linux systems with KDE 3.3.2 or better. There's some manual configuration needed. I would very much appreciate if people mailed me success & failure stories so I can see how this works. I'd appreciate it even more if people could help out with making better binary snapshot packages.

I've already checked out the current version from the Ubuntu repos 1.4.1. It's much like The GIMP but the interface reminds me Photoshop a bit. The look and feel is great, although some tools are still a bit awkward (like the Brush tool not showing a radius-sized circle).

For those, who don't know what this is about, take a look at:

[http://www.kde-apps.org/content/show.php?content=16550](http://www.kde-apps.org/content/show.php?content=16550)

And a little noob question: How do I get and install the development snapshot? :D

---

### Post by Sirin on 2006-03-23
I wonder... Will GIMP become competition with Krita? Krita has CMYK, GIMP does not. "Who will dominate the Linux graphic design world? Krita, or the GIMP? Only time will tell." :twisted:

---

### Post by mips on 2006-03-23
[QUOTE=Sirin]"Who will dominate the Linux graphic design world? Krita, or the GIMP? Only time will tell." :twisted:[/QUOTE]

None of the above.

CinePaint Glasgow is gonna wipe the floor with them and give Photoshop a good run for it's money....

[http://www.cinepaint.org/](http://www.cinepaint.org/)

---

### Post by branco on 2006-03-24
> CinePaint Glasgow is gonna wipe the floor with them and give Photoshop a good run for it's money....

I don't think OSS graphic software will ever be a match for Adobe's money-making machinery. It's a different way of thinking. I get a lot of criticism for trying to use OSS for graphic design. People want to be sure it works and they'd pay a lot of money for that (not that it's really any insurance). Free software requires of you to think differently.

Krita's CMYK support was quite buggy when it was finally implemented (at least on Ubuntu)... Well, I was hoping for much better results, especially knowing that Krita supports color managment and OpenGL rendering of images.

As far as Krita vs the GIMP goes, I don't think they are evenly matched. The GIMP is much closer to Photoshop, while Krita is a painting program (like Corel Painter). I think they can be both used for the same project (I was hoping I could use GIMP to work on images, and then convert to CMYK using Krita).

As for CinePaint, it's main target is the movie industry. I think I'm not even going to give it a go. To much firepower for my modest needs. ;)

> CinePaint is fundamentally different from other painting tools because it handles high fidelity image formats such as Kodak Cineon, SMPTE DPX, and ILM/NVIDIA OpenEXR. To do that properly requires a 32-bit per channel color core so that data isn't crushed into an 8-bit color channel. The CinePaint core is 8-bit, 16-bit, and 32-bit as needed.

---

### Post by f1dave on 2006-03-24
Funnily enough, I showed Cinepaint to a photographer friend of mine. He cried something about RAW editing, no price tag and somesuch, then proceeded to drool for a while...

---

### Post by mips on 2006-03-25
The major problem with the GIMP is that it only has 8-bit support. People who want to edit 16-bit files (RAW etc) are buggered. This is one of the areas where the GIMP cannot compete with  Photoshop.

Cinepaint on the other hand does not have this limitation as they support 16 & 32bit. Glasgow will support 64-bit images.

Cinepaint targets both the movie industry and the pro photo/image editor.

The problem with OSS seems to be companies want some form of support/backup. IBM has the right idea here. They will promote a oss product and provide consultancy/support for it. The other thing is when something is free you think it cannot be as good as a $400 product.

There are a lot of big studios (Sony etc) out there using CinePaint. The majority of render farms run on linux. Things are slowly changing.

---

### Post by mips on 2006-03-25
[QUOTE=f1dave]Funnily enough, I showed Cinepaint to a photographer friend of mine. He cried something about RAW editing, no price tag and somesuch, then proceeded to drool for a while...[/QUOTE]

Tell your friend to look again towards the end of the month as that is when the release is suppose to happen for Glasgow

---

