---
title: "xpdf can not display files converted with pstopdf utility"
date: 2005-05-03
forum: Desktop Environments
---

### Post by mmarin on 2005-05-03
Hi.

My problem is as follows:

1. I print to a file with mozilla firefox (the file is named mozilla.ps)
2. Then I convert the file using pstopdf13 with the command: 
    miguel@miguel:~$ ps2pdf13 /home/miguel/mozilla.ps
3. After successfully converting the file I open it using xpdf and the letters desapeared, just images and other things are displayed.
4. I open the file with acrobat reader and the file displays correctly.

Yea I know that this is not a big problem but xpdf is supposed to handle any 1.5 pdf compatible file, isn't it?

Thanks

---

### Post by guardian653 on 2005-05-03
I had this problem too, but with cups-pdf, though this solution may help you out:

In Firefox, goto
File>Print>Printer Properties
and type this into the command line box

```
gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -d
MozConvertedToLevel2=true - | lpr (rest of the existing lpr command)
```

[http://ubuntuforums.org/showpost.php?p=149436&postcount=2](http://ubuntuforums.org/showpost.php?p=149436&postcount=2)

---

### Post by mmarin on 2005-05-03
[QUOTE=guardian653]I had this problem too, but with cups-pdf, though this solution may help you out:

In Firefox, goto
File>Print>Printer Properties
and type this into the command line box

```
gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -d
MozConvertedToLevel2=true - | lpr (rest of the existing lpr command)
```

[http://ubuntuforums.org/showpost.php?p=149436&postcount=2](http://ubuntuforums.org/showpost.php?p=149436&postcount=2)[/QUOTE]
 Sorry... it did not work...

I think it's a problem with xpdf because I open the converted file in acrobat reader in a windows machine and the file is displayed and printed right.

Perhaps it has something to be with fonts but AFAIK the ps2pdf13 embeds the fonts in the file converted...

---

### Post by KPingus on 2005-09-28
I'm arriving very late in this discussion and it may already been solved. In any case, have you tried to
```

cat /usr/share/doc/xpdf/examples/sample-xpdfrc >> ~/.xpdfrc

```

---

### Post by Hairy_Palms on 2005-09-29
anyone know if there is an equivalent of the foxit pdf reader for linux?

---

### Post by VosaxAlo on 2005-10-22
I have tried this command, and in effect the pdf created is viewable with Evince, xpdf and Acrobat, but the problem is that **the document is created like a picture**.
No more chance to select text from this pdf!
Au contraire with the original Firefox command (lpr ...) the pdf is a real pdf when I open it in Acrobat with selectable text.

Any suggestion?

---

