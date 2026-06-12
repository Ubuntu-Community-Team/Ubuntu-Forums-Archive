---
title: "Extract text from flash website"
date: 2009-02-11
forum: General Help
---

### Post by Clayton South on 2009-02-11
Hi fellow Ubuntu lovers,

A quick question: Is there an Ubuntu program that extracts text from a flash website? Really appreciate some help.

Thanks!

-Clayton South

---

### Post by slmagus on 2009-02-11
Use wget to download the page. and then use awk or sed and some regular expression to parse out the html and get at the text. 

I assume your understand that text inside of a flash element cannot be extracted without decompiling the flash executable. 

If I may ask what website?

---

### Post by Clayton South on 2009-02-11
> **slmagus said:**
> Use wget to download the page. and then use awk or sed and some regular expression to parse out the html and get at the text. 

I assume your understand that text inside of a flash element cannot be extracted without decompiling the flash executable. 

If I may ask what website?

Hi, thanks for the quick reply!

I've never extracted text from a flash website before - it seems rather unusual in my experience that someone would use flash for text - it's usual only for video. 

Here is the website: [http://www.americell-labs.com/shopexd.asp?id=16](http://www.americell-labs.com/shopexd.asp?id=16)

Thoughts?

-Clayton South

---

### Post by slmagus on 2009-02-12
The only part that you be able to scrap text information out of is the header and price information

search around for html parsing scripts

---

