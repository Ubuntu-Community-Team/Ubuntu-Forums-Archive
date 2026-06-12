---
title: "LaTeX page numbering"
date: 2007-03-25
forum: Education &amp; Science
---

### Post by Ferio on 2007-03-25
I have a LaTeX file in which I don't want a page number to be printed. Its preamble looks like this:
```

\documentclass[a4paper,10pt]{article}
\usepackage[left=2.5cm,right=1.85cm,top=2.5cm,bottom=2cm,noheadfoot]{geometry}
\usepackage[utf8]{inputenc}
\usepackage{indentfirst}
\usepackage{url}
\pagestyle{empty}
\title{}
\author{Ferio}
\date{}

```I've just learned from *Guide to LaTeX, 4th edition*, by Helmut Kopka and Patrick W. Daly, that the "\pagestyle{empty}" command should do the trick, but it doesn't work. Am I wrong? If so, how could I do it?

Thank you in advance.

---

### Post by xadder on 2007-03-26
I just copied your lines, added 

\begin{document}
 TEST 
\end{document}


.. and got an empty page with the word TEST on. Seems to work as it should.

(But if want a title you also need to add \maketitle after begin{document})

---

### Post by NikoC on 2007-03-26
Hi there, I've just started with latex myself and when I use the   \pagestyle{empty} option it doesn't work either when I use article as a document class in the preamble. However when I change this the class to book the option does work...

---

### Post by josephus on 2007-03-26
Hi.  Your latex code works for me.
```
\documentclass[a4paper,10pt]{article}
\usepackage[left=2.5cm,right=1.85cm,top=2.5cm,bottom=2cm,noheadfoot]{geometry}
\usepackage[utf8]{inputenc}
\usepackage{indentfirst}
\usepackage{url}
\pagestyle{empty}
\title{}
\author{Ferio}
\date{}
\begin{document}
Hello World.
\end{document}

```

commenting out the pagestyle line produces a document with a page number.

I'm not sure what is going wrong, maybe you are missing a package.  were there any output warnings?

---

### Post by josephus on 2007-03-26
that's weird.  after six hours of no response, three of us replied at exactly the same time (within 1 minute of each other).

---

### Post by Ferio on 2007-03-26
In fact I've just tested it, and the problem i's the very "\maketitle" command that is triggering the number apparition. Any idea on how to get a title but not a number?

---

### Post by Ferio on 2007-03-26
I've just found that the "\maketitle" command makes the number appear; if you're using it, try to remove it and see whether it disappears or not.

Now it's just a question of finding out how to get a title but not a page number.

---

### Post by Ferio on 2007-03-26
There are warnings, but they're about the bullets for the lists I'm using in the body. The problem seems to be the "\maketitle" command (I thought my problem was in the preamble, not in the body); removing it makes the page number disappear, and if you take it back, the number reappears.

Now it's just a matter of finding out how to get a title but not a number.

---

### Post by Ferio on 2007-03-26
There's not such thing as a coincidence. As they used to said in "Lost" (and I can't believe I'm quoting a TV show):> Everythng happens for a reasonYou three replying at once, LaTeX behaving weird... ;)

---

### Post by NikoC on 2007-03-26
I was looking for arguments for the \maketitle command, but no luck so far... it appears that the package uses \pagestyle to generate the pagenumber...

Now I've been messing around a bit with a document I already had and when changing the document class to book instead of article, adding \thispagestyle{empty} to the title section the first page number is gone!

To restart numbering at the first page after the title I added
\setcounter{page}{1}

It's a work around, but not the best solution imo! Keep us updated when you come up with something!

---

### Post by josephus on 2007-03-26
Found this thread which gives a solution 

[http://lists.debian.org/debian-tetex-maint/2004/10/msg00122.html](http://lists.debian.org/debian-tetex-maint/2004/10/msg00122.html)

Basically insert \thispagestyle{empty}  after the \maketitle

---

### Post by Ferio on 2007-03-26
Wow, it does work, indeed. Thank you very much!

---

### Post by Ferio on 2007-03-26
As Josephus has told me below, it gets solved by adding "\thispagestyle{empty}" after "\maketitle".

---

### Post by Ferio on 2007-03-26
As josephus has told me below, it gets solved by adding "\thispagestyle{empty}" after "\maketitle".

---

### Post by NikoC on 2007-03-27
Just tried it out this morning and it does work! Great tip, thanks josephus!

---

### Post by wasert on 2009-01-14
```

\documentclass[a4paper]{report}
\usepackage[utf8]{inputenc}
\usepackage[spanish]{babel}
\usepackage{url}
\pagestyle{empty}

\title{Documentación sobre DHCP}
\author{Me}

\begin{document}
\maketitle
\thispagestyle{empty}
\tableofcontents
\thispagestyle{empty}

\chapter{Antecedentes}
\section{ARP}
\textit{Address Resolution Protocol} es el protocolo utilizado para encontrar la dirección del nivel de enlace, generalmente la dirección MAC, de un equipo cuando solo se conoce su dirección IP u otra dirección \end{document}


```

I still get a page number on every page after the first two pages. Is this a bug in latex?

---

### Post by ahmatti on 2009-01-15
> 
I still get a page number on every page after the first two pages. Is this a bug in latex?

It seems that also the "chapter" command also makes the page numbers appear. See this link for some solutions [http://www.tex.ac.uk/cgi-bin/texfaq2html?label=nopageno](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=nopageno).

---

### Post by frisket on 2009-01-16
> **NikoC said:**
> I was looking for arguments for the \maketitle command, but no luck so far... it appears that the package uses \pagestyle to generate the pagenumber...

No, LaTeX's default is to number all pages. Adding \pagestyle{empty} in the preamble (before \begin{document}) turns this off for the whole document. Adding it elsewhere in the document turns the page number off from that point onwards. But in both cases it may get reset by some other command: some packages may turn it on after a new \chapter, for example, and \maketitle invokes \thispagestyle{plain}, which includes a page number.

You also put the \title, \author, and \date commands in the preamble. They will work here, but it's more normal nowadays to put them immediately after \begin{document}.

In either case, no titling will appear unless you use \maketitle. Until you do, the title, author, and date are simply memorised and not displayed, because many document packages require other commands to make titling work (eg \submissiondate, \subtitle, \journalname, etc).

The point about \maketitle is that in the article document class it applies \thispagestyle{plain}, and this is what is causing the page number to appear. If you add \thispagestyle{empty} after your \maketitle, the page number goes away *for that page*.

///Peter

---

