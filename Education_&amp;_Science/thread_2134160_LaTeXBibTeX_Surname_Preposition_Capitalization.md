---
title: "LaTeX/BibTeX Surname Preposition Capitalization"
date: 2013-04-10
forum: Education &amp; Science
---

### Post by NanakiXIII on 2013-04-10
Hey all,

I was wondering if there was any way to get around this problem: if I have a BibTeX reference and the author surname starts with a preposition (like the Van in Van Gogh), this preposition should be capitalized if it is not preceded by the person's title, initial or name, but it should be lowercase if it is. Specifically, I want a \textcite to read

> as was calculated by De Sitter [1] and ...

but the reference should look like

> [1] W. de Sitter, etc.

LaTeX just uses whatever capitalization is in the .bib file and so one or the other is going to be wrong. Does anyone have any suggestions?

---

### Post by Feathers McGraw on 2013-04-11
I realise that this is not an ideal solution as it only solves your problem indirectly, but have you considered using Biblatex with Biber instead of bibtex?

I believe this will work...

There is an option "useprefix" that you can set per entry or globally (p.60 of the biblatex manual) that is set to false by default.

Setting it "true" would cite the entry with a capital letter:

De Sitter [1]

...if you entered it that way in the .bib file, and the entry would appear in your references under D rather than S, as:

[1] De Sitter, W.

Feathers

---

### Post by NanakiXIII on 2013-04-13
Thanks for the suggestion, Feathers, but unfortunately the output is exactly the same.

---

### Post by Feathers McGraw on 2013-04-13
NanakiXIII sorry that didn't help, if you find an answer please post it here because I'd be interested!

Best wishes, 

Feathers

---

### Post by NanakiXIII on 2013-04-14
One idea I have is to use the shortauthor field and put in the capitalized version there (e.g. shortauthor = {De Sitter}), but I can't figure out how to make \textcite use this shortauthor field. Does anyone know?

---

### Post by Feathers McGraw on 2013-04-14
This might help...if you enter a field like this:

author = "BBC News",

then biblatex/biber treats each word as separate, and cites as "News, BBC".

However, if you put it in like this:

author = "{BBC News}",

both words are treated as one, and you get "BBC News" out.

so perhaps putting it in as

author = "W. {De Sitter}"

would make biblatex/biber use De Sitter as the last name, and not remove the capital D using the method I posted before.

Feathers

---

### Post by xadder on 2013-04-14
I wonder if you need two almost identical entries in the bibtex file, one with {de Sitter} and the other with {De Sitter}?

---

### Post by Feathers McGraw on 2013-04-14
xadder, that would probably work, so long as it was

author = "{de Sitter}" or {{de Sitter}}

and

author = "{De sitter}" or {{De Sitter}}

or you'd have the original problem of biblatex/biber identifying the "de" as a prefix and doing funny things with it / overriding the capital.




If it's still not working, consider trying plain \cite instead of \textcite ? They may behave slightly differently.



Feathers

---

### Post by NanakiXIII on 2013-04-14
Hey guys,

If I make the .bib entry De Sitter instead of de Sitter, that fixes the \textcite, but it comes out wrong in the bibliography (i.e. W. De Sitter, which is not what I want.) I already have brackets around De Sitter too.

How would I got about using two separate entries? Won't they both end up in the bibliography and be numbered differently?

Also, \cite just prints the citation number, not the name.

---

### Post by Feathers McGraw on 2013-04-15
Interesting!

Sorry, I should have thought of that. Two entries would work with Harvard style referencing because there aren't any numbers and you could suppress one in the bibliography and \nocite the other, but unfortunately not with IEEE if that's what you're using.

Similarly, I'm used to using \citep, \citet, \cite for "(Blyth and Freitas, 1984)", "Blyth and Freitas (1984)"  and "Blyth and Freitas, 1984" respectively - I forgot with IEEE that the \cite output is so minimal.

I guess all that's left is to put the entry in so that it appears in the bibliography correctly, then use plain \cite to get the number and manually write the rest of the reference, i.e.

as was calculated by De Sitter \cite{SITTER}
/
W. de Sitter \cite{SITTER} calculated that...

The tiny things in LaTeX are always the ones that are most frustrating!

Feathers

---

### Post by NanakiXIII on 2013-04-20
Awww. I suppose I'll just have to do it manually... It will be the only thing (so far) that LaTeX isn't able to do for me. It breaks my heart.

---

### Post by Feathers McGraw on 2013-04-20
This is why I'd like to learn how to write packages!

---

### Post by NanakiXIII on 2013-04-20
> **Feathers McGraw said:**
> This is why I'd like to learn how to write packages!

Well, if you do learn and decide to fix this problem, let me know! ;)

---

