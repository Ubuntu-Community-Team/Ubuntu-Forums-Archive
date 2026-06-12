---
title: "Howto: Make a Minolta-QMS PagePro W printer work on Ubuntu 6.10"
date: 2006-08-29
forum: Desktop Environments
---

### Post by coffeejunkie on 2006-08-29
This is a quick howto for get a Minolta-QMS PagePro xxW printer to work on Ubuntu 6.10.  PagePros are low-cost B&W printers.  I have a PagePro 1250W and had trouble getting it to work, but finally managed to make it print.  Hope this is helpful for others.

Many thanks to Manuel Tobias Schiller for some critical hints!

Here's what I did to make it print:

1. Download the handy min12xxw printer driver from [http://www.hinterbergen.de/mala/min12xxw](http://www.hinterbergen.de/mala/min12xxw)

2. Read the INSTALL file in the min12xxw package and follow the steps outlined there.  If you get an error message while compiling, and it looks like this

> tmp/min12xxw-0.0.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C
compiler cannot create executables
See `config.log' for more details.


you may be missing a C runtime library. Use your package manager (Synaptic, for example) to get libglib1.2-dev and/or libglib2.0-dev. (I am not sure which file you need, or if you need both. I got both and the error disappeared.) Try to compile again. Note that you may have to use sudo as prefix for some of the installation commands mentioned in the INSTALL file.

3. Once you've installed min12xxw, you will need to get the PPD files for the printer. min12xxw has a short FAQ text explaining what this is. At any rate, you'll get it at [http://www.linuxprinting.org/show_printer.cgi?recnum=Minolta-PagePro_1250W](http://www.linuxprinting.org/show_printer.cgi?recnum=Minolta-PagePro_1250W) . Save it somewhere you can find it, e.g. on the Desktop.

4. Plug your printer into the USB port. Go to System / Administration / Printing. Click on Printer / Add Printer. Click on "Use Detected Printer" and select your MINOLTA-QMS PagePro. Click "Next" and in the Printer Driver dialog click on "Install Driver" at the bottom. Select the PPD file that you saved earlier.

5. Give the printer a name.

6. That's it!

7. PS: if you want to print two pages on one side of a sheet ("n-up" in the Windows driver language), you can do so from Acrobat Reader. You will need to install gtklp (Synaptic will get it for you; for more info see see [http://gtklp.sourceforge.net/)](http://gtklp.sourceforge.net/)), and then enter the following as printer command in Acrobat's printing menu "/usr/bin/gtklp". That calls gtklp before sending the job to the printer.  gtklp has many options you might find useful.

Anyway this works works for me.  It's a little slow but that might be the printer buffer (?)  Please let me know if anyone has figured out how to increase the speed, or if there are any mistakes in this post.

---

