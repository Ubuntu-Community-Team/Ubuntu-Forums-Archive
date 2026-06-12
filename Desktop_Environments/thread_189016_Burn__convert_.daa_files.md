---
title: "Burn / convert .daa files"
date: 2006-06-04
forum: Desktop Environments
---

### Post by m.musashi on 2006-06-04
I have a .daa file and I can't figure out what to do with it. Is there an app for burning it or converting it to an .iso?

Thanks.

---

### Post by taurus on 2006-06-04
Looks like .daa is a disk image format that supports advanced features, such as compression, password protection, and splitting to multiple volumes!  And you can use PowerISO (from Windows) to open it!!!  I wonder if you can just mount it as ISO file...

---

### Post by m.musashi on 2006-06-04
I found the info on PowerISO but it's proprietary software. I was hoping there was a Linux/FOSS option. From what I gather, the PowerISO app will convert .daa to .iso (and many other functions). All I want to do is burn a CD image. I don't know if the .daa will burn correctly but I guess I could try.

---

### Post by m.musashi on 2006-06-05
I went ahead and gave the powerISO a try and it worked fine. Of course I had to use Windows to do this. It seems .daa files are at least somewhat common as torrents so a Linux version would be nice.

---

### Post by ironfistchamp on 2006-06-09
I can't find anything other than PowerISO either :(

---

### Post by FredB on 2006-06-09
[QUOTE=ironfistchamp]I can't find anything other than PowerISO either :([/QUOTE]

Don't break your head on this... It is a crappy format used only by PowerISO.

---

### Post by taurus on 2006-06-09
[QUOTE=m.musashi]I went ahead and gave the powerISO a try and it worked fine. Of course I had to use Windows to do this. It seems .daa files are at least somewhat common as torrents so a Linux version would be nice.[/QUOTE]
I wonder if it, PowerISO, works with wine!!!  Then, you don't have to use Windows to convert your .daa to .iso then...  ;)

---

### Post by FredB on 2006-06-09
:lol:

Well, why bothering with .daa after all ? 

->[]

---

### Post by m.musashi on 2006-06-09
[QUOTE=FredB]:lol:

Well, why bothering with .daa after all ? 

->[][/QUOTE]
That's probably a good question. I never heard of .daa files before but a torrent I downloaded was that type. In the future I'll just try and avoid them. I personally can't see the point of making something not an .iso and then having to convert it back. I suppose if it shrinks the file size but there are other ways to do that.

---

### Post by FredB on 2006-06-09
[QUOTE=m.musashi]That's probably a good question. I never heard of .daa files before but a torrent I downloaded was that type. In the future I'll just try and avoid them. I personally can't see the point of making something not an .iso and then having to convert it back. I suppose if it shrinks the file size but there are other ways to do that.[/QUOTE]

I had the same story. It is just a bad format and it can burn in where you can imagine it will burn.

ISO and UDF formats are the only useful ones.

---

### Post by paridoth on 2006-07-24
i heard somewhere that poweriso was creating torrents in this format all over the place to force people to buy there program to use it, pretty clever, pretty dam evil too.

---

### Post by kingcharles1666 on 2007-01-22
there is a linux version also:

[http://www.poweriso.com/poweriso-1.1.tar.gz](http://www.poweriso.com/poweriso-1.1.tar.gz)

guess it is easily overlooked as it is a very small hint at the bottom of the download page

---

### Post by kingcharles1666 on 2007-01-22
PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

Usage:    poweriso <command> [parameters] [-switches]

<Commands>

 list <image file> <directory>    List files and directories in image file.
     Example:  List all files and directories in root direcory of /home/sam/test .iso .
     Command:  poweriso list /home/sam/test.iso / -r

 extract <image file> <dir/file name>   Extract files/directories from image fil e.
     Example:  Extract all files and directories in root direcory of /home/sam/t est.iso
               to /home/sam/test recursively.
     Command:  poweriso extract /home/sam/test.iso / -od /home/sam/test

 convert <image file>    Convert image file to other format.
     Example:  Convert /home/sam/test.daa to standard iso file
     Command:  poweriso convert /home/sam/test.daa -o /home/sam/test.iso -ot iso

<Switches>

 -r             List or extract recursively.
 -o             Specify output image file name.
 -od            Specify output folder.
 -ot <iso|daa|bin>    Specify output image file type. If not specified,
                the image type will be determined by file name suffix.
 -volsize <n>   Split output image file to multiple volumes, and set volume
                size to <n>. Example: -volsize 100M
 -setpassword <password>   Set password for output image file.
                Example: -setpassword 12345678

---

### Post by vargadanis on 2007-04-10
The answer for you questions:
[http://www.cyberciti.biz/faq/how-do-i-open-daa-direct-access-archive-files-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-open-daa-direct-access-archive-files-under-linux-or-unix-oses/)

It works perfect for me. (^_^)

---

### Post by pilot550 on 2007-04-15
Stop the madness. Use AcetoneISO. It has a graphical interface and no file size limitation. 

[http://kde-apps.org/content/show.php?content=44805]("http://kde-apps.org/content/show.php?content=44805")

---

### Post by fubarbundy on 2007-04-29
> **pilot550 said:**
> Stop the madness. Use AcetoneISO. It has a graphical interface and no file size limitation. 

[http://kde-apps.org/content/show.php?content=44805]("http://kde-apps.org/content/show.php?content=44805")

Errr... nope.. this is still madness, and it uses PowerISO's binary-only utility quite possibly in violation of the GPL and PowerISO's copyrights.

---

### Post by RockoTDF on 2007-05-15
> **fubarbundy said:**
> Errr... nope.. this is still madness, and it uses PowerISO's binary-only utility quite possibly in violation of the GPL and PowerISO's copyrights.

....and this is still SPARTAAA!!!!

Moving on.

The program is completely unresponsive to whatever I do inside, which isn't good at all.

---

### Post by dennisdunbar on 2007-11-11
Does anyone know if PowerISO works with a PPC?  I've got Gutsy on aG3 iMac that otherwise is almost perfect but I cant seem to get the "Poweriso -?" to give me anything.

---

### Post by bulletxt on 2007-11-11
first of all AcetoneISO doesn't violate anything. poweriso is freeware software. AcetoneISO doesn't include it in package. there is no violation.
second, it does not respond? what are you saying it works perfectly, you guys try things and don't know even how to use such software (wich is made to be very easy).
if you don't say what problems it's giving to you it's not fair to say in public "it's not responsive" without listing details.
this is not a good behavior.

---

### Post by ounas on 2008-06-23
> **vargadanis said:**
> The answer for you questions:
[http://www.cyberciti.biz/faq/how-do-i-open-daa-direct-access-archive-files-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-open-daa-direct-access-archive-files-under-linux-or-unix-oses/)

It works perfect for me. (^_^)
Thanks

---

### Post by aliasfoxkde on 2008-07-12
if you locate the Poweriso anywhere other than your root, for example if you leave it where you downloaded then 'poweriso -?' will not work, you will need to give it the path to the file or else your computer doesnt know what to do with the command. For example '/home/<user>/Desktop/poweriso -?' is where I placed mine after extracting the compressed file and ran the command, it's a very simple and wonderful program to use.

thanks a lot guys.

Aliasfox

---

