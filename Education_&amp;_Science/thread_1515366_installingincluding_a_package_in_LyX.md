---
title: "installing/including a package in LyX"
date: 2010-06-22
forum: Education &amp; Science
---

### Post by m4lte on 2010-06-22
hi there,
I'm using LyX on Ubunutu 10.4. I installed everything with through the 'software center' and I'm a beginner when it comes to LaTeX.

I would like to use some math symbols which I read were included in the package mathabx. **How do I install/include a package in LyX?** I had a quick look but couldn't find any simple explanation on the internet. Can anyone help me?
thanks in advance!

---

### Post by NikoC on 2010-06-25
Hmmz,

I'm currently not on an Ubuntu machine, but once you installed the package in latex (there are plenty of guides on how to do that), you can add the package to the preamble in Lyx:
Document > Settings > Latex preamble

\usepackage{mathabx}

This works on my system.

Hope this helps!

---

### Post by m4lte on 2010-06-28
Thanks Niko. I got it.

If anyone else should ever be facing this problem. Here's a general tutorial on how to install latex packages:
[https://help.ubuntu.com/community/LaTeX#Add%20on%20packages](https://help.ubuntu.com/community/LaTeX#Add%20on%20packages)
And here's a specific tutorial how to install mathabx
[http://tech-dailybites.blogspot.com/2009/09/installing-mathabx-package-for-latex-in.html](http://tech-dailybites.blogspot.com/2009/09/installing-mathabx-package-for-latex-in.html)

---

