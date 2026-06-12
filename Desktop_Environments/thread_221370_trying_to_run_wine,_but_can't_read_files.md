---
title: "trying to run wine, but can't read files"
date: 2006-07-23
forum: Desktop Environments
---

### Post by strattonbrazil on 2006-07-23
I'm trying to read a file from a CD that a university sent me.  It's a Mac/Windows CD which I've never really tried before.  I think my computer is reading them wrong, because 'ls' is giving me strange results and 'file' gives me no output.  Here's what I have:

josh@slander:/media/cdrom$ ls -lia
total 0
16582 -r-xr-xr-x 1 root root 0 1917-08-23 01:13 ecclassid field should specify the identifier of the codec class to be used.  the lpvoxwaredata->dwc
    ? ?--------- ? ?    ?    ?                ? ings field is maintained for backwards compatibility.?
16586 -r-xr-xr-x 1 root root 0 1903-05-05 13:17 kwards compatibility.?
16579 -r-xr-xr-x 1 root root 0 1978-03-22 02:36 xwaredata->dwcodecclassid fields both contained values for your request.?the lpvoxwaredata->dwcodecclassid fiel
josh@slander:/media/cdrom$ file ecclassid\ field\ should\ specify\ the\ identifier\ of\ the\ codec\ class\ to\ be\ used.\ \ the\ lpvoxwaredata-\>dwc
ecclassid field should specify the identifier of the codec class to be used.  the lpvoxwaredata->dwc: empty
josh@slander:/media/cdrom$ file 'ings field is maintained for backwards compatibility.
'
ings field is maintained for backwards compatibility.
: ERROR: cannot open `ings field is maintained for backwards compatibility.
' (Input/output error)

---

### Post by greenstar on 2006-07-23
I need more info to help. What kind of file are you trying to read? 

What extension does it have (.doc .mpg .swf)?

What app does it open with in Windows?

If I knew what kind of file it was and what app would be used to open it in Windows, I could be more useful.

Greenstar

---

### Post by strattonbrazil on 2006-07-23
I have no idea what the file extensions are in Windows.  It's my wife's CD for a proprietary biology study guide for grad school.  The program is pretty basic.  Just kind of a walkthrough quiz with explanations.  That's all I know.

---

