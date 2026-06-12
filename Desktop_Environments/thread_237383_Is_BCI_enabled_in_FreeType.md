---
title: "Is BCI enabled in FreeType?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by effo on 2006-08-16
I wonder if the BCI is enabled in the FreeType library included in Dapper 6.06? How do one find it out? If it isn't enabled, how can one turn in on? By recompiling the library?

Thanks in advance
Fredrik

---

### Post by Ragger on 2006-10-12
Good question. Could someone please answer? I would like to know myself.
According to [this font story]("http://avi.alkalay.net/linux/docs/font-howto/Font.html#freetype") FreeType compiled with BCI presents better font rendering.

---

### Post by nylle on 2006-10-19
Yes, I've been looking around and haven't found any conclusive answer to this. Apparently debians libfreetype6 package in testing and unstable have BCI enabled, but I haven't found anything on ubuntu.

---

### Post by parszab on 2006-10-26
Yes, according to the freetype source package, freetype-2.1.10/debian/changelog file:

* [ftoption.h] Enabled Graham Asher's unpatented hinting:
      #define TT_CONFIG_OPTION_BYTECODE_INTERPRETER
      #define TT_CONFIG_OPTION_COMPILE_UNPATENTED_HINTING
    Many thanks to Graham Asher and Artifex for their contribution!

While testing I've rebuilt the libfreetype6 package without BCI and after installing it the fonts were definitely not BCI-ed. So the answer is positive.

Bye:
Szab

---

