---
title: "How do I  create a PDF from a PostScript document?"
date: 2006-03-15
forum: Desktop Environments
---

### Post by traveller on 2006-03-15
Hello, I &#8220;printed&#8221; a web page as a PostScript file. Now I open it with Evince, I go to file > print, I choose &#8220;Create a PDF document&#8221; and the location I want this document to be saved, click on print and then I receive the error &#8220;Generating PDF is not supported&#8221;. Any help?

---

### Post by kaamos on 2006-03-15
I think some gnome pdf package does that.. Search synaptic. Here is a cli way to do that:
```
sudo apt-get install gs-common
ps2pdf file.ps file.pdf
```

---

### Post by traveller on 2006-03-15
[QUOTE=kaamos]I think some gnome pdf package does that.. Search synaptic. Here is a cli way to do that:
```
sudo apt-get install gs-common
ps2pdf file.ps file.pdf
```[/QUOTE]
I tried with apt-get but it I did not get anything (unless I didn't type the command correctly). Perhaps it's something else missing here... :-k

---

### Post by Sutekh on 2006-03-15
What was the output of the apt-get install command?

Did it say something like this
```
user@ubuntu:~$ sudo apt-get install gs-common
Reading package lists... Done
Building dependency tree... Done
gs-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
user@ubuntu:~$
```
Aka you already have gs-common installed.

Try the other command
```
ps2pdf file.ps file.pdf
```

---

