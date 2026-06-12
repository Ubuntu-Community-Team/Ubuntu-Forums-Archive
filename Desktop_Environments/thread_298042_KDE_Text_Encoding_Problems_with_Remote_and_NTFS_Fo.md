---
title: "KDE: Text Encoding Problems with Remote and NTFS Folders and Kerry"
date: 2006-11-12
forum: Desktop Environments
---

### Post by drx on 2006-11-12
I have the UTF8 related following issue in KDE:

Kubuntu is running on two computers, sometimes i connect in between them in Konqueror with SFTP, url like sftp://me@192.168.1.1/bla/blubb

Then all my folders and files with Umlauts (ÖÄÄ) an Cyrillic Letters (&#1052;&#1080;&#1088; &#1044;&#1080;&#1085;&#1086;&#1079;&#1072;&#1074;&#1088;&#1086;&#1074;) are displayed Unicode-garbled, meaning the encoding when using sftp seems to be the classic 8 bit ISO-Latin1.

The same happens when i mount NTFS drives: My filenames are UTF8, but konqueror shows them as Latin1 garbled. Kerry, the front-end to Beagle (localindexing service), shows file names as Latin1 ... when i click "reveal in file manager", folders that contain umlauts in Names are not found, the URL shown by Konqueror contains two squares instead of the desired letter.

Is there a setting anywhere where i can switch **everything** to UTF8? I was so happy to finally leave all this 8bit enconding behind ..! :)

---

