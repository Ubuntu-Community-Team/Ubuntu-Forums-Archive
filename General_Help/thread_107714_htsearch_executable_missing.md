---
title: "htsearch executable missing"
date: 2005-12-23
forum: General Help
---

### Post by snowsquirrel on 2005-12-23
I install htdig for use with kdevelop.  But the htsearch executable seems to be missing.  Anyone know which package I need to install to get htsearch?

~S

---

### Post by mlomker on 2005-12-26
I'm not familar with the product...looks like it's CGI.  Here's the output from apt-file:

```

mlomker@mlomkernote:/$ apt-file search htsearch
axiom-hypertex: usr/lib/axiom-20050901/bin/htsearch
axiom-hypertex: usr/lib/axiom-20050901/lib/htsearch
htdig: usr/lib/cgi-bin/htsearch
htdig: usr/share/man/man1/htsearch.1.gz
htdig-doc: usr/share/doc/htdig-doc/html/htsearch.html
khelpcenter: usr/bin/khc_htsearch.pl
nessus-plugins: var/lib/nessus/plugins/htsearch_location.nasl
wwwoffle: etc/wwwoffle/htdig/htsearch.conf
wwwoffle: usr/lib/cgi-bin/wwwoffle-htsearch
zope-cmfplone: usr/share/zope/Products/CMFPlone/skins/plone_ecmascript/highlightsearchterms.js
zope-cmfplone: usr/share/zope/Products/CMFPlone/skins/plone_ecmascript/testHighlightsearchterms.js

```

---

### Post by flai on 2006-02-10
it is installed with the htdig package ... under /usr/lib/cgi-bin/htsearch just put that on kdevelop menu-> settings ->config ... -> Documentation -> Full text search -> htsearch executable

and hopefully it'll work :)

take care

---

### Post by j-strap2 on 2006-03-11
I had the same problem with the missing executable. flai's solution worked for me.

---

