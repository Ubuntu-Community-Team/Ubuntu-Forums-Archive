---
title: "BibTex and long URLs"
date: 2009-03-21
forum: Education &amp; Science
---

### Post by gauthma on 2009-03-21
Hey all,

I've been trying to add a bibliography entry for this link: [http://lists.gnupg.org/pipermail/gnupg-announce/2003q4/000160.html]("http://lists.gnupg.org/pipermail/gnupg-announce/2003q4/000160.html")

That URL string is 66 chars long, as shown by:
```
$ echo -n 'http://lists.gnupg.org/pipermail/gnupg-announce/2003q4/000160.html' | wc -c 
66

```

The bibtex entry is as follows:
```
@Electronic{ gnupg:elgamal,
	url = "http://lists.gnupg.org/pipermail/gnupg-announce/2003q4/000160.html",
	title = "GnuPG's ElGamal signing keys compromised"
}
```

So far so good. The problem is with the .bbl file that is generated. The part the corresponds to the above entry is as follows:
```
\bibitem{gnupg:elgamal}
Gnupg's elgamal signing keys compromised.
\newblock \ifshowURL {\showURL
  \path|http://lists.gnupg.org/pipermail/gnupg-announce/2003q4/000160.html|}\f%
i.
```

As you can easily guess, the problem is in the last two lines, the "\fi" command is split! This causes an error like this:
```
./lists.bbl:21:Undefined control sequence. ...mail/gnupg-announce/2003q4/000160.html|}\f
```

If I manually edit the .bbl file, so it looks like this:
```
\path|http://lists.gnupg.org/pipermail/gnupg-announce/2003q4/000160.html|}\fi.
```

Then all works fine! But I'm unable to avoid bibtex from breaking the line. If I add more characters to the url, the line still breaks, just at a different location. If it breaks in such a way that I does *not* break any command, then no error occurs, but the url will be split. 

I've also tried to use the url and hyperref packages, inserting the url (in the .bib file) like this: \url{my_long_url_here}, but the \url part shows up in the final pdf...

Does anyone have any suggestion on how to avoid bibtex from breaking lines in such a fashion?

---

