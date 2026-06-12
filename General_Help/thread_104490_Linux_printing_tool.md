---
title: "Linux printing tool"
date: 2005-12-16
forum: General Help
---

### Post by phux on 2005-12-16
Hi,

i wonder, if there is a printing tool to preview the printing result.
There is a great tool for windows ( its called FinePrint ) which lets you preview and change the documents before you print them.

Especially for PDF printing it is often necessary to print 4 pages on one piece of paper or to remove graphics or to zoom (to avoid too much blanc space) and stuff.
Look at [http://www.fineprint.com/products/fineprint/benefits.html](http://www.fineprint.com/products/fineprint/benefits.html)
for more details.

This tool is my only reason to keep Windows as second boot...

cya

---

### Post by hajk on 2005-12-16
When I need to shrink several pages onto a single physical page (like A4), I use the /usr/bin/psnup command. Of course, this command transforms Postscript to Postscript, so for it to work on PDF you would first have to use /usr/bin/pdf2ps to transform your PDF file to PS, and afterwards transform the transformed PS back to PDF with /usr/bin/ps2pdf. Mmm, there ought to be a simpler way of doing this... but at least you don't need Windoze for it. ;)

---

### Post by phux on 2005-12-16
If thats the only way (dont believe it :) ) i will stick with windows, because i have to print several pdfs a day...

The real preview of the print-result is the best thing about fineprint... hope they release a java version or something like that...

---

### Post by noximyre on 2005-12-23
I use Multivalent: [http://multivalent.sourceforge.net/](http://multivalent.sourceforge.net/)

Download the .jar file from [http://sourceforge.net/project/showfiles.php?group_id=44509](http://sourceforge.net/project/showfiles.php?group_id=44509)

I put it in **/usr/local/multivalent**, but you can put it wherever you want. Make sure to add the .jar to your path. I put these lines at the end of my ~/.bashrc file:

```

CLASSPATH="$CLASSPATH:/usr/local/multivalent/Multivalent.jar"
export CLASSPATH

```

To put 4 pages on one, once the .jar is in your path (you'll have to re-login for the path changes to take effect), just run:

```

java tool.pdf.Impose your_file.pdf

```

For more options, look at [http://multivalent.sourceforge.net/Tools/pdf/Impose.html](http://multivalent.sourceforge.net/Tools/pdf/Impose.html) It has good examples of usage further down the page.

You can do a lot of other things with it: [http://multivalent.sourceforge.net/Tools/index.html](http://multivalent.sourceforge.net/Tools/index.html) I think you can zoom, but I'm not sure about deleting images.

Hope that helps!

---

### Post by phux on 2005-12-24
Hmm thats pretty difficult to do for every pdf i print...

I thought of an Add-In for Adobe Reader or something.

Printing 2 or 4 pdf-pages on one Din A4 page is the most important thing...

---

### Post by noximyre on 2005-12-25
I got a better solution! Download Evince, the new document viewer for Gnome (probably works in KDE and other windows managers). With apt, it's just:

```

sudo apt-get install evince

```

I think it does all you use Acrobat Reader for (I haven't used Acrobat in too long to know). In Evince, do File > Print > Layout and choose 2 pages to 1 or 4 pages to 1. (You can also do rotation.) I'd set my PDFs to always open in Evince if you find this is a good solution.

Let me know how it goes!

---

### Post by brainkilla on 2005-12-25
It's great I stumbled across this thread, since I have a problem with psutils package. It won't play nice with n-up printing. I changed all possible settings, in printer driver, in printing-dialogue, tried generating PostScript first and n-uping it in console... nothing, ziltch, nada... preview gives me regular pages, just rotated - "lanscaped" in a way, wich makes no difference to the printer - it prints it out as regular page of course. And psnup -2 gives two scaled pages on one paper sheet, but only one is visible! Yup, first half is visible, the other one blank! Anyone has a faintest idea what might help me or what the problem is? Thanks in advance

---

### Post by phux on 2005-12-25
[QUOTE=noximyre]I got a better solution! Download Evince, the new document viewer for Gnome (probably works in KDE and other windows managers). With apt, it's just:

```

sudo apt-get install evince

```

I think it does all you use Acrobat Reader for (I haven't used Acrobat in too long to know). In Evince, do File > Print > Layout and choose 2 pages to 1 or 4 pages to 1. (You can also do rotation.) I'd set my PDFs to always open in Evince if you find this is a good solution.

Let me know how it goes![/QUOTE]

I was pretty happy about this reply, but then i saw, that i already use evince as default...

The 4-pages-on-one-paper or any other option does not work...
It just prints the default way, ignoring any changes i mage in the print menu :(

---

### Post by brainkilla on 2005-12-25
Hm, that's basicly the same problem I have, I've just played around a bit more. as I verbosely described ;) . But I cannot find a solution, therefore I'm all ears for any proposition...

---

### Post by noximyre on 2005-12-30
If my printer didn't just print out garbage, I'd be able to try some other solutions. For now the only way I know that works is to use Multivalent. (Strange thing is, I got the printer to stop printing garbage, then I rebooted, and it started with the garbage again. Haven't been able to get it back since.)

---

### Post by phux on 2006-01-12
Hmm i tried several ways to print my files now... nothing works with my crappy Lexmark wannabe-printer.

But for those that have a real printer, the tool xpp might work well.
It can be installed with
```
sudo apt-get install xpp
```
and does everything you can do with console printing.


Well...Now i officially HATE Lexmark.
If i ever meet someone working in their printer-section i might kill him!

---

### Post by jesus_pereira on 2006-01-16
[[IMG]http://img44.imageshack.us/img44/383/2page1sheet6mp.th.jpg[/IMG]](http://img44.imageshack.us/my.php?image=2page1sheet6mp.jpg)[[IMG]http://img43.imageshack.us/img43/8956/4page1sheet5dd.th.jpg[/IMG]](http://img43.imageshack.us/my.php?image=4page1sheet5dd.jpg)[[IMG]http://img43.imageshack.us/img43/5179/aarkprinter4pages1sheet4hn.th.jpg[/IMG]](http://img43.imageshack.us/my.php?image=aarkprinter4pages1sheet4hn.jpg)

Image 1: print 2 pages on a single sheet of paper with Evince;
image 2: print 4 pages on a single sheet of paper with Evince;
image 3: print 4 pages on a single sheet of paper with Adobe Acrobat Reader and kprinter running on Gnome.

---

### Post by Duch on 2006-01-17
My experience with xpp, psutils and evince was unsuccessfull.

Multivalent works great for me. I've created this alias to convert a pdf
to 2-pages-on-1 pdf easily:

alias pdf2='java -classpath /<path>/Multivalent20060102.jar tool.pdf.Impose -nup 2 '

---

### Post by phux on 2006-01-18
[QUOTE=jesus_pereira]Image 1: print 2 pages on a single sheet of paper with Evince;
image 2: print 4 pages on a single sheet of paper with Evince;
image 3: print 4 pages on a single sheet of paper with Adobe Acrobat Reader and kprinter running on Gnome.[/QUOTE]

Well i might be new to ubuntu, but im not stupid :)

As i wrote earlier, the settings wont work... i already testet that but my printer just throws out blank papers after changing ANYTHING for the print-layout via console, evince or whatever...
Bad driver-support of the worst printer-company possible.

Guess i really have to transform the stupid pdfs everytime i print them.

---

