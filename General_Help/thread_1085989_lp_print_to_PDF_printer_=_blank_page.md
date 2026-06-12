---
title: "lp print to PDF printer = blank page"
date: 2009-03-03
forum: General Help
---

### Post by lutherhex on 2009-03-03
Running Ubuntu 8.04
I would like to be able to print any file to the local PDF printer from the terminal.

So far I have done this:
apt-get install cups-pdf ghostscript
That automatically creates a printer named PDF.

Printing images, plain text files, and .PDF files works as expected. However when printing .doc or .xls files the result is a single blank page .pdf file that is 2kb in size.

This is the print command I am using:  lp -d PDF /path/to/file.doc

**

Oddly enough when I actually open the .doc file and select the PDF printer it works. Why does it work there, but not in the command line?

JES

---

### Post by absolutezero1287 on 2009-03-03
My guess would be that the GUI is using different parameters.

---

### Post by kaibob on 2009-03-03
> **lutherhex said:**
> Running Ubuntu 8.04
I would like to be able to print any file to the local PDF printer from the terminal. <snip>

Printing images, plain text files, and .PDF files works as expected. However when printing .doc or .xls files the result is a single blank page .pdf file that is 2kb in size.<snip>
The following command will print OpenOffice documents (including DOC and XLS) to PDF from a terminal window:

```
openoffice -norestore -nologo -pt cups-pdf filename
```

---

### Post by lutherhex on 2009-03-04
Thanks kaibob, but I am sorry it didn't work. 

Error from running command openoffice -norestore -nologo -pt cups-pdf filename :
```
unixadmin@ubuntu8.04:~# openoffice -norestore -nologo -pt cups-pdf /home/unixadmin/Desktop/Notes.doc
unixadmin@ubuntu8.04:~# /usr/lib/openoffice/program/soffice.bin X11 error: Can't open display:
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)
```

I am running an headless server that is supposed to grab documents and convert them into .PDF
So while no one is logged into the server a cron job will run a script that prints those documents to PDF.

JES

---

### Post by kaibob on 2009-03-04
Before posting I printed a test DOC document to PDF using the suggested command-line and it worked fine. I just did this again with a separate document with success. So, the command does work.

I do not know anything about headless servers, and I don't understand the issued error message. Perhaps someone else will be able to help with this. Sorry I couldn't be more help.

---

### Post by lutherhex on 2009-03-04
No problem kaibob.

You are correct the command works, but not in my setup. Try SSH into your server and then run the command to see what I see  :-)

After reading the openoffice man page there are two more switches -headless and -invisible that looked promising, but oddly enough didn't. Perhaps today isn't my day.

**

Taking this from a different angle, how do I setup a Postcript printer and have it print to file? I could then see if the result is still an 2kb blank 1 paged file, or if it actually contains all of the data.

JES

---

### Post by lutherhex on 2009-03-05
Well, I upgraded from ubuntu 8.04 to 8.10 and still have the same results.

I did find a un-answered post from an year ago, that is similar to mine:
[https://lists.ubuntu.com/archives/ubuntu-users/2008-February/136774.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-February/136774.html)

The differencing being s/he used lpr while I used lp, either way the outcome is the same 1 page blank 2kb pdf.

---

### Post by lutherhex on 2009-03-05
As Professor Farnsworth has said: "Good news, everyone!"

Using a tip from a fellow Ubuntu user Jason Straight about unoconv and kaibob's openoffice idea. I searched a bit more and tracked down the errors I was getting and installed a couple more packages.

Tested on 8.04 and 8.10
```
apt-get install cups-pdf openoffice.org openoffice.org-java-common openoffice.org-headless unoconv
unoconv -f pdf file.doc
```

unoconv: [http://dag.wieers.com/home-made/unoconv/](http://dag.wieers.com/home-made/unoconv/)
openoffice from terminal: [http://www.oooforum.org/forum/viewtopic.phtml?t=56063](http://www.oooforum.org/forum/viewtopic.phtml?t=56063)

As expected the PDF output is placed into cups-pdf's default directory of ~/PDF

I still would of liked cups-pdf to handle all formats, but this works and I didn't need to install Xwindows (gnome/kde). SSH and web server bliss :-)

---

