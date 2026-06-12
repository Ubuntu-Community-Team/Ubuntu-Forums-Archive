---
title: "Leaving Linux for digital photography?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by abstauber on 2006-07-20
Dear Community,
I urgently need your help, because I feel like I need to leave linux soon. But let me explain.

I'm with Linux since Redhat 7.3 and tried a lot of distributions until Ubuntu was founded. So far so good… 
A hobby of mine (a quite new one) is digital photography and that's the reason why I'm forced to boot into Windows more than I'd like to. 

1. Monitor Calibration
Is there any hardware solution with linux support out there (haven't found one).
If not, does anyone have a good software solution? Is there a chance to use ICC profiles as well?

2. Printing & Scanning
I chose an Epson model because of it's good linux support (I used to believe that), but it doesn't print at all right now, although beeing detected in Cups. 
It's an all-in-one Epson RX 640.. the only available drivers are for a 630… might that be the problem? 

Scanning also doesn't work and the Sane-frontend only detects my tv card ;)
Before that I had a HP 990 cxi with a terrible printing quality under Cups (and great quality in that other OS).. but at least I could print.

3. Image Processing
At least here I'm satisfied :) Photoshop and Neatimage are working well with wine and DigiKam is also suitable for archivation (allthough it crashes quite often when using labels).

Now I'm considering buying a Mac in order to avoid windows ;) 

Or is there a chance to get linux photo-ready? Are there amateur-photgraphers out there using linux?

---

### Post by gerscht on 2006-07-20
> **abstauber said:**
> DigiKam is also suitable for archivation (allthough it crashes quite often when using labels).

try f-spot ([http://f-spot.org/]("http://f-spot.org/")). the search functionality is not quite as good as in digikam, but it runs very fast and stable. 
They're also working in the CSV version on the option to write the keywords in the file (in an EXIF like standard, I forgot the name... :-k ), which in my opinion is quite important as you don't have to rely on a specific program.

---

### Post by philippe_carlo on 2006-07-20
Getting nice printing results in Linux depends on the driver. [Here]("http://www.linuxprinting.org/suggested.html"), I read that using the [Gimp Print Driver]("http://www.linuxprinting.org/show_driver.cgi?driver=Gimp-Print") for epson printers is supposed to give nice results.

---

### Post by abstauber on 2006-07-21
Thanks for your replies. Just to mention, printing is not the biggest problem here ;) 
I already tried gutenprint without pleasing results... maybe having a RX640 instead of the RX630 is the problem, as I only get white pages. 
Well my bigger concern is colormanagement... since I haven't read anything about it or hobby photographers using linux.

---

### Post by gerscht on 2006-07-21
Me again :D 
> **abstauber said:**
>  Is there a chance to use ICC profiles as well?
At least scribus (a DTP program) uses ICC profiles. Have a look [here]("http://docs.scribus.net/index.php?lang=en&page=cms"), it describes the use of ICC in scribus, but perhaps it's transferable to other applications as well. ([http://docs.scribus.net/index.php?lang=en&page=cms]("http://docs.scribus.net/index.php?lang=en&page=cms"))

---

### Post by chele on 2006-07-28
You might consider getting a dedicated photo printer, rather then a general all-in-one device, one that is known to be well supported using gutenprint.

[http://gutenprint.sourceforge.net/p_Supported_Printers.php3](http://gutenprint.sourceforge.net/p_Supported_Printers.php3)

Cheaper then moving to OS X, and freer as well!

---

