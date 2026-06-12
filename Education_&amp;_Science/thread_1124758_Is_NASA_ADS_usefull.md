---
title: "Is NASA ADS usefull?"
date: 2009-04-13
forum: Education &amp; Science
---

### Post by bubblehead74 on 2009-04-13
Hi,

I am developing a PDF manager [I, Librarian]("http://bioinformatics.org/librarian"), which works seamlessly with PubMed and PubMed Central. I use these repositories heavily for my work. However, I was coquetting with the idea to enter the world of physicists, because I found a wonderful resource called [NASA ADS]("http://adsabs.harvard.edu/abstract_service.html"). Is this THE resource that you guys use? Would it be useful to have a PDF manager integrated with this service? Thanks for your comments.

---

### Post by hubie on 2009-04-13
Absolutely useful.  Tremendously useful.  It is pretty much all I use.

By the way, whether you decide to include it or not, thank you for providing very useful software to the larger community.

---

### Post by bubblehead74 on 2009-04-14
Thanks for your answer. NASA ADS is obviously useful for astrophysicists, but what about particle physicists, or other branches of physics? In any case, I will probably start playing with its integration into I, Librarian, because they have a nice interface and can provide references in XML, often with direct hyperlinks to full text PDFs.

---

### Post by mzilhao on 2009-04-14
the general relativity and high-energy physics community make extensive use of [SPIRES]("http://www.slac.stanford.edu/spires/") and [arXiv]("http://arxiv.org").
your software looks very useful, thanks a lot!

---

### Post by hubie on 2009-04-15
> **bubblehead74 said:**
> NASA ADS is obviously useful for astrophysicists, but what about particle physicists, or other branches of physics?

As you might expect, ADS includes Planetary Sciences and Solar Physics Journals.  It also includes the APS journals as well as the SPIE conference proceedings, which covers a very large chunk of the non-astrophysics stuff.  It also searches ArXiv and science education research journals.

If you want to figure out how to interface with ADS, you can start [here]("http://doc.adsabs.harvard.edu/abs_doc/help_pages/linking.html").

---

### Post by bubblehead74 on 2009-04-22
> **hubie said:**
> If you want to figure out how to interface with ADS, you can start [here]("http://doc.adsabs.harvard.edu/abs_doc/help_pages/linking.html").

Thanks for the resource. It looks straightforward enough. I will finish the transition of I, Librarian from beta to the release version, and then I will definitely look at ADS. I would appreciate getting some input on desired features of such integration. Literature mining must be very different in biology and physics .

---

### Post by GammaStream on 2009-04-26
Awesome for referencing when joined with latex and bibtex.

---

### Post by noblepa on 2009-05-14
:KS NASA ADS is absolutely useful for Astro and allied branches.

:popcorn: I have installed I, Librarian and see that it is fantastic.
 
):P If you could add NASA ADS, Arxiv, SPIRES it will be even more fantastic. Please do it fast and post the update info here.

---

### Post by bubblehead74 on 2009-05-21
I integrated NASA ADS and arXiv. You may try the [demo]("http://www.bioinformatics.org/librarian/demo/"). Let me know, if it is a step in the right direction. After some testing, I will include these features in the official release. Hopefully, SPIRES will follow as time allows.

---

### Post by hubie on 2009-05-24
I downloaded I, Librarian and went to install it on our Centos5 server.  I went to try it out and I found that it wouldn't work because there is the call to [FONT="Fixedsys"]sys_get_temp_dir[/FONT], which apparently is only good for PHP versions >= 5.2.1.  Unfortunately, Centos 5 runs 5.1.6.  I'm not sure what version Ubuntu has in the repos.

I found some web pages that tell you how to upgrade PHP to 5.2 on Centos, but it looked like a path I didn't want to go down on our office server.

I did get it to work though.  [This page]("http://us2.php.net/manual/en/function.sys-get-temp-dir.php") (in the user comments) tells one how to back-port sys_get_temp_dir into PHP 4 and 5.1.  I used the function given at the bottom of the page and I included it in the functions.php file.  I also had to add [FONT="Fixedsys"]include_once 'functions.php'[/FONT] to data.php.  With those changes it seems to be running, and I will try it out with our company to see how well it works.

I should have prefaced my comments with the statement that I don't know a lick of PHP, and I'm just now figuring out how it, apache, etc. all play together.  Thus, if there was a better way to get the code working than the path I took, I would be happy to hear about it.

---

