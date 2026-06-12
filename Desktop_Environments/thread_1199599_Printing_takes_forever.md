---
title: "Printing takes forever"
date: 2009-06-29
forum: Desktop Environments
---

### Post by MathSWE on 2009-06-29
Hi!

I have a Brother MFC-9840CDW connected through the LAN to my Ubuntu Jaunty Desktop. Printing in general is really slow. Now I am trying to print a JPEG picture with large resolition. The print job size is 27 Mb according to the print status window.

It has been chewing on this print for over 2 hours now. CPU is at 100%. Whats wrong?

//Mathias

---

### Post by scrooge_74 on 2009-06-29
Are you using SAMBA or CUPS?

---

### Post by MichaelBKK on 2009-06-30
Not sure about the OP, but I'm having the same problem.  HP LJ 2550ln configured through CUPS.  Takes forever to print anything, especially images, and seems to do some really stupid things.

For example, I asked for 10 copies of a 2-page document. I clicked off collation so it would print faster - in previous versions it would send the data for 1 page and tell the printer to print 10 copies, but now it resends the entire data for a page 10 times!  It took forever to get the 10 copies, where in previous versions it would have taken only minutes.

---

### Post by darthmob on 2009-06-30
I experience similar problems. I have got a Kyocera attached with the default cable (that large one).

it used to work pretty nice but it has been very slow for a while now. it occasionally goes up to 100% cpu as well.

---

### Post by scrooge_74 on 2009-06-30
I'm starting to feel your problems are driver related, check if your printers are supported by CUPS.

The day I went out to get me a printer/scanner I made sure it was supported before I bought it.

The list is [here]("http://www.openprinting.org/printer_list.cgi")

---

### Post by gbryant on 2009-08-16
> **scrooge_74 said:**
> I'm starting to feel your problems are driver related, check if your printers are supported by CUPS.

I'm having the same problem -- tell it to print multiple copies, uncollated, of a graphics-heavy page, and it uploads the same page over and over. I'm using the HP LJ 5si, [totally supported]("http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_5Si"), claims to work "perfectly." Not so.

For the record, I solve the problem by taking the file to an old clunker Windows box running Windows '95. No problem there. Now, that hurts. (Note: same printer, not networked -- hard-plugged with the printer cable. We roll the printer from machine to machine on a dolly.)

I've also tried going into administration setup of the printer and setting it to make, say, 10 copies of everything, then sending one copy to that printer. Same result: slow slow slow. Uploads the page anew for each copy. :confused:

---

### Post by scrooge_74 on 2009-08-18
Still you should check which printer drivers the system is using, you have several options from what I read.

---

### Post by sola on 2009-08-19
I have the same problem with network printing. The printer is on an Intrepid machine (LaserJet 6L).

This is not driver related because a lot of people - with different printers - have this problem.

I believe we can add this to the list of broken things in Jaunty.

I am starting to feel that Jaunty is the worst Ubuntu release for some time. 
Some of the problems on my Toshiba m200 system (apart from broken LAN printing):
- Auto-login doesn't work, so I have to login every time (and the calendar says 2009)
- Resume is unstable, sometimes kills the X server (and all of the apps) and I get a GDM login screen
- Desktop effects and Compiz fail when in dual monitor mode
- Since yesterday, boot is very slow (it was quite fast before). Thanks to auto-update, I think I will disable it.

Jaunty is quite a step back from Intrepid.

---

### Post by scrooge_74 on 2009-08-20
I dont plan to use 9.04, I'm confy with 8.04 which is stable enough for me, but I do see lots of issues with drivers around (video specially)

---

### Post by Motorhead Kaze on 2009-09-06
Printing has always been awful for me in Ubuntu -- since Feisty. It took me a year to find out that there was one version of the driver for my printer that stops and performs a "cleaning" every few copies, and one version that just prints like I think it should. Still, both are half the speed -- if not even slower -- than when I print in XP. Over time, I just decided it was easier for me to keep double booting for the days when I need to print or use my scanner.

I had given up on this idea of printing in Ubuntu until Scrooge_74 asked about whether the printer was hooked up through CUPS or SAMBA. So I came to ask:

1. My printer is hooked up via a USB cable, does that make any difference? 
2. How do I find the answer to this CUPS vs. SAMBA question in my PC? Is there a line I can type in the terminal to find out if my driver supports CUPS? 

If there is something I can do to make the printer work regular speed in Ubuntu, I will sure do it! 

BTW, I agree -- no reason to come out of Hardy yet. It works, that is all I want.

---

### Post by simonyee on 2009-09-06
Ok Maybe the printer are not the problem but the usb/parallel power is not enough ?

generally try to look into the drivers from the manufacturers

---

### Post by scrooge_74 on 2009-09-06
> **Motorhead Kaze said:**
> Printing has always been awful for me in Ubuntu -- since Feisty. It took me a year to find out that there was one version of the driver for my printer that stops and performs a "cleaning" every few copies, and one version that just prints like I think it should. Still, both are half the speed -- if not even slower -- than when I print in XP. Over time, I just decided it was easier for me to keep double booting for the days when I need to print or use my scanner.

