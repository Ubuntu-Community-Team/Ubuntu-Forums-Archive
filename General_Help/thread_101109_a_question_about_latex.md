---
title: "a question about latex"
date: 2005-12-09
forum: General Help
---

### Post by jordilin on 2005-12-09
While processing a file with latex, it does not load british hyphenation patterns. Latex loads american english by default, is there any way to load british english patterns so you can use them? I have seen that there's a file called /etc/texmf/languages.dat, in where you can enable british english, but I don't know how to proceed afterwards.
Thanks

---

### Post by runlevel0 on 2005-12-09
[QUOTE=jordilin]While processing a file with latex, it does not load british hyphenation patterns. Latex loads american english by default, is there any way to load british english patterns so you can use them?[/QUOTE]

First of all: It would be helpful if you paste the preamble.

As far as I understood you know that there is a british language pack but don't know who to use it...

Put this into your preamble
```

\usepackage[british]{babel}

```

Or you could declare 'british' globally within the documentclass tag: 

```

\documentclass[british]{book}
\usepackage{babel}

```

Note that you will perhaps need the babel package installed 
(AFAIK it's in Ubuntu's default LaTeX install).

A third way would be to specify local hyphenation patterns using the [color=#009900]\hyphenation[/color] tag in the preamble:
```

 \hyphenation{Linux,me-ta-bo-lic,hyp-henat-io-n}

```

This means: Linux is never separated, 'metabolic' is hyphenated in the correct way, and 'hyphenation' is separated in a rather weird way as an example. What I don't know is if an explicit \hyphenate tag will override the hyphenation schemes of the language packages.

If you are planning on using LaTeX a lot, I would suggest using KDE with it's fantastic Kile editor: It's a LaTeX editor (source, not WYSIWYG) with built in glossary, tabbed browsing and lot's of automation, wizards, code navigation features and lot's of bells and whistles. It's a nice app for learning LaTeX and also a powerful pro-tool.



Let us know it you have further problems.

---

### Post by jordilin on 2005-12-09
Well, you are right I can put \usepackage[british]{babel} but I don't know if the british hyphenation is really loaded. When you run latex in the shell appears the following whether you have put in the preamble \usepackage[british]{babel} or not:

Babel <v3.7h> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, catalan, croatian, czech, danish, dutch, finnish, greek, iceland
ic, irish, italian, latin, magyar, norsk, norsk, portuges, romanian, russian, s
lovak, slovene, spanish, swedish, turkish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf/tex/latex/base/article.cls

As you can see, british doesn't appear and in /etc/texmf/languages.dat the british hyphenation patterns are not enabled. See an abstract of the file languages.dat:

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% The US-english patterns should be loaded *always* and as *first* ones.
% Define USenglish as an alias for american.
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
american ushyph1.tex
=USenglish

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% UK english, TWO LINES! To enabling these lines, remove %! and the space.
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%! british  ukhyphen.tex
%! =UKenglish

% english should always be defined. Either an alias for american or british.
=english

**But I don't know if commenting out the line about british is enough or not** 
I'm using Ubuntu Breezy Badger 5.10.
As for Kile, it's an excelent application to work with latex :cool:

---

### Post by runlevel0 on 2005-12-09
[QUOTE=jordilin]
But I don't know if commenting out the line about british is enough or not
[/QUOTE]

Ah, OK, LOL.

Before tampering with the files, try this option first:
```

\usepackage[UKenglish]{babel}

``` 

In case it does not work you can uncomment the two lines defining the british hyphenation and comment the US american out. It works, but doing it from within the document seems more elegant ;)

---

### Post by jordilin on 2005-12-09
Thanks indeed, but it seems that Ubuntu does not provide the latest version of latex/tex, which I find disappointing. Ubuntu 5.10 ships the 2001 latex version, when the latest stable one is from 2003.

---

