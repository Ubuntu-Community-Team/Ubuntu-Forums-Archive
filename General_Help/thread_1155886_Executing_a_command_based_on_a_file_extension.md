---
title: "Executing a command based on a file extension?"
date: 2009-05-11
forum: General Help
---

### Post by Develgo on 2009-05-11
Hi. I receive invoices via email that can be read with Striata Reader. I've installed striata reader and everything works fine, but files have to be opened from the command line like this:
$ striata-reader FILENAME.emc
 
What I'd like to do is double-click the *.emc file and have the command execute automatically, IE. pass the file name as a parameter to striata reader. Has anyone ever done anything like this or know how I can possibly do it? :confused:

---

### Post by hw-tph on 2009-05-11
Try doing this in Nautilus (the file manager): Right-click on a .emc file, select Properties from the context menu, and then have a look at the Open With tab. Add Striata Reader there (you might need to add it as a custom command) and then try double clicking an .emc file in the file manager. It should open automatically.

---

### Post by unutbu on 2009-05-11
In Nautilus, the Ubuntu default file browser, right-click on the .emc file. Select Properties>Open With. A list of apps will pop up. If Striata Reader is not in that list, click "Add">"Use a custom command" and type in striata-reader.

---

### Post by Develgo on 2009-05-11
> **unutbu said:**
> In Nautilus, the Ubuntu default file browser, right-click on the .emc file. Select Properties>Open With. A list of apps will pop up. If Striata Reader is not in that list, click "Add">"Use a custom command" and type in striata-reader.
**Thanks a million! This works perfectly.**

---

### Post by mokimoki on 2010-02-15
I have Ubuntu 9.10 installed on both my desktop pc & laptop. I have installed Striata Reader to view my encrypted bank statements. When I try opening a statement I get a message saying "java.io.IOException:broken pipe".I have Java 6 installed. What does this mean and how do I resolve it?

Thank you in advance

---

