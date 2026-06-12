---
title: "Endnote help!!?? Please help!"
date: 2007-07-24
forum: Education &amp; Science
---

### Post by _Poincare on 2007-07-24
Hello,

I have searched the forums and read others' comments but none seem to be lucid. First, I am a PhD student who switched to Ubuntu this summer. I am happy, for the most part, with the performance and organization of Ubuntu. HOWEVER, being a dissertator, I need to write several journal articles and also (hopefuly) complete my dissertation on time. My format is APA 5th edition and my problem is that I have been dual booting into Windows since Endnote and Office do not work well under WINE, Crossover Office, QEMU, or VMWare. I have tried... please don't tell me to just use it through these virtualizations.  

I am looking for an alternative to Endnote which will INTEGRATE nicely with Open Office. Here is what I have tried so far:

**Bibus**: Does not support formating bibliographies in APA style and I am not computer/programming literate enough to even figure out how to make a new "style".  :(

**Open Office's Bibliography feature:** This just plain sucks and isn't even usable as far as I am concerned.

**Zotero**: Still doesn't come close to having the FLEXIBILITY that I need and does not adequately support the APA 5th Ed. format.  

**LaTex/BibTex:** WTF is this?  As a non-computer-science/programming user, I can't even begin to understand how to use this crap. I can't even begin to understand how to format, convert, format again and then import??  Why can't linux software be easy to use?

**Tellico**: Does not support the flexibility I need AND does not support APA 5th.

**RefDB**: I can't begin to use it's "queries" usefully and it does not have anywhere near the flexibility of Endnote. What a mess...:confused:

**Pybliographer**: Does not format bibliographies. No functionality.

So, with all this there is STILL no decent semi-functional, easy-to-use, flexible alternative to Endnote which I can use.  Please friends, I am desperately seeking help on this. If any researcher, teacher, or fellow PhD student has found an alternative that works easily, and does not require you to be a programmer, please reply.  ](*,) ](*,) ](*,)

Thank you.

---

### Post by KyleBrandt on 2007-07-24
I am going to go ahead and tell you want you don't want to hear, so don't read on if you really feel virtualization is not on option.  Office 2007 works well for me through virtualization, I am using VirtualBox, a vmware type program that is free and can be installed with synaptic/apt.  How much memory do you have?  If you have 1 gig it really shouldn't be a problem to run word in a vm session running XP.  Sorry I don't know of a solution that is exactly what you are looking for, but it might be worth giving virtualization one last try through virtual box if you have enough memory (and make sure you allot enough memory to the virtual machine when setting it up).

---

