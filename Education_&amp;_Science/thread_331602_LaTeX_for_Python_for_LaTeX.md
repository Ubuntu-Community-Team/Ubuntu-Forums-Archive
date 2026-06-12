---
title: "LaTeX for Python for LaTeX?"
date: 2007-01-04
forum: Education &amp; Science
---

### Post by Steveire on 2007-01-04
I am using LaTeX to write my thesis, which requires some python code. I 
 found the listings package some time ago, to do code highlighting, and 
 I've attempted to configure it to look like the highlighting produced 
 by the KDE text editor Kate. My attempts have been largely successful, 
 but I've had to use a work-around to get digits and special characters 
 highlighted. 
 
As a result, the highlighting is not as I'd like it. It highlights the 
 digit '1' in button1, and all digits and specified 'keywords' in 
 strings and the shebang line. If I could use the emph command on the 
 digits and braces/brackets etc that would be a lot better because it 
 would handle comments and strings as I expect it to. I have been 
 unsuccessful in trying to use the emph command on these characters 
 however. I even tried using character codes like chr(53), but to no 
 effect. 
 
Any pointers on getting this right are welcome. 
 
Here is a sample: 
```

 \documentclass[11pt]{report} 
  \usepackage{palatino} 
  \usepackage{listings} % Gives syntax highlighting for python code. 
  \usepackage{color} % Used for syntax highlighting. 
  \usepackage{textcomp} % Used for syntax highlighting. 
 
 % This gives syntax highlighting in the python environment 
  \renewcommand{\lstlistlistingname}{Code Listings} 
  \renewcommand{\lstlistingname}{Code Listing} 
  \definecolor{gray}{gray}{0.5} 
  \definecolor{key}{rgb}{0,0.5,0} 
  \lstnewenvironment{python}[1][]{ 
  \lstset{ 
  language=python, 
  basicstyle=\ttfamily\small, 
  otherkeywords={1, 2, 3, 4, 5, 6, 7, 8 ,9 , 0, -, =, +, [, ], (, ), \{, \}, :, *, !}, 
  keywordstyle=\color{blue}, 
  stringstyle=\color{red}, 
  showstringspaces=false, 
  emph={class, pass, in, for, while, if, is, elif, else, not, and, or, 
  def, print, exec, break, continue, return}, 
  emphstyle=\color{black}\bfseries, 
  emph={[2]True, False, None, self}, 
  emphstyle=[2]\color{key}, 
  emph={[3]from, import, as}, 
  emphstyle=[3]\color{blue}, 
  upquote=true, 
  morecomment=[s]{"""}{"""}, 
  commentstyle=\color{gray}\slshape, 
  framexleftmargin=1mm, framextopmargin=1mm, frame=shadowbox, 
  rulesepcolor=\color{blue},#1 
  }}{} 
  \begin{document} 
 
 \lstlistoflistings 
  \clearpage 
 
 Code listing \ref{svntoolsource} shows a sample. 
 
 \begin{python}[caption={SvnTool source code},label=svntoolsource] 
  #!/usr/bin/env python 
  #-*- coding: utf-8 -*- 
 
 class MyClass(MyOtherClass): 
  """ 
  Some Docstring 
  """ 
  def _init_(self): 
  fruitbowl = ["pear", "peach", "banana"] 
  for fruit in fruitbowl: 
  print fruit 
  if fruit is "pear": 
  continue 
  elif fruit is "banana": 
  break 
  else: 
  pass 
  if fruitbowl is not None: 
  var = True 
  else: 
  var = False 
  a = 3 
  b = -4 
  string = "one-two" 
  name = "Username: " 
  self.button1.connect(self.button1, 
  SIGNAL('clicked()'), 
  self.login) 
  return 
  \end{python} 
 
 \end{document} 

```

I posted this on comp.text.tex but it has so far been overlooked.

---

### Post by UbuWu on 2007-01-06
Maybe you could use [pygments]("http://pygments.pocoo.org/") to convert the code to latex?

---

### Post by Steveire on 2007-01-13
Yes, I actually tried pygments before finding listings. I prefer listings because it preserves the code without markup all over it in the .tex files. I have emailed the maintainer of that package now, so hopefully I'll get some help on it and won't have to learn everything about tex .sty files from the ground up...

