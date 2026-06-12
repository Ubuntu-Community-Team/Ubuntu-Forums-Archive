---
title: "Bibliographic Databases"
date: 2008-01-29
forum: Education &amp; Science
---

### Post by rax_m on 2008-01-29
Hi all

I'm curious to know how most commercial Bibliographic databases work. Do you still have to manually enter all of the information into the fields before the database becomes useful? 
Basically what I'm wondering is: Is there an automated way for a PDF journal article to be imported into the database? 

I'm asking because I'm thinking of using Bibus as my database probably with OO. And wondering if there is more work involved maintaining the opensource product compared to a commercial product. 

Thanks in advance
Cheers
Rax

---

### Post by machoo02 on 2008-01-30
I haven't used any commercial reference managers in the last few years, but when I was using Endnote, you were required to enter all of the citation informatin by hand.  There is a program called [Referencer]("http://icculus.org/referencer/") (similar to [Papers]("http://mekentosj.com/papers/") for OS X) that can scan .pdf files for DOI codes and retrieve the citation information over the internet and add it to your reference database.  I think that Referencer can export Bibtex files, which can be imported into Bibus.

---

### Post by plvera on 2008-01-30
Hi:

Most commercial programs (including Endnote) will let you import references you find using Pubmed. This feature certainly cuts down on the typing!

---

### Post by rax_m on 2008-01-31
Thanks for the info guys! 

Unfortunately most of the articles I will be downloading are biological, so I'll be connecting to sciendirect, jstore and the like. Guess there's going to be some typing for me to do. 

Though.. my uni has an online personal DB called refworks which I can use.. but then I have to be online all the time.

---

### Post by machoo02 on 2008-01-31
If you're going to use Bibus, you can use the built-in PubMed search to look for some of your articles.  It might not get them all, but it should save you a little typing.

---

### Post by knattlhuber on 2008-02-17
> **rax_m said:**
> Thanks for the info guys! 

Unfortunately most of the articles I will be downloading are biological, so I'll be connecting to sciendirect, jstore and the like. Guess there's going to be some typing for me to do. 

Though.. my uni has an online personal DB called refworks which I can use.. but then I have to be online all the time.

You probably won't have to do any typing. Most databases allow you to download the references in BibTeX or RIS format, which you then can import into Bibus or whatever software you will be using.
As for RefWorks: It's a big piece of C.R.A.P. in my opinion. It's unreliable, clunky, and cumbersome. We used it in a course on systematic reviews, and virtually everybody in the course experienced problems with RefWorks.

---

### Post by dfmalh on 2008-07-18
Hi I am using JabRef (2.3.1), it works well for citing in Kile.

You can download/save your citations (RIS format works better for JabRef than the BibTeX format), then import them into your DB.

I use mostly ScienceDirect, PNAS, AEM, AJEV, MCB, Wily, but other that I have come across also give you the option to download/save the citation.

I haven't explored the build in "search tools". I don't think it is as powerful as e.g. EndNote.

Hope this helps.

---

### Post by dfmalh on 2008-07-18
I was also wondering...

Does anybody know if it is possible to download/save citations of books (not journals)? I have a number of scientific books that I cite, but have to manually enter all the details... It would be much easier to just download the citation, and have everything in the right place.
.

---

### Post by knattlhuber on 2008-07-18
> **dfmalh said:**
> I was also wondering...

Does anybody know if it is possible to download/save citations of books (not journals)? I have a number of scientific books that I cite, but have to manually enter all the details... It would be much easier to just download the citation, and have everything in the right place.
.

