---
title: "PDF password crack / removal ?"
date: 2008-12-07
forum: General Help
---

### Post by iheartubuntu on 2008-12-07
Im trying to find a PDF password crack or removal program for linux. I have several PDF books I bought years ago for my Palm PDA and they are all password protected. I cant remember if it was a password I created or one given to me when I bought each PDF book. Anyways, I cant figure it out and I have like 20 books of mine I cant open! Any ideas? Thanks.

---

### Post by Skripka on 2008-12-07
> **shirteesdotnet said:**
> Im trying to find a PDF password crack or removal program for linux. I have several PDF books I bought years ago for my Palm PDA and they are all password protected. I cant remember if it was a password I created or one given to me when I bought each PDF book. Anyways, I cant figure it out and I have like 20 books of mine I cant open! Any ideas? Thanks.

I'd suggest thee get to Google.  There are lots of programs that strip the PDF file print/password restrictions.....many of them are payware, and a few are freeware.

---

### Post by iheartubuntu on 2008-12-07
I could find something in windows, but Im trying my best to stick to all linux/Ubuntu stuff. maybe if i can find something working with Wine, it would be fine too.

Does anyone have any ideas of something for linux or works with Wine?

---

### Post by iheartubuntu on 2008-12-07
bump .. any good solutions out there?

---

### Post by b0b138 on 2008-12-07
sudo apt-get install pdfcrack

---

### Post by mkvnmtr on 2008-12-07
I found two in the package manager some time ago. One was named John and I have forgotten the other. If the pdf cracker offered by the other poster doesn't work for you just search for "password cracker" in the package manager.

---

### Post by iheartubuntu on 2008-12-07
Thanks for the tips. I added PDFCRACK, but apparently it does not support eBook passwords. When running pdfcrack I get this message..

> The specific version is not supported (EBX_HANDLER - 0)

I went the repository and search a on "password" came across a program called "OphCrack". Thanks mkvmtr.I followed the directions to load a table (from the ophcrack website) and am now trying to run the software on my PDF. Ophcrack claims 99.9% crackability, so we'll see :)

It appears like it will take approx 2 hours to run through the first table (im on a P4 laptop with 1gb ram) and there are four tables to search through.

---

