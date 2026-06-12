---
title: "Latex: beamer and bibliography"
date: 2011-09-03
forum: Education &amp; Science
---

### Post by erotavlas on 2011-09-03
Hi all,

I would like to add a references to my presentation. I know how to use the bibliography command for an article or thesis. I have tried to use it, but all references don't fit an a single slide and latex doesn't create new slide automatically.
How can I do?

Thank you

PS this is my latex code
```
\documentclass[9pt]{beamer}

\usepackage{amsmath,amssymb,amsfonts}
\usepackage{amsthm}
\usepackage{graphicx}
\usepackage{graphics}
\usepackage{url}
\usepackage{hyperref}
\usepackage{setspace}

\graphicspath{{figure/}}

\newenvironment{myslide}[1] 
{\begin{frame}{\begin{center}#1\vskip-10pt\end{center}}}{\end{frame}}

\mode<presentation>
{
\usetheme[headheight=0.005cm,footheight=0.001cm]{Goettingen}
\usecolortheme{lily}
\setbeamertemplate{theorem}[ams style]
\setbeamertemplate{theorems}[numbered]
}

\setbeamertemplate{footline}[frame number]
\setbeamersize{text margin left=0.15cm,text margin 
\begin{document}

\begin{myslide} {References}
\bibliographystyle{plain}
\bibliography{bibliography} 
\end{myslide}

\end{document}

```

---

### Post by FreeTheBee on 2011-09-03
If it almost fits you could shrink the contents a bit using ```
\begin{frame}[shrink=shrinkpercentage]{Frame title} 
... 
\end{frame}
```

Another option is to use the allowframebreaks option,

```
\begin{frame}[allowframebreaks]{title}
\bibliography{refs}
\end{frame}
```

---

### Post by erotavlas on 2011-09-04
Thank you very much. The second option allowframebreaks works well.

---

