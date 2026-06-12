---
title: "GnuCash on KDE - or another small bus. finance package? Any ideas?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by malacoda on 2005-11-06
Almost weaned myself off windows.  The only thing really holding be back from the final step is Quicking Home & Bus.  GnuCash looks like it might work but I'm not sure if/how it'll run under KDE.

Anyone know what gnome dependencies I'd need to load for it to work under KDE and if doing this results in any bugs?

Or, does anyone know of another good small bus. finance app for linux (Moneydance, Kmymoney only appear to do personal finance, not small bus.).

I'm hoping to not have to buy Money and run it under Wine... trying to avoid another MS dependency.


Malac

---

### Post by Manny C on 2005-11-06
Have you tried [KMyMoney]("http://kmymoney2.sourceforge.net/")?

---

### Post by imnes on 2005-11-06
If you're not against spending some money, MyBooks is supposed to be pretty decent (more along the lines of QuickBooks than Quicken though)  

[http://www.appgen.com/aptus/my_books_professional_linux2.htm](http://www.appgen.com/aptus/my_books_professional_linux2.htm)

[IMG]http://www.appgen.com/aptus/screen_shots/1ambp.jpg[/IMG]

Also, under the latest version of Crossover Office ([http://www.codeweavers.com/](http://www.codeweavers.com/)) you can install Internet Explorer and run the QuickBooks Online Edition.  (The benefit there being that they maintain your data, presumably with frequent backups, and you can access your data from any PC with Internet Explorer).

[http://oe.quickbooks.com](http://oe.quickbooks.com)

[IMG]http://oe.quickbooks.com/images/screen_billable_expense.jpg[/IMG]

I've been faced with the same problem you have, and after checking things out I've settled on using the QuickBooks Online Edition.  (It didn't work well under the previous release of Crossover Office, but in my testing it works just fine with their latest.)  After checking all my options it seems like the best way to go.

I'm not sure on this but you may be able to import your existing data into the QuickBooks Online program.  If you want to check it out you can go download a trial version of Crossover Office, install Internet Explorer and Adobe Acrobat Reader to it, and then go to the QuickBooks Online Edition site and demo their stuff.  (They have a fictional company setup so you can start playing with the program right away).

Instead of using the Windows version of Adobe Acrobat in Crossover Office, I configured it to use my Linux version of Adobe Acrobat 7 instead, works fine.  If you need to know how to do that I can give you a link to the instructions.

Basically whenever you need to print something (invoices, reports, etc) they get displayed in PDF format so you can save / print them.

Nick

---

### Post by Zwack on 2005-11-06
I've used GnuCash in the past and it seems to work pretty well if you need to do double entry book keeping.

I can't say that it is what you want or need, but it may well be.  

I'm not an accountant though so I don't know if it is what you want or need.

Z.

---

### Post by funkydan2 on 2005-11-06
GnuCash runs just fine under KDE.  Just install the package "gnucash" through apt-get or synaptic or whatever your favourite interface is and it will install all the required dependencies as well.

I haven't tried GnuCash with Kubuntu, but when I was running VectorLinux GnuCash looked much nicer under KDE than it ever has under Gnome.

I don't know if it's a good Small Business app - the best way to work it out is to read the documentation on the website and install it and have a go.

---

### Post by CyberCam on 2006-06-28
Whatever you do... do not purchase Appgen's MyBooks Pro! It's a horrible piece of software and it very, very buggy! There is only one guy that does the technical support and it takes him two days to respond to an e-mail. Printing doesn't work on Dapper Drake among a number of things. After paying for the software they basically told me in a nutshell, we can't help you! So, save your money and a number of headaches, DON'T BUY Appgen MyBooks Pro!

---

### Post by SuperMike on 2006-06-28
[QUOTE=malacoda]Almost weaned myself off windows.  The only thing really holding be back from the final step is Quicking Home & Bus.  GnuCash looks like it might work but I'm not sure if/how it'll run under KDE.

Anyone know what gnome dependencies I'd need to load for it to work under KDE and if doing this results in any bugs?

Or, does anyone know of another good small bus. finance app for linux (Moneydance, Kmymoney only appear to do personal finance, not small bus.).

I'm hoping to not have to buy Money and run it under Wine... trying to avoid another MS dependency.


Malac[/QUOTE]


Try Grisbi.

---

### Post by rahelvey on 2006-07-03
downloade gnucash twice from synaptic but cant find it where would it be?

---

### Post by GOwin on 2006-07-04
[QUOTE=rahelvey]downloade gnucash twice from synaptic but cant find it where would it be?[/QUOTE]

Didn't you find it under office applications? If that fails, launch it manually via the command line. Press alt-F2 and type in gnucash

---

### Post by rahelvey on 2006-07-04
ran gnucash 1.9.8 from site then found it /usr/bin/gnucash copied to home then placed a launcher on desktop and now it works great good program for my use thanks

---

### Post by Al3xanR0 on 2006-07-06
[QUOTE=SuperMike]Try Grisbi.[/QUOTE]

I will have to agree with SuperMike try [GRISBI]("http://www.grisbi.org/screenshots.en.html"), the download link is on the leftside. If you are lucky it may be in the repositories, but if you want the most recent stable release download it from the provided link.

---