### Post by cormpadre1 on 2008-12-07
oph crack is a windows sam file cracker,it will not help with your pdf's, i would think you will need to look for a pdf password cracker specifically
it seems like pdf crack should do what you want 
handy usage link :- [http://www.ubuntugeek.com/howto-crack-pdf-file-password.html](http://www.ubuntugeek.com/howto-crack-pdf-file-password.html)

---

### Post by Neo_The_User on 2008-12-07
Download a few different windows PDF file crackers via google, get wine ([http://www.winehq.com](http://www.winehq.com)) and crack away!

---

### Post by iheartubuntu on 2008-12-08
Still no luck. Ive attempted to use ImageMagick with the command line:

> convert with_password.pdf without_password.pdf

**** This file uses an unknown security handler.
   **** The file was produced by: 
   **** >>>> 9-&#65533;&#65533;&#1141;0j$PS1b&#65533;I{h&#994;V&#65533;&#65533;&#1008;&#65533;&#65533;&#65533;z&#65533;&#65533;&#65533; <<<<
Error: /undefined in pdf_process_Encrypt

As you can see, no luck. I guess this ebook I purchased from Amazon five years ago is going to be impossible to open! Ive emailed them for some help.

---

### Post by meindian523 on 2008-12-08
Please don't bump within 24 hours.This is a huge forum with members in many different timezones,and if you don't get answers means that the people who know aren't logged in yet and the guys who ARE logged in don't know the answer.

---

### Post by iheartubuntu on 2008-12-08
> **meindian523 said:**
> Please don't bump within 24 hours.This is a huge forum with members in many different timezones,and if you don't get answers means that the people who know aren't logged in yet and the guys who ARE logged in don't know the answer.

Thanks for the tip. After bumping within 24 hours i did have several people offer tips and ideas. Although none worked for me, they might work for someone else who doesnt have a DRM ebook they purchased and are just trying to open a password encrypted PDF, like one from a previous employee or something else to that effect. So, was my bump worthless? Probably not judging by the responses. Some of which I never knew about. Ive learned something from it, and others might too.

---

### Post by meindian523 on 2008-12-09
That still doesn't mean you can't be a good citizen of the forums.Bumping frequently puts your thread on top,no doubt,and gets you help too,but it doesn't help other guys who have issues at least as important(sometimes more) than yours.Plus,it makes you seem like demanding support,whereupon it's wise to remember we are helping out here because we LIKE to,not because we are paid or have an obligation to or anything.:)

---

### Post by hyper_ch on 2008-12-09
years ago I used "PDF Password Remover 2.2" to remove the password from PDF slides from one of my profs... he wanted use to sit at the computer and look at the slides...

---

### Post by shekhark on 2009-01-07
pdfcrack hasn't worked for me but this did [http://www.ensode.net/ensode/pdf-crack.jsf](http://www.ensode.net/ensode/pdf-crack.jsf) The code for this is here [http://www.ensode.net/downloads/PdfUnlock.java](http://www.ensode.net/downloads/PdfUnlock.java)

---

### Post by iheartubuntu on 2009-01-07
> **shekhark said:**
> pdfcrack hasn't worked for me but this did [http://www.ensode.net/ensode/pdf-crack.jsf](http://www.ensode.net/ensode/pdf-crack.jsf) The code for this is here [http://www.ensode.net/downloads/PdfUnlock.java](http://www.ensode.net/downloads/PdfUnlock.java)

Ohh how I wish this would have worked for me! Unfortunately I got this message...

> 
There was a problem unlocking the provided PDF file. Please make sure it is a valid PDF file and try again.

Please note that if this free utility does not work to your satisfaction, there are several software packages for PDF manipulation that might serve your needs better. 

---

### Post by iheartubuntu on 2009-05-23
It  didnt work for me, and its a big long shot, but you can try installing Adobe Acrobat (I used 6.0), then go to ADVANCED > BATCH PROCESSING > CREATE NEW SEQUENCE

give it a name, select the command "security" add it to your processing list, click OK, select the remainder of the options you want, and then run that sequence.

I did this about 3 years ago on a PDF file that I had put a password on but could no longer remember it. Its not working though for my Amazon purchased ebooks. Must be a strong encryption.

---

### Post by doublewitt on 2010-01-29
Use Okular and in the settings, untick "Obey DRM limitations". Okular is in the Ubuntu software center.

---

### Post by radimvice on 2010-04-13
Adding to what doublewitt suggested, you can open the file in Okular and use the Print to File (PDF) option - this will create a new PDF file from the original data, and the new file won't have any security restrictions.

---

### Post by crichard on 2010-04-13
It's an old thread :)
Have you tried some web services(?) which help to remove pdf restrictions.?

[http://pdfpirate.net/](http://pdfpirate.net/)

[http://www.pdfunlock.com/](http://www.pdfunlock.com/)

---

### Post by KingYaba on 2010-04-26
Thanks for posting those two web links but your pirate pdf link did not work. The website loads and everything but removing the DRM did not work. 

I'm using PDF Crack which is one of those brute force methods. This could take forever. :)

---

### Post by Susuzhang on 2010-05-13
PDF password cracker?Is it like PDF Password Recovery 5.0?I use this tool,quite well.

---

### Post by iheartubuntu on 2010-07-28
> **crichard said:**
> It's an old thread :)
Have you tried some web services(?) which help to remove pdf restrictions.?

[http://pdfpirate.net/](http://pdfpirate.net/)

[http://www.pdfunlock.com/](http://www.pdfunlock.com/)

Thought I would update my PDF cracking quest. Still a NO GO. Ive tried these two sites above with no luck. The first one gives me a blank 2 page PDF file. The second page gives me an error "The uploaded file seems to be subject to a non-standard encryption from a 3rd party". I have tried PDF2DJVU and also PDF2SVG with the similar error codes.

Ive also tried opening the file in GIMP (doc is encrypted) and in Okular with no luck.

If you think you can crack it, please try. And if so, please provide details here how to do so, thanks!

Link to the ebook I purchased back in 2002 (its a book called Riptide by Douglas Preston):

[http://tinyurl.com/2albwhl](http://tinyurl.com/2albwhl)

Thanks someone for any help!

---

