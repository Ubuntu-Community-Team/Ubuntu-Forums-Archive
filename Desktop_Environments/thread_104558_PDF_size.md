---
title: "PDF size"
date: 2005-12-16
forum: Desktop Environments
---

### Post by Mozzer on 2005-12-16
I am very happy with Open Office's ability to export to PDF; it's an excellent idea to integrate it into a (free!) word processing application.

However, I just have one slight niggle...

When I export a certain document in Windows, it gives me about a 44KB output file. On Ubuntu though, the same document runs up at 123KB.

Is there any particular reason for this like some settings that are different on Ubuntu?

It may not sound like a big deal but if I want to post said PDFs on a forum with limited attachment space it's a tad annoying and it means I have to be in Windows to be efficient. And you know I don't want that ;)

So if anyone can help I'll be very grateful.

Mozzer

---

### Post by earobinson on 2005-12-16
hum, anything intresting about this doc (pictures and the like)
try it with a new doc and just type hello world. can you post the doc in question?

EDIT: also are you running the same version of open office on windows and linux?

---

### Post by hod139 on 2005-12-16
There is a neat tool called pdfopt, which converts a given pdf into an "optimized" copy.  From the man page:
```

pdfopt [ options ] input.pdf output.pdf
pdfopt  uses  gs(1) to convert the Adobe Portable Document Format (PDF)
       file "input.pdf" to a so-called optimized form in "output.pdf".   Opti-
       mization  puts  the  elements  of the file into a more linear order and
       adds "hint" pointers, allowing Adobeâ€™s Acrobat(TM) products to  display
       individual  pages  of  the  file  more  quickly when accessing the file
       through a network.

       Note: input.pdf and output.pdf must not be the same.  If they are,  the
       file  will  probably be destroyed.  pdfopt currently does not check for
       this.

```
As the description hints, this package is part of the ghostscript package, and should already be installed on your system.

---

### Post by Irony on 2005-12-16
If you just hit the pdf icon in Ooo it will do the default pdf size.

However, to modify the compression go;

*File > Export as pdf*

Just follow it through and select the compression.

---

### Post by Mozzer on 2005-12-16
Ok, on Ubuntu, a document with 3458 words makes a 123KB file.

A document with 2 words ("Hello world") produces a 114KB file. Something's not right there.

The version of OpenOffice on Ubuntu is 1.9.129. And I can't be bothered to reboot into Windows to check that one; I'll find out later.

---

### Post by earobinson on 2005-12-16
Well With 2 diferent versions the test is not fair.

---

### Post by Mozzer on 2005-12-16
[QUOTE=hod139]There is a neat tool called pdfopt, which converts a given pdf into an "optimized" copy.  From the man page:
```

pdfopt [ options ] input.pdf output.pdf
pdfopt  uses  gs(1) to convert the Adobe Portable Document Format (PDF)
       file "input.pdf" to a so-called optimized form in "output.pdf".   Opti-
       mization  puts  the  elements  of the file into a more linear order and
       adds "hint" pointers, allowing Adobe&#226;&#8364;&#8482;s Acrobat(TM) products to  display
       individual  pages  of  the  file  more  quickly when accessing the file
       through a network.

       Note: input.pdf and output.pdf must not be the same.  If they are,  the
       file  will  probably be destroyed.  pdfopt currently does not check for
       this.

```
As the description hints, this package is part of the ghostscript package, and should already be installed on your system.[/QUOTE]

I tried using this and it just doubled the size of a PDF from 103KB to 200KB :confused:  Nice try though.

EDIT: It turns out on Windows that the OO version is actually 2.0 instead of 1.9.129. As far as I can see the export settings are exactly the same. And the 103KB file I mentioned above is only 17KB in Windows...

---

### Post by wylfing on 2005-12-16
It very well could be the result of having two different versions of OO.org, even though the version differences are slight. But I would also guess that OO.org calls the print subsystem on each platform to perform certain parts of the task, and that leads to differences.

I just exported a document to PDF on Ubuntu and then exported the same document again on Windows, using identical versions of OO.org. The Ubuntu version came out at 65KB. The Windows version came out at 69KB. So *something* is different about the PDF output process.

By the way, the pdfopt utility is not a file size reducer. It's an optimizer, designed to speed up the processing of the PDF file. It can certainly result in larger file sizes, and quite often does.

---

### Post by hod139 on 2005-12-16
[QUOTE=wylfing]By the way, the pdfopt utility is not a file size reducer. It's an optimizer, designed to speed up the processing of the PDF file. It can certainly result in larger file sizes, and quite often does.[/QUOTE]

Thanks for clearing that up for me. :oops: I had used it a long time ago, and I guess I didn't realize what is was optimizing!!

---

### Post by LucidParody on 2005-12-19
I saw there were a couple topics about this, neither of which had any solutions so I thought I would add my own:

Change your font to either Bitstream Vera Serif or Bitstream Vera Sans.  I found a two page paper that was 250kb in verdana/times new roman went down to 28kb (!) in either of those fonts.

Why? I don't know.  But hey, at least we know the how, now.

---

