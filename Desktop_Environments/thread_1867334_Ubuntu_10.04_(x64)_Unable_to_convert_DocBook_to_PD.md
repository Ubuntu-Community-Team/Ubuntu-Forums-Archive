---
title: "Ubuntu 10.04 (x64): Unable to convert DocBook to PDF"
date: 2011-10-22
forum: Desktop Environments
---

### Post by noloader on 2011-10-22
Hi All,

I'm trying to familiarize myself with DocBook. I started with O'Reilly's sample at [https://prod.oreilly.com/external/tools/docbook/docs/authoring/docbook_source/](https://prod.oreilly.com/external/tools/docbook/docs/authoring/docbook_source/).

From the command line:

$ docbook2pdf book.xml
Using catalogs: /etc/sgml/catalog
Using stylesheet: /usr/share/docbook-utils/docbook-utils.dsl#print
Working on: <path>/book.xml
openjade:<path>/book.xml:8:19:E: there is no attribute "href"
openjade:<path>/book.xml:8:43:E: there is no attribute "xmlns:xi"
openjade:<path>/book.xml:8:78:E: element "xi:include" undefined
openjade:<path>/book.xml:9:74:E: element "xi:include" undefined
...
$

book.xml is:

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE book PUBLIC "-//OASIS//DTD DocBook XML V4.4//EN"
"http://www.oasis-open.org/docbook/xml/4.4/docbookx.dtd">
<book>
 <title>DocBook Authoring Guidelines</title>

 <xi:include href="bookinfo.xml" xmlns:xi="http://www.w3.org/2001/XInclude" />
 <xi:include href="ch00.xml" xmlns:xi="http://www.w3.org/2001/XInclude" />
 <xi:include href="ch01.xml" xmlns:xi="http://www.w3.org/2001/XInclude" />
 <xi:include href="ch02.xml" xmlns:xi="http://www.w3.org/2001/XInclude" />
 <xi:include href="ch03.xml" xmlns:xi="http://www.w3.org/2001/XInclude" />
</book>

I also fetched the schema specified at
[http://www.w3.org/2001/XInclude](http://www.w3.org/2001/XInclude), and tried to manually include it:
`docbook2pdf -d schema.xml book.xml.` Things only got worse.

I'm on Ubuntu 10.04 (x64). The DocBook package is installed.

$ docbook2pdf --version
DocBook-utils version 0.6.14 (jw version 1.1)
$ openjade --version
openjade:I: "OpenJade" version "1.4devel"
openjade:I: "OpenSP" version "1.5.2"
^C #not sure why it hangs the shell...
$ uname -a
Linux studio 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC
2011 x86_64 GNU/Linux

Any ideas? Thanks in advance.

Jeff

---

### Post by noloader on 2011-10-22
The problem is OpenJade does not understand XInclude  ([http://www.mail-archive.com/docbook-apps@lists.oasis-open.org/msg16648.html](http://www.mail-archive.com/docbook-apps@lists.oasis-open.org/msg16648.html)).  It appears Ubuntu's tools are very outdated.

A ugly workaround is to use xmllint to preprocess the xinclude statements (in case others need it):
```
$ xmllint --xinclude book.xml > book-pp.xml ; docbook2pdf book-pp.xml  ; mv book-pp.pdf book.pdf ; rm -f book-pp.xml book-pp.tex
```

 Many thanks to Christopher Maden.

---

