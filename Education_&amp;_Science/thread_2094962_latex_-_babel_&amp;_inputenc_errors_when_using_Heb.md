---
title: "latex - babel &amp; inputenc errors when using Hebrew"
date: 2012-12-15
forum: Education &amp; Science
---

### Post by hefetza on 2012-12-15
Hello,
I'm considiring using latex instead of libreoffice writer as my main tool for writing essays (I'm a history student). I'd love to start using it but just can't get Hebrew working.
I've downloaded a Hebrew text file which works ok. The only problems I get are the babel error message (which I don't really care about since the pdf output works) and that I can't see the Hebrew fonts when they are in my text editor. I've uploaded it so you can see.

I've tried to insert my own text into the same file but I get (from TexWorks) two error messages:
> Package babel Warning: No hyphenation patterns were loaded for
(babel)                the language `Hebrew'
(babel)                I will use the patterns loaded for \language=0 instead.
and:
> ! Package inputenc Error: Keyboard character used is undefined
(inputenc)                in inputencoding `8859-8'.I get the same messages when I writing my own text, such as:
> \documentclass {article} 
\usepackage[hebrew,english]{babel}
\begin{document} 
&#1513;&#1500;&#1493;&#1501; &#1506;&#1493;&#1500;&#1501;!
\end{document}adding \usepackage[utf8]{inputenc} gives me:
> ! Package inputenc Error: Unicode char \u8:&#1513; not set up for use with LaTeX.and adding \usepackage[utf8x]{inputenc} gives me:
> ! LaTeX Error: File `utf8x.def' not found.I'm using the texlive on Debian Wheezy. I have installed the texlive hebrew package as well.
I've have searched for a solution for hours and though I have found some references to these problems, none of the offered solutions seems to work.

I would really appreciate your help.

---