### Post by nlow04 on 2005-12-20
I currently use Windows XP.  I heard the Crossover Standard Office should be compatible with a lot of Windows programs.  I'm thinking about switching to Ubuntu operating system.

If anyone installed Ubuntu Operating system, can you transfer your photos from your CDs to this operating system if you saved it under Windows XP?

Does Ubuntu come with a disk defragment program, a program if your battery is low, a program that can read pdf files, a media player that plays music and dvds, and a program that unzips zip programs, a program that scans for spyware, and does Ubuntu come with a anti virus program as well as a firewall.  

Even though this is an open source operating system, is it very secure to keep hackers from getting into my system?

Please respond.  Thanks.

Nathan

---

### Post by Game_Ender on 2005-12-20
[QUOTE=LucidParody]I saw there were a couple topics about this, neither of which had any solutions so I thought I would add my own:

Change your font to either Bitstream Vera Serif or Bitstream Vera Sans.  I found a two page paper that was 250kb in verdana/times new roman went down to 28kb (!) in either of those fonts.

Why? I don't know.  But hey, at least we know the how, now.[/QUOTE]

That is most likely because the PDF file format has support for embedding fonts in the document.  My bet is the Bitstream Vera Serif and Bitsream Vera Sans are included standard with PDF viewers and therefore don't have to be embedded in the PDF, while Times New Roman does.  The embedded font is probably what is taking up all the extra space.

---

### Post by Game_Ender on 2005-12-20
Lets address these issue by topic:

**Photos-** Yes photos you have saved on Windows XP can be transferred to Ubuntu.  The files are most likely in JPEG format (ie they have the .jpg or.jpeg file extension) and you can just burn them to a CD an copy them onto your new Ubuntu install.

**Security-** You can get a firewall for Ubuntu, I have heard Firestarter is good, and that is really the only security tool you needed.  Due to the nature of Unix systems, you have to give a program permission to make changes to your system files.  This means you don't have programs installing themselves on your computer and so, there is really is no need for a virus scanner or spyware tools.  Not to mention the fact that there are so few Linux users that writing a virus for them would be a waste of time.  This being said, i have never heard of virus or spyware program for linux.  Out of the box Ubuntu is much more secure than Windows is.

**Media-** This is where things get harry, you will have no problem playing your MP3s (but not wma files), video is a little more difficult.  I don't have experience with this, but I know there are some scripts that will all the necessary virus software for you.

**Basic Programs-** This is where Linux beats windows in Spades.  The Ubuntu package system lets you search for and install over 15,000 thousand free pieces of software.  This is includes little programs for everything imaginable.  Including those tasks that have you paying for little $15 windows apps.  So, yes linux has does have an unzipping program (from the command line it is called "unzip" and "zip")

.

---

### Post by mcmillan on 2005-12-20
nlow04
Your questions seem a little off-topic, I don't know if you meant to post on this thread but maybe a moderator can seperate this into it's own thread. 

Crossover is supposed to let you run Windows apps, there's also wine and cedega. I haven't really tried any too much except for experimenting with wine a bit so I can't say how likely it is to get something too work. I'd recommend keeping the windows and dual booting at least at first in case there's something you really need that you can't get working in linux. 

There should be no problem transferring the pictures from CD, as far as I know pretty much all the picture formats are non-specific to a operating systems. Compression and pdfs are no problem at all. I know there's some applets that show battery power. I don't know if there shown by default on laptops, but I've seen the option to add them to a panel on my desktop. The media is available, but may take a little configuring. There are instructions at [www.ubuntuguide.org](www.ubuntuguide.org) They're for the older version, but I think it's pretty similar. It shouldn't be too difficult to find something similar for Breezy as well, I just don't have it handy since I haven't upgraded yet. 

For a firewall I've heard iptables is enabled by default, which acts as a firewall if I've interpreted things correctly. If you want to be able to modify it easily there's frontend programs you can install, I use firestarter which seems to work pretty well. As for the rest they aren't really necessary in linux. The disk doesn't fragment, so you don't need a defragmenter. And unlike in Windows you should never normally be running with root (administration) privilidges Viruses and spyware essentially don't exist for linux since it's really difficult for them to access anything other than your home folder which is just where personal files are. There are virus scanners, but that's mostly just to make sure you don't pass something nasty on to someone else rather than for protecting your own system. That should answer your question about security too I imagine.

After I typed this I see Game_Ender beat me to this. Hopefully this helped.

---

### Post by Mozzer on 2006-01-13
BUMP.

Having used Automatix to upgrade to OpenOffice 2.0 instead of 1.9.whatever I can now confirm that a PDF containing the words "hello world" is now only 13.5KB. Although my other documents aren't quite as small as their Windows equivalents, it's certainly a big improvement (now only 65.4KB instead of about 150KB).

---

### Post by earobinson on 2006-01-13
Thanks for the update!

---

### Post by ponkan on 2006-03-13
Hate to revive an old topic, but that's often better than starting it over.... Does anyone know which fonts are already included in pdf viewers and which need to be embedded? Is the list of "safe" fonts universal, ie identical from adobe acrobat to xpdf to evince?

---

