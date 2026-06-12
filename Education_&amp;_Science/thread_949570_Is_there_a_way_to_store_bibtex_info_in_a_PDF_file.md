---
title: "Is there a way to store bibtex info in a PDF file ?"
date: 2008-10-16
forum: Education &amp; Science
---

### Post by stumbleUpon on 2008-10-16
Is there a way in which one can store bibtex info right in a PDF file?

This would be an extremely elegant solution to manage scientific papers. PDF files are sometimes renamed and moved around and hence storing the file location and bibtex info in a bibtex file is not very useful.

However if the bibtex info can be stored in the file itself, and can be retrieved easily, one could write a simple program to read and catalog all PDF files in a directory very easily.

I tried the method of using PDF file attachments but there is a problem.
([http://ubuntuforums.org/showthread.php?t=908027](http://ubuntuforums.org/showthread.php?t=908027))

Since i have not got any replies for the above post, i was wondering if people knew any other way so store bibtex data in a PDF file.

---

### Post by earlycj5 on 2008-10-16
Am I understanding you correctly? JabRef writes XMP data to PDF files.
 
[http://jabref.sourceforge.net/help/XMPHelp.php](http://jabref.sourceforge.net/help/XMPHelp.php)

---

### Post by stumbleUpon on 2008-10-17
Yes, i have explored Jabref.

But there is a problem with the way Jabref stores XMP metadata.
It stores the complete path to the file and also the file name. So that if  move around the file or rename it, and then import it, Jabref cant open the PDF file because the file location entry and filename are set to the old values.

Besides if one wants to change the info stored in the XMP metadata of the PDF file, how does one do that in Jabref?

---

### Post by earlycj5 on 2008-10-17
> **stumbleUpon said:**
> Yes, i have explored Jabref.

But there is a problem with the way Jabref stores XMP metadata.
It stores the complete path to the file and also the file name. So that if  move around the file or rename it, and then import it, Jabref cant open the PDF file because the file location entry and filename are set to the old values.

Besides if one wants to change the info stored in the XMP metadata of the PDF file, how does one do that in Jabref?


You can't just edit the information for where the file is stored and rewrite the XMP data to PDF?

Seems like if you write the information to the PDF it doesn't matter what program you use, if you move it the information is out of date.  Perhaps I'm not understanding your motivations or question here?

---

### Post by stumbleUpon on 2008-10-18
> **earlycj5 said:**
> You can't just edit the information for where the file is stored and rewrite the XMP data to PDF?


At least it cant be done in Jabref. I write a bibtex info of a file to its XMP metadata. Then change the name of the file or move it. Import it again into Jabref. It reads the bibtexinfo correctly. But the file location is the old one. And so it cant open the PDF file when in click on it. Asking it to update the XMP metadata again, it complains of 'No PDF Linked'. I have to manually again change the file location entry.

> **earlycj5 said:**
> You can't just edit the information for where the file is stored and rewrite the XMP data to PDF?

Seems like if you write the information to the PDF it doesn't matter what program you use, if you move it the information is out of date.  Perhaps I'm not understanding your motivations or question here?

The ideal situation of what i wanted is the following.

(1) i have a directory full of PDF files
(2) i have written a python script that scans all the files in this directory (and any subdirectories for further subject classification)
(3) converts the first page of the PDF to an image format for preview (i dont know how to embed a PDF viewer inside python yet)
(4) by some method, it should check if each PDF file already has the bibtex info stored in it (one method is that of PDF attachments as i mentioned earlier, but that does not allow editing the attached attached files)
(5) if the file already has the bibtex info, it appends this info as an entry into a pybliographer ([http://pybliographer.org/](http://pybliographer.org/)) database. This is later used to implement a search engine
(6) after scanning all the files, the script has a GUI displaying the paper title for all the files that it could find the bibtex info. Those files for which it could not get the bibtex info, it highlights them in some color
(7) the program also has options to
   (a) open the pdf file in an appropriate viewer or even for annotation ([http://ubuntuforums.org/showthread.php?p=5580600#post5580600](http://ubuntuforums.org/showthread.php?p=5580600#post5580600))
   (b) go to the publishers site (via resolving the DOI)
   (c) edit the bibtex entry (for instance if i want to add notes, comments, update certain entries...etc)

The difficulty is that of points (4) and (7c). If i could only read and write bibtex info easily right into the PDF file, i think i would have a wonderful personal manager tailored to my needs.

I could just run the script and scan all the documents. Taking care of newly added files or onces that have been removed would be trivial.

I have attached a screenshot of the GUI of my script with this post. The GUI can be worked and made to look much cleaner. Besides one can add many more functionalities once the main program gets going.

---

### Post by gamelux on 2011-06-15
Hey StumbleUpon, did ever found any elegant solution for embedding the bibtex info into the pdf file? I am looking for something that would work in the command line to embed in a bash script (something like scanning a bibtex file with links to the pdf and embedding the bibtex into the pdf).

---

