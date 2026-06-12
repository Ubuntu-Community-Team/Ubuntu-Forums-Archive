---
title: "How to debug clipboard issues"
date: 2010-07-31
forum: Desktop Environments
---

### Post by matteosistisette on 2010-07-31
Hi,

I'm trying to debug some issue with copying data to the Clipboard from an Adobe AIR application (with AIR's clipboard API) and pasting it into an OpenOffice spreadsheet.

Is there any application that would let me inspect the system's clipboard contents in detail? By "in detail" I mean:
- see ALL the information the clipboard contains, including any kind of metadata. As far as I understand the clipboard may contain data in several "formats" (for example bitmap images, text, rich text...) so the information about what format the data is must be stored somewhere
- see the content both as ascii and Hex, so I can tell, for example, whether a newline is coded as CRLF or just LF

I've already installed Glipper but it does nothing of this.
Pasting into Gedit may help me just a little bit to say whether the data has been copied into the clipboard and whether text data is roughly right, but I cannot see low-level information that can help me debug any kind of issue.

Is there such a tool? If not, can anybody suggest any trick that can let me see low-level raw byte content of the clipboard even if in a less readable way?


Thank you very much in advance
bye
m.

---

