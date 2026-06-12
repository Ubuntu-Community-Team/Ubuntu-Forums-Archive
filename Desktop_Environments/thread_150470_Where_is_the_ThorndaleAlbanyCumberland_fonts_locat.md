---
title: "Where is the Thorndale/Albany/Cumberland fonts located?"
date: 2006-03-26
forum: Desktop Environments
---

### Post by tibbe on 2006-03-26
In /etc/fonts/font.conf three fonts used for the web are listed:
```
<!--
 AMT provides metric and shape compatible fonts for these three web font
 families.
 -->
        <alias>
                <family>Times New Roman</family>
                <accept><family>Thorndale AMT</family></accept>
        </alias>
        <alias>
                <family>Arial</family>
                <accept><family>Albany AMT</family></accept>
        </alias>
        <alias>
                <family>Courier New</family>
                <accept><family>Cumberland AMT</family></accept>
        </alias>
```
Where (on the filesystem) are these fonts located? I couldn't find them in /usr/share/fonts.

---

### Post by Jaded Phoenix on 2007-08-21
AFAIK, there are none of such fonts in Ubuntu by default. The reason is simple: these are **sold** by Monospace Imaging. Visit their site and buy the fonts for $42 each if you wish...

By the way: while AMT fonts were designed using the Microsoft fonts metrics, Nimbus fonts family is the most compatible with the PostScript metrics. Use Nimbus, I've found it the most accurate GPL replacement for the MS's fonts.

---

