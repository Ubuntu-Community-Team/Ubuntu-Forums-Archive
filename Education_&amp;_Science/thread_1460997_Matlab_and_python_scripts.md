---
title: "Matlab and python scripts"
date: 2010-04-23
forum: Education &amp; Science
---

### Post by FreeTheBee on 2010-04-23
Hi, I use a combination of matlab (R2009b) and python for data analysis. I have a set of python scripts that extract the important stuff from data files and then I use matlab to play with the actual data. Therefore, I often call these python scripts from matlab using the dos() command. In winXP this works fine but in karmic I get an error saying for example "/bin/bash: extrcurve.py: command not found".
When I call the same python scripts from a terminal they work fine, since I did add the folders to my path. I also added them in my path in matlab, just to be sure, but this didn't work.
Anyone knows how to fix this?

---

### Post by FreeTheBee on 2010-04-23
Solved it by adding 
export PATH="$PATH:\path\to\scriptfolder" to the MATLAB/bin/matlab file.

Sometimes google is a worse friend than the help function, I shamefully admit :-)

---

