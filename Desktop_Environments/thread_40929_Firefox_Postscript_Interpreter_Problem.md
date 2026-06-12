---
title: "Firefox Postscript Interpreter Problem"
date: 2005-06-11
forum: Desktop Environments
---

### Post by palsyboy on 2005-06-11
Anytime I try to print from Firefox, a page prints with the following message:
_________________________________________________
[i]The Postscript interpreter in your printer is 2014.116
This printout requires at least version 2015 or greater

To make a Unix/Linux Gecko browser (eg: Netscape or Mozilla) produce output that will work on any level 2 interpreter change the "Print Command" to use Ghostscript to convert the output down to basic level 2; eg: change the print command from

lpr [OPTIONS]

to (all on one line)

gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -dMozConvertedToLevel2=true - | lpr [OPTIONS]

for level  1 use:

gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -dLanguageLevel=1 -dMozConvertedToLevel1=true - | lpr [OPTIONS]

If you are printing this from a file use Ghostscript to convert it to basic level 2; eg: change the print command from

lpr [OPTIONS] <FILENAME>

to

gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -dMozConvertedToLevel2=true <filename> | lpr [OPTIONS]

for level 1 use:

gs -q -sDEVICE=pswrite -sOutputFile= -dNOPAUSE -dBATCH -dLanguageLevel=1 -dMozConvertedToLevel1=true <FILENAME> | lpr [OPTIONS][/i]
_________________________________________________

I've search around on google.com/linux, and nothing was helpful.  Does anyone know what I need to do?  Thanks.

---

### Post by pkaeding on 2005-06-13
I was also having this problem, and I think I found the solution.

If you go to about:config, and change the value of:
```
print.printer_PostScript/[yourprintername].print_command
```
to:
```
gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -dMozConvertedToLevel2=true - | lpr ${MOZ_PRINTER_NAME:+'-P'}${MOZ_PRINTER_NAME}

```
It seems to fix the problem.  You can also put that line in the print command box in the Print/Properties dialog (that way is probably much easier)

Hope that helps!

-Patrick

---

### Post by palsyboy on 2005-06-13
That solved it perfectly.  Thanks! :D

---

### Post by stoffe on 2005-08-03
That line solved my problem too. 

It had me stumped for the longest time... our printer here (a Lexmark T630) didn't output anything at all, although it started up, looked busy etc, just that nothing came out. Testpages and other programs worked just fine...

Anyway, just wanted to say thanks!

---

### Post by Mentalbug on 2005-08-08
You rock! [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img]

This actually fixed the problems I had with Firefox and cups-pdf.  (I just had continuous horizontal lines where there was supposed to be words and stuff :p)

Now it seems to be working like a charm, thanks! ;)

---

### Post by plm99 on 2005-08-10
Didn't work for me, Firefox just crashes whenever I just press "print". Before I changed to the suggested command it would print a blank page.

I'm using an HP networked printer with hplip-0.9.4 driver, if that makes any difference. The printer test page works fine.

I'm on Firefox 1.0.6

Any more ideas?

---

### Post by sjpwong on 2005-08-22
[QUOTE=pkaeding]
It seems to fix the problem.  You can also put that line in the print command box in the Print/Properties dialog (that way is probably much easier)[/QUOTE]

If i change that line it works until I restart Firefox.  For some reasonit is not actually saving the changes.

Any tips?

TIA.

---

### Post by tmh on 2005-09-14
Is there a bug out against this?
This printout is one of the funniest usability snafus I've had with ubuntu -- print a document, get a page of commandline instructions totally incomprehensible to the novice.
I don't know where the bug is -- obviously somewhere along the line, something should automatically figure out what your printer can handle and do the right thing!

---

### Post by robertoneto123 on 2005-09-27
Hey, Firefox crashes for me too when I put this line. Could someone solve this thing?

---

### Post by pkaeding on 2006-01-02
[QUOTE=robertoneto123]Hey, Firefox crashes for me too when I put this line. Could someone solve this thing?[/QUOTE]

I'm not really sure, since it does work for me, but I know that the above command is case-sensitive.  I think you should be able to just paste it into the appropriate field, but if you are typing it by hand, I would double-check that.

---

