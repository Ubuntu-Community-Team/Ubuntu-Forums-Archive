---
title: "Need help for spell check in texmaker"
date: 2009-02-26
forum: Education &amp; Science
---

### Post by wangcongno on 2009-02-26
This is my first time to use texmaker, this software is very good I think, except one thing, i.e. the spell check is not working on my computer....

I downloaded the dictionary package from the website in the help document, extract it in my computer and configure is right, I think. But... it's not checking my wrong spell....

Any suggestions??

---

### Post by hzambran_cl on 2009-02-26
Assuming that you followed the instructions given on:

[http://www.xm1math.net/texmaker/doc.html#SECTION03]("http://www.xm1math.net/texmaker/doc.html#SECTION03")

my only suggestions are:
a) re-open your document, and/or
b) put the cursor at the begining of your document

It works for me.

Regards

---

### Post by wangcongno on 2009-02-26
> **hzambran_cl said:**
> Assuming that you followed the instructions given on:

[http://www.xm1math.net/texmaker/doc.html#SECTION03]("http://www.xm1math.net/texmaker/doc.html#SECTION03")

my only suggestions are:
a) re-open your document, and/or
b) put the cursor at the begining of your document

It works for me.

Regards

Thank you 4 ur reply.
I do follow the instructions.
No matter where I put my cursor, nothing changes....
:(((((((((((((((((((((((((((((

---

### Post by QuimNuss on 2010-01-14
You should check if spellchecking works on OpenOffice. If it does, you have dictionaries installed, so it must be a misconfiguration of Texmaker. What worked for me is selecting the myspell dictionaries, located under 

```

/usr/share/myspell/dicts/

```

You can do a

```
locate en_US.dic
```

to find them too.

---

### Post by gadget3000 on 2010-03-14
You need to put all the files from the openoffice zip file (e.g. en_GB.zip) into the same folder as the *.dic file. You then select the dictionary from the configure menu in texmaker.
The same applies to the thesaurus.

---

### Post by boldexplorer on 2010-10-04
Thank you QuimNuss! 

Your suggestion worked like a charm.
Changed the configured the Spelling dictionary setting in Texmaker to /usr/share/myspell/dicts/en_GB.dic and now the spelling works. I didn't even have to restart Texmaker. 

On a subsequent issue, do you know how to add words to the dictionary? 

Thanks

---

### Post by greatwil on 2010-10-05
> **QuimNuss said:**
> You should check if spellchecking works on OpenOffice. If it does, you have dictionaries installed, so it must be a misconfiguration of Texmaker. What worked for me is selecting the myspell dictionaries, located under 
 
```

/usr/share/myspell/dicts/

```
 
You can do a
 
```
locate en_US.dic
```
 
to find them too.
 
> **hzambran_cl said:**
> Assuming that you followed the instructions given on:
 
[http://www.xm1math.net/texmaker/doc.html#SECTION03](http://www.xm1math.net/texmaker/doc.html#SECTION03)
 
my only suggestions are:
a) re-open your document, and/or
b) put the cursor at the begining of your document
 
It works for me.
 
Regards
 great resources! thank you !

---

### Post by sergio91pt on 2010-10-28
just gonna quote what I said on another topic regarding this issue:

> **sergio91pt said:**
> as larsonj said use the ones in /usr/share/hunspell/
I was looking for the pt-pt dic, and the myspell package installs it to the hunspell directory wich works!

guys, you might want to use [TexMakerX]("http://texmakerx.sourceforge.net/") instead, as it has an option to change to GTK!

---

### Post by stallinux on 2012-02-13
> **gadget3000 said:**
> You need to put all the files from the openoffice zip file (e.g. en_GB.zip) into the same folder as the *.dic file. You then select the dictionary from the configure menu in texmaker.
The same applies to the thesaurus.


Still did not work. I copied en_US.dic to /usr/share/myspell/dicts/
But, indeed, you have to put [SIZE=4][COLOR=Red]**all**[/COLOR][/SIZE] files there, not only the .dic

Then it works! (Sometimes it helps to read :-) )

---

