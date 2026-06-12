---
title: "Enabling PDF annotation for Adobe Acrobat reader"
date: 2009-05-16
forum: General Help
---

### Post by MountainX on 2009-05-16
I'm running Jaunty and I want to annotate some PDF documents that were emailed to me. They are enabled for annotation already and my co-authors have made comments in the documents. Now I need to annotate and send them back in the same format.

The article indicates the Linux version of acroread will do this.
[http://www.hrstc.org/node/31](http://www.hrstc.org/node/31)

So I did these steps, but I cannot find a way to annotate:
```
sudo gedit /etc/apt/sources.list
    enable the jaunty partner repository by uncommenting 2 lines
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo update-apt-xapian-index
sudo apt-get install acroread
```

When I open an editable document in acroread, I do not get any option to turn commenting on.

What am I missing?

---

### Post by bjrnfrdnnd on 2009-12-16
Did anyone succeed in getting the annotation feature in acroread to work? Or the video playback, maybe?

---

### Post by jhformosojr on 2011-03-29
mabuhay :)

good news for those who are stucked with their pdf files... download mendeley from [www.mendeley.com](www.mendeley.com) and all your troubles with pdf files will be gone. i have been using mendeley to process, manage and collaborate all my pdf files. it allows saving of pdf annotations, you can also highlight, copy text and it even builds a bibiliography of all the pdf files used - but the best of all, it is highly integrated with openoffice, libreoffice and word for windows. 

email me at [email]jhformosojr@gmail.com[/email] should you want to know more about mendeley. i'll be more than willing to assist you.

---

### Post by MountainX on 2011-03-29
> **jhformosojr said:**
> 
good news for those who are stucked with their pdf files... download mendeley from [www.mendeley.com]("http://www.mendeley.com") and all your troubles with pdf files will be gone. .

Interesting idea... Unfortunately, it's not free as in freedom (i.e., not open source). It's also not free as in beer. It costs $4.99 to 9.00 per month for the premium plan, but they don't even tell you that until after you sign up for a limited free plan. 

If I were going for a solution like this I think I'd look at [http://www.zotero.org/](http://www.zotero.org/) or maybe [http://icculus.org/referencer/](http://icculus.org/referencer/) ...or maybe [http://connotea.com/](http://connotea.com/)

I just took a look at Zotero. Here's something from the zotero site:

> Zotero makes it a breeze to import PDFs

> Zotero can take PDFs of scholarly papers and query the Google Scholar  database for matches. The most straight-forward way it does this is by  matching up an embedded Digital Object Identifier (DOI), but that's far  from necessary. If Zotero finds the PDF  in Google Scholar, it creates a new library item for the paper,  downloads the bibliographic metadata from and attaches the original PDF  to the new item. Begin by dragging your existing PDFs into your Zotero  library (currently broken on linux) or use the “Store Copy of File”  option from the add new item menu (green plus sign). Once they appear in  the middle column, select the ones for which you wish to retrieve  metadata. Right click on them and select “Retrieve Metadata for PDF”.  If Zotero was able to find a match on Google Scholar, you should be all  set. With this feature, there should be no major hurdles to switching  to Zotero and taking full advantage of all its powerful search,  indexing, organizational and citation features.  

Maybe not perfect, but interesting... thanks for the idea.

---

