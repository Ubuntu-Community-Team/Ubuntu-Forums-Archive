---
title: "Humanities Writing in Lyx with Referencer - MLA??"
date: 2009-03-01
forum: Education &amp; Science
---

### Post by krgp on 2009-03-01
Hi all. Humanities prof. and linux newb here.

I'm using Intrepid, with a recently installed Lyx for writing and Referencer for bibliography management. I love the "cite in lyx" feature of Referencer, and the stripped-down feeling of lyx. My book is proceeding nicely, but I'm starting to worry that I should have stayed in a more traditional word processor.

Here's a list of my problems:
(1) I'm a humanities professor and need to use MLA citation style. HOW??? (so frustrating.)
(2) Altho my bibtex keys appear in the text of my lyx document, as inserted by Referencer, I don't know how to "automatically" have lyx generate a bibliography at the end that refers to the parentheticals in the text.
(3) I need to be able to export from Lyx into a format that my colleagues can review, i.e. rtf or doc or even odt. I need really really basic instructions for how to do this. I think I need to load some software but I don't know which, or how to do it.

Any ideas? 

I've read all of the documentation for humanities people at the lyx site. I've read the tutorials, etc. I haven't been able to find much at all on Referencer. I'm not a good linux person, but I am a good researcher.

---

### Post by eljalill on 2009-03-01
I usually don't use LyX myself (I use LaTex with Kile), so I am not sure, about the citations style. But anyway it might help, if you could describe what MLA looks like? There are very many citations styles available, and I am sure one of them would match with what you have to use. 

I am doing social sciences, and I surely have the same problem with not having a document format which I can share easily, as most of my collegues can't cope with a .tex document. However, some have either Acrobat writer, or Foxit Reader, with which they can edit, or at least comment the .pdf files. Else, the only thing I've found practicable was to copy past the text from the .pdf into an openoffice writer document. 

And just another comment, even though unasked: there is a *lot* of help and support available for using "proper" LaTex. In my view, this makes is preferrable to using LyX. Although at first sight more complicated, I find it more logical as well.

---

### Post by akniss on 2009-03-01
[http://ubuntuforums.org/showthread.php?t=639643](http://ubuntuforums.org/showthread.php?t=639643)

[http://ubuntuforums.org/showthread.php?t=394289](http://ubuntuforums.org/showthread.php?t=394289)

---

### Post by kleeman on 2009-03-01
This looks like what you may want:

[http://www.neilandtheresa.co.uk/Wiki/LyX%20MLA%20Template/](http://www.neilandtheresa.co.uk/Wiki/LyX%20MLA%20Template/)

---

### Post by krgp on 2009-03-02
Thanks for the swift replies.

I had already found the two on MLA and Latex, but of course I use Lyx and am completely baffled by "straight" Latex and the coding required.

The Lyx MLA template link is more promising...

But any ideas about the rtf, odt, or doc export from Lyx? About working with Referencer? -- This is the workflow that my colleagues and I employ, and although others would like to switch to linux, and even lyx, without the rtf/doc option, I doubt it will happen. 

Thanks again.

---

### Post by krgp on 2009-03-02
So I have downloaded an MLA .sty file but I'm encountering a problem that I often have when working with the forums for linux, an OS I am new to--namely, steps are skipped in instructions for how to use these nifty tweaks people have designed.

In this case, I cannot figure out how to actually USE a .sty file. Where do I PUT it on my hard drive? How do I tell Lyx to USE it?

Any help would be greatly appreciated. As you know, time spent futzing with the computer is time not spent writing.

---

### Post by krgp on 2009-03-02
So I just found an answer to my question about .sty files. Here: [http://ubuntuforums.org/showthread.php?t=684085&highlight=.sty+lyx](http://ubuntuforums.org/showthread.php?t=684085&highlight=.sty+lyx)

---

### Post by parktownprawn on 2009-03-03
> **krgp said:**
> Thanks for the swift replies.

But any ideas about the rtf, odt, or doc export from Lyx? About working with Referencer? -- This is the workflow that my colleagues and I employ, and although others would like to switch to linux, and even lyx, without the rtf/doc option, I doubt it will happen. 

Thanks again.

well its easy to export the document to a plain text document.

go to 

File > Export > Plain Text

RTF/DOC is slightly more challenging

1. Install the program tth. Open a terminal and type

```
sudo apt-get install tth
```

or use Synaptic.

2. Go to lyx and reconfigure it

Tools > Reconfigure

3. Restart lyx

4. You can now export your file to HTML

5. File > Export > HTML

6. This will create a subdirectory in the directory where your lyx file is containing an html file. Open this file Using OpenOffice.

7. From OpenOffice you can export the HTML file to a .doc or .rtf file.

---

### Post by kleeman on 2009-03-03
On the citation issue if I understand correctly you are asking how to create a bibliography at the end of your document once you have inserted your citation in the body of your work. This can be achieved using

Insert-----> List/TOC---->Bibtex Bibliography

A dialog appears and you choose what style you want the bibliography in.

I thought the template I linked to already had the bibliography inserted however...

As far as exporting to doc goes, that can be complicated as the last post shows. It depends how you collaborate but if your colleagues are just commenting on the manuscript and not extensively re-editing then why not just send them a pdf file? That is easily created in lyx using the export function in the File menu.

If your colleagues are reediting extensively and do not wish to use lyx you have a problem and may be advised to use open office instead. This easily creates doc files.

The key with productive collaboration in my experience is that people can easily exchange software. No point fighting against folks addicted to MS Word. Not productive imho.

---

