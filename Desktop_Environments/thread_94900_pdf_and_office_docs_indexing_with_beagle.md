---
title: "pdf and office docs indexing with beagle"
date: 2005-11-25
forum: Desktop Environments
---

### Post by xain on 2005-11-25
Hi, I recently installed Beagle and I thinks it's great ... the only missing indexing files I miss are pdf and office (namely doc, xls and ppt). What must I do in order to enable this indexing ?

beagle-index-info shows:

Index information:

Name: EvolutionDataServer
Count: 18

Name: Mail
Count: 6466

Name: KMail
Count: 0

Name: Files
Count: 10820

Name: GaimLog
Count: 25

Name: IndexingService
Count: 0

Name: Tomboy
Count: 12

Name: Blam
Count: 0

Name: Liferea
Count: 0

Name: Akregator
Count: 0

Name: Kopete
Count: 0

Name: Google
Count: -1

Name: NetworkedBeagle
Count: -1


Thanks

---

### Post by royg1234 on 2005-12-03
I was wondering about this too.  I could search PDF files a few weeks ago, but I just tried it and it won't work.  Doc fiels never worked.

---

### Post by royg1234 on 2005-12-03
actually, I just checked again.  I seem to be able to search some pdfs, but not pdfs from The New Republic.  Is there something in place that makes copyrighted pdfs not searchable?

---

### Post by DrBair on 2005-12-03
I just dug this little page up: [http://beaglewiki.org/Beagle_Filter_Facts](http://beaglewiki.org/Beagle_Filter_Facts)

On the PDF front it says we need 2 command-line utilites from xpdf which isn't there by default on Breezy atleast.  Grabbing xpdf from synaptic *should* make it work.

---

### Post by royg1234 on 2005-12-09
apparently, for beagle to index Microsoft Word doc files, you need to install a package called **wv**

```
sudo apt-get install wv
```

---

### Post by NeTo on 2005-12-10
[QUOTE=royg1234]apparently, for beagle to index Microsoft Word doc files, you need to install a package called **wv**
[/QUOTE]

I haven't tried that yet, but wouldn't that need a beagle recompile?

---

### Post by royg1234 on 2005-12-11
yeah, I tried and couldn't get it to work.  It involves doing cvs stuff, and you need the *newest* versions of beagle, and wv.  I'm just gonna wait.

---

