---
title: "Print multiple pages per sheet in Openoffice?"
date: 2006-03-02
forum: Desktop Environments
---

### Post by naked on 2006-03-02
Is this possible?  Looking through the small number of printing options I can't seem to find anything.

L

---

### Post by naked on 2006-03-06
Anyone?

---

### Post by mustang on 2006-03-06
I do not believe its possible. 

To print multiple pages on one paper, you would have to 

a) export to PDF in openoffice

b)use pdf2ps to convert to .ps

c)use psnup to get x # of pages per page
(xpdf for some reason will not open up the .ps outputted by psnup for me, might differ for you--if so, you can skip the follow step)

d)use ps2pdf to convert back to pdf 

Perhaps there is a quicker way?

---

### Post by hod139 on 2006-03-06
slightly quicker way:
 a) export to PDF in openoffice
b) use pdfnup to print multiple pages per sheet.

pdfnup is really useful, and works much better than psnup for pdfs.

Edit:  The default page size is A4 for pdfnup.  For US users, you need to say 
```

pdfnup --paper letterpaper foo.pdf

``` Also, the default "nup" is 2x1, where puts 2 pages side by side.  If you wanted say 4 pages, you would say 
```

 pdfnup --paper letterpaper --nup 2x2 foo.pdf
 
```

edit2: To install pdfnup, you need the pdfjam package.

---

### Post by xmastree on 2006-03-06
How many pages do you want on one sheet? AFAIK, there's no way apart from typing it that way in the first place, using either columns or a borderless table.

Anything more complex and you're into the realms of desktop publishing rather than word processing.

---

### Post by mustang on 2006-03-06
[QUOTE=hod139]slightly quicker way:
 a) export to PDF in openoffice
b) use pdfnup to print multiple pages per sheet.

pdfnup is really useful, and works much better than psnup for pdfs.

Edit:  The default page size is A4 for pdfnup.  For US users, you need to say 
```

pdfnup --paper letterpaper foo.pdf

``` Also, the default "nup" is 2x1, where puts 2 pages side by side.  If you wanted say 4 pages, you would say 
```

 pdfnup --paper letterpaper --nup 2x2 foo.pdf
 
```

edit2: To install pdfnup, you need the pdfjam package.[/QUOTE]

Ah super cool tip hod139. Thank you so much. Didn't even know a pdfnup existed. And here I was converting back and forth---thanks again!

---

### Post by naked on 2006-03-06
I have several large documents (20-100) pages that need to be edited.  If I can print 4 sheets per page then I can really save some paper.

This was easy in Windows land.  Seems like it should be easy here as well.

L

---

### Post by eg-maverick on 2006-10-01
I need the same thing but it seems like there is no hope on the horizon. Both old unix and windows drivers can print multiple sheets per page. I would love to see this in ubuntu.
Is there a place to make enhancement requests?
Craig

---

### Post by ezuli on 2006-10-03
Is there any easy way to print a (pdf)book?
That means two pages per side and two sides per sheet. It would be handy, if I could print one side of every sheet, then manually turn pile and then print other sides. I dont want to mess pdf-file's page order, because that's not worth it.

I have seen this kind of program, but it was for Windows.

---

### Post by kolesarm on 2006-10-10
> **ezuli said:**
> Is there any easy way to print a (pdf)book?