---

### Post by Steveire on 2007-03-03
This has been resolved. The maintainer of the listings package got back to me, and the result is below and in the attachment.

```

\documentclass{article}
\usepackage{color}
\usepackage{listings}
\usepackage{textcomp}
\usepackage{setspace}
\usepackage{palatino}

\renewcommand{\lstlistlistingname}{Code Listings}
\renewcommand{\lstlistingname}{Code Listing}
\definecolor{gray}{gray}{0.5}
\definecolor{green}{rgb}{0,0.5,0}

\lstnewenvironment{python}[1][]{
\lstset{
language=python,
basicstyle=\ttfamily\small\setstretch{1},
stringstyle=\color{red},
showstringspaces=false,
alsoletter={1234567890},
otherkeywords={\ , \}, \{},
keywordstyle=\color{blue},
emph={access,and,break,class,continue,def,del,elif,else,%
except,exec,finally,for,from,global,if,import,in,is,%
lambda,not,or,pass,print,raise,return,try,while},
emphstyle=\color{black}\bfseries,
emph={[2]True, False, None, self},
emphstyle=[2]\color{green},
emph={[3]from, import, as},
emphstyle=[3]\color{blue},
upquote=true,
morecomment=[s]{"""}{"""},
commentstyle=\color{gray}\slshape,
emph={[4]1, 2, 3, 4, 5, 6, 7, 8, 9, 0},
emphstyle=[4]\color{blue},
literate=*{:}{{\textcolor{blue}:}}{1}%
	{=}{{\textcolor{blue}=}}{1}%
	{-}{{\textcolor{blue}-}}{1}%
	{+}{{\textcolor{blue}+}}{1}%
	{*}{{\textcolor{blue}*}}{1}%
	{!}{{\textcolor{blue}!}}{1}%
	{(}{{\textcolor{blue}(}}{1}%
	{)}{{\textcolor{blue})}}{1}%
	{[}{{\textcolor{blue}[}}{1}%
	{]}{{\textcolor{blue}]}}{1}%
	{<}{{\textcolor{blue}<}}{1}%
	{>}{{\textcolor{blue}>}}{1},%
framexleftmargin=1mm, framextopmargin=1mm, frame=shadowbox, rulesepcolor=\color{blue},#1
}}{}

\begin{document}

We can see in Code Listing~\ref{ex1} that... And compared to Code Listing~\ref{ex2} something else.

\begin{python}[moreemph={[4]42},caption={Simple python example No. 1},label=ex1]
#!/usr/bin/env python3

class MyClass(MyOtherClass):
  """
  Some Docstring ()
  """
  a = 3
  b5 = -42
  q = (3, 5, j)
  SIGNAL('clicked()'),
  "A String"
\end{python}

\begin{python}[moreemph={[4], 46, 48},caption={Simple python example No. 2},label=ex2]
#!/usr/bin/env python 
#-*- coding: utf-8 -*- 
 
class MyClass(MyOtherClass):
  """ 
  Some Docstring 
  """ 
  def __init__(self):
    fruitbowl = ["pear", "peach", "banana"]
    for fruit in fruitbowl:
      print fruit
      if fruit is "pear":
        continue
      else:
        pass
    if fruitbowl is not None:
      var = True
    else:
      var = False
    a = 3
    b = -46
    c = 3.48
    someDict = {'one':1, 'two':2, "three":3}
    aTuple = (1, 2, 3, 4, 5)
    string = "one-two=3"
    name = "Username: "
    self.button1.connect(self.button1,
        SIGNAL('clicked()'),
        self.login)
    return
\end{python}

\lstlistoflistings

\end{document}

```

---

### Post by james39 on 2009-12-30
Apologies for digging up a very old thread, but I just wanted to say thanks for this code. It's proving very useful for a project I'm working on.

I was wondering if someone could advise if it would be possible to force a word wrap within this environment, as some of my lines of code are running off the page.

Thanks

---

### Post by teMplaryum on 2011-12-17
Like poster before me, I too am sorry for revamping this thread, but I wanted to say thanks for this excellent snippet, helped me a lot with typing beautiful chunks of Python code in Latex.

---

