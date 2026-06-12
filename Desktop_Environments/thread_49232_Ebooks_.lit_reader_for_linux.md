---
title: "Ebooks .lit reader for linux?"
date: 2005-07-15
forum: Desktop Environments
---

### Post by lorenzo on 2005-07-15
Does anyone knows if a microsoft reader like software exist to read ".lit" ebooks on ubuntu?

---

### Post by Fizile on 2005-07-29
I also am looking for this.  Also, I am unable to successfully run Microsoft Reader through crossover office.

---

### Post by kleeman on 2005-07-29
Check this out but watch out for the DMCA:

[http://www.kyz.uklinux.net/convlit.php](http://www.kyz.uklinux.net/convlit.php)

---

### Post by Fizile on 2005-07-29
[QUOTE=kleeman]Check this out but watch out for the DMCA:

[http://www.kyz.uklinux.net/convlit.php](http://www.kyz.uklinux.net/convlit.php)[/QUOTE]
 Yeah i couldnt get that working for whatever reason, ill put more tweak into it.

---

### Post by kleeman on 2005-07-30
Got it working after I compiled as root. I've attached the executable as a zipfile

---

### Post by mtalexan on 2006-07-17
So now Convert Lit works so I can convert my ebooks if I want, but I've got a few GB of ebooks that I share with a windows system.  Does anyone know of a way to read them without converting them?

---

### Post by KillerKiwi on 2006-08-07
I usually turn them into PDF's....

Use the convert tool to explode into html

Open in OOo2 copy the text
Create a new Ooo2 document paste in the text
change the format to something nice, verdana

Export to PDF

You could proably to that all via command line

---

### Post by KeithEckstein on 2006-10-25
I converted all mine to PALM format as the Palm Reader seems to work fine under Wine on all versions of Linux that I've tried.  I cna't remember the exact process but it involved converting (via a batch process) all the .LIT files to text and then converting them to Palm format.  I did it all from a Windows machine (I don't have one anymore!) but the executable may well work under Wine.  I'm about to do another batch (this weekend) - will take notes in case it might help anyone.

All the best

Keith 

P.S.  I find that PDF works well (perghaps is the best format) for technical books and documents but, for fiction, the Palm Reader is more comfortable.

---

### Post by djRobbieF on 2006-12-04
I just install IE 6 and then MS Reader under WINE.  it works perfectly.

---

### Post by rykel on 2006-12-19
> **djRobbieF said:**
> I just install IE 6 and then MS Reader under WINE.  it works perfectly.

hi,

how did u install IE6 and MS Reader to work?

did u install IE6 thru' IEs4Linux?

as u can see from the screenshot, i have successfully installed IE6 thru IEs4Linux, but MS Reader installer failed to install... any help please?

---

### Post by starscalling on 2007-02-22
bump :guitar:

---

### Post by jerbucket on 2007-02-28
Along the same lines, does anyone know of a library to convert .txt to lit files and that I can invoke using Ruby?  

:confused:

---

### Post by elgreengeeto on 2007-04-07
> **mtalexan said:**
> So now Convert Lit works so I can convert my ebooks if I want, but I've got a few GB of ebooks that I share with a windows system.  Does anyone know of a way to read them without converting them?

You could write a script that runs Convert Lit on a .lit file in the background, outputs into a temporary directory, and then opens the resulting html file in the web browser of your choice. If I write it myself I'll post here.

---

### Post by elgreengeeto on 2007-04-26
> **elgreengeeto said:**
> You could write a script that runs Convert Lit on a .lit file in the background, outputs into a temporary directory, and then opens the resulting html file in the web browser of your choice. If I write it myself I'll post here.

I went ahead and wrote that script. So, to keep my promise, here it is.

This is the first useful bash script I ever done wrote. Not the cleanest code ever. But it seems to work. Any comments appreciated! Enjoy.

**This script requires a working version of clit installed!**
(The binary kleeman attached above works on my system.)

---

### Post by poet_will on 2007-04-30
How do you get the clit12 executable to work??  I have double clicked it and nothing happens.  thanks

Will

---

### Post by inksmithy on 2007-05-08
You don't double click it, you call it from within the command line.

ie: ```
clit12 [flag] [filename] [filename]
```

---

### Post by Waldo323 on 2007-05-08
> **inksmithy said:**
> You don't double click it, you call it from within the command line.

ie: ```
clit12 [flag] [filename] [filename]
```

I think you need to have 
```
clit12 [flag] [filename] [foldername]
```
if I read it right , please correct me if I am mistaken... (I am using clit1.8  )
also if the folder does not exist you need to include a "/" at the end of the folder name

---

### Post by dewzenol on 2007-07-16
aaaaand here it is:
[http://openberg.sourceforge.net/](http://openberg.sourceforge.net/)
Anyone ever tried this on a nokia 770?

---

### Post by calaban9 on 2007-07-19
> **rykel said:**
> hi,

how did u install IE6 and MS Reader to work?

did u install IE6 thru' IEs4Linux?

as u can see from the screenshot, i have successfully installed IE6 thru IEs4Linux, but MS Reader installer failed to install... any help please?

Taking bits and pieces i got from this thread and other places I got the reader to install using the folowing... method

found (google) the ie6_overrides.reg file
and ran:

wine regedit ie6_overrides.reg

The installed ie6 via wine (those instructions can be found easily)

Then installed dcom98.exe with the following line:

 WINEDLLOVERRIDES="ole32=n;rpcrt4=n;oleaut32=n" wine dcom98.exe

then made sure there was nothing from pervious installs (the permission denied error i see in your screen shot)

rm -r /home/me/.wine/drive_c/Program\ Files/Common\ Files/InstallShield/

Then ran the reader installer with:

WINEDLLOVERRIDES="ole32=b;rpcrt4=b;oleaut32=b" wine MSReaderSetupUSA.exe 

And it worked...

---

### Post by aircooledbusnut on 2007-07-27
first off, I am a complete linux noob.  I am trying to learn.  I could not get either convertlit 1.8 or 1.5 to compile at all.  I get about two lines of errors and that is it.  any help would be greatful.
Thanks

---

### Post by calaban9 on 2007-07-30
You have to download the math libraries from [http://math.libtomcrypt.com/](http://math.libtomcrypt.com/)
before you can compile it.

---

### Post by seamus7 on 2007-07-30
I found the following instructions for installing Microsoft Reader here in a comment at the bottom of the web page: [http://appdb.winehq.org/appview.php?iVersionId=1003&iTestingId=13053](http://appdb.winehq.org/appview.php?iVersionId=1003&iTestingId=13053)

1. Install IE6 using IES4LINUX.
2. Start IE6 and download Microsoft Reader from the MS website. Choose Open not Save.
3. Activation may or may not work. Didn't for me. But it might not be necessary.

My questions:
* How to get .LIT files to open individually and automatically in Microsoft Reader? (finding .LIT files by browsing within Microsoft Reader's library page is tedious if one has many E-books, especially if they follow varying naming conventions)
* How to get .LIT files to be automatically associated with Microsoft Reader? (same as above)
* Can Microsoft Reader display two pages at a time in Full Screen?
* Is there an Open Source Reader planned or in development which will support the proprietary .LIT format? (I hate using WINE)

---

### Post by Yoric on 2007-08-03
> **elgreengeeto said:**
> You could write a script that runs Convert Lit on a .lit file in the background, outputs into a temporary directory, and then opens the resulting html file in the web browser of your choice. If I write it myself I'll post here.

That's what [OpenBerg Lector]("http://www.openberg.org") does for you...


[QUOTE=seamus7] Is there an Open Source Reader planned or in development which will support the proprietary .LIT format? (I hate using WINE)[/QUOTE]

Same as above, OpenBerg Lector. It still requires Convert Lit, but once it's configured you can read your .LIT files from Firefox.

---

### Post by aircooledbusnut on 2007-08-05
Im new to Linux but I found a .deb file for Libtommath at [http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath](http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath) and a .deb file for Convert lit at [http://ace-host.stuart.id.au/russell/files/debian/sarge/clit/](http://ace-host.stuart.id.au/russell/files/debian/sarge/clit/).  Instructions for use are on the specific pages for each.  Enjoy.

---

### Post by Ryzol on 2007-08-13
Where do I put libtommath? I put it in /usr/lib but the .deb still says I do not have it.

---

### Post by ziofil on 2007-08-18
I can't find ie6_overrides.reg, do someone know where is the file? the site indicated is not more working... :confused:

---

### Post by aj61779 on 2007-11-19
I downloaded ConvertLit but have no idea how to get it to work.  Complete newbie.  need line by line commands for terminal.  have also downloaded the lib to math file that was mentioned above.  both of the unextracted zip files are saved tot he desktop.  have also downloaded openberg but will not work till converlit is working.  help please

---

### Post by eeeandrew on 2007-11-20
hi guys, I@m completely new to linux I downloaded the executable clit12 file to my desktop..it says about running it in command line but I'm not sure exactly how to put in the filename and stuff as the argument...could someone post example code please?

---

### Post by dysphasi on 2007-12-02
Has anyone actually got openberg working with lit files? 

I've installed all the dependencies, but for whatever reason, if I open the lit file with or in firefox it just asks me what I want to do with the file, if I tell it I want to use firefox, it just opens a new page and asks me again...this behaviour repeats.

And yes, I have pointed firefox to clit. Any help would be much appreciated.

---

### Post by Yoric on 2007-12-21
> **dysphasi said:**
> Has anyone actually got openberg working with lit files? 

I've installed all the dependencies, but for whatever reason, if I open the lit file with or in firefox it just asks me what I want to do with the file, if I tell it I want to use firefox, it just opens a new page and asks me again...this behaviour repeats.

And yes, I have pointed firefox to clit. Any help would be much appreciated.

Are you using a locally downloaded file ? Is the extension .lit (in lower-case) ? If you attempt to find the MIME type of this file, using "file -i", what is the result ?

---

### Post by melisandre on 2007-12-30
Ok, so I got the IE4Linux, it works fine. I installed - everything's perfect. But if I open the program it shows me the opening screen for an instant, and then exits by itself. Not only that, but the files are not on my WINE "drive_c" and the .lit files are still not recognized.

---

### Post by djRobbieF on 2008-01-01
> **rykel said:**
> did u install IE6 thru' IEs4Linux?

Wow, I'm late with this reply!  Haha.  But just in case anyone else (in the present) has the same question...

No, you can't do it that way (or at least, you wouldn't want to) becuase IEs4Linux uses its own wine environment.  Just download the IE6 installer from Microsoft and install it.  [here](http://www.microsoft.com/downloads/thankyou.aspx?familyId=1e1550cb-5e5d-48f5-b02b-20b602228de6&displayLang=en)

Then download MS Reader [here](http://www.microsoft.com/reader/downloads/pc.mspx) and install them in that order.

I know it sucks to use a MS product... but at least it's free (no cost) and it works.

---

### Post by melisandre on 2008-01-01
> **djRobbieF said:**
> Wow, I'm late with this reply!  Haha.  But just in case anyone else (in the present) has the same question...

No, you can't do it that way (or at least, you wouldn't want to) becuase IEs4Linux uses its own wine environment.  Just download the IE6 installer from Microsoft and install it.  [here](http://www.microsoft.com/downloads/thankyou.aspx?familyId=1e1550cb-5e5d-48f5-b02b-20b602228de6&displayLang=en)

Then download MS Reader [here](http://www.microsoft.com/reader/downloads/pc.mspx) and install them in that order.

I know it sucks to use a MS product... but at least it's free (no cost) and it works.

Really? because i was able to install it but it instantly closes... would that be a result of IE4Linux too?

---

### Post by morghanphoenix on 2008-01-05
Easy fix for the closing as soon as it opens.

msvcirt.dll

free to download with a quick google search, just drop it in the wine drive /windows/system folder. If you try launching the MS reader from a console rather than just clicking the link it gives an error message that the file is missing. Course this may not be your problem, haven't used ubuntu in some time, but usually if a fix works for fedora it'll work for ubuntu as well.

---

### Post by mahiyar on 2008-01-06
Thanks aircooledbusnut, the deb files work beautifully especially after scouring the net and using a couple of makes did not solve my problem. Now on to next step convert .htm to pdf.

---

### Post by DrOni on 2008-01-09
> **Yoric said:**
> Are you using a locally downloaded file ? Is the extension .lit (in lower-case) ? If you attempt to find the MIME type of this file, using "file -i", what is the result ?

I'm having the same problem. I tried opening the file from various locations, the extensions are fine (I have tried several different files). I was unable to determine it's MIME type.

---

### Post by DrOni on 2008-01-16
> **dysphasi said:**
> Has anyone actually got openberg working with lit files? 

I've installed all the dependencies, but for whatever reason, if I open the lit file with or in firefox it just asks me what I want to do with the file, if I tell it I want to use firefox, it just opens a new page and asks me again...this behaviour repeats.

And yes, I have pointed firefox to clit. Any help would be much appreciated.

After doing a bit more reading up, I found out how to fix this little problem. Check that you don't have any programs selected for .lit files to be opened with. In other words, right click a .lit file, click on the open with tab and remove all programs. Then open your file from the Firefox menu.

---

### Post by killerinparadise on 2008-01-18
> **DrOni said:**
> After doing a bit more reading up, I found out how to fix this little problem. Check that you don't have any programs selected for .lit files to be opened with. In other words, right click a .lit file, click on the open with tab and remove all programs. Then open your file from the Firefox menu.

Thanks so much this worked perfectly, can't believe I didn't catch that, thanks again

---

### Post by anathema415 on 2008-06-18
If I purchase a ebook for the Microsoft Reader from Penguin group will it work with OpenBerg?

---

### Post by christooss on 2008-07-02
I created a script that converts lit to pdf. It works but you will need three aplications to sucessesfully convert lit to pdf

First there is Clit very nice howto is based here:

[http://ubuntuliving.blogspot.com/2007/02/converting-lit-files-in-ubuntu.html](http://ubuntuliving.blogspot.com/2007/02/converting-lit-files-in-ubuntu.html)

and than html2ps and ps2pdf

Than move my sciript to dir with .lit files and wait. Sometimes convertion takes really long time. Specialy htm to ps conversion. I added -d option for debuging html2ps cause it gives you at least some verbose mode.

Script looks like this. Nothing special but does the trick.
```

#!/bin/sh
for bla in *.lit
do
base=`basename "${bla}" .lit`
clit "${bla}" test/
done

cd test/

for blabla in *.htm
do
base=`basename "${blabla}" .htm`
html2ps -d "${base}.htm" > "${base}.ps"
ps2pdf "${base}.ps" "${base}.pdf"
## mv test/ ${base}
done
mkdir pdfji/
mv *.pdf pdfji/

```

---