### Post by UbuWu on 2007-07-24
Full bibliographic features are planned for openoffice 3.0. See also [http://bibliographic.openoffice.org/](http://bibliographic.openoffice.org/)

For now, the best alternative as far as I have found is bibus. You can change the citation style to APA 5th by setting the values as described here: [http://www.oooforum.org/forum/viewtopic.phtml?p=139917](http://www.oooforum.org/forum/viewtopic.phtml?p=139917)

---

### Post by machoo02 on 2007-07-24
Just for clarity's sake, WINE and Crossover are not virtualization, they are compatibility layers.  Think of them as mini Rosetta Stones, translating between Windows and Linux system calls.  Qemu, VMWare, and VirtualBox are virtual machine software - like having another computer inside of your computer.  Windows is installed into this fake computer, and thinks that it is inside a real one  As long as your physical computer has the specs to run the virtual machine software, the only way you would have problems running office and endnote together inside of those is if you have problems running them on XP.

Bibus **does** support the APA style manual, and one of the default styles (en_apa2) seems to be based on the APA Manual 5th edition.  Try that one to see if it fits your needs; if things need minor tweaking, I have made up a couple of styles for bibus and can give you a few pointers.

Anyway...I feel your pain.  I'm a PhD student myself, recently broken away (mostly) from Windows.  But I really do wish Endnote would integrate better with Office inside of WINE/Crossover.  If you really want to use this combo, don't bother with cite while you write functionality and use the RTF document scan...that works beautifully (and this lets you use OpenOffice to create your .rtf files)!

---

### Post by Typhoon on 2007-07-24
LyX. Use LaTeX/Bibtex without the pain. It is a killer app.

On the other hand, if you have special needs such as multiple indexes or cross references to something other than page numbers (eg, paragraph numbers), then nothing, NOTHING, beats LaTeX.

Typhoon

---

### Post by _Poincare on 2007-07-25
> **machoo02 said:**
> 
Just for clarity's sake, WINE and Crossover are not virtualization, they are compatibility layers.  Think of them as mini Rosetta Stones, translating between Windows and Linux system calls.  Qemu, VMWare, and VirtualBox are virtual machine software - like having another computer inside of your computer.  Windows is installed into this fake computer, and thinks that it is inside a real one  As long as your physical computer has the specs to run the virtual machine software, the only way you would have problems running office and endnote together inside of those is if you have problems running them on XP.

Bibus **does** support the APA style manual, and one of the default styles (en_apa2) seems to be based on the APA Manual 5th edition.  Try that one to see if it fits your needs; if things need minor tweaking, I have made up a couple of styles for bibus and can give you a few pointers.

Anyway...I feel your pain.  I'm a PhD student myself, recently broken away (mostly) from Windows.  But I really do wish Endnote would integrate better with Office inside of WINE/Crossover.  If you really want to use this combo, don't bother with cite while you write functionality and use the RTF document scan...that works beautifully (and this lets you use OpenOffice to create your .rtf files)!

OK. See, I could use VMWare, virtualbox, or whatever but that is not something I would like to do. If I am going to be using any compatibility layer or virtualization it just makes more sense to natively boot for speed and performance issues. I get better performance natively that trying to mess with compatibility / virtualization.  So, this seems to miss the point: finding a solution under Linux; C.E.: without compatibility/virtualization. Because WINE/CrossOver Office do not support Endnote's CWYW. 

Bibus under OpenOffice is also a mess. Yes v1.3 "supports" the APA format, but is does not format references properly. I just verified this with bibus v1.3 and OpenOffice 2.2.1. Also, bibus now apparently does not "insert citation" correctly since it's giving me pipe errors (yes, I followed the documentation about how to set this up).  Also bibus does not support the large number of sources I have. So, with each new source that I need to add, which it does not support (such as government document, congress bill, etc) that means I need to add each of these as a custom citation. That's over 40 custom citations on my part. 

In my original post I talked about easy-to-use and functional. From my perspective, this does not make bibus either of these. PLUS, it still foos on trying to even format a bibliography or insert a citation. 

See the complications here?  

So again, I'm just back to using Endnote under Winxp natively which does not do much for my transition to Ubuntu. In fact, if anything it's more impetus to stay with XP; although I'd like to switch. The functionality and bugs (on the Linux side) just aren't worked out yet. 

Shame.

---

### Post by akniss on 2007-07-25
Honestly, you will probably be better off going back to Windows then.  If you are not willing to take a couple hours to learn how to create your own style for Bibus, then go back to the software that you keep telling us is so much better.  There is no perfect option at this time.  The way I see it you can either:
[LIST=1]
[*]Use Endnote on Windows since it works so perfectly
[*]Use Endnote in VirtualBox or Wine, and deal with the performance 'penalty'
[*]Take the time to learn how to use Bibus + OOo properly
[*]Convince Microsoft and Thompson to port Word and Endnote to run natively on Linux
[/LIST]
You seem to want us to hand you a perfect solution for linux, without putting ANY effort of your own toward your goal... this is not usually how it works in the open source world.  Bibus is fantastic software; I and many others have used it with OOo and MS Word for dissertations and publications.  In order to do so, we took the time to learn how to generate the required styles.  It is not the fault of Bibus that it doesn't have every possible style.  That would not be possible for a project that is almost completely maintained by a single person.  But he has given Bibus the capability to be customized in almost infinite ways.  This requires EFFORT on your part.  

It seems that you are not willing to take the time to learn how to use Bibus properly, and you seem unwilling to use compatibility or virtualization solutions.  So it seems to me that your last two options are to convince Microsoft and Thompson to create native GNU/Linux versions of Word and Endnote or continue using the two programs in Windows.  Its up to you to decide which of those solutions seems more realistic.

---

### Post by UbuWu on 2007-07-25
> **akniss said:**
> 
[LIST=1]
[*]Use Endnote on Windows since it works so perfectly
[*]Use Endnote in VirtualBox or Wine, and deal with the performance 'penalty'
[*]Take the time to learn how to use Bibus + OOo properly
[*]Convince Microsoft and Thompson to port Word and Endnote to run natively on Linux
[/LIST]

5. Wait for openoffice 3.0 (at least another year)

---

### Post by tweedledee on 2007-07-25
> **_Poincare said:**
> Hello,

I have searched the forums and read others' comments but none seem to be lucid. First, I am a PhD student who switched to Ubuntu this summer. I am happy, for the most part, with the performance and organization of Ubuntu. HOWEVER, being a dissertator, I need to write several journal articles and also (hopefuly) complete my dissertation on time. My format is APA 5th edition and my problem is that I have been dual booting into Windows since Endnote and Office do not work well under WINE, Crossover Office, QEMU, or VMWare. I have tried... please don't tell me to just use it through these virtualizations.  

I am looking for an alternative to Endnote which will INTEGRATE nicely with Open Office. Here is what I have tried so far:

**Bibus**: Does not support formating bibliographies in APA style and I am not computer/programming literate enough to even figure out how to make a new "style".  :(

Perhaps you've been a great deal more successful with Endnote than I ever was, but I found OO + Bibus to at least as useful & stable as Word + Endnote, and I find Bibus MUCH easier to customize than Endnote (with both programs I've found that something is always just a little off).  Creating styles for Bibus takes about half an hour or so to figure out, and then it's really very fast after that (even for your 40! custom formats).  There are a variety of threads regarding difficulties with OO & Bibus communication, almost always solved by a simple reinstallation (which is a helluva lot easier than such an activity would be under Windows!).  Is any of this software perfect?  No.  I have a long list of complaints with both OO and Bibus, and many other pieces of software I'm using.  However, I find that on the balance, the list is shorter and made of up of smaller complaints than with the equivalent Windows/MS software.  If you find otherwise, then you should probably just stick with Windows - ideals aside, when it comes to writing your dissertation, you just need something that works for what you are trying to do.  If you don't feel you have the time to adapt to new programs now, then don't, do it when you do have time.  But don't make the claim that Word+Endnote is easier or simpler or anything else - it's not.  It's just different, and a matter of what you are used to.

---

### Post by hugmenot on 2007-07-27
Just a few remarks. If your software is provided by your institution I see no reason to use inferior solutions. And bibus being inferior to EndNote is due to the latter being highly developed. I, for instance,  to typeset my latest poster used Illustrator, which was a joy to use. I could tell it to be high quality software. It even supports micro-typography features, something I only expected LaTeX to handle.

It&#8217;s a matter of software quality. A collegue in the lab used Inkscape for his poster, and sure enough he managed to do it, but I bet it was clunky, and the output was a 150MB PDF file. So, Inkscape is new, bibus is new, no big deal. Now, calling LaTeX crap is testament to your naivité. TeX is a proven solution for more than 30 years. It formats documents in a quality and elegance of workflow MS Word will never reach.

Other than that, perhaps taking another look at bibus is worthwile. I tested it with Word when I recommended it to someone, and it seemed functional. It defaults to a style called APA, which looked and smelled like APA, if the exact revision doesn&#8217;t match, perhaps taking your formatting requirements with a grain of salt might be in order. Did you know that more than 20% of all citations are faulty?

Yeah, and concentrate on your content.

---

### Post by edoviak on 2007-07-29
I'm also writing my dissertation. I will never let any office product (be it MS Word or OOo Writer) touch a single word of it. Word processors are nice for typing letters, but they should NEVER be used for academic work.

You may have noticed that a large share of the working papers have a certain "look." They all have the same fonts, formatting, etc. Those papers were written with LaTeX. **[COLOR="Red"]If you're serious about a career in academia, then get serious about LaTeX and BibTeX.[/COLOR]** 

The question is how to begin. It looks daunting, but it's not. The best way to think about LaTeX is to think back and remember that cool little "Reveal Codes" feature that WordPerfect used to have. In a certain sense, typing in LaTeX is a little like typing those codes along with the text of your dissertation. 

Sounds daunting, but it isn't.

**Here's why it isn't so hard:**  First, you're not going to type half the code. Second, you're going to copy and paste half of the code into your paper. Third, you're going to use Kile to insert the other half of the code for you. **So don't let the code scare you !!!**

**But why would you even want to play with all that code?** Here's one very good reason: Suppose you use a word processor to write your paper and the journal doesn't accept your paper. (I hope that doesn't happen to you, but suppose it does). You'll want to revise the paper and submit it to another journal. Before you can resubmit it however you'll have to spend weeks revising all of that formatting. 

Now let's consider the same scenario, but this time suppose that you had used LaTeX. You change one line of code and the entire paper is automatically reformatted.

Here's another very good reason to use LaTeX instead of a word processor: When you type in a Word Processor, you always see what the printed version will look like and you start thinking too much about what it looks like and you stop thinking about what it says. ("Oh, let me just shorten that sentence so it doesn't run on to the next line." or "Oh, I'll put an extra hard return in there, so that the next section begins on a new page.") 

In LaTeX, all you see is text, so you stop worrying about formatting and you start thinking about your paper.
[B]
But isn't it hard to type all of that code? No! Because you're not going to type the code![/B] Here's what you're going to do: First, you're going to install Kile (a LaTeX front-end) on your Ubuntu system. Second, you're going to install Pybliographer (a BibTeX database) on your Ubuntu system. 

Then you're going to log into MS Windows, you're going to export all of your EndNote references to BibTeX format, return to Ubuntu and import them with Pybliographer. Then delete MS Windows, EndNote and Wine from your computer and never ever touch that corrosive software ever again. They're like cocaine: "You can check out any time you like but you can never leave." Time to enter rehab!

I included some sample LaTeX code for you to follow (see below), but Kile's drop down menus are the best source of commands. With Kile, you can jump into LaTeX in five minutes or less.

Pybliographer is just database and it's really easy to use. The only thing you have to remember is that authors names must be entered this way: "Last, First" (without the quotes of course).

Then just insert a \bibliography{} command at the end of your document (see example below) and you're on your way to producing professional papers.

The first time you compile your TeX document, you'll get some error messages saying that it can't find the list of references. Don't worry about it. Just compile your TeX document again and view the pretty results.

Here are some websites with useful information:

citations -- [http://users.aims.ac.za/~mackay/](http://users.aims.ac.za/~mackay/)

document styles -- [http://www.artofproblemsolving.com/LaTeX/AoPS_L_GuideLay.php#docsty](http://www.artofproblemsolving.com/LaTeX/AoPS_L_GuideLay.php#docsty)

tables -- [http://www.maths.tcd.ie/~dwilkins/LaTeXPrimer/Tables.html](http://www.maths.tcd.ie/~dwilkins/LaTeXPrimer/Tables.html)

Hope this helps,
- Eric



\documentclass[letterpaper,12pt]{article}
\usepackage{amsmath}

\usepackage{natbib}
\bibliographystyle{abbrvnat}

\pdfpagewidth 8.5in
\pdfpageheight 11in

\setlength\topmargin{0in}
\setlength\headheight{0in}
\setlength\headsep{0in}
\setlength\textheight{9.0in}
\setlength\textwidth{7.0in}
\setlength\oddsidemargin{0in}
\setlength\evensidemargin{0in}
\setlength\parindent{0.25in}
\setlength\parskip{0.25in}

%opening
\title{Type the Name of Your Paper Here}
\author{Name Here}

\begin{document}

\maketitle

\begin{abstract}

Type your abstract here.

\end{abstract}

Type an introduction here.

\section{Name of a Section}

Type a section here.

Assume that output, $Y$, is produced using capital, $K$, and labor, $L$, according to the simple Cobb-Douglas production function:
\begin{equation}
Y=K^{\alpha}L^{1-{\alpha}}.
\end{equation}

Then you need to type in a table of results:

\begin{center}
\begin{tabular}{|l|ccc|}
\hline
\multicolumn{4}{|c|}{ \textbf{Table 1} } \\
\multicolumn{4}{|c|}{ percentage change in output } \\
\hline
& \textbf{ $ \gamma_{L} = 0.05 $ } & \textbf{ $ \gamma_{L} = 0.10 $ } & \textbf{ $ \gamma_{L} = 0.15 $ }\\
\hline
\textbf{ $ \alpha = 0.10 $ }  & $ 0.110 $ & $ 0.120 $ & $ 0.132 $ \\
\textbf{ $ \alpha = 0.30 $ }  & $ 0.319 $ & $ 0.339 $ & $ 0.362 $ \\
\textbf{ $ \alpha = 0.70 $ }  & $ 0.714 $ & $ 0.728 $ & $ 0.742 $ \\
\hline
\end{tabular}
\end{center}


\section{Conclusion}

Conclude here and don't worry about anything else because the next command will take care of all of your references for you.

\bibliography{/home/yourname/folder/dissertation_references.bib}

\end{document}

---

### Post by hugmenot on 2007-07-29
> But why would you even want to play with all that code? Here's one very good reason: Suppose you use a word processor to write your paper and the journal doesn't accept your paper. (I hope that doesn't happen to you, but suppose it does). You'll want to revise the paper and submit it to another journal. Before you can resubmit it however you'll have to spend weeks revising all of that formatting.

Yeah, but unless he is in physics, mathematics and computer science there is a miniscule chance the journal will accept his manuscript as a Latex source. The big majority has workflows based on manuscripts being .doc, with pica sized text, double spacing, figures in the end and separately; and no frills.

---

### Post by tweedledee on 2007-07-29
> **edoviak said:**
> I'm also writing my dissertation. I will never let any office product (be it MS Word or OOo Writer) touch a single word of it. Word processors are nice for typing letters, but they should NEVER be used for academic work.

You may have noticed that a large share of the working papers have a certain "look." They all have the same fonts, formatting, etc. Those papers were written with LaTeX. **[COLOR="Red"]If you're serious about a career in academia, then get serious about LaTeX and BibTeX.[/COLOR]** 

Echoing hugmenot, you are massively overgeneralizing.  In my field (chemistry and biochemistry), LaTex is absolutely NOT allowed as a journal submission format.  Not a single major journal allows it.  Moreover, the researchers in the field are so welded to MS Office that even using OpenOffice to exchange files is frequently a painful experience.  Is this rational?  Not really.  But it is the reality.

That said, having nearly lost my MS thesis several times to Word, I've found OO to be much better at handling my PhD dissertation.  And while I'd love to use LaTex for it, and journal papers, the truth is that OO is not as bad as you make it out to be; as I stated earlier, a lot of this is really a matter of what you are used to.

---

### Post by hugmenot on 2007-07-29
Sure, that another point, collaboration with colleages. When you give your stuff to a collegue for review and particularly redacting (as in editing). You better give it to them in PDF format if they are not familiar with LaTeX. But then they cannot edit. Even worse, there&#8217;s no clean and newbie friendly way to track changes and merge revisions.

So in scientific reality, unless you work alone all the time you will stumble on hindrances mainly because your peers don&#8217;t use it.
If you work alone it&#8217;s perfect, but in a less geeky surround where collaboration is essential, it&#8217;s not practical.

---

### Post by troy7777 on 2007-07-29
> **tweedledee said:**
> ...In my field (chemistry and biochemistry), LaTex is absolutely NOT allowed as a journal submission format.  Not a single major journal allows it....

ACS accepts TeX/LaTeX submission, according to this: [http://pubs.acs.org/paragonplus/submission/tex.html](http://pubs.acs.org/paragonplus/submission/tex.html)

---

### Post by edoviak on 2007-07-29
> **tweedledee said:**
> Echoing hugmenot, you are massively overgeneralizing. In my field (chemistry and biochemistry), LaTex is absolutely NOT allowed as a journal submission format.
Perhaps you're right. I put the blinders on and forgot that their are fields other than economics. 

> **tweedledee said:**
> That said, having nearly lost my MS thesis several times to Word, I've found OO to be much better at handling my PhD dissertation.  And while I'd love to use LaTex for it, and journal papers, the truth is that OO is not as bad as you make it out to be; as I stated earlier, a lot of this is really a matter of what you are used to.
In economics, we type a lot of equations and MS Equation Editor simply does not cut the mustard. Not only is it difficult to format, but it frequently crashes and turns every equation that you painstakingly typed into an uneditable image. In fact, our university specifically forbids us from using MS Equation Editor in our dissertations.

I do like OpenOffice's Formula Editor and the textual way of creating an equation, but I never got into it because I started typing LaTeX with Kile at about the same time.

[QUOTE=hugmenot]Even worse, there&#8217;s no clean and newbie friendly way to track changes and merge revisions.[/QUOTE]
**[COLOR="Red"]Sounds good to me!!![/COLOR] I hate "Track Changes."** I prefer that someone types up their comments. That forces them to comment on the content of the paper and forget about trivial stuff like punctuation. 

(Punctuation and grammar is important, but odds are I'll revise the sentence at a later point anyway, so it's a waste of time to point out grammar and punctuation mistakes in an early- or intermediate-stage draft).

- Eric

---

### Post by tweedledee on 2007-07-30
> **troy7777 said:**
> ACS accepts TeX/LaTeX submission, according to this: [http://pubs.acs.org/paragonplus/submission/tex.html](http://pubs.acs.org/paragonplus/submission/tex.html)

That's an interesting heads up, and a relatively new (positive!) development, apparently as part of their submission system upgrade.  But I also noted all the caveats they put on the submission in that format.

---

### Post by tweedledee on 2007-07-30
> **edoviak said:**
> **[COLOR="Red"]Sounds good to me!!![/COLOR] I hate "Track Changes."** I prefer that someone types up their comments. That forces them to comment on the content of the paper and forget about trivial stuff like punctuation.

While I don't actually disagree with your sentiment (as I suspect most do, as local collaborators almost always print the document and make changes by hand), most people I expect to be working with remotely prefer the "track changes" approach; or barring that, at least the ability to type the comments directly into the document (which you can't do with a PDF in any efficient manner).  Again, much of these choices boil down not to preference or rational choices, but simply what other people expect.  Windows users in particular tend to have a very low tolerance for anything outside their normal experience.

---

