---
title: "Help on GNU R &amp; SPSS file"
date: 2006-03-04
forum: Education &amp; Science
---

### Post by towsonu2003 on 2006-03-04
I'm trying to convert an spss.sav file to something that R can understand. I try to use foreign / read.spss but whenever I use
```

foreign
#or#
read.spss
```
it says "object not found". I am doing something wrong but what? If I can convert this file, I can start trying to learn R finally...

I have r-cran-foreign installed tru the repos, along with about 20 more crans. any help would be really appreciated... thanks.

---

### Post by NoNo_231 on 2006-03-04
If it is an extra package that is installed it has to be loaded first. Try something like this. 
load.package(foreign)
or whatever your package is called

---

### Post by towsonu2003 on 2006-03-04
didn't work: 
```
> load.package(foreign)
Error: couldn't find function "load.package"
> load.packages(foreign)
Error: couldn't find function "load.packages"
```

---

### Post by NoNo_231 on 2006-03-04
Ok you are right. My mistake. I always miss this.
The comand is library() eg 
library(foreign)

The empty library() shows you the packages you have downloaded.

---

### Post by towsonu2003 on 2006-03-04
wow this is some hardcore stuff. let's see if I will stay stable after this experience... 

thanks a LOT!! I would never have found it.

---

### Post by NoNo_231 on 2006-03-04
Oh something more about R. Make a dir and before you start R cd in it. When quiting with q() command you can save workspace in it, so you don't loose your data. 

R package is analogous to S-plus.

Good luck!

---

### Post by towsonu2003 on 2006-03-04
thanks again :) I did make a new dir, but it looks like it doesn't save the data. I'm not surprised, as this is my second day (15 hours...) with R. I'll found a couple of pdfs tomorrow to get started with this wierd thingy (now that I know -kinda- howto import my dear data). Thank god there are people (you) who know about R in the forums :) I wish my stupid schools weren't stuck with windows and offered alternative courses to spss.

---

### Post by NoNo_231 on 2006-03-04
Try this
[http://cran.r-project.org/doc/manuals/R-intro.pdf](http://cran.r-project.org/doc/manuals/R-intro.pdf)
It is from the official site. I found most of the info there.

I wish that too. At least S-plus. It is closer to R. The truth is that SPSS and Minitab are easier. I use in Windows Minitab. For an enterprise Minitab is the best I think. There is also ecxel for windows.

For Linux if you want some easy (but not much statistical job to do you can try Gnumeric (Tools>Statistical analysis) and OpenOffice (but you have to download a package called OOoStat_0-4.zip - Here is an address [http://prdownloads.sourceforge.net/ooomacros/OOoStat_0-4.zip?download](http://prdownloads.sourceforge.net/ooomacros/OOoStat_0-4.zip?download) )

---

### Post by NoNo_231 on 2006-03-20
I found a GUI for R. Here in the forums. The R Commander package (r-cran-rcmdr) actually provides a pretty good gui. If somebody needs it.

---

### Post by towsonu2003 on 2006-03-20
[QUOTE=NoNo_231]I found a GUI for R. Here in the forums. The R Commander package (r-cran-rcmdr) actually provides a pretty good gui. If somebody needs it.[/QUOTE]
And for anyone who, like me, is clueless about how to use R, to launch the gui, start R and type library(Rcmdr). -if I remember correctly

---

### Post by NoNo_231 on 2006-03-20
Right!! ;) And if someone wants to know how a package works could type library(,package) eg library(,Rcmdr). It gives the help file. (Found it by mistake - that's not the official command - but it works).

---

### Post by towsonu2003 on 2006-03-20
[QUOTE=NoNo_231]Right!! ;) And if someone wants to know how a package works could type library(,package) eg library(,Rcmdr). It gives the help file. (Found it by mistake - that's not the official command - but it works).[/QUOTE]
that's a nice tip. I shall try it once I go home.

---

