---
title: "LaTeX / LyX vs. Word Processing"
date: 2005-12-02
forum: Education &amp; Science
---

### Post by akniss on 2005-12-02
Howdy all.  There's been some discussion about the ease (or difficulty) of using LaTeX in some academic disciplines in a couple forums.  At the suggestion of parktownprawn, I decided to move this discussion here in hopes that new users of LaTeX can get some honest opinions of whether it is the right choice for them.  I'll start it off with some of my own observations.  

I am pretty new to open source software in general, but my first two experiences were wonderful.  The R statistical package, and OpenOffice.org (both under Windows to start, now Ubuntu).  I have been using OOo to format my thesis and other technical publications and the use of styles has saved me many hours of formatting.  However, the bibliography management aspect of OOo leaves much to be desired.

I recently installed Pybliographic to try and manage my citations more efficiently, and really liked the interface.  The next logical step was to try LyX and use it for document formatting.  I used LyX to type a publication, but then only hours before a deadline could not figure out how to get the document into a format that my co-authors could read AND edit electronically. (They are not Latex users.) I finally got the paper exported as a .tex document, then used latex2rtf to get things into an editable electronic form, but then all the pretty formatting was gone and rather than saving time, I ended up wasting several hours trying to make up for my poor decision to experiment with a program so close to a deadline.

I would be interested to hear from some of you any advantages or disadvantages of using Latex/Lyx compared to word processors.  Opinions will probably vary with respect to discipline, so if you would please mention which field you are in, that may be helpful to others who are debating 'taking the plunge' into Latex.

---

### Post by kleeman on 2005-12-02
I use lyx and latex exclusively in the writing of papers. From my experience this is quite common in the following disciplines:

Meteorology, Oceanography, Physics and Mathematics.

Collaboration is always a sticking point however I always find that a latex file is pretty easy to edit with a regular text editor or kile (if you have math).  Latex file structure is quite easy to decipher. If I have a lot of equations in my paper I loathe M$ word or OOwriter as there is way too much klutzing around required whereas latex lets you forget typesetting.

Often exclusive use of lyx can get you into trouble because many journals have very exacting formatting requirements. They will however often provide a latex style file so what I do is write the paper in lyx and then export to latex and hand edit for finishing touches with respect to style.

The pdf export on lyx is a nice way to generate read only versions of the manuscript.

Just my .02c

---

### Post by GeneralZod on 2005-12-02
I originally wrote my PhD Thesis (edit for subject, as requested: maths-heavy Computer Science) in Word, and after a while it became utterly unmanageable, so I (very, very reluctantly) switched to LaTeX on the suggestion of my supervisor.  In the end, I was *very* glad I did! :)

Here are my observations in comparison to Word; note that not all the "Pro's" are features that LaTeX has but Word doesn't - some of them are simply aspects where I feel LaTeX performs better, or is more "natural".

Pros:

- *Gorgeous* output, especially for equations; Word's kerning and other features leave quite a lot to be desired.

- Excellent handling of references, from citations to individual Theorems and equations.

- Plain text means you can use the editor of your choice.

- As a corollary to the above - LaTeX is as stable as the editor you are using.  Also, a TeX project will likely be very small.

- Less tangibly - encourages separation of presentation from content, which is generally good practice.  As a practical consequence, you can alter the style and formatting completely just by making a small, one-time change or dropping in a different style file - this is excellent if you are writing a paper for submission to multiple journals all with different style/ formatting requirements.

- Again, less tanglibly, but LaTeX is programmable - TeX is Turing-complete! :)

- The automatic formatting is very good, and I rarely have to tweak anything to make it look great.

- Easily export to PDF with working hyperlinks.

- Apparently good for note-taking in maths-heavy subject - equations can be typed, which means that the practiced LaTeX user can just type and type and never take their fingers off the keyboard, and easily keep up to speed with both text and equations.  Sometimes, a GUI is more cumbersome.

