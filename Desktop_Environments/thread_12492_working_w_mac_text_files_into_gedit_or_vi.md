---
title: "working w/ mac text files into gedit or vi"
date: 2005-01-24
forum: Desktop Environments
---

### Post by fashions on 2005-01-24
need help with mac text file loosing tabs and cr when working with them in ubuntu. 

i have a 13,000 line text file that want to use grep on. when imported into my ubuntu box i have lost the tabs and carriage returns. the file has become one line!

on local network, have mac text file saved to linux server. used smb to move file to ubuntu box via drag / drop to home directory. (samba shared directory not mounted)
when this file is view from mac os with text editor on the linux server tabs / cr ok. 
when viewed on the ubuntu box with vi or gedit, the file becomes one line. ??

what is going on ???  HELP

thanks,
fashions

---

### Post by adamw on 2005-01-26
You could try using tr
try this from your command-line:
tr '\r' '\n' > fileout < youroriginalfile

This will convert your line endings from carriage returns to linefeeds, the basic difference between Mac and UNIX files.
For more info on tr, type "man tr" at your command prompt.

hth,
Adam Winiecki

---

### Post by fashions on 2005-01-27
[QUOTE=adamw]You could try using tr
try this from your command-line:
tr '\r' '\n' > fileout < youroriginalfile

This will convert your line endings from carriage returns to linefeeds, the basic difference between Mac and UNIX files.
For more info on tr, type "man tr" at your command prompt.

hth,
Adam Winiecki[/QUOTE]

thanks Adam
gave it a try and am missing something big time
  $ tr '\r''\n' > inv.sktestcr < inv.sktest
tr: two strings must be given when translating

# inv.sktestcr was the new file
# inv.sktest was the original file.
hmmm.....

went back and took a closer look at example above and noticed a space between the single quotes and bam .... new file with many lines instead of one line.  YAHOO!

a very big thank you. !  =D>

---

