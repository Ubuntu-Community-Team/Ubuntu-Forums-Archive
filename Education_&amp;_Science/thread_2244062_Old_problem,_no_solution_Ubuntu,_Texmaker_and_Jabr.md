---
title: "Old problem, no solution: Ubuntu, Texmaker and Jabref"
date: 2014-09-13
forum: Education &amp; Science
---

### Post by peterpan4 on 2014-09-13
Dear all,

I am trying to create a bibliography in Texmaker and I run into the same problem which many people seem to have run into without finding a tutorial or a clear, applicable solution.

When trying to compile my jabref file (saved both as .bib and without suffix), I simply get a "Process exited with error(s)" message and &#8220;undefined citation&#8220; in the log.

Texmaker usually works (.tex compiles without problems) so I'm not used to asking questions about it. What can I provide to make this problem reproducible for you and thus possible for others to follow? I think one well answered post could solve this problem for everyone to google & follow but that does not exist yet.

I have tried the F1 F11 F1 F1 trick, F1 compiles, F11 provides the problem above. I have tried to install biber but found no version of it in the software center. I have tried to upgrade Texmaker manually via the website but got an error message. I have changed my folder structure to avoid underscores, no results. I have played around with different suggestions for "Options-Configure Texmaker-Bibtex", no results. I have tried to compile it in Windows: no problem. However, my Texmaker might be set up quite differently in Windows, I installed it a long time ago.

 When one googles "Jabref Texmaker Ubuntu" one finds hundreds of posts with similar issues. I'm not sure if it is an ubuntu problem but the suggested solutions seem to be ubuntu specific which is why I am asking here.

This seems to be a standard problem, is there a standard solution? Or a program which works? I am not fixed on either Texmaker or (especially) Jabref.

Any help would be greatly appreciated!

---

### Post by peterpan4 on 2014-09-13
When i go into the section I load with \bibliography{...} I see entries of this type:

% This file was created with JabRef 2.7b.
% Encoding: UTF-8

@ARTICLE{Campos2001,
  author = {Nauro F. Campos},
  title = {Will the Future Be Better Romorrow? The Growth Prospects of Transition
    Economies Revisited},
  journal = {Journal of Comparative Economics},
  year = {2001},
  volume = {29},
  pages = {663-676},
  owner = {frank},
  timestamp = {2014.09.12}
}

so that doesn't look to bad. But why does Texmaker not simply use this information?

---

### Post by steeldriver on 2014-09-13
I'm not familiar with jabref, but in my (limited) experience of bibtex it is very picky about "special" characters (even things that appear commonly in citations - such as punctuation and parentheses)

Perhaps if you post the complete error message and the bibtex entry for the failing citation someone will be able to spot what it's complaining about?

---

### Post by peterpan4 on 2014-09-14
Thanks for your answer! The problem is that there is no error message. The command line simply reads "Process exited with error(s)" and the log gives no error messages except if I included a \cite{...} when it tells me that the citation is unspecified.

---

### Post by steeldriver on 2014-09-14
Sorry I'm having trouble understanding exactly what you're saying - can you clarify that you 

1. have created an appropriate *somefile*.bib file in the same directory as the .tex file

2. have run BibTex on the .bib file to create a *somefile*.bbl file?

3. included the bibliography in your .tex document e.g.

```

[COLOR=#800000]\bibliography[/COLOR][COLOR=#000000]{somefile[/COLOR][COLOR=#000000]}[/COLOR]

```

What command exactly is being run that is producing the "Process exited with error(s)" response?

---