- There were a couple of times where the examiner did not like the symbol I used for various things.  Since I'd defined each of these symbols as a LaTeX macro (partly out of convenience; partly due to the separation of style and content), I could change these throughout my Thesis (including where there were nested deep inside equations) with a very small change.  I dread to think how long this would have taken if I had been using Word! This "pro" is pretty niche, though.

Cons:

- *Very* steep learning curve.

- Not WYSIWIG, although, as I mentioned above, you can basically just type and type and let LaTeX handle all the formatting.  I'm not sure how far using LyX ameliorates this as I've never tried it.

- Word is much, much better for collaborative editing and, I guess, revision control.

- As you noted, there is apparently no good means of providing people with a well-formatted doc that non-LaTeX users can edit.

- Overkill for small docs - a word processor is usually more time-efficient.

- Tables are much easier in Word.

Basically, if someone were looking to write a technical doc of non-trivial size, I would recommend LaTeX practically without hesitation.  Otherwise...not so much - the Majority of other tasks are better served by a nice, easy-to-use, WYSWIWIG word-processor.

---

### Post by akniss on 2005-12-02
My first goal in giving tex a try was the need to find a good bibliographic management package.  I think pybliographic will fit that need, but given my difficulty in using Latex does anyone know of a Bibtex front-end that will allow me to use it with a word processor?  I would love to have some sort of 'cite while i write' functionality with OOo.   Or am I asking too much?

BTW... I asked what discipline everyody comes from, but then didn't give my own.  I'm in the life sciences (plant science specifically) where the use of Latex is quite rare.

---

### Post by majikstreet on 2005-12-02
I've never used LaTeX/LyX before... Never really considered it.. The only "word processing" that I do is some stuff for school, eg: reports, papers, etc.... Sometimes just random stuff.....

I use AbiWord right now.. .I'm a GUI guy when I'm writing... I like CLI when editing system files or stuff like that..

---

### Post by kleeman on 2005-12-02
[QUOTE=akniss]My first goal in giving tex a try was the need to find a good bibliographic management package.  I think pybliographic will fit that need, but given my difficulty in using Latex does anyone know of a Bibtex front-end that will allow me to use it with a word processor?  I would love to have some sort of 'cite while i write' functionality with OOo.   Or am I asking too much?

BTW... I asked what discipline everyody comes from, but then didn't give my own.  I'm in the life sciences (plant science specifically) where the use of Latex is quite rare.[/QUOTE]

Well lyx is pretty easy to use with bibliographic management packages. Check out the help documentation of lyx for details. Another bibliography frontend I've used is jabref which is a java app.

---

### Post by parktownprawn on 2005-12-03
[QUOTE=akniss]I would love to have some sort of 'cite while i write' functionality with OOo.   Or am I asking too much?
[/QUOTE]

