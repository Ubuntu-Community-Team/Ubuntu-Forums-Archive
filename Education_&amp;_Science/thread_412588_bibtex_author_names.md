---
title: "bibtex author names"
date: 2007-04-18
forum: Education &amp; Science
---

### Post by stilllikepine on 2007-04-18
Hello,
I am having trouble with my bibtex file.
When I downloaded entries from medline they were formatted like:
Author = {J. T. Blackburn and B. L. Riemann and J. B. Myers and S. M. Lephart}
However for apacite style to work they need to be like:
Author = {Blackburn, J. T., and Riemann, B. L. etc}

I am trying to use sed to reorganize the author names

I got as far as this:
sed "s/^\([A-Z]\. \), \([A-Z]\. \), \([A-Z][A-Za-z]*\)/\3 \1 \2/" test.txt

but there seems to be an error

Any help would be appreciated.

James

---

### Post by earlycj5 on 2007-04-18
You're submitting your bibtex file or???

If you're referring to your bibliography style (which I think is what you're talking about?), you need to use another bibliography style, has nothing to do with the bibtex file itself.

There's plenty of styles to download, guessing this might be the right style?
[http://www.ctan.org/tex-archive/biblio/bibtex/contrib/apacite/](http://www.ctan.org/tex-archive/biblio/bibtex/contrib/apacite/)

---

### Post by WebDrake on 2007-04-19
> **stilllikepine said:**
> When I downloaded entries from medline they were formatted like:
Author = {J. T. Blackburn and B. L. Riemann and J. B. Myers and S. M. Lephart}
However for apacite style to work they need to be like:
Author = {Blackburn, J. T., and Riemann, B. L. etc}


You should not have to change your BibTeX file in order to use different bibtex styles.  Just change the \bibliographystyle{} command in the initial declarations.

For example,

```

\documentclass{article}

\bibliographystyle{apacite}

\begin{document}
    %your article goes here
\end{document}

```

The whole point of BibTeX is that the formatted output doesn't depend on the way the data is written in the .bib file.  In the BibTeX file you can have for example,

```
author="A. B. Collins and David Edgar Guest and Hawthorne, Igor Joseph"
```

And depending on what bibliography style you pick they might come out as,

A. B. Collins, D. E. Guest and I. J. Hawthorne

or

Collins, A. B., Guest, D. E. and Hawthorne, I. J.

or various other combinations (e.g. some bibliography styles only want the *first* author's surname first and list the others normally).

The only reason you should have to change your .bib file is to add more references to it.  The question of how that data looks when it's put in a document is up to the bibliography style.

Does that sort things for you or are there complications?

---

### Post by WebDrake on 2007-04-19
Hmm.  Just to be sure I downloaded a copy of apacite and it does indeed appear to have some serious problems.  I got a horrific stream of error messages under Kile.

Perhaps you should try the **apalike** bibliography style instead?

---

### Post by stilllikepine on 2007-04-19
Thanks - I also got  a stream of errors with my bib file and apacite.
I used the same bib file and a different style and got no errors.

---

### Post by WebDrake on 2007-04-19
> **stilllikepine said:**
> Thanks - I also got  a stream of errors with my bib file and apacite.
I used the same bib file and a different style and got no errors.

OK.  So the package has serious bugs and shouldn't be used.

I did wonder why it wasn't in the standard tetex packages because I knew there was an APA-related one in there somewhere.  apalike it must be, then.

---

### Post by earlycj5 on 2007-04-20
> **WebDrake said:**
> Hmm.  Just to be sure I downloaded a copy of apacite and it does indeed appear to have some serious problems.  I got a horrific stream of error messages under Kile.

Perhaps you should try the **apalike** bibliography style instead?

Sorry, I should've checked that myself before suggesting it.

If you didn't get it figured out yet you can make a custom .bst file.

```

latex makebst

```

Answer the questions and it will make the custom bibliography style for you.  I used it recently to make a custom style for an annotated bibliography I'm working on.

---

### Post by WebDrake on 2007-04-20
> **earlycj5 said:**
> If you didn't get it figured out yet you can make a custom .bst file.

```

latex makebst

```

Answer the questions and it will make the custom bibliography style for you.  I used it recently to make a custom style for an annotated bibliography I'm working on.

I've not heard of this but it sounds very cool---could you give some more info? :)

---

### Post by xadder on 2007-04-21
I've also been seeing this problem using the natbib package. I don't remember experiencing this before, so I wonder if something changed in texlive (I used tetex until recently).

These days I take care to use the Smith, A. instead of A. Smith notation, but it is irritating to have to do this.

---

### Post by WebDrake on 2007-04-22
I'm using tetex on my system and have no problems with natbib.  Can you clarify the problem?

---

### Post by earlycj5 on 2007-04-22
> **WebDrake said:**
> I've not heard of this but it sounds very cool---could you give some more info? :)
I'll just link to and copy what I found out about it googling something a while back I found this page:
[http://www.andy-roberts.net/misc/latex/latextutorial3.html](http://www.andy-roberts.net/misc/latex/latextutorial3.html)

> 
**Customising bibliography appearance**

In my mind, one the main advantages of Bibtex, especially for people who write many research papers, is the ability to customise your bibliography to suit the requirements of a given publication. You will notice how different publications tend to have their own style of formatting references, which authors must adhere to if they want their manuscript publishing. In fact, established journals and conference organisers often will have created their own bibliography style (.bst file) for those users of Bibtex, to do all the hard work for you.

It can achieve this because of the nature of the .bib database, where all the information about your references is stored in a structured format, but nothing about style. This is a common theme in Latex in general, where it tries as much as possible to keep content and presentation separate - as it should be!

A bibliography style file (.bst) will tell Latex how to format each attribute, what order to put them in, what punctuation to use in between particular attributes etc. Unfortunately, creating such a style by hand is not a trivial task. Which is why Makebst (also known as custom-bib) is the tool we need.

Makebst can be used to automatically generate a .bst file based on your needs. It is very simple, and actually asks you a series of questions about your preferences. Once complete, it will then output the appropriate style file for you to use.

It should be installed with the Latex distribution (otherwise, you can download it) and it's very simple to initiate. At the command line, type:

latex makebst

Latex will find the relevant file and the questioning process will begin. You will have to answer quite a few (although, note that the default answers are pretty sensible), which means it would be impractical to go through an example in this tutorial. However, it is fairly straight-forward. And if you require further guidance, then there is a comprehensive manual available. I'd recommend experimenting with it and seeing what the results are when applied to a Latex document.

If you are using a custom built .bst file, it is important that Latex can find it! So, make sure it's in the same directory as the Latex source file, unless you are using one of the standard style files (such as plain or plainnat, that come bundled with Latex - these will be automatically found in the directories that they are installed. Also, make sure the name of the .bst file you want to use is reflected in the \bibliographystyle{style} command (but don't include the .bst extension!).


HTH!

If you mean you need help on the annotated bibliography then let me know what you want to know about that.  :)

---

### Post by WebDrake on 2007-04-22
It helps very much---what a fantastic tool!  Thank you so much for introducing me to it. :KS

---

### Post by xadder on 2007-04-23
Hi WebDrake, 

I can't reproduce this problem just now, so maybe all is well with standard natbib. (I have beenn using various journal .bst files also, which may have been the problem).

---