### Post by hubie on 2009-05-24
Now that I have it working, if I go to Tools I can see under Installation Details that I do indeed need PHP version 5.2.0 or greater.  :)

---

### Post by bubblehead74 on 2009-05-24
> **hubie said:**
> I went to try it out and I found that it wouldn't work because there is the call to [FONT="Fixedsys"]sys_get_temp_dir[/FONT], which apparently is only good for PHP versions >= 5.2.1.

If you can't upgrade your PHP, this should be easy to fix. Edit data.php - insert this at the end:

```
$temp_dir = 'path/to/your/temp';
```

> **hubie said:**
> Unfortunately, Centos 5 runs 5.1.6.  I'm not sure what version Ubuntu has in the repos.

Ubuntu definitely has 5.2.something, because I tested I, Librarian with an 8.10. I am not sure at this moment what other functions won't work. Data filtering for sure.

> **hubie said:**
> I also had to add [FONT="Fixedsys"]include_once 'functions.php'[/FONT] to data.php.  With those changes it seems to be running, and I will try it out with our company to see how well it works.

I don't understand why this needed to be done. It worries me a little bit. :D

---

### Post by hubie on 2009-05-27
First off, you are correct about my install using PHP 5.1; data filtering does not appear to work.  No matter what I add or search for, text doesn't show up in the right panel.  Oh well.  Maybe I'll see whether I can either upgrade PHP, or perhaps install a second copy and run a second apache on a different port.

EDIT:  Odd: I didn't see anything in the right-hand frame until I logged out, then suddenly the entry for the paper appeared in the right hand frame.


I've also tried out your demo.  I added a paper from arXiv, which seemed to go in just fine.  I also tried to add a pdf manually and I think I've found a problem.  Just to prove that if you don't keep a user from doing something stupid he'll find a way to mess up, the paper I added did not have any fields filled in (I thought that perhaps the info would be pulled from the paper).  The paper that ended up in the library has no title, and so there is nothing to click on to bring up the record to edit and/or delete it.

I'll keep playing around with it.  Just using the demo has motivated me to upgrade PHP so that I can install my own copy.

---

### Post by bubblehead74 on 2009-05-27
> **hubie said:**
> First off, you are correct about my install using PHP 5.1; data filtering does not appear to work.  No matter what I add or search for, text doesn't show up in the right panel.

That is not due to data filtering. I actually checked, and I removed all instances of this function due to incompatibility with PHP 5.1. So this problem is something else. I only tested I, Librarian on Ubuntu and Fedora with 5.2.8 and 5.2.4 respectively. Unfortunately, I don't have resources to check all Linux distros.

> **hubie said:**
>  I also tried to add a pdf manually and I think I've found a problem. Just to prove that if you don't keep a user from doing something stupid he'll find a way to mess up, the paper I added did not have any fields filled in (I thought that perhaps the info would be pulled from the paper).  The paper that ended up in the library has no title, and so there is nothing to click on to bring up the record to edit and/or delete it.

Indeed, I, Librarian will attempt to extract DOI from a PDF. Then it will search PubMed and fetch all metadata. In the future, I will add fetching metadata from NASA ADS, plus extracting arXiv ID and fetching metadata from arXiv.

I have tried really hard, but I cannot reproduce this bug. It is definitely a bug, because under no circumstances should a user be able to record an item without a title. If you could reproduce it, please, let me know step by step how you did it.

---

### Post by hubie on 2009-05-27
I am able to reproduce the bug, but as I warned you before, I had to work hard to do what I needed to do to mess it up. :)

I first went to Add Record and selected Manual Upload.  I chose my pdf file then didn't fill in any fields because I was curious whether it would pull out the information.  I hit record, it looked like it took the file (because when it came back, it seemed to have assigned the file a number for its name along with the pdf extension).  I went back to the Library, and nothing was there.  I tried it again, and I got a warning about there being a duplicate file, but still nothing showed up in the library.

The next thing I tried was to do "Import from File".  I assumed this meant that this was what one needed to do to import the information from the file, so I hit Browse and chose the pdf file again.  The particular article I used (from the journal Optik), and I can send it to you if you need it, had the banner across the top "ScienceDirect," so naturally I chose "RIS" for the import option because it mentions Science Direct.  The only box checked was the default "Add to Shelf" and I hit "Import".  This is what added the empty entry to the library, and I was able to reproduce it on the demo as well.

