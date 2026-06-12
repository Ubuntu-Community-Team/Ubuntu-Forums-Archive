---
title: "literature documents organizer"
date: 2007-10-15
forum: Education &amp; Science
---

### Post by neoflight on 2007-10-15
folks,

if you are a or ever been grad student...

i have a lot, i mean a lot of PDF and 'other' documents in my literature collection. sometimes when iam really tight with my time, I download those on to the desktop for reading or referencing and after sometime i forget that i had such a document. sometimes i have a copy in my flash drive/email/network drive/laptop etc and if confuses the hell out of me especially when dealing with close deadlines...

is there any tool available for linux or windows where i can save the pdfs and organize automatically and provide the bibliography info so that i can import it later for latex doc if needed? 

* a tool which can facilitate subject/ context/author/year wise folder organization,

*conference/journal/thesis/technical memos etc categorization 

* duplicate document recognition

*backup utility (copy to and from hard drives/flash drives/network folders etc)

if we do not have a comprehensive tool like this, u know anyone working on this type???i would like to contribute too...

thanks

---

### Post by UbuWu on 2007-10-16
[Referencer]("http://icculus.org/referencer/") does some of it.

---

### Post by jonathonblake on 2007-10-17
> **neoflight said:**
> 
confuses the hell out of me especially when dealing with close deadlines..

Especially when those documents don't have metadata that can be easily retrieved.

> 
* a tool which can facilitate subject/ context/author/year wise folder organization,

I wish the PDFs I dealt with had that information in their meta data.  
> 
* duplicate document recognition

I extract that from the tripwire report that is generated every day. 
(It assumes that two documents, of the same size,and with same hash sums are duplicate documents. )

>  *backup utility (copy to and from hard drives/flash drives/network folders etc)

Are you wanting something to work in the background,or only to synchronize when you tell it to?

> if we do not have a comprehensive tool like this, u know anyone working on this type?

If you don't mind the traditional Unix philosophy of "one small tool for one small job", then tools for most of these currently exist.  The parts just need to be installed, and maybe glued together. 

xan

jonathon

---

### Post by hugmenot on 2007-10-19
> **neoflight said:**
> 
is there any tool available for linux or windows where i can save the pdfs and organize automatically and provide the bibliography info so that i can import it later for latex doc if needed? 


I recommend you stop dropping loose PDF files somewhere into your filesystem and start organizing them.

In scientific writing the meta-data of the articles you read is equally important to the actual content, so it&#8217;s important to keep them associated. You can do that with "jabref". It is not as automated as I wish it was, but it facilitates the work a great deal.

I usually start out with the jabref window and do a Medline/pubmed search. If your field is not indexed by pubmed, maybe one of the other search engines works for you.