i had the same problem and found this thread:
[http://ubuntuforums.org/showthread.php?p=1438275]("http://ubuntuforums.org/showthread.php?p=1438275")

it's working fine for me

---

### Post by ezuli on 2006-10-10
Thank you, kolesarm (and docplastic of course).
I'll have to test that when I have time.

---

### Post by eg-maverick on 2006-10-11
> **kolesarm said:**
> i had the same problem and found this thread:
[http://ubuntuforums.org/showthread.php?p=1438275]("http://ubuntuforums.org/showthread.php?p=1438275")

it's working fine for me

It still is a poor workaround for something that should be available "out of the box". I tried the fp route you referred and yes it does work but it requires at least 3 additional steps and then file management (removing .ps files, etc.). Plus it works well for A4/5 environments but not for U.S. sized paper. Oh well...

---

### Post by eg-maverick on 2006-11-08
I was hopeful that edgy would solve this problem. No joy. When I do a search on this, it is clear that the request is coming from many people. How do we get this considered for the next release?

---

### Post by matthew on 2006-11-09
> **eg-maverick said:**
> I was hopeful that edgy would solve this problem. No joy. When I do a search on this, it is clear that the request is coming from many people. How do we get this considered for the next release?I'm afraid this is something the Ubuntu developers have no control over...to request a specific feature in a specific program (eg. the ability to print multiple pages on one sheet of paper...in OpenOffice.org) then one needs to contact the developer(s) of the specific program in question. In this case, Ubuntu just includes OpenOffice.org in whatever state it exists at the time as soon before the official Ubuntu release as possible.

I do know OpenOffice.org is in active development as there was added during this cycle a feature that I had wanted for some time and had requested from them via their web site (sorry, it was a long time ago so I don't have the link...). You might try looking around there.

---

### Post by Ecthelion on 2006-11-09
Can't you do it like they do on [this page?]("http://http://web.ics.purdue.edu/~park143/index.php?title=Setp_16th_1")

When you have to print, click on generic printer, location custom, and then putting the right command in the line? (this is a suggestion/question)

I remember doing something like that when I wanted do print multiple pages / sheet in dapper.

What I write down are only suggestions, I do not really know how to do it, but if you want to find out I think it's something like that.

EDIT: interesting <part> of my link:
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Through the use of pipes you can generate some very useful output in one single command. For example, you want to print code.c with syntax highlighting, fancy header, four pages per sheet, and duplexed (double-sided). You can do this with the following single command:

   1. enscript --fancy-header --pretty-print --landscape --color -p - code.c | psnup -4 -l | lpr -Phydra -Z duplex 

Note: The -l option tells psnup that your input is in landscape format. For more info, check the appropriate manual pages. 

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Maybe some of the more experienced of you can use [the link]("http://http://web.ics.purdue.edu/~park143/index.php?title=Setp_16th_1") to find out more about multiple page printing

---

### Post by Ecthelion on 2006-11-09
Alright It seems that I was wrong...

You can do it using
psnup -4|lpr
but it's only for pdf's...

Sorry about that.

To make up for my little mistake:
I asked my brother and he gave my this handy tip (still for pdf printing)
install xpdf
do 
```
echo "psFile \"|psnup **-2**|lpr\"">>~/.xpdfrc 
```
and then xpdf will print all your pages in duplex, so you don't have to configure it each time
(if you want more then  pages the sheet change the  in the number you want)

This is ofcourse only when you use xpdf and want to print pdf's

---

### Post by lagartoflojo on 2006-11-11
Okay, I hope this helps.
If you have exported all your doc and odt files to PDF, you can use an application that is in synaptic called **gtklp**. To use it, you run```
gtklp myfile.pdf
``` in a terminal. Once the app starts, you can add more files from within it, and you can choose many  options for the print job, like printing multiple pages per sheet. I tried printing an odt file from gtklp and it did not work (it printed garbage) so that's why you would have to export to pdf first.

---

### Post by patrickfromspain on 2006-11-11
for me, evince won't print multiple pages on one sheet, but gpdf will do it just fine.

---

### Post by dextur on 2006-11-20
Thanks! Installed gpdf and now i can print multiple pages per sheet again.

---

### Post by eg-maverick on 2006-11-22
> **matthew said:**
> I'm afraid this is something the Ubuntu developers have no control over...to request a specific feature in a specific program (eg. the ability to print multiple pages on one sheet of paper...in OpenOffice.org) then one needs to contact the developer(s) of the specific program in question. In this case, Ubuntu just includes OpenOffice.org in whatever state it exists at the time as soon before the official Ubuntu release as possible.

I do know OpenOffice.org is in active development as there was added during this cycle a feature that I had wanted for some time and had requested from them via their web site (sorry, it was a long time ago so I don't have the link...). You might try looking around there.

you're right. I thought it was a driver issue but it's an app issue. Thanks.
Craig

---

### Post by eg-maverick on 2006-11-22
> **dextur said:**
> Thanks! Installed gpdf and now i can print multiple pages per sheet again.

Adobe Reader 7.0 does this as well. Now if we could get something to print booklet formats :cool: (by the way, this can be done in OpenOffice Writer).
Craig

---

### Post by mahavishnu on 2006-11-25
I don't believe there's no way of printing 2 pages in a sheet in OO !!!

I've found a way of doind this: **[COLOR="DarkRed"]Landscape / Brochure[/COLOR]** options.

But the page order are all messed. This mode doesn't print sequentially.

Okay, in Adobe Reader it's easy, but how do it in OO !!:confused:

---

### Post by eg-maverick on 2006-11-25
> **mahavishnu said:**
> I don't believe there's no way of printing 2 pages in a sheet in OO !!!

I've found a way of doind this: **[COLOR="DarkRed"]Landscape / Brochure[/COLOR]** options.

But the page order are all messed. This mode doesn't print sequentially.

Okay, in Adobe Reader it's easy, but how do it in OO !!:confused:

There are 2 ways I found it OOo. One is the way you describe and it is very good if you want to print a brochure/booklet style document. I've been using it for that with good results. The second is to select <page preview>. Then select <print options page preview>. Select the number of pages per sheet and then select <print page view> in the preview toolbar. Works well also. I hope this helps.
Craig

---

### Post by Copter on 2006-11-28
hi!

thats the thing i needed. thnx a lot. nothing else from here except gtklp worked for me. using Dapper, Xerox 3122.

copter :]

---

### Post by dennis1200 on 2007-01-23
for ubuntu folk, like myself, xpp is a fantastic solution (it's in the repositories, i know). COMPLETE gui for cups (100% configurable), able to do it all, at least on my hp 4215. i finally can print out 4 pages on one side, double-sided setup (i still have to do two print jobs, but it is easy enough), and no dropped pages (even in acrobat reader, selecting "even" or "odd" pages will do just that, giving you a 4-page-on-one with pages 2,4,6,8. xpp automatically does it right: 1,2,3,4, then 9,10,11,12. just switch even to odd on the second run-through, and you'll get 5,6,7,8! I can't believe this hasn't been discussed more in the forums, or integrated into a general print dialog for ubuntu. printing was the final frontier for a transition from windows. now I don't even need that old xp dinosaur:D

EDIT:
And a note on gtklp (which I hadn't used because I couldn't figure out how to print stuff with it) - there is a bug if you start gtklp not from a terminal, the File tab doesn't show up (meaning you can't open a file to actually print). Now I think I'll switch, since gtklp it looks nicer.

---

### Post by srimalj on 2007-08-03
HEY ALL THESE POSTS ARE BEATING AROUND THE BUSH..

HERES THE QUESTION AND A SIMPLE ANSWER.. IT WORKED FOR ME :)

_[B]QUESTION:_ Howto print multiple pages per sheet in Openoffice?

_ANSWER:_

As of OO.o 2.2 ,

1) Go to 'page preview'

2) Set the number of pages you want displayed per page in the preview by clicking on the 'Page preview: multiple pages' button. (Example 2 pages)

3) Click on 'print page view' button.[/B]


Thats it!

Regs

Srimal.

---

