---
title: "cups-pdf printing no extension on file"
date: 2010-04-24
forum: Desktop Environments
---

### Post by khagberg on 2010-04-24
I am running 10.04 beta2 and have installed cups-pdf printing. I can print to the PDF printer and it works fine saving the file to ~/PDF. It saves it with the PDF extension as expected. I am trying to save the file by default to a windows share. I changed the DEVICE URI line to smb://HOME/SERVER/PDF. When I print, the job shows up on the windows share but without a PDF extension. 

Any help would be great.
Thanks

---

### Post by labinnsw on 2010-04-26
> **khagberg said:**
> I am running 10.04 beta2 and have installed cups-pdf printing. I can print to the PDF printer and it works fine saving the file to ~/PDF. It saves it with the PDF extension as expected. I am trying to save the file by default to a windows share. I changed the DEVICE URI line to smb://HOME/SERVER/PDF. When I print, the job shows up on the windows share but with a PDF extension.It is unclear what your are trying to achieve. Cups pdf printer makes a pdf document of whatever you are trying to print. Your title says there is no extension, but the body of your request indicates that there is, as should be expected, PDF extensions.

---

### Post by khagberg on 2010-04-26
Sorry I am an idiot. Corrected the original post and restated below

Is I mentioned, when I installed cups-pdf it by default creates a ~/PDF directory and that is where it puts the files. When it is pointing to ~/PDF, it creates the PDF files with the PDF extension as you would expect. 

I need to automatically save these to a windows share and when I configure the DEVICE URI line to point to the smb share, I can print to the cups-pdf printer and it will create the pdf file but when it saves the file, it saves it with no extension.

---

### Post by labinnsw on 2010-04-27
[This]("http://tombuntu.com/index.php/2008/03/26/change-the-pdf-printer-output-directory/") did not work for me, but I don't understand why not. See if it works for you.

[This worked]("http://ubuntuforums.org/showpost.php?p=7739165&postcount=159") in firefox and you can allways use the PDF button or export in OpenOffice.

To mimic almost exactly your current set up and get the extension, restore cups default settings and replace smb://HOME/SERVER/PDF with a link of the same name. ```
sudo ln -s ~/PDF smb://HOME/SERVER/PDF
``` and share ~/PDF. (Making ~/PDF the link, does not work.)

---

### Post by khagberg on 2010-04-28
Thanks for the response.

When I tried the command you recommended it produced a broken link. I tried several different ways including a mounting the smb share directly to the ~/PDF directory. I got it to mount and could manually save files but whenever I printed to the cups-pdf printer i got the same response which is a valid pdf file without and extension.

---

### Post by labinnsw on 2010-04-29
> **khagberg said:**
> Thanks for the response.

When I tried the command you recommended it produced a broken link. I tried several different ways including a mounting the smb share directly to the ~/PDF directory. I got it to mount and could manually save files but whenever I printed to the cups-pdf printer i got the same response which is a valid pdf file without and extension.

What you need to do is:
1.    Restore the default cups settings (you already said that worked.
> **khagberg said:**
> I can print to the PDF printer and it works fine saving the file to ~/PDF. It saves it with the PDF extension as expected.

2.    Now share ~/PDF. 

3.    Then create a short cut on the Windows share, to ~/PDF. That is what the command does. (only, we call in symlink in Linux)

The only problem should be that when your Linux system is off, those PDFs which have not been saved elsewhere will become unavailable.

At first I was asking you to make ~/PDF the short-cut but when I tested it, that did not work. I then tried making the destination the short-cut. That worked.

I have also pointed out that you can "print to file" from most applications and specify the destination, the format, (ps or pdf) and even name the file. > **labinnsw said:**
> [This worked]("http://ubuntuforums.org/showpost.php?p=7739165&postcount=159") in firefoxThis works in much the same way as "Save as."

---

### Post by khagberg on 2010-05-08
This issue turned out to be an issue with apparmor.

After doing 

apt-get install apparmor-profiles
ln -s /etc/apparmor.d/usr.sbin.cupsd /etc/apparmor.d/disable/
apparmor_parser -R /etc/apparmor.d/usr.sbin.cupsd
/etc/init.d/cups restart

I could then save to a windows share and have it maintain the extension.

Thanks

---

### Post by labinnsw on 2010-05-09
Nice to know. How did you manage to work that out?

---

### Post by khagberg on 2010-05-10
Found the following URL that referenced broken cups pdf printing at 

[http://linuxmoc.wordpress.com/2008/11/27/printing-to-pdf-broken-in-ubuntu-intrepid/](http://linuxmoc.wordpress.com/2008/11/27/printing-to-pdf-broken-in-ubuntu-intrepid/)

Figured I would give it a shot and it worked.

---