I do have a question: was Manual Import the proper choice originally?  I understand why it wouldn't have found the info for any of the fields because it was a journal article that isn't in PubMed, but it seems to have imported the file but it doesn't show up anywhere that I can find like the files do when I do a PDF Batch Import, where they are given names that start with "Unknown file".

My other question, and this goes to the source of the bug, is, is the Import from File option for importing only the journal metadata, i.e., I assume I was not supposed to have fed it a pdf file?

---

### Post by bubblehead74 on 2009-05-28
> **hubie said:**
> I first went to Add Record and selected Manual Upload.  I chose my pdf file then didn't fill in any fields because I was curious whether it would pull out the information.  I hit record, it looked like it took the file (because when it came back, it seemed to have assigned the file a number for its name along with the pdf extension).

That's correct. I, Librarian will attempt to extract DOI from the PDF and search for the corresponding metadata in PubMed (NASA ADS and arXiv coming soon). If nothing is found, PDF is conveniently preloaded, you only need to manually enter the title plus as much info as you want and hit Record in order to finish the process. You can also paste DOI, and hit Record, that will also look for the metadata, but in your case it won't work, because the record is not stored in PubMed.

> **hubie said:**
> The next thing I tried was to do "Import from File".  I assumed this meant that this was what one needed to do to import the information from the file, so I hit Browse and chose the pdf file again.  The particular article I used (from the journal Optik), and I can send it to you if you need it, had the banner across the top "ScienceDirect," so naturally I chose "RIS" for the import option because it mentions Science Direct.  The only box checked was the default "Add to Shelf" and I hit "Import".  This is what added the empty entry to the library, and I was able to reproduce it on the demo as well.

Aha. Yes. This feature is meant to import reference metadata from files of these formats: RIS, Endnote XML and ISI Export File. I really need to start writing tutorials. I commited a fix; the Import File will no longer try to parse PDF. This should avoid this problem.

> **hubie said:**
> I do have a question: was Manual Import the proper choice originally?

Yes. See the explanation above.

> **hubie said:**
> ...when I do a PDF Batch Import, where they [PDF files] are given names that start with "Unknown file".

This is because it works the same way. PDF Batch Import will attempt to extract a DOI, and fetch the metadata from PubMed (hopefully NASA ADS and arXiv will follow soon). If nothing is found, you can choose to record the PDF as unknown, or not to record it. I admit the usefulness of I, Librarian for folks not using PubMed is limited right now. But I am working on including NASA ADS and arXiv in order to change that.

---

### Post by bubblehead74 on 2009-05-28
Just to explain better. There are three ways to populate I, Librarian.

1. You can start with PDF files (Manual Upload or Batch Import). The current limit is that it is not useful for literature outside biomedicine.

2. You can use Import from File to batch upload metadata from RIS file. Almost every online database allows saving references in RIS. Like you mentioned Science Direct: (i) Search for the references of your interest, (ii) check them, (iii) click Export Citations, (iv) choose Citations and Abstracts and RIS format, (v) save the file on your hard disk, and (vi) upload the file using Import from file. Import the corresponding PDF files using the Edit window (click on the record title, to get there).

3. Third way is to seamlessly import references from PubMed, PubMed Central and soon from NASA ADS and arXiv. In case of PubMed Central and arXiv, you will be able to seamlessly import PDF files as well.

---

### Post by hubie on 2009-05-28
In my first case, where I loaded the file without filling in any fields, the file seemed to have been preloaded, but I cannot see the file in the Library or shelf so that I can go back an edit the entry.  

Obviously the way to avoid this is to put something in the fields from the start, such as the DOI as you suggested, but how do I get access to the file now that it is preloaded?  The clue to me should have been that after the file was preloaded and it didn't fill in any information into the data fields, that is when I should have added some kind of additional information.

---

### Post by bubblehead74 on 2009-05-29
> **hubie said:**
> I loaded the file without filling in any fields, the file seemed to have been preloaded, but I cannot see the file in the Library or shelf so that I can go back an edit the entry. ...how do I get access to the file now that it is preloaded?

When you upload a PDF without any accompanying metadata, the file is uploaded to the server and is sitting in temp directory and waiting for your decision. You can click on the link which says ddd.pdf in Manual Upload form to download the file back, if that is what you mean by access. At this stage the PDF is not yet recorded in the collection. If you want to record it, you have to enter some title and hit Record again. If you want to abandon it, click on Manual Upload again. The file will be cleaned from the temp directory later.

---