There may be in the future ([http://bibliographic.openoffice.org](http://bibliographic.openoffice.org))

You could try bibus ([http://bibus-biblio.sourceforge.net/](http://bibus-biblio.sourceforge.net/)) which  claims to have this feature. it looks like a bit of a pain to install on ubuntu - you would probably have to compile it yourself. 

[QUOTE=akniss]
BTW... I asked what discipline everyody comes from, but then didn't give my own.  I'm in the life sciences (plant science specifically) where the use of Latex is quite rare.[/QUOTE]

there are quite a few (quantitive) biologists using and publishing in latex

[http://arxiv.org/archive/q-bio](http://arxiv.org/archive/q-bio)

---

### Post by GoldBuggie on 2005-12-03
For having really good looking and manageble tables, formulas and most of all layout, LaTeX is THE thing to use. Just the concept is good, that is having to concentrate on the substance instead of the layout. Sure you have to define how you want it to look but it is all a matter of simple start and end tags. Very simple and the whole document gets the same structure. Then if you want to change the layout the whole document gets changed withit. The .tex file becomes very portable as well.

Now...what is good with a WYSIWYG word processor? Well...If you just want to make a few notes in 3 minutes then it is very easy and you most often don't have to remember what the tag name is.(some nice editors like kile do have shortcut buttons).

But for writing documents LaTeX stands up.

I have several times used a WYSIWYG processor and the whole format of things sometimes really gets messed up and you have to spend some time trying to fix the font or layout etc and when it is done you fell like you can't touch anything cause it will break the layout I have achieved.

I've asked some ppl in the research area why they like using TeX. The main thing seems to be that they want to present their data in a nice and professional way. It just looks ugly when using Word they often say(these ppl are not windows haters) and it is so hard to get it the way I want it in Word.

About LyX...If ppl are comfortable with LyX then fine, but when I wanted to learn LaTeX I started with LyX since I was afraid of using a more textbased editor. But somehow I did something wrong...the layout and all looked very good but when I pressed the compile button it gave me an error.(I think it had something to do with wrong number of tags etc etc not sure). I had no idea how to remove the error since the error come from the underlying TeX structure. So I stopped using LaTeX. Then after 6 months I gave it a go again, but this time not with LyX. Sure..I got some error sometime but since I now know what is happening since I am the one writing it, it all becomes easy to change.

Long live LaTeX:D

---

### Post by Wolki on 2005-12-03
[QUOTE=GeneralZod]- Overkill for small docs - a word processor is usually more time-efficient.[/QUOTE]

I half agree with this one. For documents containing few pages, where you have to follow a style sheet that's not that well supported, it's probably easier to do it in OOo, especially if one's not that familiar with the innards of LaTeX.

Writing letters in LyX is really great though - They look very nice, with nearly no effort, since the templates are great. You'd have to learn a few of the LyX peculiarities, but that shouldn't be hard and it takes little time to write stuff after that.

---

### Post by ssam on 2005-12-03
i use latex for my lab reports in my physics degree.

if find it useful because:

you can define your notation and easily change it. for example
```
\newcommand{\htldensity}{\rho}
```
then use \htldensity in equations
now if i decide to use rho for something else, i can easily change all existing occurances.

equation numbering. you just name each equaion and refer to it by name and latex sorts out the numbers for you.

i dont have to worry about typesetting. i just assume the latex devs know best.

collaboration: its all text based so you could put it under revision control. you can use includes to to break up a large document into small files. it makes all your equations correctly numbered when you merge documents.

---

### Post by kleeman on 2005-12-03
As a further shameless plug for lyx (apart from my moniker that is ;-)), in the next version (1.4) there is going to be extensive support for collaboration. See here:

[http://wiki.lyx.org/LyX/NewInLyX14](http://wiki.lyx.org/LyX/NewInLyX14)

And since someone said latex is better than lyx above, here's why you should use lyx:

[http://wiki.lyx.org/LyX/ReasonsToUseLyxInsteadOfLatex](http://wiki.lyx.org/LyX/ReasonsToUseLyxInsteadOfLatex)

btw I wrote my thesis with latex in 1986 ;-)

---

### Post by hajk on 2005-12-03
...and I did mine in the original TeX around the same time.;)

---

### Post by akniss on 2005-12-03
> **kleeman]As a further shameless plug for lyx (apart from my moniker that is  said:**
> http://wiki.lyx.org/LyX/NewInLyX14[/url]


The change tracking and branches in the new LyX version sound great!  Here is my problem, however...  Collaboration only becomes a "cinch" if your colleagues are using LyX as well.  I'm living in a Microsoft world, and although i really don't want to be a Microsoft girl, the reality is that until I have a way to export the LyX files EASILY to a .doc or .rtf format, using LyX or LaTeX is not going to be a possibility.  Even if there were a way to export it to the new open document format or something would make things easier for me.  I realize that this kind of defeats the purpose of using Latex in the first place, so maybe its just not going to work for me.

---

### Post by akniss on 2005-12-03
[QUOTE=parktownprawn]There may be in the future ([http://bibliographic.openoffice.org](http://bibliographic.openoffice.org))
[/QUOTE]

yeah... this was originally a goal for 2.0, but got put on the back burner.  Very disappointing.  I'm just really surprised that even though the majority of OOo users are in the academic world, bibliography management seems to be a really low priority.  I sometimes wish that insead of trying to make things "easy" for MS Word converts, they would just continue focusing on making the product better.  Adding useful features such as this would do more for adoption than any amount of MS cloning.  Just one man's opinion...

---

### Post by parktownprawn on 2005-12-03
[QUOTE=akniss]The change tracking and branches in the new LyX version sound great!  Here is my problem, however...  Collaboration only becomes a "cinch" if your colleagues are using LyX as well.  I'm living in a Microsoft world[/QUOTE]

well even if you are writing a paper with someone who isn't using Linux you may still be able to convince them to use Lyx for windows. 

[http://wiki.lyx.org/Windows](http://wiki.lyx.org/Windows)


back when i still made regular use of my windows partition i had lyx working under XP without any problems

---

### Post by kleeman on 2005-12-03
[QUOTE=parktownprawn]well even if you are writing a paper with someone who isn't using Linux you may still be able to convince them to use Lyx for windows. 

[http://wiki.lyx.org/Windows](http://wiki.lyx.org/Windows)


back when i still made regular use of my windows partition i had lyx working under XP without any problems[/QUOTE]
Yeah this is a good point. I think Lyx (for Windows) is actually better than Scientific Word which was my old Winblows option. Of course this presumes you are dealing with tons of equations or difficult typesetting.

---

### Post by akniss on 2005-12-03
I rarely need to use more than a few 'special' symbols in formulas.  As for typesetting, the stylist in OOo nearly always does the trick.  The only thing I'm really missing is the bibliography mgt, which several folks have given me pointers on.  I guess for my needs, latex really doesn't offer a huge advantage, especially since it IS compatible with Word, which most of my colleagues use.

---

### Post by dannemil on 2005-12-31
> **kleeman]As a further shameless plug for lyx (apart from my moniker that is  said:**
> http://wiki.lyx.org/LyX/NewInLyX14[/url]

And since someone said latex is better than lyx above, here's why you should use lyx:

[http://wiki.lyx.org/LyX/ReasonsToUseLyxInsteadOfLatex](http://wiki.lyx.org/LyX/ReasonsToUseLyxInsteadOfLatex)

btw I wrote my thesis with latex in 1986 ;-)

I am glad to find a discussion thread on Lyx. I just started using Lyx on Linux (Ubuntu), and I love it. I have run into a problem trying to get citations and bibliographies. I have the database of references in bibtex format. I tell Lyx to add that bibliographic section at the end of the paper and add citations at appropriate places in the text.

When I view dvi, all I get for the citations in the text is (?,?) and no reference list appears at all at the end of the paper. I don't even get the Reference section inserted into the paper.

Any idea why this is happening? I am using apacite as the bibliographic style, but it doesn't seem to matter what I do with this database, nothing gets the citations into the text.

Jim

---

### Post by kleeman on 2005-12-31
So you need to do two things generally for this to work:

1) Insert ---> Lists and TOC ---> Bibtex Bibliography

A rectangle appears at the end of the paper and if you click on it you will get a dialog where you need to specifiy the location of your bib file.


2) Insert ---> Citation

A dialog opens and you need to highlight the reference you want. Double click on it  and then click OK.

If this is what you did and it is not working with any bib style then I would suspect your setup. Do you have natbib checked in Layout ---> Document--->Bibliography ? I don't and have had problems with it.

There is a good wiki here btw:

[http://wiki.lyx.org/pmwiki.php/BibTeX/BibTeX](http://wiki.lyx.org/pmwiki.php/BibTeX/BibTeX)

---

### Post by dannemil on 2006-01-01
[QUOTE=kleeman]So you need to do two things generally for this to work:

1) Insert ---> Lists and TOC ---> Bibtex Bibliography

A rectangle appears at the end of the paper and if you click on it you will get a dialog where you need to specifiy the location of your bib file.


2) Insert ---> Citation

A dialog opens and you need to highlight the reference you want. Double click on it  and then click OK.

If this is what you did and it is not working with any bib style then I would suspect your setup. Do you have natbib checked in Layout ---> Document--->Bibliography ? I don't and have had problems with it.

There is a good wiki here btw:

[http://wiki.lyx.org/pmwiki.php/BibTeX/BibTeX](http://wiki.lyx.org/pmwiki.php/BibTeX/BibTeX)[/QUOTE]

Thanks. I followed your instructions and found out after many trials that the bibtex file that I was using had an illegal line break between multiple authors, so Lyx would not process it correctly. After removing those line breaks, it worked as it should. Now I have to get the reference export routine in my citation software to stop putting those line breaks between multiple authors in the bibtex export.

Jim

---

### Post by kleeman on 2006-01-19
For those who are interested there is a new version of lyx out (1.3.7) and I have created some standard breezy debs. They should appear on the lyx website binary download section fairly soon. Version 1.4 with a ton of new features is likely to be released in early February.

---

### Post by jerome bettis on 2006-01-19
i've never used lyx but after using latex, i'd recommend you try it instead - that steep learning curve translates into very powerful & nice to use.  i use gvim + the latex suite package as an editor, bibtex, aspell -c for spell check, and this makefile.  i posted it at the bottom of this thread : [http://www.ubuntuforums.org/showthread.php?t=116484](http://www.ubuntuforums.org/showthread.php?t=116484)

---

### Post by kleeman on 2006-01-20
The debs are now up on the lyx site. Standby for the glitzy new 1.4 release.

Jerome: I agree latex is very powerful (I did my doctoral thesis with it). What migrated me to lyx in the end was that in order to use all that power you needed a good memory or a thick manual by your side. Probably if you use it very regularly to write papers (say once a month) this would be fine but I found I was constantly scratching my head over syntax. With lyx you can export to latex easily and then polish things up easily (formatting etc). lyx is not as powerful as latex but it serves my needs and I do quite a bit of math.

---

### Post by raphtee on 2008-08-18
I wrote my Ph.D. thesis in theoretical particle physics back in 2002.  At the time the thought of using Word in a thesis where there was heavy usage of mathematical notation would not have been a good idea.  Perhaps It has improved but from reading other posts perhaps not.

Personally I believe that WYSIWYGs have the problem that they force one to think about layout and appearance during the writing process, and I dont think that is such a good thing.  Also most lock you into a proprietary format. Though OOO and ODF has mitigated that somewhat, I recently found that I had trouble opening up old Star Office and old Open Office presentations that I did back in 2001.  The problem with any binary stored format is that you are depending on the existence of software to continually be able to read it.  And in my short lifetime I have a number of documents dating way back to high school that are now essentially lost to me.  However everything I did in TeX and LaTex (which is all ascii text) is still around and all I have to do is run it through latex and I have my documents again.

Also I believe someone already mentioned this, but I recall that in Physics (especially theoretical Physics) many journals (and the ArXiV servers) preferred things in Latex using the Latex style file they provided.  

So for Physics and I bet Math, Word, and OOO are just not that great.

Travis Miller

---

### Post by hajk on 2008-08-18
You're so right, I recently went to an Amiga computer club meeting where somebody had a PC with an old 5.25" floppy drive. There I succeeded in copying my own 20+ year old PhD thesis to a USB stick, it was written in the original TeX. And, surprise, it still compiled to a pdf file with pdftex. Even if that hadn't been possible, the little "untex" utility would have made a reasonable ASCII file from it. Try and do that with a 20+ year old WordPerfect file...

---

### Post by Vivaldi Gloria on 2008-08-20
> **GeneralZod said:**
> Cons:

- *Very* steep learning curve.

I disagree here. Someone showed me basics for a couple hours and it was enough. 

> Not WYSIWIG, although, as I mentioned above, you can basically just type and type and let LaTeX handle all the formatting. 

Con?? On the contrary. This is the main point of LaTeX - you don't bother with the page format and appearance of the document which makes you loose time, makes the document rigid, and afterall humans are not very good at it. LaTeX takes care of all visual design of the document so you just type the content, and believe me, typing is much faster than typing plus visual design.

> - Word is much, much better for collaborative editing and, I guess, revision control.

Both word and latex are bad when it comes to collaborative editing. There are editors out there just designed for that. And you can use latex in them.

> - As you noted, there is apparently no good means of providing people with a well-formatted doc that non-LaTeX users can edit.

Isn't this true for everything? 

> - Overkill for small docs - a word processor is usually more time-efficient.

For docs smaller than half of a page I'd agree.

> - Tables are much easier in Word.

I always found word's tables awkward and its spaces off to be honest. But I haven't used word for years and maybe it's better now. I'm talking about the regular word here, not the sci word. Don't know how are sci word's tables.

---

### Post by kleeman on 2008-08-21
> **raphtee said:**
> I wrote my Ph.D. thesis in theoretical particle physics back in 2002.  At the time the thought of using Word in a thesis where there was heavy usage of mathematical notation would not have been a good idea.  Perhaps It has improved but from reading other posts perhaps not.
Travis Miller
Yeah I used latex for my theoretical physics Phd (particle physics) back in 1985. As I remember it the diagrams (symmetry groups) were a challenge! Around 1995 I stopped using latex because I kept forgetting commands and eventually started using lyx. As I submit a lot of papers with math in them to various journals I find I need to export the lyx document to latex and insert the body into a standard style template and compile with latex. Lyx is not flexible enough yet to allow for the multifarious things demanded by journals. Writing in lyx and exporting to latex works really well though since lyx is just a front end really for latex.
The latest version of lyx (the 1.5 series) has a collaboration facility although I have never used it....

---

### Post by briansers on 2008-08-21
> **Vivaldi Gloria said:**
> 

Both word and latex are bad when it comes to collaborative editing. There are editors out there just designed for that. And you can use latex in them.



Just out of curiosity, what editors are you talking about?

---

### Post by Vivaldi Gloria on 2008-08-21
> **briansers said:**
> Just out of curiosity, what editors are you talking about?

> 
Real-time collaborative text editing software

    * Abiword (multi-platform) is a free software, open source editor that added a real-time collaborative editing plugin in the 2.6 release. This editor is the basis for the collaborative Write activity on the OLPC XO-1.[10]
    * ACE (Linux, Microsoft Windows, Mac OS X, Solaris, FreeBSD) is a free software, collaborative text editor.
    * CoWord (Microsoft Windows) converts Microsoft Word into a real-time collaborative word processor and allows multiple users to collaboratively edit the same Word document at the same time.
    * GNU Emacs provides basic collaborative editing support under the X Window System, using the "make-frame-on-display" command.
    * GNU Screen allows multiple users to share one console screen, but they have to share a single cursor.
    * Gobby (Linux, Microsoft Windows, Mac OS X) is a free software, open source project.
    * Google Docs (browser-based).
    * ICT is a framework that allows multiple users to edit a shared document with unmodified, heterogeneous single-user editors.
    * MoonEdit (Linux, Microsoft Windows, FreeBSD) is free for non-commercial use and allows basic collaborative editing.
    * Plutext is open source software for real-time collaborative editing of docx documents stored in Alfresco, with any of three clients: Word 2007 with an add-in (on XP or Vista), docx4all (all platforms supporting Java 6), or a web browser
    * SubEthaEdit (Mac OS X).
    * UNA (multi-platform) is a multi-user development environment for software engineers, which includes a real-time collaborative editor.

[edit] Other real-time collaborative editing software

    * Borland CodeWright has a CodeMeeting feature that supports chatting and exclusive file editing (1 user per file).
    * Coccinella is an instant messaging client with whiteboard and VoIP.
    * EditGrid supports real-time event-driven collaborative editing of spreadsheets on the web.
    * Marratech is commercial software with a whiteboard function.
    * WhiteBoardMeeting is a multi-user whiteboard for Skype.
    * NetSketch is a real-time collaborative drawing application for the iPhone.


from

[http://en.wikipedia.org/wiki/Collaborative_real-time_editor](http://en.wikipedia.org/wiki/Collaborative_real-time_editor)

Also there are various revision control systems out there.

---

