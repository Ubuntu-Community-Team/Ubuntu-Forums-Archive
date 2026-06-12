---
title: "Working with Windows colleagues"
date: 2009-05-17
forum: General Help
---

### Post by phen on 2009-05-17
Hello!

Since May 1 I am working at the university and i am going to write a phd thesis. Usually pdf is the format of choice to share documents and especially a long document like a thesis. BUT last week my professor told me that he only accepts word documents. no pdf, no latex just Word.

Other colleagues tried to explain that pdf offers tools to make notes to documents, too. but nothing helped.

Now i am ruling out my options: find a perfect latex or pdf to word converter; write in openoffice with docx compatibility; using virtualbox with windows; or going dual boot (i would hate to) :-(

what do you think would be the best? I need a reliable solution because i soon have to concentrate on the content, not on the file format of the document :) thanks for help

bye

---

### Post by s.fox on 2009-05-17
Hi,

Perhaps I am misunderstanding but could you not simply write your thesis in open office writer and save in .doc format?     The people at the university should be able to open it fine.  Or is it necessary for you to save in .docx ?

-Ash R

---

### Post by mark.giblin on 2009-05-17
I would .rtf the file because that means that wordpad can also read it if for some reason the end user has not got .doc or OO stuffs the .doc when writing it to disc.

I have noticed some .doc's I have made will not open in MS Office but the .rtf files open and they also open in wordpad.

Their is nothing wrong with pdf files, I think your tutor is not beeing accomodating and if his system is not up to date, then its possible that he has not got the most recent reader.

Fact that PDF files are a standard document that you can protect at different levels is possibly why that professor does not like them, he possible is copying and pasting stuff and that is something in pdf's that you can set as a no no option...

Perhaps if you went to the Uni net admins office and say you have a message from professor <insert name here> that he is having conectivit issues as well as some other problems like he can not open pdf files and needs his computer updated, etc.. Get the so-n-so that way... But remember to give a false name for yourself if asked.

---

### Post by mb_webguy on 2009-05-17
Unless you've already written a non-insignificant portion of your thesis, I'd just use OpenOffice and save as a Word document.  Every pdf converter I've ever used has been... less than perfect, some more so than others.

You missed an option, btw...  MS Word 2003 will run just fine under Wine.  OpenOffice is great, and can save documents in Word format, but some of the more advanced features don't necessarily translate perfectly from Word to OpenOffice or vice versa.  If you have a copy of Office 2003 laying around, just install it under Wine and you don't have to worry about any possible incompatibilities.

---

### Post by phen on 2009-05-18
thanks for your answers!

What I have seen is that Word via Wine is not perfect. There were Copy/Paste issues and some errors with the window borders.

Is openoffice saving as .doc reliable ? I need all the features for my document which is going to be quite long. I think that converting to .doc is not allways 100%. I thought that (because docx is somehow more open than .doc) docx would work better

If nothing helps, i use virtualbox with xp and word2007, at least its all paid by the university

---

### Post by Volt9000 on 2009-05-18
If you want to guarantee 100% compatibilty, the best thing to do is run Word in a virtual machine running Windows. A bit overkill for something as simple as typing up a document, but in this case apparently a necessity.

As an aside, just my 2 cents' worth, I think it's incredibly silly that a professor would accept ONLY an MS Word document. At least PDF-- an incredibly common cross-platform format that's universally accepted.

Just out of curiosity, did you ask him/her why PDF is not allowed?

---

### Post by Old *ix Geek on 2009-05-18
> **Volt9000 said:**
> As an aside, just my 2 cents' worth, I think it's incredibly silly that a professor would accept ONLY an MS Word document.I must jump on my anti-M$ soapbox for a moment.  OP, if people like you don't speak up to people like your professor and inform them that you're a Linux user and don't have M$ Word, how will they ever know?  They need to have the error of their ways pointed out to them, else we can continue to expect the assumption that everyone uses windoze. :rolleyes:

---

### Post by Jerry N on 2009-05-18
Most professors **DON'T** like having their errors, shortcomings, and biases pointed out to them!  Any satisfaction you derive from doing that may be short lived, come the next grade posting time.  DAMHIKT!

Jerry

---

### Post by sloggerkhan on 2009-05-18
I think you should do it on open office, save it in ODT and tell your professor that because his version of word hasn't been updated to support all international document standards he needs to install [http://www.sun.com/software/star/odf_plugin/](http://www.sun.com/software/star/odf_plugin/) to work with your paper.

---

### Post by phen on 2009-05-18
> **Volt9000 said:**
> 
As an aside, just my 2 cents' worth, I think it's incredibly silly that a professor would accept ONLY an MS Word document. At least PDF-- an incredibly common cross-platform format that's universally accepted.

Just out of curiosity, did you ask him/her why PDF is not allowed?

It seems that they had copy paste issues with pdfs a not so long time ago. i know what they were talking about. you need several non standard symbols for german language, and there exist several ways to get them into an pdf (encoding, latex packaes, bla bla). apparentely, that caused problems somehow. the cause that they dont allow pdfs anymore is that they often need text snippets or figures for posters or conference abstracts or other articles. 

I have to admit, that if you want to create a poster in powerpoint, the simplest way is to copy images/texts from another office software, even if pdf would not be THAT difficult in comparison.




> 
I must jump on my anti-M$ soapbox for a moment. OP, if people like you don't speak up to people like your professor and inform them that you're a Linux user and don't have M$ Word, how will they ever know? They need to have the error of their ways pointed out to them, else we can continue to expect the assumption that everyone uses windoze. 

I am getting paid by him to do my research, and they pay everything i need. even a windows and word copy for home. the argument that i dont own a copy of word is not valid and makes it even harder to argue with your new employer in the first 3 weeks :).

Still, I dont like to go dual boot with my private pc and I think that Im going to virtualize windows.... 

ps: im working in the field of medical/laboratory engineering, which is a windows world. every single piece of software (drivers, user interfaces, etc) for equipment is windows. No chance to change this world in the short term....  I think i need a virtual machine :)

thank again for the replies!

---

### Post by SoCalChris on 2009-05-18
Personally, if I were writing my phd thesis, and was told that it is required to be in MS Word format, I'd suck it up and install Word in a VM as you'd suggested. It's not worth going on a moral crusade against MS in this circumstance.

---

### Post by phen on 2009-11-19
hello all,

after some time, i thought to give a small update.

Word equation editor drives me mad!!!

But there is hope: Word 2007 reads clean-formatted openoffice documents quite well. openoffice math is much better than word equation editor, but still it is not latex. 

i will give ekee a try next time, it converts latex formula into images. using links in your document should make this a good solution.

I miss embedded postscript with psfrag. they want their images in bad quality..

---

