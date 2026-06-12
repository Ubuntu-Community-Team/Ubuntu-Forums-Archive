---
title: "Includegraphics{file}?"
date: 2010-02-06
forum: Education &amp; Science
---

### Post by virsto on 2010-02-06
First, I am using Ubuntu 9.10 with Texmaker 1.9.9. I am very new to both Ubuntu and Texmaker and am still in the testing/experimenting mode. 

I recently installed (sucessfully) TexLive 2009 (before installing Texmaker) in:

     /usr/local/texlive/2009/...

and this seems to be fine. However, I am unable to use the LaTeX command that is defined in Texmaker: LaTeX -> includegraphics{file}.

For example in one of LaTeX documents I executed this command and after defining the graphics file had the following:
      
   \includegraphics[scale=1]{smpfig.eps}

Then when I try to compile the file containing this, I get the following error message:

  [COLOR=Red]![/COLOR][COLOR=Red] Undefined control sequence.[/COLOR] 
  l.810 \includegraphics 
  [scale=1]{smpfig.eps}

Why, the error? Is \includegraphics undefined in TexLive 2009? If yes, then how can I work around this problem?

Thanks,
--V

---

### Post by Abdus on 2010-02-06
TeX/LaTeX don't know anything about graphics by themselves. The command you are trying to use \includegraphics is not recognized by LaTeX.

To be able to import images, you must load an appropriate package first, that add \includegraphics command and many many more. I suggest using package named graphicx. YOu do this by using \usepackage command. A sample file below.

It's sometimes painful to learn LaTeX. I know that myself. But it surely pays later. :)

```
\documentclass{article}
[COLOR="DarkGreen"]\usepackage{graphicx}[/COLOR]
[COLOR="Red"]\begin{document}%[/COLOR]
Test document that tries to include graphics named mypicture.eps.

Note that there is no need to specify the file extension,
it is enough to say `mypicture'. Thus this:

\includegraphics[scale=1]{mypicture.eps}

and this:

\includegraphics[scale=1]{mypicture}

produce the same output.

Also note that any packages you load must be loaded \emph{before}
the document starts.
[COLOR="#ff0000"]\end{document}[/COLOR]
```

---

### Post by virsto on 2010-02-07
Thanks for the help! :p
I have things running ok now.

--V

---