I had given up on this idea of printing in Ubuntu until Scrooge_74 asked about whether the printer was hooked up through CUPS or SAMBA. So I came to ask:

1. My printer is hooked up via a USB cable, does that make any difference? 
2. How do I find the answer to this CUPS vs. SAMBA question in my PC? Is there a line I can type in the terminal to find out if my driver supports CUPS? 

If there is something I can do to make the printer work regular speed in Ubuntu, I will sure do it! 

BTW, I agree -- no reason to come out of Hardy yet. It works, that is all I want.

To your questions:

1. the USB cable wont make a difference.
2. CUPS is what you use as print server, samba is for networking with XP machines, in some instances you need to put a ref to the printer in samba so other machines (using XP) can access it, if not config well it could be a mess.

The thing with printers in Linux is that sometimes you have several options for drivers.  HP has some tools you can use with their printers. When I buy a new one I first check if it has drivers for Linux then I buy it.  From checking on [linuxprinting.org]("http://linuxprinting.org") some printers have different options for drivers and their capabilities. People could think that in XP is just easy to use, but in true I sometimes find it easier on linux. My printer is configured to be use over the network. At present I switched my laptop to Debian 5.0 and this time I didn't even needed to configure the printer it magically was.


Lets do a recap here:

Brother MFC-9840CDW  <--- Need to head out to [BROTER's driver page]("http://solutions.brother.com/linux/en_us/download_prn.html#MFC-9800") to get drivers.

HP LJ 2550ln  <-- the [2550L]("http://www.openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_2550L") seems to work (don't know if the n has something different, aint the n for those that have network capability that you can configure their internal print server? I remember using one of those LJ 4000n or something was cool to just put the ip address and get the config page on the browser (many years ago dont laugh)

KYOCERA <--no make and model can check, but proly driver related.

HP LJ 5s <-- has drivers, but what Linux version of OS are you using? There could be other issues there, saying that it hurts having to see it work on Win 95 or other version you forget that originally all of these printers were made thinking on MS so they had drivers for it.

LaserJet 6L <--- same problems, one more reason to think print servers and stuff like this need to run on stable versions (even old ones) and not bleadding edge. Any of you ever saw one of those Novel print servers? that you would go in the mornings and power the thing up and it would be booting from a floppy while everybody in the office was using win 98 or even XP?  It did the job it wasn't bleeding age.

I still remember my HP LJ 1100, printed good in XP, when I changed to Debian printing was slow, I lived with that till found the correct drivers after and upgrade (I was using Sarge as OS in those days).

---

### Post by phen on 2009-09-08
hello!

using jaunty I have the same problem: very slow printing on a HP deskjet. It was auto-detected out of the box and works well, but only very slow. I tried all available settings like HPLIP etc.

---

### Post by SupraGuy on 2009-09-08
I'm having similar issues with Jaunty.

I have several printers, some are local, some are remote over VPN.

In all cases, printing from Windows is fine.  There's a Windows 2003 server on the LAN, and I can print to any of the printers and get the expected response times.

All printers are Lexmark T642 printers.  Not the newest, but they do their job.

I have 5 of these printers in total.  2 are local, and connected to the LAN.  3 are in different cities, and are connected via a hardware VPN.  Network response is okay to these locations.

All 5 printers are configured using the LPD protocol.  /etc/cups/printers.conf will contain lines like:

DeviceURI lpd://citylexmark.companyname.local/RAW

All 5 are configured identically using the driver: Generic PCL5e Printer Foomatic/hpijs(recommended)

The printers on the LAN work beautifully.  No delays, printing starts when it should, and goes as fast as I expect.

The printers in the other cities...  Not so much.  If I send it raw PCL (Generated by the application that I'm running) it seems to be okay, but the other output that my application generates is PDF files.  These work great on the local printers, but take 10 minutes or more on the remote printers per page.  Unfortunately, the PDF output is used for invoicing, so a large run takes WAY too long.

I've seen the links to a replacement /usr/lib/cups/filter/pdftops

I'm going to switch the print drivers over to Generic PostScript to see if that helps.  If it slows down the PCL output, that's nowhere near as bad. (Though still not good!) since that tends to be much lower volume.

I suppose that I might try seeing if I can send the print jobs to the Windows server via Samba as well, but using Windows to handle spooling to printers when there's a Linux server on the network seems inherently wrong to me...

---

### Post by scrooge_74 on 2009-09-08
You have any older Ubuntu or Debian around to test your settings? Seems lot of people have issues with Jaunty drivers for stuff from video to printer and things in between

---

### Post by Chewy2 on 2009-09-30
I'm having the same problem with slow printing. It prints small amounts of plain text just fine but anything beyond that it takes forever. It would have probably taken a couple of hours just to print a two page article if I had the time to wait for it. I just ended up switching to Vista just so I could print it out.

I've got a Canon Pixma ip3000 which is supported by CUPS. It is also connected to my router with a dlink print server. I'm running Jaunty as well.

---

### Post by scrooge_74 on 2009-10-01
Sounds like driver issue

---

