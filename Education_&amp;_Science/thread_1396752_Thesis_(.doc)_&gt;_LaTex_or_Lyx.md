---
title: "Thesis (.doc) &gt; LaTex or Lyx?"
date: 2010-02-02
forum: Education &amp; Science
---

### Post by sisyphus1978 on 2010-02-02
So I have a thesis already completed in word (.doc) format. I've actually converted it to txt (antiword) and was wondering if anybody had an opinion as to what the best way to reconstruct the thesis in LaTex would be? I've been looking at Lyx and it seems really good when you're starting a project, but all of my words etc have been written. I just have to cut and paste it into a new document.  I was kinda hoping I could just markup my thesis with LaTex and boom, it'd be done, but it doesn't seem to be that easy.

Anyway, I'm reading up on it, so maybe I'll answer my own question. Thanks for listening.

---

### Post by Onesimus on 2010-02-02
If your thesis is completed, why are you wanting to convert it ?  what benefit would it offer ?  

I remember when I finished my thesis, I just wanted to never ever see it again !

If you could provide more info, then you may get a better response.  What are you trying to achieve ?

---

### Post by sisyphus1978 on 2010-02-02
Oh there's no hurry about it  but 1) it's currently a word document (so you can imagine that the formatting is less than perfect) 2) all the words are actually written. I don't mind spending a year learning LaTex and typesetting the thing (it's not like I have to write it again) 3) I don't particularly want to get started one way and have to lose all the work I've done (like reconverting it back to word or something like that). For example I probably have my references in some kind of endnote file somewhere (I actually finished the thing years ago but my supervisor has never read it (long story for different time). And I was thinking about redoing all my graphs in R (from SPSS).

I guess I'm looking for: "well Lyx will be okay for what you want" or "just get a LaTex book and work it out: you're supposed to be smart"...

/beats playing tetris

---

### Post by Simian Man on 2010-02-02
If you have it as Text, it's really not hard to add the LaTeX markup.  For a start, just include the boilerplate header and footer and it should compile.  Then add \title, \section and \subsection and it will start to look pretty decent.  You can include images pretty simply with \includegraphics.

I don't know how much more formatting you need; I rarely need more than those things I mentioned.

---

### Post by earlycj5 on 2010-02-02
> **Simian Man said:**
> If you have it as Text, it's really not hard to add the LaTeX markup.  For a start, just include the boilerplate header and footer and it should compile.  Then add \title, \section and \subsection and it will start to look pretty decent.  You can include images pretty simply with \includegraphics.

I don't know how much more formatting you need; I rarely need more than those things I mentioned.

I agree.

My university also kindly provided the templates for me, all I had to do was fill them in.  If that's the case you can copy/paste into the files provided and have the formatting ready to go.

---

### Post by sisyphus1978 on 2010-02-02
I'll get going with LaTex then. Thanks. :)

---

### Post by Abdus on 2010-02-02
> **Onesimus said:**
> If your thesis is completed, why are you wanting to convert it ?  what benefit would it offer ? 

Absolutely superior typesetting quality - this is why LaTeX exists. I know Word, Open Office and LateX by heart, I'm a typesetter. Some clients insisted on their works being typeset in Word/OO so I did my best, using all the most sophisticated app. features, yet the effect was never even close to LaTeX's output.

Some extremely simple examples of Word/OO flaws - SPACES:
- 'bounding space' is fixed width, so looks strange when other spaces in the line are stretched,
- some languages (like US English) demand more spacing after each sentence. Word/OO don't support it (maybe latest versions).
- some languages demand certain amount of spaces between certain symbols, like in '&4'. Word/OO give you either a full space or none. In LaTeX you can set proper width for all the instances in the text.
- some languages demand some symbols on a certain height on the line, for example: '-'. Word/OO don't support raising those in an *efficient* manner.

And so on, tons of this.


Back to the topic: What you decided to do is exactly what I do when I get a text to be typeset. First I demand a PDF so that I see what author meant to do with the text, then I strip it of all style marking (make a .txt) and start hand-marking it up. First chapters sections, and paragraphs - this is a very simple process that shouldn't take you long. 

With that you will already see your document nicely typeset. Then you can add \tableofcontents and double check your document structure. Then I would go for any footnotes, any special formatting of the text if you use any (italics, bold, superscript), so that no text setting are lost during textization process. And then, depending on your needs, it's time to start tweaking the design: 
- page design,
- head/foot,
- section formatting,
- text formatting,
and you will have almost ready thesis done. This however will require a LOT of learning, will also provide some frustration for sure. :) 

