---
title: "Epson head cleaner and other printer tools?"
date: 2007-08-02
forum: Desktop Environments
---

### Post by wkulecz on 2007-08-02
Are epson printer tools available for Ubuntu 7.04?  Things like nozzle check and head cleaning and ink level monitoring.

Around here Epson printers are useless in short order without the ability to run a head cleaning.

--wally.

---

### Post by IanW on 2007-08-03
You'll need either "escputil" or "mtink", both are in Synaptic.

---

### Post by wkulecz on 2007-08-03
Ah, one of the major impediments to non-geek usage of Linux/Ubuntu, why do we need two?  Which would be better for an Epson Stylus Photo 825?  Sure they are "free", but time is money.

If Ubuntu includes Epson inkjet printer drivers by default (which seemed to be the case for my 7.04 installation) it should most definitely also include these necessary tools and make them accessable from the printer properties dialog.

I'm pretty down on Epson printers -- we've spent way more on ink used for head cleaning that ink used for actual printing, but the photo print quality is very good once its cleaned and working.

A little googling suggests mtink is the only one my wife will have a chance of using since its GUI based  compared to escputil command line.

I'm curious to see how well photos will print on Linux using GIMP as photoshop and video editing are the two things keeping windows on my desktop.  MY wife doesn't do photo printing but she does scan and print copies of pages.  After getting her Canon N1240U scanner working ("scanbuttond -r 1000000" kludge for the USB_SUSPEND problem was required) it looked like the scan quality was very good on the monitor but the printout was awful doing an Xsane copy so either our heads need cleaning again (not unexpected by past history) or the default Epson driver is pretty lousy, I suspect the former.

--wally.

Edit: Further googling suggests that mtink supports the 870 but not the 825, whereas the gimp-print(gutenprint 5.01) doc at sourceforge lists support for both.

---

### Post by wkulecz on 2007-08-03
The mtink utility doesn't work with our 825, it could be usable by normal people if it supports your printer, although you have to be a geek to run it from the command line as no menu entries are setup by synaptic.


Epson check ink levels:
     escputil -r /dev/usblp0 -s

Epson print nozzle check:
      escputil -r /dev/usblp0 -n

Epson clean:
      escputil -r /dev/usblp0 -c

Of course the -r parameter will depend on how your printer is connected :(

How non-geeks are supposed to make any use of this I'll never fathom.

There needs to be buttons in the printer properties box to launch these commands and display the output so normal people can use Epson printers effectively.

HTH,
--wally.


Edit:  Cleaning the heads got good print quality back, the driver seems to work very well for plain paper at least.

---

### Post by wkulecz on 2007-08-03
After cleaning the heads I printed one page of this thread from firefox.  Don't seem to be losing anything here with this printer compared to doing the same on Windows.

Used Xsane to make a color copy of a junk mail from comcast, worked quite effectively and again about as good as with windows on plain paper.

Should meet my wife's need for printing and scanning just fine, although she'll be pestering me everytime the heads need cleaning -- which about anytime its been more that a few days between printouts :(

I'll try some photo printing as soon as I get some more free time, but ithis is not a requirement for her as she doesn't do this on windows.

Also happy to report the built-in memory card reader works.  Had the developers included the needed ink level check, nozzle check, and head cleaning commands as part of the printer properties, I could honestly say that  getting this printer to work on Ubuntu was easier than it was on windows.

--wally.

---

### Post by wnelson on 2007-08-04
You can use a GUI called stylus-toolbox to capture info, clean and align an epson printer.

[http://stylus-toolbox.sourceforge.net/](http://stylus-toolbox.sourceforge.net/)

Walt

---

### Post by Anlace on 2007-10-06
I'm trying to figure out a way to check ink levels in a Epson Stylus Photo R220.

I just tried stylus-toolbox and it was another awful experience.  No documentation, even though all of the dependencies were met it still complained of not being able to find a module called "glade."  The forums are dead, there's no one to assist with the problem.  Great idea but just doesn't work.

Good luck with your search, I will watch this thread as well as my own.

---

### Post by ajgreeny on 2007-10-07
Don't know about the specific models of printer you have but mtink certainly works with a Epson Stylus Photo 830U on a usb port.  You must make sure you are a member of the lpadmin group or you will not get the program to detect the printer, and that took me a while to figure out.  When you install mtink there is a message that is not very helpful about this but I did get it done eventually.   I think mtink is great for doing everything that I could in windows and definitely the one to get.

Incidentally, if your epson printer is apparently not covered by the cups print drivers already in ubuntu, get the gutenprint drivers installed.  My 830u was not covered by the defaults in ubuntu but the gutenprint driver did the trick.

---

### Post by gadgetgirl02 on 2007-12-01
I've been trying to run escputil and mtink, and neither of them can find the printer (or a file telling them where the printer is).

I checked, and my ID is a member of lpadmin, but when I enter "sudo mtink", mtink loads and says that it has no access to the printer device file. If I tell escputil to use usb/lpd0 using the command "escputil -r /dev/usblp0 -c", it gives the error "Cannot open /dev/usblp0 read/write: No such file or directory".

I'm running Gutsy with my printer (an Epson 777) connected directly to the router's USB port. I tried substituting the printer's URI for usb/lpd0, but no luck.

---

### Post by clevedonal on 2008-01-22
[I]I have mtink, and after reading this post, i tried  sudo mtink - it found my Epson R220 on /dev/usblp0 and showed ink levels, allowed me to run nozzle check, and nozzle clean...  

al[/I]

---

### Post by Redptc on 2008-02-02
I believe I should acknowledge some success following tutorial help from the 'Forum' especially from Linuxwizard!

The best kind of help because he just pointed me in the right direction.

I now have the correct printer driver for my Epson C67 and a set of maintenance tools via Mtink. I also feel like a Geek because I had to do lot of it myself.:cool:

[COLOR="Red"]redptc[/COLOR]\\:D/

[COLOR="Lime"]*My only grumble is that I have to go into the terminal to do it but it all works!*[/COLOR]

---

### Post by oscarand on 2008-03-28
Hi, if are you interested, I developped a graphical utility based on escputil to display ink levels (at the moment supports only 4 cartridge printers), clean and align print heads...if are you intersted mail me to [email]oscarand@libero.it[/email] and I'll send you my program for free. Thanx

---

