---
title: "gnucash install help Parser perl"
date: 2006-07-23
forum: Desktop Environments
---

### Post by Mel_K on 2006-07-23
Hi,

I am installing gnucash 2.0.0 and get this error as I try to configure:

**checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool**

I have checked the synaptic and I definitely have the Parser perl installed.
What should I try?

---

### Post by uberdog on 2006-07-31
The package you want installed is libxml-parser-perl.  Try:
sudo apt-get install libxml-parser-perl

---

### Post by initself on 2006-08-06
> **uberdog said:**
> The package you want installed is libxml-parser-perl.  Try:
sudo apt-get install libxml-parser-perl

How did you know that?

---

### Post by lexrexus on 2007-02-28
Hi,  I have same error for 'nother install and don't have access to 'net w/linux yet.  Altavista searches for source for lbxml-parser-perl yield nothing. same for said in this forum.  Where do I go to download it in windows & put on Lnx desktop to install it from there .. and, um where/how do I put it so it will be used/found by whatever needs it???  I don't speak geek, or even Linux.  Running Dapper. 
Thanks!

---

