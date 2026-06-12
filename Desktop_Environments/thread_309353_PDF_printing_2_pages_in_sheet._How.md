---
title: "PDF: printing 2 pages in sheet. How?"
date: 2006-11-29
forum: Desktop Environments
---

### Post by mahavishnu on 2006-11-29
How can I print 2 pages in a single sheet in ADOBE READER 7 ?

The dialogue box is differnte from windows version of ADOBE READER.

There's no scalling options?

---

### Post by mitch.c on 2006-11-29
> **mahavishnu said:**
> How can I print 2 pages in a single sheet in ADOBE READER 7 ?
You can use cups lp or lpr command with the n-up option from the command line:
```
$ lp -o number-up=2 /path/to/your.pdf
```
See [http://www.cups.org/documentation.php/options.html](http://www.cups.org/documentation.php/options.html) for more documentation about printer options.
> **mahavishnu said:**
> The dialogue box is differnte from windows version of ADOBE READER.

There's no scalling options?
The acroread print dialog is limited (compared to Windows) since it cannot make assumptions about the printing subsystem.

---

### Post by mahavishnu on 2006-12-02
Couldn't print. Don't know what this error means. Sorry for the noob questions.

lp: Error - no default destination available.

---

### Post by mitch.c on 2006-12-02
> **mahavishnu said:**
> Couldn't print. Don't know what this error means. Sorry for the noob questions.

lp: Error - no default destination available.
It means you haven't set a default printer. So add the printer name:
```
$ lp -d yourprintername -o number-up=2 /path/to/your.pdf
```

---

### Post by mahavishnu on 2006-12-02
thanks mitch.  let's see this:

ubuntu@ubuntu-desktop:~$ lp -print -d DeskJet-840C -o number-up=2 pt7.pdf
lp: Error - priority must be between 1 and 100.

---

### Post by aysiu on 2006-12-02
Have you tried using Evince instead of Adobe Reader? I have the option to scale in the print dialogue for Evince.

---

### Post by lazork on 2006-12-03
I'm trying to do the same thing here (i.e. printing multiple pages per sheet), but the evince dialog doesn't seem to work. Not only doesn't it print multiple pages, but the option to print odd/even pages only does nothing as well.
Any ideas how to fix this? Or is there any other way to do it?

---

### Post by mitch.c on 2006-12-03
> **mahavishnu said:**
> thanks mitch.  let's see this:

ubuntu@ubuntu-desktop:~$ lp -print -d DeskJet-840C -o number-up=2 pt7.pdf
lp: Error - priority must be between 1 and 100.

Ummm... I don't know where you got the -print option, but I don't think it exists (the error message is ambiguous). The command should be:
```
$ lp -d DeskJet-840C -o number-up=2 pt7.pdf
```
Try again.

---

### Post by den benne on 2006-12-03
try kpdf, this does the trick for me

---

