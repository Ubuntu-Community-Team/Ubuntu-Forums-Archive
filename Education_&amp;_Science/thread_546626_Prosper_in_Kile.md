---
title: "Prosper in Kile"
date: 2007-09-09
forum: Education &amp; Science
---

### Post by edoviak on 2007-09-09
I just spent five hours figuring out how to use the[** Prosper**]("http://amath.colorado.edu/documentation/LaTeX/prosper/") document class in [**Kile.**]("http://kile.sourceforge.net/") I'm writing, in part, to make sure that no one else endures such a painful experience and, in part, to find out how bad my solution was. 

I've been writing my dissertation in **Kile**, so I had already installed the **TeTeX** package, on which **Prosper** depends, (I think).

I began by installing the **Prosper** package (which placed the files in my  **/usr/share/texmf/tex/latex** directory). I then tried to create some slides, but I could not understand why the slides that I compiled were always blank. I did a web search and found [**this page,**]("http://linuxnotebook.wordpress.com/2007/08/13/presentations-with-latex-prosper-class/") which suggests manually installing the **prosper**, **contrib-prosper** and **seminar** packages manually. Before going too far however, I noticed that there already was a **seminar** directory in my 
**/usr/share/texmf-tetex/tex/latex/** directory, so I decided to untar the [**prosper** and **contrib-prosper** archives]("http://sourceforge.net/project/showfiles.php?group_id=14812") into that directory. Once again, my slides were blank. 

Finally, I hit upon a solution that worked: 
[LIST=1]
[*]Compile the TeX file with Kile's **LaTeX** button
[*]Convert the DVI to a PS file with Kile's **DVItoPS** button
[*]Convert the PS to PDF with Kile's **PStoPDF** button
[*]View the PDF.
[/LIST]

Would this clumsy solution have worked if I had not untarred the **prosper** and **contrib-prosper** archives into the **/usr/share/texmf-tetex/tex/latex/** directory? In other words, was there any need to download the archives and install manually?

Thanks,
- Eric

---

### Post by LaserJock on 2007-09-09
How were you trying to build/view your slides before?
Your "clumsy solution" is how I normally use Kile :).  I don't think you needed to get the prosper and contrib-prosper tarballs.

-LaserJock

---

### Post by edoviak on 2007-09-09
**[COLOR="Red"]Wow! That was fast! Thanks Laser.[/COLOR]**
> **LaserJock said:**
> How were you trying to build/view your slides before?
Your "clumsy solution" is how I normally use Kile :).  I don't think you needed to get the prosper and contrib-prosper tarballs.

I prior to getting the tarballs, I tried to view the DVIs (with KDVI) and I tried to compile to PDF. Upon seeing a blank DVI/ blank PDF, I got discouraged and I didn't think to convert the DVI to PS.

I was also getting a lot of error messages, which I can no longer reproduce. 

(Sorry. I know that isn't very helpful, but I don't have the time to retrace my steps. I have to give a presentation on Tuesday).

- Eric

---

