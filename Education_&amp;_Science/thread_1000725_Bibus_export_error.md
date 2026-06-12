---
title: "Bibus export error"
date: 2008-12-03
forum: Education &amp; Science
---

### Post by Micronaut on 2008-12-03
Hi,

I have been using Bibus (on Ubuntu 8.10) and inputted >100 references.  I need to export the database to ris and endnote format but I am getting some kind of python error message when exporting to any of the formats in Bibus:

Traceback (most recent call last):
  File "/usr/share/bibus/BibFrame.py", line 1053, in onMenuFileExportRIS
    self.__FileExport('RIS',enc='latin_1')
  File "/usr/share/bibus/BibFrame.py", line 1044, in __FileExport
    exporter.write(ref)
  File "/usr/share/bibus/Export/RIS.py", line 55, in write
    self.infile.write(record)
  File "/usr/lib/python2.5/codecs.py", line 638, in write
    return self.writer.write(data)
  File "/usr/lib/python2.5/codecs.py", line 303, in write
    data, consumed = self.encode(object, self.errors)
UnicodeEncodeError: 'latin-1' codec can't encode character u'\u2013' in position 1245: ordinal not in range(256)


Has anybody else got any experience of this problem in Bibus and how to correct it?

Thanks for any assistance.

---

### Post by Micronaut on 2008-12-03
> **Micronaut said:**
> Hi,

I have been using Bibus (on Ubuntu 8.10) and inputted >100 references.  I need to export the database to ris and endnote format but I am getting some kind of python error message when exporting to any of the formats in Bibus:

Traceback (most recent call last):
  File "/usr/share/bibus/BibFrame.py", line 1053, in onMenuFileExportRIS
    self.__FileExport('RIS',enc='latin_1')
  File "/usr/share/bibus/BibFrame.py", line 1044, in __FileExport
    exporter.write(ref)
  File "/usr/share/bibus/Export/RIS.py", line 55, in write
    self.infile.write(record)
  File "/usr/lib/python2.5/codecs.py", line 638, in write
    return self.writer.write(data)
  File "/usr/lib/python2.5/codecs.py", line 303, in write
    data, consumed = self.encode(object, self.errors)
UnicodeEncodeError: 'latin-1' codec can't encode character u'\u2013' in position 1245: ordinal not in range(256)


Has anybody else got any experience of this problem in Bibus and how to correct it?

Thanks for any assistance.

I was encoding references with non-standard Latin characters. Encoding in UTF_8 produces a correct output file.

---

### Post by frogotronic on 2011-06-16
yep, solved it for me as well

---

