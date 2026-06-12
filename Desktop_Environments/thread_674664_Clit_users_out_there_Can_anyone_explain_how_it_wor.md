---
title: "Clit users out there: Can anyone explain how it works?"
date: 2008-01-21
forum: Desktop Environments
---

### Post by Blob on 2008-01-21
OK get your mind out of the gutter...

Clit is the Convert lit program to convert .lit ms reader ebook files to something else.
I got it working and it converts but I don't know what it converted to. I tried opening the converted file with various programs but nothing worked

There is no documentation with this program and I looked and searched this site and the whole web and found nothing like what flags are available as the syntax says to use a "flag". What is that?

Thanks for any help.

---

### Post by jon_gunnar on 2008-01-22
> **Blob said:**
> OK get your mind out of the gutter...

Clit is the Convert lit program to convert .lit ms reader ebook files to something else.
I got it working and it converts but I don't know what it converted to. I tried opening the converted file with various programs but nothing worked

There is no documentation with this program and I looked and searched this site and the whole web and found nothing like what flags are available as the syntax says to use a "flag". What is that?

Thanks for any help.

What I found at the homepage were this:

Q: How do I use the program to convert to HTML or text format? When I run it with no parameters it only mentions something called OEBPS.
A: OEBPS refers to the Open eBook specification. There are several programs which can read Open eBook format, including the Opera web browser.

What file ext. you get? Wikipedia gives this info about the Open eBook :
[http://en.wikipedia.org/wiki/Open_eBook](http://en.wikipedia.org/wiki/Open_eBook)

---

### Post by Blob on 2008-01-22
Hi Jon, I get a file with no extention that is the exact size as the original. I tried opening it with firefox and a half dozen other programs including FBreader but the only thing I see are garbage characters like trying to view a binary in a text editor.

Do you know what it means to insert a flag?

"To explode, you type: clit <flags> <litfile.lit> <directory to explode into>\
For Example:
        clit ebook-propietary.lit ebook-oebps\   
If the directory does not exist, you MUST put a trailing \ or / after it!"

I just noticed what you said about the OEBPS compliant package. I will look into this. For some reason, in other posts, I thought that clit converts a .lit file to and .html file? I must have read this incorrectly. I guess it only converts to oebps.

---

### Post by Blob on 2008-01-22
Figured it out for anyone else that might need to convert .lit Microsoft reader formatted files.

You have to install Convert lit [http://www.convertlit.com/](http://www.convertlit.com/), better known as "clit". I already forgot how I installed it but I remember it was easy and painless in Ubuntu 7.10

You  then have to go to Firefox add-ons and install OpenBerg lector in firefox:
"Welcome to OpenBerg Lector
OpenBerg

  Thank you for downloading OpenBerg Lector 5, version of July 8th, 2007, English (US). 
  Lector is a free, modern, versatile, open-standard,
  open-source e-Text reader, designed to operate from within
  Firefox. Actually, you are currently using both Firefox
  and Lector to read an e-Text.
  
 Thanks to Lector, you just have to click on a link to an e-Text
  or e-Book and that book will be opened and readable.
  
 If you wish to go to the next page, scroll down (either with your
  mouse or using <Page Down>) and continue scrolling
  down when you have reached the end of this page. You can also
  press <Alt>+<Page Down> to change
  page immediately.
  Don't worry if it
  resists a bit, that's to avoid changing pages by accident. Other
  than that, everything works like Firefox, including bookmarks,
  history, printing..."

You then use this format at the terminal command line to convert a file:

You@linux_desktop$ clit ebook_name.lit ebook_name.oebps/

Don't forget the slash at the end!

This will convert the .lit MS Reader formatted file into an .html file complete with all images that you read with firefox!! into a new folder in the same directory the file is in.

Totally cool.

---

### Post by jon_gunnar on 2008-01-22
> **Blob said:**
> Hi Jon, I get a file with no extention that is the exact size as the original. I tried opening it with firefox and a half dozen other programs including FBreader but the only thing I see are garbage characters like trying to view a binary in a text editor.

Do you know what it means to insert a flag?

"To explode, you type: clit <flags> <litfile.lit> <directory to explode into>\
For Example:
        clit ebook-propietary.lit ebook-oebps\   
If the directory does not exist, you MUST put a trailing \ or / after it!"

I just noticed what you said about the OEBPS compliant package. I will look into this. For some reason, in other posts, I thought that clit converts a .lit file to and .html file? I must have read this incorrectly. I guess it only converts to oebps.

I see that you have figured out both the flags and the rest yourself.Good work:)
Interestingly it will not build at my 7.10 system.

---

