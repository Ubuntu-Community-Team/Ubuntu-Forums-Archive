---
title: "PDF manager for scientific papers!"
date: 2009-07-13
forum: Education &amp; Science
---

### Post by fisheater on 2009-07-13
Hi all,

I am a scientist with a hard drive full of research papers in PDFs and want to get some order.

Looking for a PDF manager that can organize them, let me annotate them, and let me print them.

Inspired by Papers ([http://mekentosj.com/papers/](http://mekentosj.com/papers/)) and Mendeley ([http://www.mendeley.com/](http://www.mendeley.com/)), but neither of them are FOSS or opensource. 

I stumbled across one that the New Scientist raved about, but of course, I forget its name.

Any suggestions on good, opensource PDF organizers?

System: Ubuntu 9.04 64 bit.


Thanks

FE

---

### Post by hubie on 2009-07-14
Lately I've been playing around with [I, Librarian]("http://www.bioinformatics.org/librarian/index.php").  It has a nice batch upload feature.

---

### Post by tgalati4 on 2009-07-14
man scrollkeeper

---

### Post by XCan on 2009-07-14
Since you probably are already using latex to write your paper and bibtex to cite, I would definitely say get a manager that integrates well with .bib files. I use Jabref (in synaptic) for this purpose, and am very happy with it.

---

### Post by machoo02 on 2009-07-14
[Referencer]("http://icculus.org/referencer/")

---

### Post by slaanco on 2009-07-14
referencer +1

---

### Post by fisheater on 2009-07-14
Wow, thanks for the replies!

I have tried i, librarian (but it was too complicated to set up). I am linux n00b. I may fuss a bit more and see if I can get it running.

I have tried JabRef, but couldnt make sense of how to import PDFs.

I have now tried Referencer and it seems to be a good fit. 

Thanks again for pointing me in the right direction.

FE

---

### Post by XCan on 2009-07-14
Easiest way to import a pdf in JabRef is simply to drag the pdf onto the entry it should be associated with. One entry can be associated with multiple pdfs too. :)

---

### Post by anatolica on 2009-07-17
Referencer +1

However there is also [gPapers]("http://gpapers.org/"), which is very much like Papers (mekentosj); and though still in subversion, it can be run from within jaunty not with that much difficulty (you'll need a couple of tweaks):
see homepage at: [http://gpapers.org/]("http://gpapers.org/")
And for the code page: [http://code.google.com/p/gpapers/]("http://code.google.com/p/gpapers/")
The only thing I couldn't manage to get working is the Google scholar parser: I couldn't make it work yet (broken???)

Although not as mature as Referencer, gPapers is more what I'd like to see developed interface-wise (if only I knew how to code!). Or even better, a merge of both Referencer and gPapers would be great indeed.

---

### Post by bubblehead74 on 2009-08-24
> **fisheater said:**
> I have tried i, librarian (but it was too complicated to set up).

Please note that there are both [graphical and console installers]("http://bioinformatics.org/librarian") available now for Ubuntu.

---

### Post by bubblehead74 on 2009-08-24
> **hubie said:**
> Lately I've been playing around with [I, Librarian]("http://www.bioinformatics.org/librarian/index.php"). It has a nice batch upload feature.

Hubie! You can batch upload with the help of NASA ADS and Crossref in version 2.0.9. Enjoy!

---

### Post by ssri on 2009-08-24
You can try [Zotero](http://www.zotero.org/), which fully integrates with firefox, imports ref files from endnote and has an openoffice plugin, almost mimicking Word+Endnote.  Unfortunately, AFAIK, it does not have citation formats for many journals out there.  I still use virtualbox with xp & word+endnote for my paper/grant writing.

---

### Post by ssri on 2009-08-24
Actually, here's a wiki site that compares different reference managers and their integration with various word processors.

[http://en.wikipedia.org/wiki/Comparison_of_reference_management_software](http://en.wikipedia.org/wiki/Comparison_of_reference_management_software)

---

### Post by XCan on 2009-08-24
Tip: Whatever you choose, just make damn sure your database is following some kind of standard. Those Word-compatible crap will just screw you over in the future with their lock-in mentalities. IMHO stick to .bib.

---

### Post by aspergerian on 2009-10-30
Although I have a personal collection of >1000 pdf files (mostly med research), I'd like (at this point) to have a manager for citations & abstracts, mostly from PubMed. I'd like to be able to search within my collection and to output selected citations/abstracts in various formats. This has become more urgent due to PubMed's new on-screen format.

This morning, I tried I'Librarian, and followed the directions txt as best I could. After the download and subsequent to extract, nothing happened. I used synaptic to see if apache and/or php are installed on my computer. Seems that apache isn't and php is. ???

I've installed Heron on two netbooks but am still a noob.  

I've read all posts in this thread. Suggestions appreciated.

---

### Post by bubblehead74 on 2009-10-30
> **aspergerian said:**
> This morning, I tried I'Librarian, and followed the directions txt as best I could. After the download and subsequent to extract, nothing happened.

Did you **extract** the tar.gz package? Did you click on **extracted** installer? If you only double-click a tar.gz, the File Roller will open it, but not extract it.

---

### Post by aspergerian on 2009-10-30
> **bubblehead74 said:**
> Did you **extract** the tar.gz package? Did you click on **extracted** installer? If you only double-click a tar.gz, the File Roller will open it, but not extract it.

Thank you for the prompt reply. I went to: 
[http://www.bioinformatics.org/librarian/downloads.php](http://www.bioinformatics.org/librarian/downloads.php)

I chose to try:

I, Librarian 2.0.9
graphical installer
(2.6 MB)
Not for upgrading. Extract and read instructions.
 
I did not try the tar.gz package, because as a noob I've often found them (or not found them) creating a program where it ought not be (my error as a noob, no doubt). 

My netbook's Heron (probably not UNR) showed me a file to extract and a text file. I read the text file and clicked on extract, but nothing seemed to happen. Also, as a noob who has installed Heron on two netbooks, along with several other programs. I'm leery of extract that may or may not open files within a directory whereby a mess is created.

Further instruction appreciated. I'd very much like to install and try I' Librarian.

---

### Post by bubblehead74 on 2009-10-30
If you have Netbook Remix, I doubt Apache will work. You need Ubuntu Desktop.

Installation instructions:

[LIST=1]
[*]Download either the graphical or the console installer. They are both packaged as tar.gz. This package contains instructions and the installer file.
[*]Right-click the tar.gz file and select Extract here. This will extract the files to the directory where you are.
[*]Double click the extracted graphical installer and enter your password when prompted. The installation will take several minutes.
[*]Open your web browser and go to [http://localhost/librarian](http://localhost/librarian).
[*]If everything seems fine, delete the extracted files. You don't need them anymore.
[/LIST]

If you want to uninstall, just remove these packages with Synaptic: apache2, php5, php5-sqlite. Finally delete the /var/www/librarian folder.

---

### Post by aspergerian on 2009-10-30
I tried again, the install seems to have worked on my HP Mini netbook with Heron.

---

### Post by aspergerian on 2009-10-30
I spend many hours per week in Pubmed, which just changed its format. 

I've written to the Pubmed help desk about RIS format and have tried Pubmed's XML and Medline formats saved a text document on my desktop. But I've not been able to import small batches of citations into I'Librarian via "import from file".

---

### Post by bubblehead74 on 2009-10-30
No need to visit pubmed.org at all. In I, Librarian, go to Add Record, then click Pubmed in left menu and enter your tagged search. You can even save your search for later use. You can search PubMed Central the same way. If you have lots of PDF on your hard drive, try PDF Batch Import. There are some basic tutorials here:

[http://www.bioinformatics.org/librarian/tutorials.php]("http://www.bioinformatics.org/librarian/tutorials.php")

---

### Post by aspergerian on 2009-10-30
> **bubblehead74 said:**
> No need to visit pubmed.org at all. In I, Librarian, go to Add Record, then click Pubmed in left menu and enter your tagged search. You can even save your search for later use. You can search PubMed Central the same way. If you have lots of PDF on your hard drive, try PDF Batch Import. There are some basic tutorials here:
[http://www.bioinformatics.org/librarian/tutorials.php]("http://www.bioinformatics.org/librarian/tutorials.php")


Generally, I don't want to save all items generated by a Pubmed search but prefer to select the several or many that I want from a larger list presented by Pubmed. That's why "Import from File" seems most relevant. That's why I'm wondering about RIS: 


Import from File
[http://www.bioinformatics.org/librarian/loadrecords.php#3](http://www.bioinformatics.org/librarian/loadrecords.php#3)
The Import from File feature serves to import reference metadata from various file formats including the Endnote XML export file, the ISI export file and RIS files from many supported repositories. This feature does not record PDF files. You can use the Import from File form to record a single reference or thousands of references at once. It is aimed to provide a convenient way to import references from Internet databases that cannot be accessed directly from I, Librarian. After you perform the search for articles of your interest at a database website of your choice, export them into a RIS file. Ask your database provider how to do it. Save the RIS file to your computer. In order to import the references, go to Add Record->Import from File. Next, select the file to import, indicate the file type, choose whether you wish to record references into your Shelf or Clipboard and click the Import button.

---

### Post by bubblehead74 on 2009-10-30
Of course. When you get the list of PubMed items, middle-click on a title of those items that you are interested in. A more detailed description will open in a new tab. You will also see various links to find a PDF file on internet. Once you find the PDF click record, add your PDF to the form and click on Record again.

For the PDFs you already have, you should really try PDF Batch Import. Just copy your PDFs into library/batch subfolder, grab a coffee and watch I, Librarian do its thing. :-)

Import from file is useful for web services that cannot be accessed directly with I, Librarian (Science Direct, Scopus and so on).

I have not been to PubMed website for months. There is no need if you use I, Librarian. I did not even know they changed the interface.

---

### Post by aspergerian on 2009-11-01
bh74, 

Thnx for the replies. For the moment, I'm going to seek a bibliographic program that imports Medline format. For a current project, I need to manipulate a large number of variously categorized abstracts/citations and don't need (at this time) to catalog my pdf collection. 

Currently, I have Bibus 1.4.3 extracted into a file on desktop, so I'll be learning tar.gz installation in ubuntu, but will post that lamentation as another thread.

---

### Post by UbuWu on 2009-11-01
> **aspergerian said:**
> 
Currently, I have Bibus 1.4.3 extracted into a file on desktop, so I'll be learning tar.gz installation in ubuntu, but will post that lamentation as another thread.

In Ubuntu 9.10 Bibus is available from the reposiroties.

---

### Post by UbuWu on 2009-11-01
> **aspergerian said:**
> 
Thnx for the replies. For the moment, I'm going to seek a bibliographic program that imports Medline format. For a current project, I need to manipulate a large number of variously categorized abstracts/citations and don't need (at this time) to catalog my pdf collection. 


Zotero is probably the easiest to import data through pubmed. You can easily import data from a single abstract or from a list of search results.

---

### Post by aspergerian on 2009-11-01
> **UbuWu said:**
> In Ubuntu 9.10 Bibus is available from the reposiroties.

Zotero is probably the easiest to import data through pubmed. You can easily import data from a single abstract or from a list of search results.

I tried zotero for quite a while, found it seemed too willing to grab screen shots, file became huge. I'm very interested in ways of shaping output that includes abstracts. 

I tried zotero yesterday while in pubmed. I'm not sure zotero has adapted to the change in pubmed that occurred this past week. 

Thank you for replying.

---

### Post by aspergerian on 2009-11-01
PS: I've a new notebook to arrive. It'll be dual boot as I intend to keep using Photoshop CS4 (Win7 & U 9.10). As a work towards having that computer the way I want it (including with Bibus), I'd like to continue using my HP Mini 1000 running Heron only and do so without daring to upgrade sequentially to 9.10.  I can update the HP Mini after I have the new notebook fully functional. And to compound my folly, I'll planning to install w7 and 9.10 as 64 bit programs. Meanwhile, learning to install Bibus-1.4.3 from a tar.gz would be very helpful.

---

### Post by samden on 2009-11-01
I've moved to Mendeley myself (on both 9.04 and Windows XP), and find it does a great job of managing my .pdf files, including syncing them between my computers. The latest version can integrate with Zotero somewhat, which may be useful for anyone wishing to migrate over.

Closed source though.

---

### Post by earlycj5 on 2009-11-01
> **samden said:**
> I've moved to Mendeley myself (on both 9.04 and Windows XP), 
Closed source though.

Much as I *love* Mendeley, this gives me mixed feelings.  They almost act open source, but not quite.  Still, good software, I've seen big strides in improvement since I started using it and having a way to centralize my PDFs on all my machines and have web access is wonderful.

---

### Post by ilsh on 2011-07-07
Peaya Paper. I use it all the time. +1
[http://www.peaya.com](http://www.peaya.com)

---

