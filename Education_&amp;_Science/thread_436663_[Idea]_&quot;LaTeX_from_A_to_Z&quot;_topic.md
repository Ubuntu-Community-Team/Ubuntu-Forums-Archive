---
title: "[Idea] &quot;LaTeX from A to Z&quot; topic"
date: 2007-05-08
forum: Education &amp; Science
---

### Post by Zdravko on 2007-05-08
I strongly suggest that we make an important topic here about LaTeX. It should be like a collection of usefull links to tutorials and additional packages. It would be lovely! :KS

---

### Post by ssam on 2007-05-08
i suggest that the wiki would be a good place to start this.
[https://wiki.ubuntu.com/LaTeX](https://wiki.ubuntu.com/LaTeX)

---

### Post by kleeman on 2007-05-09
You mean like this:

[http://tug.org/TeXnik/mainFAQ.cgi?file=index](http://tug.org/TeXnik/mainFAQ.cgi?file=index)

:lolflag:

---

### Post by Zdravko on 2007-05-12
Okay, I will use this topic to ask my questions.
How do I install the package algoritmx? I have already Kile.

---

### Post by parktownprawn on 2007-05-13
> **Zdravko said:**
> 
How do I install the package algoritmx? 

If that is just a package for Latex try the instructions on 

[https://help.ubuntu.com/community/LaTeX](https://help.ubuntu.com/community/LaTeX)

---

### Post by Zdravko on 2007-05-13
I managed to do it alone! I am proud of this!
Next question: is there a way to convert a latex document to a Word doc document?

---

### Post by xadder on 2007-05-13
I use latex2rtf. Does a pretty good job, even adding figures and equations (as images anyway). Usually needs some hand-work afterwards, but I find I can write in LaTeX, use latex2rtf, and then clean up faster than writing in Word (or rather oowriter or abiword) alone. At least if using equations and references.

A problem is that latex2rtf is built upon tetex, not texlive.  On my system Synaptic  wants to remove all of texlive in order to install latex2rtf, and I didn't want that. However, installation of latex2rtf from the projects home-page (google for it) is dead easy, so thats what I did.

---

### Post by Zdravko on 2007-05-13
Okay, we move on.
I want a piece of text to be set in a specific width - e.g. it shouldn't occupy the whole length of  the page. Instead it should be columnized at half of it. I tried the \parbox, but it doesn't seem to work for me. I get a lot of errors.

---

### Post by Zdravko on 2007-05-15
Is this a difficult question?

---

### Post by parktownprawn on 2007-05-15
try using minipage:

\begin{minipage}{0.5\columnwidth}

your text here

\end{minipage}

---

### Post by venik212 on 2007-05-15
Can anyone tell me how to make Kile aware of the Latex packages I have installed with TexLive?  It is ignoring natbib, for example, even though natbib is installed.
What do I do?

---

### Post by Zdravko on 2007-05-15
I am afraid I don't understand you.  Kile works with tex-live. It is incompatible with tetex. You shouldn't have any problems with tex-live.

---

### Post by ahmatti on 2007-05-16
> **venik212 said:**
> Can anyone tell me how to make Kile aware of the Latex packages I have installed with TexLive?  It is ignoring natbib, for example, even though natbib is installed.
What do I do?

Try running

```
$sudo mktexlsr 
```

 this makes latex aware of new packages

---

### Post by Zdravko on 2007-05-30
Okay. how do I reset chapter numbering in books? It seems that in every part the chapters have continuous  numbering.

---

### Post by Zdravko on 2007-06-09
I think I managed the chapter numbering stuff. Now it is time for a more serious stuff.
I used the beamer class to create a pdf presentation of a scientific article. I also wanted to include some statistical graphics, made in MS Excel. Under OpenOffice, I just did an export to *png of all graphics I am interested in. Then I included them in the slides. Unfortunately I noticed that by zooming everything in the image looses contrast and gets blurred. I am afraid that on a big panel my graphics will appear ugly. What do I do now? Maybe I should include them in LaTeX in another way? Please, tell me!

---

### Post by Richard_L on 2007-06-09
"Under OpenOffice, I just did an export to *png of all graphics I am interested in."

Try use pdf instead.
Under OpenOffice, just do an export to *pdf of all graphics you are interested in.

---

### Post by Zdravko on 2007-06-10
Then how do I embed them in the LaTeX presentation?

---

### Post by Richard_L on 2007-06-10
I haven't used beamer but I think you should use \includegraphics{filename} and load \usepackage{graphicx, color}. But read the beamer tutorial.

---

### Post by parktownprawn on 2007-06-11
you could also try export them as postscript.

---

### Post by dimitrispao on 2007-06-14
[IMG]http://s3.bitefight.gr/c.php?uid=16402[/IMG]

---

### Post by Zdravko on 2007-06-14
[dimitrispao]("http://ubuntuforums.org/member.php?u=322625"), wtf?

---

### Post by jbor7755 on 2007-06-21
Can  anyone tell me how the isotope package works?
I am in physics and need to type a lot of isotopes so it could be more usefull than using mchem (and definitely more usefull than maths mode!)

---

### Post by neoflight on 2007-06-21
> **Zdravko said:**
> I managed to do it alone! I am proud of this!
Next question: is there a way to convert a latex document to a Word doc document?

that defies the whole purpose ..dosnt it? well one way to do is to convert to pdf and copy-paste .:)

---

### Post by Typhoon on 2007-06-22
In a way, I suppose it does defeat the purpose, but if you are dealing with publishers you may not have a choice.

latex2rtf usually works pretty well if you are using the standard document classes.

If you are using something less usual, tex4ht works very well. The command "oolatex" will convert into an OpenOffice document. Depending on your system, the oolatex command may be hidden: mine is in /usr/share/tex4ht/oolatex which is not on my PATH so it needs to be entered in full.

HTH,
Typhoon

---

### Post by Zdravko on 2007-06-23
Help! I cannot include bmp or svg pictures in the slideshow! 
I use:
\includegraphics[scale=0.4]{arcs2}
where arcs2.bmp
But it says: ./RSWSN.tex:247:File `arcs2' not found. \end{frame}

---

### Post by frisket on 2007-06-28
Don't forget that if you typeset something in a narrower width without making the font size smaller, you will almost certainly get overfull and underfull hboxes simply because the text won't fit nicely.

Dare I ask *why* you want to typeset the text in a half-width column? That might be a key to the solution. Is the column to be centered, or placed left or right?

---

