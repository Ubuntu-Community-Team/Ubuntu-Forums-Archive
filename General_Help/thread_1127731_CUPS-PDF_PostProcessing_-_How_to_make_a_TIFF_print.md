---
title: "CUPS-PDF PostProcessing - How to make a TIFF printer"
date: 2009-04-16
forum: General Help
---

### Post by epedersen on 2009-04-16
Warning: The problem with using this method to create TIFFs is that the CUPS-PDF printer is hacked and will continue to generate TIFFs until the /etc/cups/cups-pdf.conf 'PostProcessing' line is commented out again.  It's not hard to fix, but it's not pretty.  Maybe someone else can run with this and come up with a more elegant solution.

Proceed at your own risk.

I needed to make a TIFF-creation printer, rather than a PDF printer.  Luckily there is a good template to work from using the 'cups-pdf' package.  The cups-pdf package is installed from the terminal with the following command:

```
apt-get install cups-pdf 
```

I modified the cups-pdf.conf file to de-comment the 'PostProcessing' section and added the path to my post-processing script (included below).  The pdfpostproc.sh script probably shouldn't be in the /etc/cups folder, but I'm lazy and don't want to have to look for things. ;)
```

sudo gedit /etc/cups/cups-pdf.conf
```

Change:

```
### Key: PostProcessing
#<Comments removed for clarity>
# PostProcessing

```
To:

```
### Key: PostProcessing
#<Comments removed for clarity>
PostProcessing /etc/cups/pdfpostproc.sh
```


Save the 'pdfpostproc.sh.txt' file (below) as '/etc/cups/pdfpostproc.sh' and change it to be executable with:

```
sudo chmod 755 /etc/cups/pdfpostproc.sh
```

Restart the CUPS server with:
```

sudo /etc/init.d/cups restart
```

Try printing a test page.  Go to 'System', 'Administration', 'Printing', and right-click on the 'PDF' printer.  Choose 'Properties', and click on 'Print Test Page'.  There should be a file called Test_Page.TIF in your ~/PDF folder.  (You may have to make a PDF folder under /home/<your username>/ folder before the script works properly.  Also, please see the reference to AppArmor below.)

This project was inspired by this [_thread_]("http://ubuntuforums.org/showthread.php?t=750426").  I shamelessly took the author's "pdfpostproc.sh" script and hacked it to bits.:P

**A NOTE ABOUT APPARMOR**
You may need to modify AppArmor's behavior with the following code, otherwise no TIFF's will be created:

```
sudo aa-complain cupsd
```

The blessed pdfpostproc.sh script:

---

### Post by dundee5 on 2009-12-10
Great, thank you!

---

### Post by splashd on 2012-11-23
Thanks, That was very helpful:)

---

### Post by wildmanne39 on 2012-11-23
Old thread closed.

---

