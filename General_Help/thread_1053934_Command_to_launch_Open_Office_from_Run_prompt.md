---
title: "Command to launch Open Office from Run prompt?"
date: 2009-01-29
forum: General Help
---

### Post by Pipps on 2009-01-29
Hello

Apologies if this question has been asked before. I haven't been able to find the answer I need from an inital Google search.

I have installed Open Office 3 into the latest version of Ubuntu using the instructions found openly on the web.

I would like to be able to ascertain the command to be able to load Open Office Writer or Open Office Calc from the Run prompt. -writer and -write do not appear to work.

Please help! Thanks.

---

### Post by abhilashm86 on 2009-01-29
go to terminal,type

openoffice

it worked fine for me,i guess it works for latest version also,did it work

---

### Post by abhilashm86 on 2009-01-29
use man openoffice or info openoffice,
that should give you much information about the usage from terminal point of view...........

---

### Post by overlord.gaurav on 2009-01-29
OpenOffice.org Word Processor
```
ooffice -writer
```

OpenOffice.org Presentation
```
ooffice -impress
```

OpenOffice.org Spreadsheet
```
ooffice -calc
```

OpenOffice.org Drawing
```
ooffice -draw
```

---

### Post by Pipps on 2009-01-29
Thank you for your replies.

When I type *ooffice -writer* in the 'Run Application' prompt, I receive the following error message:

> Error starting file '/home/user/oofice- writer'. No such file or directory.

What could be wrong?

---

### Post by SteveDee on 2009-01-29
> **Pipps said:**
> Thank you for your replies.

When I type *ooffice -writer* in the 'Run Application' prompt, I receive the following error message:



What could be wrong?

Is it installed properly and in the right directory?

In a terminal window type: whereis ooffice

It should be in: /usr/bin

---

### Post by sedawk on 2009-01-29
With 2.4 I do this from a shell:
```

oocalc mytable.ods
oowriter mytext.odt

```

---

### Post by overlord.gaurav on 2009-01-29
If you installed using the download on the OOo website, you can start
Writer by typing at the command line:
```
soffice -writer
```
or
      ```
swriter
```

Writer will start and create a new document. Likewise, you can start
other OOo components from the command line:

 Spreadsheet```

soffice -calc
```                
 Drawing```

soffice -draw
``` 
 Presentation```

soffice -impress
```
 Formula```

soffice -math
```
 Web page```

soffice -web
```

---

### Post by Pipps on 2009-02-02
I have independently found a command which works:

```
openoffice.org3 -writer
```

I'm sorry to say that none of the other commands which were suggested seemed to worked.

Thanks for your help anyway.

---

### Post by dtower on 2009-11-23
I downloaded Open Office from the website, and the commands above just freeze up the terminal. When I try to start it through GUI, it crashes. Is there something I'm missing? I'm using Ubuntu 9.10 and everything worked fine on Ubuntu 9.04 before the upgrade. The Ubuntu native version of OOo crashed when I tried to save .doc files, so I completely removed it and installed from the website. Now, it usually crashes on startup, but if I do somehow get it running (usually by opening a "draw" or another kind of document first and then File-> New document--> Writer), it runs beautifully with no crashing. Getting it started is the trick, though. Right now, even other types of documents won't open, for example.

---

