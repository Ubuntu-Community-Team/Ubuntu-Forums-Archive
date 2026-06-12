---
title: "Japanese font pack for Acrobat 0.7"
date: 2006-02-03
forum: Desktop Environments
---

### Post by Psimon on 2006-02-03
I need to find a Japanese font pack to enable me to read Japanese PDF's. I've tried the Adobe web site and searched in Synaptic but had no luck.

There is a Japanese version of Acrobat but I don't really want my menus to come up in Japanese.

Does anyone know a way around this problem?

---

### Post by CompShrink on 2006-02-16
Go into Synaptic and install xpdf. There's also an xpdf-japanese package, though even without that i could open several japanese pdfs I have with xpdf.

As for adobe's reader, because less face it, Adobe's has a more full and robust implementation, I'm downloading the Japanese font from the official site, and I'll tell you if I get that working.

Edit:
Yes, it does work. But 2 warnings, be careful of these:
1. The install location is not the same as the breezy deb package's install location. When it asks you for the install location, type in:    /usr/lib/Adobe/Acrobat7.0
THIS IS ESSENTIAL OR IT WILL NOT WORK!
2. This has to be run from a path with no spaces in it. /home/USERNAME/JPNKIT should be fine, that's what I used (my username is only 5 letters, so I don't know if it has a character limit as well).

Otherwise, works, I can now open my few test japanese PDFs in Adobe's official reader. Download this at:
[http://www.adobe.com/products/acrobat/acrrasianfontpack.html](http://www.adobe.com/products/acrobat/acrrasianfontpack.html)
Remember, change the OS away from windows, and yes breezy's Adobe reader is 7.0x .

---

### Post by Hiroshima on 2006-05-19
I wanted to do the same thing... but after downloading the file from Adobe's site, I got stuck. (I did get the files into the Adobe folder, and they are untar-ed  I think, but the "no Japanese language support - please install" message still comes up).

Could someone give a step by step how to on what to do with the archived file (or provide a link if it's already written somewhere)

Thank you,

Hiroshima

---

### Post by andyket on 2006-07-26
> **Hiroshima said:**
> 
Could someone give a step by step how to on what to do with the archived file (or provide a link if it's already written somewhere)


I wrote a [step-by-step guide]("https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto") about this on the Ubuntu Wiki. Hope it works.

---

### Post by Hiroshima on 2006-07-29
Thanks for the link and the instructions!  I have run across a problem with acrobat and skim.  I don't know if this is just for Kubuntu, or if skim will not allow acrobat to open in Ubuntu as well.  

Might I suggest a note to that effect on your howto?  It would be a shame to have people do all the setup work installing acrobat and the the Japanese, only to find that acrobat won't open.

I have not tried UIM yet, it worked with acrobat when I used Ubuntu, but havent't tried it in Kubuntu yet.

Cheers,

Hiroshima

---

### Post by Hiroshima on 2006-10-27
One more hint for Newbies (after six months of Ubuntu/Kubuntu I still fit in here)
After downloading the file from Adobe (following the link in CompShrink's post [http://www.adobe.com/products/acrobat/acrrasianfontpack.html](http://www.adobe.com/products/acrobat/acrrasianfontpack.html)

double click on the downloaded file, archive manager will open up.  Extract the files (I just did it to Desktop since this step is temporary).

When it is finished, you will have a folder called JPNKIT. 
This next bit confused me a little, but it seemed to work: Inside the JPNKIT folder, right click the file called INSTALL, and go to _S_crtipts>root-nautilus-here

When the new folder opens (looks just like the one you just left, the INSTALL icon will look different, but double click on it anyways. When the script opens, follow the instructions "y" for yes "accept" for yes, and "/usr/lib/Adobe/Acrobat7.0" for the location.  

That should do!

Of course, following Andyket's wiki [https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto](https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto) will also work if you like using the terminal. (I think this is how I did it in Kubuntu and it worked beautifully) 

Good luck

---

### Post by dfmalh on 2008-05-16
Hi everybody,

I am using Adobe Reader 8.1, and installed via the Package Installer (gdebi-gtk 0.3.8 ) that opens up when I "double click" on the AdobeReader_enu-8.1.2-1.i386.deb file that I downloaded from the Adobe website.

I installed Adobe while I was still using Feisty 7.10, but have sins upgraded to Heron 8.04.

I have to install the Japanese Language Pack: FontPack81_jpn_i486-linux.tar.gz to open some PDF documents.

I tried to install it, but struggled a bit, and this is how I solved the little problem. 

I also tried the How to from this link: [https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto](https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto)  and found it very useful, and def. recommend it!

Here is what happens:

tar -zxvf FontPack81_jpn_i486-linux.tar.gz creates the dir JPNKIT

cd JPNKIT (works)

sudo ./install (does not work, but sudo ./INSTALL does start the Language Kit installation)

I follow the instructions (y), (accept), and are then prompted as to specify the location where I installed the Adobe Reader. The How to says that one should not accept the default "/opt" dir, and that the default location is "/usr/lib". I tried this, went looking for the dirs, and then used : locate /Adobe/Reader8/Resource to actually confirm that in my case the default dir is in fact "/opt". Once I entered that, it was smooth sailing from there...

Installing Common binaries ... 
Done

Installing Common resources ... 
Done

Installing Japanese language resources ... 
Done
Installation completed.


Hope this helps someone! Thanks for the nice How to!

---

