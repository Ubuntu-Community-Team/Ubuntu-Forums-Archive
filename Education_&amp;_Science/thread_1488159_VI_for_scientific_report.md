---
title: "VI for scientific report"
date: 2010-05-19
forum: Education &amp; Science
---

### Post by km0r3 on 2010-05-19
[SIZE="4"]Short question: Is there any possibility to use (G)Vim for writing my report without loosing professionalism and flexibility?[/SIZE]

I have to do a scientific report and I began using OpenOffice, though I'm very a big fan of the VI text editor and tired of using a non-flexible text manipulation tool like OpenOffice.

More details:
The teacher really cares about the (f*cking) page borders with exact given margins and fonts. So I really need a good tool, which *can* handle all those things.
The report/investigation then should be an Open Format.

**Any suggestions?**

---

### Post by km0r3 on 2010-05-19
Wow, LaTeX looks really great. It's used even for writing books. Really cool stuff, but looks somehow bloated and complex.

Can someone beat LaTeX?

---

### Post by randyklein99 on 2010-05-19
Just use Latex.  It's pretty much a standard for technical writing.

---

### Post by radioboy on 2010-05-20
The complexity of LaTeX is compensated by the rigorous paging you are looking for. 
And after all, it's not difficult to get used to it, so the complexity tends to dissipate on time. :D
So you have an idea, I barely use OpenOffice anymore.
All my reports and presentations *are belong* to LaTeX.

Check [Beamer]("http://en.wikipedia.org/wiki/Beamer_%28LaTeX%29") and [Tikz]("http://www.texample.net/tikz/examples/"), too!

---

### Post by InfernalNeutrino on 2010-05-20
Don't forget about the [vim-latexsuite]("http://vim-latex.sourceforge.net/").

I can also attest to the fact that latex is an excellent tool for this sort of work. I haven't used office to write a paper / presentation / homework writeup etc. since I began grad school 3 years ago, and I believe my work is better for it. It certainly *looks* better :) .

---

### Post by km0r3 on 2010-05-20
> Check Beamer and Tikz, too!
Thanks, man! *Beamer* looks very, very good! This replaces OpenOffice Presentation entirely!

> Don't forget about the vim-latexsuite.

I can also attest to the fact that latex is an excellent tool for this sort of work. I haven't used office to write a paper / presentation / homework writeup etc. since I began grad school 3 years ago, and I believe my work is better for it. It certainly looks better  .

The vim-latexsuite is very useful! I tinkered around with it for some hours. This almost exactly what I've searched for.

Thanks for all the responses. I think I will stick with LaTeX.

---

### Post by FreeTheBee on 2010-05-20
You can make LaTeX as complex as you want, but for regular use it is not as difficult as is sometimes implied imho. I would suggest to read through "The not so Short Introduction to Latex" to get a good overview.

[http://mirror.ctan.org/info/lshort/english/lshort.pdf]("http://mirror.ctan.org/info/lshort/english/lshort.pdf")

The TeX FAQ is also an excellent source of information. It also has several links to other guides.

[http://www.tex.ac.uk/faq]("http://www.tex.ac.uk/faq")

---

### Post by ahmatti on 2010-05-21
You could also use reStructuredText [http://docutils.sourceforge.net/rst.html](http://docutils.sourceforge.net/rst.html). It is a markup language that can be converted to latex, html, pdf, odp and odt documents.

It is not as versatile as Latex, but the syntax is far simpler and supports more output formats. I used it today to produce a presentation and a report almost from the same source (Yes, I know that can also be done with Latex).

---

### Post by gunksta on 2010-05-21
I really wish I could use latex rather than a word processor for some of my work projects. I just got done with a 150+ page user's guide to a tool I am making for a client. My boss uses Word. Thus, I must use Word for creating these sorts of documents. (I do love KVM.)

We have had extensive problems with formatting inconsistencies, page numbering, etc. I can not count the number of times I have had to redo something - simply because Word screwed it up or I used Bold where I should have used Italics for some odd-ball formatting issue. 

**Once again - I must conclude that word processors are not appropriate for long, complex or important documents.**

I miss being in school where I had the flexibility to use real tools.

---

### Post by hubie on 2010-05-21
> **gunksta said:**
> I miss being in school where I had the flexibility to use real tools.

Boy that is the truth.  Lately I've been doing a lot of PowerPoint engineering where I'm making slides as part of a group.  I waste so much time fixing formatting changes because we are using different versions of PPT where one is even on a Mac.  I'm just dying to use Beamer, but that is a non-starter.

---

### Post by ahmatti on 2010-05-22
> **hubie said:**
> Boy that is the truth.  Lately I've been doing a lot of PowerPoint engineering where I'm making slides as part of a group.  I waste so much time fixing formatting changes because we are using different versions of PPT where one is even on a Mac.  I'm just dying to use Beamer, but that is a non-starter.

@Hubie and @gunksta you should really try reSTructrured text as I suggested in my previous post. One of the reasons I like it is that you can convert the source to odt and odp, which can then be converted to the needed MS formats... Also there is ascii package for R that allows you to use reST with Sweave.

---

### Post by gunksta on 2010-05-24
I'm sure I could use restructure text, latex, etc and create a one-way work-flow to write a document and then send it to someone else as a .doc, .docx, etc.

The challenge is developing a system capable of allowing me to collaborate. Again - the school metaphor is appropriate. In school, you write a paper and submit it to the professor on the pre-determined date. End of Story. After the professor reads it you will receive a grade, and depending on the professor/school you may or may not get a copy of the paper back with comments and reactions.

But, I almost never work that way. I may write an outline and rough-draft of a report. My boss may take it and fill in parts of the background and negotiation process that I'm not familiar with and someone else might contribute to the structure, graphics, etc. In the process, this file may involve 3-4 contributors and will go back and forth multiple times.

This is where a latex or rest work flow breaks. I can not (easily) take a returned document, with changes tracked, and generate appropriate mark-up to work on via a text editor.

I do sometimes write drafts and outlines in plain text and only later import into a word processor, but collaborating on a document (in many professional domains) means you are working with word processors.

It's not great but I also don't see a reasonable way to convert everyone to latex. I honestly think Lyx might cause permanent mental damage and anguish.

---

### Post by km0r3 on 2010-05-24
> **gunksta said:**
> 
But, I almost never work that way. I may write an outline and rough-draft of a report. My boss may take it and fill in parts of the background and negotiation process that I'm not familiar with and someone else might contribute to the structure, graphics, etc. In the process, this file may involve 3-4 contributors and will go back and forth multiple times.

This is where a latex or rest work flow breaks. I can not (easily) take a returned document, with changes tracked, and generate appropriate mark-up to work on via a text editor.

That's true. 

For relatively short documents I think I would still prefer a WYSIWYG word processor, but now think of writing documentation or writing a book... 
My markup since using LaTeX is much more consistent than before ( and so from others).

I'm also seeing other advantages in using LaTeX typesetting... You can set up a repository with them using a tool like, for example, `git`. With OpenOffice document this is fairly possible because they're saved as a compressed archive on the disk.

---