I would suggest [Zotero]("http://www.zotero.org"). Zotero is a Firefox extension that harvests citations from webpages, like PubMed, OvidSP, amazon.com (and many others). The results are stored in Zotero's reference database and can then be exported easily.
The way it works is that you go to the amazon page (or your U's library catalogue page) of the book that you wanna reference. Then a small icon appears in the URL bar, you click it, confirm the import and that's it. You can even do the bibliography management of a scientific paper with Zotero. It has OOo connectivity and can create a bibliography while you cite.

---

### Post by bapoumba on 2008-07-18
> **knattlhuber said:**
> I would suggest [Zotero]("http://www.zotero.org"). Zotero is a Firefox extension that harvests citations from webpages, like PubMed, OvidSP, amazon.com (and many others). The results are stored in Zotero's reference database and can then be exported easily.
The way it works is that you go to the amazon page (or your U's library catalogue page) of the book that you wanna reference. Then a small icon appears in the URL bar, you click it, confirm the import and that's it. You can even do the bibliography management of a scientific paper with Zotero. It has OOo connectivity and can create a bibliography while you cite.

+1 (just came in here to suggest zotero :))

---

### Post by dfmalh on 2008-07-18
Thanks, I will have a look.

I was was just wondering about the availability of a "Download Citation" link or button/link, like you see on the journal pages.

---

### Post by knattlhuber on 2008-07-18
> **dfmalh said:**
> I was was just wondering about the availability of a "Download Citation" link or button/link, like you see on the journal pages.

Zotero will give you exactly that once you've installed it.

---

### Post by dfmalh on 2008-07-19
Hi, I added Zotero, but no "book" appear in url bar...

Here is one of the books (link) that I want to cite. Maybe I am doing something wrong.

[http://eu.wiley.com/WileyCDA/WileyTitle/productCd-0470010371.html](http://eu.wiley.com/WileyCDA/WileyTitle/productCd-0470010371.html)

Could you see if it works on your end?

---

### Post by knattlhuber on 2008-07-19
You have to start Zotero by clicking on the "zotero" button in the status bar.

Mind you, that website you provided does not seem to work (yet) with Zotero.

Try this one instead:
[http://www.worldcat.org/wcpa/isbn/9780470010372](http://www.worldcat.org/wcpa/isbn/9780470010372)

Click on the book symbol in the URL bar. The book is now added to your collection. You can export your collection by right-clicking the collection in the left panel and choose export.

---

### Post by knattlhuber on 2008-07-19
I just saw that with worldcat.org Zotero seems to not be able to pick up the book's edition.
[Amazon.com]("http://www.amazon.com/Handbook-Enology-Chemistry-Wine-Stabilization/dp/0470010371/") works fine though.

---

### Post by dfmalh on 2008-07-22
Hi, I tried it, and it works. I will use it for a while and see if I like it more than JabRef. At the moment I prefer JabRef. 

Also, you can't export your citation to a file while Zotero is running, it take over and imports the citation.

I guess, you can export from Zotero, and then import into JabRef, but that is an extra step...

---

### Post by anatolica on 2008-12-06
I strongly recommend Zotero, as you can export to/ import from RIS/BibTex, etc. and you can also create bibliographic items from webpages according to your needs. see the screencasts at zotero homepage, I believe you'll find it very suitable to most your needs.

---

### Post by jeff.kaden on 2008-12-12
Thanks knattlhuber
Links you referred are informative enough.

---

### Post by FountainDew on 2008-12-13
Hi, i'm new to Linux and I'm curious about Zotero. I'm a very basic user that has to write papers with reference lists for my science classes. I've been shown how to use refworks but only with Microsoft Office. I downloaded Zotero, exported the library into an RIS file and opened it in OO Word, but all I got was some weird format that requires alot of editting. Is this how to use this program correctly?

---

### Post by UbuWu on 2008-12-14
> **FountainDew said:**
> Is this how to use this program correctly?

No, you should install the openoffice extension. See [http://www.zotero.org/support/openoffice_integration](http://www.zotero.org/support/openoffice_integration)

---

### Post by FountainDew on 2008-12-14
thanks UbuWu. I gotta say, after using Zotero for two days, I quite like the simplicity of it.

---