Then apply graphics/tables - possibly extremely time consuming job.

And after you do all this you go for details. Countless details. :D

If you want to understand what and why is happening with your document, don't use LyX - work with the code. The learning curve may be steep, especially when it comes to changing the default settings or applying graphics, but it's worth the effort.

If you want you can show me the .doc version of the thesis, I could point you to some useful packages - these depend on what you need in the document.

---

### Post by xadder on 2010-02-03
I'd also vote for straight latex, it isn't hard.

About references, if you have them as endnote, I'd recommend using jabref to first import them, and then save as bibtex. This can save loads of time, and if using latex then jabref is fantastic to use anyway. (Many other bib software progs exist, so search for those, but I like jabref's simplicity and use of the simple ascii bibtex file as the only database)

---

### Post by sisyphus1978 on 2010-02-03
Thanks for all the good advice. That's what I was looking for. I'm going to look over things (LaTex books, style guides, work out converting bibliography). I'm sure that will keep me going for a while and I'll see how I get on.

:)

Thanks Abdus for the super reply. Lots to think about and get on with.

---

### Post by sisyphus1978 on 2010-02-03
After just a few hours of gedit (with LaTex plugin) and this[ UCL_thesis.cls]("http://www.cs.ucl.ac.uk/research/students/Latexforthesis.htm") I found, the thesis is almost as good as the final word doc. Boy, do I wish I'd done this sooner. :)

---

### Post by Abdus on 2010-02-03
> **sisyphus1978 said:**
> After just a few hours of gedit (with LaTex plugin) and this[ UCL_thesis.cls]("http://www.cs.ucl.ac.uk/research/students/Latexforthesis.htm") I found, the thesis is almost as good as the final word doc. Boy, do I wish I'd done this sooner. :)

From your previous posts I understood you're going to achieve a perfect output, no matter how long it takes. If it is so, you could consider using other class. It may seem handy at the beginning to use the thesis class, but I doubt it is so comprehensive, user friendly a feature rich as some other classes, including the 'leading' Memoir.

What I mean is: As long as you want only the default settings of a class, any class will do. But I predict a time will come you will wish to modify things here and there. This is where it starts to matter what class you're using, things that count are for example:
[LIST=1]
[*]Quality of documentation,
[*]User friendliness of customization settings,
[*]Number of people who use the class, so that you'll be able to get any help in the internet.
[/LIST]
This is why I strongly recommend switching to Memoir, which is far the best mega-class I know right now. Switched to it recently and it was a good decision.

---

### Post by sisyphus1978 on 2010-02-03
It wasn't a random decision to use that ucl file. The University of London sets specific format requirements for its theses (and UCL is part of the UL, as is my own college) hence I thought it best to use a starting point that appears to follow those standards.

And I never said a perfect output. I just said I wanted to learn LaTex (a bit) and convert the thesis from word to LaTex.

Now I understand why you are suggesting using memoir, but given what I've written, am I not better off just sticking with this one (or should I adapt memoir to the specifications I require)?

---

### Post by Abdus on 2010-02-03
> **sisyphus1978 said:**
> Now I understand why you are suggesting using memoir, but given what I've written, am I not better off just sticking with this one (or should I adapt memoir to the specifications I require)?

As above: If you're fine with your current class defaults, or if you are ready to learn it the hard way in case of modifications - stick with it, nothing wrong about that. But if you now predict you would like to seriously modify the default, you might go Memoir )or other complete 'mega-class') - it is just easier to manage/modify your document with all the help these mega-classes provide.

---

