---
title: "error creating image"
date: 2008-12-12
forum: General Help
---

### Post by mmm14850 on 2008-12-12
hello all.  i'm attempting to create a png image from TeX syntax using the tex2png tool ([http://www-cdf.fnal.gov/~cplager/latex/](http://www-cdf.fnal.gov/~cplager/latex/)).  I was running into a different error before, but downloading more appropriate Perl modules solved it.  However, now I am having issues with the actual image creation and ghostscript writer.  I've attached my error from command line below.  

Has anyone experienced anything like this before?  Any help is much appreciated.  :guitar:  Thanks

administrator@administrator-desktop:~/Desktop$ ./tex2png.pl -output theimage
Please enter text, finished by <ctrl>-D on a blank line.
{\mathcal B}(t\bar{t} \rightarrow W b Z c) = 
\frac{ N_\mathrm{candidates} - N_\mathrm{background} }
{{\mathcal A} \cdot \int {\mathcal L} dt \cdot \sigma_{t \bar{t}}}

Thank you.
Use of uninitialized value in split at ./tex2png.pl line 329, <> line 3.
Latex compilation successful. Creating 'png' file.


GPL Ghostscript 8.61: Unrecoverable error, exit code 1
pnmcrop: bad magic number - not a ppm, pgm, or pbm file
pnmcat: EOF / read error reading magic number
pnmcat: EOF / read error reading magic number
pnmdepth: EOF / read error reading magic number
ppmquant: EOF / read error reading magic number
pnmtopng: EOF / read error reading magic number
pnmfile: bad magic number - not a ppm, pgm, or pbm file
tex2png_temp5837_theimage.png does not have a valid png signature.  Aborting embedding

---

### Post by ibuclaw on 2008-12-12
1) Are you sure that what you input to the program is correct?

2) Where did you get the app from?

Regards
Iain

---

### Post by mmm14850 on 2008-12-12
I got the app from the site that same site I linked above: [http://www-cdf.fnal.gov/~cplager/latex/#png](http://www-cdf.fnal.gov/~cplager/latex/#png)

I assume my input to the program was correct, since I follow the below example (copied from the site above).  After making the first call to console, it asked for more input and I followed the directions exactly, so I assume it is not an input problem.

***EXAMPLE FROM LINKED SITE***

You can download the script tex2png.pl and run it from your computer (see the software requirements below). It is installed on the /cdf/home/ area on the CDF linux computers as /cdf/home/cplager/bin/tex2png.pl. This script not only makes a .png file, but also embeds the latex source code in the output file so images can easily be updated.

For example (text I typed in brown):

cplager@Fcdflnx4> ~cplager/bin/tex2png.pl -output broneside
Please enter text, finished by <ctrl>-D on a blank line.
{\mathcal B}(t\bar{t} \rightarrow W b Z c) = 
\frac{ N_\mathrm{candidates} - N_\mathrm{background} }
{{\mathcal A} \cdot \int {\mathcal L} dt \cdot \sigma_{t \bar{t}}}

Thank you.
<img src="broneside.png" width="367" height="69">

******

---

### Post by ibuclaw on 2008-12-12
Thanks for that.

I believe this is your solution:
```
sudo apt-get install netpbm
```
Here is the output I get:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96160&stc=1&d=1229112102[/IMG]

Regards
Iain

---

### Post by mmm14850 on 2008-12-12
hmm...i still get the same error, despite calling both 

sudo apt-get install libcompress-zlib-perl
and
sudo apt-get install netpbm

i followed the example exactly, typing in that syntax, skipping a line, and and pressing ctrl+d. im relatively new to linux, and i have a fresh ubuntu VM running on VMware Server.  possible that i am missing more packages that i might need?  that your workstation already has?

---

### Post by mmm14850 on 2008-12-12
AHA!  Problem solved.  I needed to run > sudo apt-get install texlive as well.  

thanks for your help tinivole.

---