Once I got the article into the table I categorize it into one of my thematic groups. Jabref uses a filter-like model with subsets for this. Then I just click on the web-link which ends up at the DOI-mediated website. I copy the [http://-link](http://-link) to the PDF and let Jabref download it. The advantage is that it sorts the file into my literature folder and it renames the file according to my scheme, for easy retrieval. It also then has a link to the PDF, that I can just click to open the document later. I.e., I can use the web-link, and I can use the PDF link. I never search my hard disk for the file.

Jabref can actually write the meta-data to the PDF file so that desktop searches can find it. That includes XMP meta-data, which emerges as a standard for PDF, like ID3 for Mp3.

If you&#8217;re unlucky you have to enter the info by hand, but there&#8217;s an autocompletion feature, so that you can reuse previous fields, like authors, etc.

---

### Post by alex-v on 2007-10-26
I use [http://citeulike.org]("http://citeulike.org") to organize my bibliography. It knows how to import data from sites such as jstor and arxiv. It also allows to upload the papers for storage so I have immediate access to them online. When I need to work with local bibtex file I export it from the web site and use kbibtex to browse.

---

### Post by hugmenot on 2007-10-26
I checked out citeulike.com and the BibTeX record it generates for PubMed at least looks reasonable. 
Still, I&#8217;ll stick to JabRef. It has loads of useful features and I definitely need a local solution.

---

### Post by neoflight on 2007-10-27
thanks a lot for your input guys....
many of the files ihave now do not have the meta-data ...
so have to manually enter stuff ..

right now i am using referencer.... 

am working on the jabref as well...

---

### Post by raja on 2007-10-30
Hello everyone,

I have been encountering the same problems for some time. I have lots of pdfs on my work pc, but searching for the one I want when I do want one was quite difficult. 

I didnt know of referencer and started out with my own solutions, writing up something in python. Subsequently, I learned about referencer, but am sticking to what I wrote. 

Briefly, what I do is this
- See if the doi (digital object identifier) is there in the pdf metadata.
- Else parse the first page of the text for the doi.
- Once doi is found, the full metadata can be obtained from Pubmed.
- If doi cannot be found, parse the first page for journal name, issue no., pages, etc, then connect to pubmed to search for the article and get the full metadata.

This automated processing picks up the metadata for atleast 75% of the documents (and almost all the newer articles). For the others, I can manually enter the pmid or doi and the metadata will be retrieved automatically.

All the retrieved metadata is stored in an sqlite database which can be searched easily by authors name, year of publication, words in title, etc. The code is still very raw (though functional) and if anyone is interested in providing ideas or other help, you are most welcome to contact me.

---

### Post by vixensjlin on 2008-02-29
What if all my pdf files are named like "PubmedID.pdf"?  (Pubmed ID is a number which is unique for every bio-related paper)

Could any program automatically connect pubmed, retrieve meta info and organized accordingly?

---

### Post by raja on 2008-03-02
Vixensjlin,

The only difficulty with that approach is the tedious job of finding the pmid for each article and renaming it accordingly - especially if you have an old collection of a thousand articles. The approach of parsing the pdf for the doi or the pmid works well too. This is the approach I adopted (though my project has been languishing for want of time at [http://code.google.com/p/medlib](http://code.google.com/p/medlib)).

Anyway since your question is about the possibility of doing this, the answer is that it is quite trivial. Pubmed provides an interface to query with pmid and retrieve the record information. The Biopython library makes this very easy though you can do this without Biopython too. The following code is an illustration and uses the biopython library (sudo aptitude install python-biopython).

```
"""
Get information about a journal article 
from the pmid
"""

from Bio import Medline, PubMed

rec_parser = Medline.RecordParser()
medline_dict = PubMed.Dictionary(parser = rec_parser)


testpmids = [17239715, 17098829, 17200449]


def get_info(pmid):
    """
    Return the record information for any pmid
    """
    record = medline_dict[pmid]
    return (record.title, record.authors, record.source)
    
if __name__ == "__main__":
    for pmid in testpmids:
        title, authors, source = get_info(pmid)
        print title, authors, source
        print "--------------------------------"
    

```

---

### Post by tim104 on 2008-12-22
I used a program in Windows called EasyArticles ([http://www.synaptosoft.com/EasyArticles/](http://www.synaptosoft.com/EasyArticles/)). It allows you to search Pubmed from within the program and, if available, it automatically downloads the pdf. I recently switched over to linux and have been looking for a replacement.....

---

### Post by samden on 2008-12-23
tim104: If all you're looking for is a reference organiser, try zotero. It can probably do something with the .pdfs too, I'm not sure, but it works great for references and will work on Linux, Windows, Mac etc so if you still switch around you can have it installed everywhere. It is a firefox extension, so integrates well with internet resources, and will also insert references in Openoffice.org or Word.
[http://www.zotero.org](http://www.zotero.org)

---

### Post by ahusain on 2008-12-25
i know this doesn't help much but for mac users an application called papers works great. 

you can find it here 

[http://mekentosj.com/papers/](http://mekentosj.com/papers/)

unfortunately it isn't free. however you can get a discounted license for students ($26) that as far as i know has all the features of a regular license.

---

### Post by gerbman on 2008-12-25
+1 jabref.

---

### Post by sybille on 2008-12-26
> **samden said:**
> tim104: If all you're looking for is a reference organiser, try zotero. It can probably do something with the .pdfs too, I'm not sure, but it works great for references and will work on Linux, Windows, Mac etc so if you still switch around you can have it installed everywhere. It is a firefox extension, so integrates well with internet resources, and will also insert references in Openoffice.org or Word.
[http://www.zotero.org](http://www.zotero.org)

Zotero is very good for organizing PDFs. You can find more information about using Zotero with Ubuntu here:
[https://help.ubuntu.com/community/Zotero](https://help.ubuntu.com/community/Zotero)

---

### Post by earlycj5 on 2009-01-05
Papers looks good and is exactly what I want but it's for OSX only.

Zotero and Jabref are bibliography managers that allow you to do some stuff with the PDF files, not proper PDF managers IMO. I have Bibus to do bibliography management, I want something to organize the PDF files themselves like Digikam or F-Spot do for photos. I still want Referencer to work, properly.  That is a true PDF manager.

*edit*  Just downloaded the latest version of Referencer, it's getting better, finding more of the information associated with articles.

---

### Post by gerbman on 2009-01-05
> **earlycj5 said:**
> Zotero and Jabref are bibliography managers that allow you to do some stuff with the PDF files, not proper PDF managers IMO. I have Bibus to do bibliography management, I want something to organize the PDF files themselves like Digikam or F-Spot do for photos. I still want Referencer to work, properly.  That is a true PDF manager.

What do you mean by a "proper" PDF manager? I use JabRef to organize my PDFs in exactly the same way that I use F-Spot to organize my photos. Create (sub-)groups, then just drag-and-drop the groups onto the PDFs. You can then select combinations of groups, etc., just like F-Spot.

Perhaps you meant that JabRef is specifically designed for LaTex, in which case you're right...if you don't care about LaTex then you probably want to stay away from JabRef.

---

### Post by sybille on 2009-01-05
Zotero can be used as a document manager. The tagging features are especially helpful for this, and it's also worthwhile to use a full-text indexing service, either the one that can be set up in Zotero or something like Tracker or Beagle. I have several hundred PDFs and many other files (word processor documents, multimedia files and web page snapshots) in Zotero, and I find it works really well for me to organize these things.

FYI, in the development version of Zotero (version 1.5), there is a new feature that will retrieve metadata for PDFs automatically from Google scholar. Here's a demo video:
[http://www.zotero.org/support/retrieve_pdf_metadata_screencast](http://www.zotero.org/support/retrieve_pdf_metadata_screencast)

But there are different tools for different needs, and every researcher has a particular way of working. I can see why a person might prefer to have a stand-alone application rather than working within Firefox, for example.

---

### Post by xadder on 2009-01-07
+1 for jabref. It is a wonderful app, and since it stores all info in the bibtex file it is very easy to work by-hand if needed. I use keywords to label pdfs by subject.

---

### Post by earlycj5 on 2009-01-07
> **gerbman said:**
> What do you mean by a "proper" PDF manager? I use JabRef to organize my PDFs in exactly the same way that I use F-Spot to organize my photos. Create (sub-)groups, then just drag-and-drop the groups onto the PDFs. You can then select combinations of groups, etc., just like F-Spot.

Perhaps you meant that JabRef is specifically designed for LaTex, in which case you're right...if you don't care about LaTex then you probably want to stay away from JabRef.

It's just semantics I guess.  It's just my perception of what the different programs focus on I suppose.  I've used and still use JabRef as well.

---

### Post by DrakeGis on 2010-07-26
You should try Mendeley Desktop (free not open). It is not perfect, but can certainly help, it allows you to insert bibliographic notes on OpenOffice Docs, some kind of online backup. 

[http://www.mendeley.com/](http://www.mendeley.com/)

---

