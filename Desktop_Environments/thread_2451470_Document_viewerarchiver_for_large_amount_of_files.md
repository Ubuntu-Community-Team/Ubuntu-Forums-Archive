---
title: "Document viewer/archiver for large amount of files"
date: 2020-10-05
forum: Desktop Environments
---

### Post by jenniferruurs on 2020-10-05
I have pdf files of all our clients in pdf file. All our customers have their own PDF file. The name of the pdf file is based on customer id (each customer has its own id).


Now I have so many (150000 in one folder with 20 subfolders) PDF files that searching for this PDF is extremely slow.


Is there a document archive system where I can automatically open these PDF files in a viewer and archive them and that this system opens the documents quickly?

---

### Post by TheFu on 2020-10-05
What, exactly, do you mean by "document archive system?"

Fast PDF files don't have scanned images inside them.
Fast PDF files are created directly by the document authoring tools - either through an "Export to PDF" option or through a printer driver like Adobe Distiller.  Distiller used to make the most optimized, fastest, automatically hyperlinked (TOC and Index) PDF files.

Viewers are usually outside the document management system, so the speed to open those documents is dependent on the PDF source type, network performance, how optimized the PDF files are and lastly, how fast the viewing computer is.  I used to work in the DMS field.  Actually wrote a library management program at the first client. We handled millions of documents and had most available around the world for about 6000 internal clients. A few documents, health stuff, were restricted to only the individual user and the medical team.

If you need to search PDF files, don't use the PDF search. Those are tool slow. Use something like **Recoll**, which can pre-index all the files. Recoll is like google for your system.  There is a GUI or you can do a little scripting to have a webpage search form and search results.

Recoll is just a file search tool. There are many others.  [https://www.linuxjournal.com/article/6652](https://www.linuxjournal.com/article/6652) is an article from a former coworker and friend for how to create indexes which can be used to quickly find documents.  I used to do it that way, before I found recoll.

As for a DMS, that's a completely different question.  I've deployed many of them, some costing $2M+.  There is a free DMS called Alfresco, but they follow the "open core" model. Most of the time, people end up spending $250K to create pretty front-ends to Alfresco so end-users aren't frightened.  WhiteHouse.gov had a Drupal front-end and Alfresco DMS on the back end under Obama, for example.  I deployed Alfresco, only the free stuff, inside my tiny company.  Due to all the enterprise features, it slowly died from lack of use.  When a few project managers refuse to use a tool because it was too complicated, I knew it was time to give up.  In the end, we used organized directories and Unix permissions to control access instead.  I setup recoll to index the corporate documents daily and provided a search form.

Another consideration would be to put the documents into something like NextCloud or OwnCloud.  India (the country) has the worlds largest OwnCloud setup. Every citizen of India gets their govt documents placed into the OwnCloud instance that they can access to see (view) exactly what the govt documents say.  [https://owncloud.com/news/mylinuxrig-com-indian-government-embraces-owncloud/](https://owncloud.com/news/mylinuxrig-com-indian-government-embraces-owncloud/)  If the Indian Govt thinks it scales for their needs, perhaps that could work for you as well?  

I have a NextCloud (it is a fork of OwnCloud) instance for my family. There are some very nice things about it, but we generally do not use the document storage capabilities at all.

If you want to open a bunch of PDF files, all in the same directory, in some specific order, just to validate them 1-time, perhaps a little script is all you need?  If you pass all the names into the PDF viewer, it will open all those files up into separate windows. That's a pain when you want 1 file open and for the next file to be opened only after the prior file was closed. A little script can make that open-1-file at a time possible.

One last thought, probably not very useful at all.  There is a document/book system called **Calibre**. It handles PDF, epub, and probably 5 other formats. If the correct tools are installed, it can convert between those formats, so an epub can be converted to a PDF, if you like.  Conversion from PDF to other formats seldom makes a readable document, in my experience, but all the text do end up in the new format, just not always in the correct order. PDF files can be authored in strange ways. Pages with multiple columns drive the converters crazy. Calibre can only search file metadata, not the complete text inside.

So, there are youtube introductions for most of these things, so you don't need to do a bunch of reading to figure out if any would be useful.  Alfresco would have the largest learning curve.

---

