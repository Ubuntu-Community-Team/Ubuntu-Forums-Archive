---
title: "Howto add 'edit template' option for LibreOffice templates, Lubuntu 18.04 LTS"
date: 2018-08-29
forum: Desktop Environments
---

### Post by mikeymikec on 2018-08-29
I migrated from Win7 to Linux a few months ago.  One thing I make liberal use of in my business is having a load of invoice templates stored in my invoices folder, and in normal use I'd just double-click on a template to start writing a new document based on that template.  In Windows I'd go into Windows Explorer, into my invoices folder, double-click on a template, off I go.

If however I wanted to edit a template on Windows, I'd right-click on the template and click on 'Open' (as opposed to the double-click action is 'New' which would open a new document based on that template), which would allow me to make changes to the template itself.

One thing I'm finding a bit fiddly on Lubuntu is how to go about editing a template file (and firing up a quick VM of Kubuntu suggests a similar problem, don't know about Ubuntu though), because right-clicking on the file in a pcmanfm window just gets me options along the lines of 'which program do I want to open this file with'.  I wonder whether creating a custom command line option is the way I need to go (available through 'open with...'), but I'm a bit nervous about that option as I don't know how to undo a mistake I'll inevitably make if I try to figure it out myself (I guess a way of testing prior to making the custom entry would be to run the command line I'm testing through terminal to see whether I get the desired result?  But that's not all that needs to be done there).

On L/Kubuntu the only way I can see to edit a template is to start by firing up LibreOffice, then File > Templates > Open Template.

I'm using Lubuntu 18.04 LTS with LibreOffice 5.4, and the test VM was Kubuntu 18.04 I think with LibreOffice 6.0.

---

### Post by ajgreeny on 2018-08-29
Your way of managing templates by having them in the normal document folders is not the way LO does things but I can't comment on Microsoft Office as I never use it, and have not done so for about 25 years or more. I am also not sure whether you want to make a permanent change to a LO template or just use a template and make changes to it for a single document or invoice.

Both are possible but to make the change permanent you need to open a template ,make the edit or create a new one, then go to **File ->Template ->Save as template** where you can choose which type of template it will be, usually My Templates for ones you create.  By default any templates are saved in the configuration folder of LO, ie, ~/.config/libreoffice/4/user/template/ as name.ott (or name.ots for calc templates) and when opened from the **File ->Templates ->New Document from template** will open an untitled new file so will not inadvertently overwrite a template when you save a file.

Apologies if I misunderstood your Windows way of dealing with templates and have got this completely wrong.

---

### Post by mikeymikec on 2018-08-30
I should have said that I've been using OpenOffice/LibreOffice on Windows since I stopped using MSO around 2002-2003, so how I described editing templates on Windows is how I've been editing LibreOffice templates on Windows and storing them wherever I want (it also made for smaller backups back in the days when I was more concerned about that, just being able to back up my Documents folder was nice).

As for the 'open with' option I'm talking about, here's how it is with Windows out of the box:
[IMG]http://lorien.legolas.com/edited%20screenshot.png[/IMG]

That 'open' entry is something I'd like to implement on Lubuntu, but before I started faffing around with that I wanted to check if anyone had any easier ways of editing templates or if anyone had already done what I wanted to do.

---

### Post by mikeymikec on 2018-12-19
I had a crack at this myself in the end, it wasn't as tricky as I expected.  This page helped:
[https://help.libreoffice.org/Common/Starting_the_Software_With_Parameters](https://help.libreoffice.org/Common/Starting_the_Software_With_Parameters)

Right-click on a LibreOffice template, click on 'open with...'.
Click on the 'custom command line' tab.
Command line to execute:  libreoffice -o
Application name: Edit template
Click on OK

That will get you an entry on the right-click list labelled 'Edit template'.  This is as far as you - strictly speaking - have to go to achieve adding an entry to the right-click menu.

It doesn't have an icon, so if you want to add one you need to edit the configuration file that Lubuntu just generated.
It is stored in ~/.local/share/applications, and its file name looks automatically generated to me so you'll need to look for a file that has just been edited in there.
Ignore mimeinfo.cache, mine was virtually empty.
I have one called 'userapp-libreoffice -o-NTVYTZ.desktop' (interestingly with apostrophes at each end of the file name)
Edit whatever file that looks like the one I've just mentioned with your favourite text editor and add a line:

```
Icon=libreoffice-startcenter
```
(I got that from /usr/share/applications/libreoffice-startcenter.desktop)
Save the file.

Now you should have a fully-functional right-click open for LibreOffice writer templates.  You could give it a LO Writer icon if you liked (change 'libreoffice-startcenter' to 'libreoffice-writer'), but I feel that it's mildly helpful to have a different icon in order to help steer the brain towards the correct choice.

---

