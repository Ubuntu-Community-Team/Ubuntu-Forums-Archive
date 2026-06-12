---
title: "Multimedia &amp; Attachments in Unicode documents using PdfLatex"
date: 2010-07-15
forum: Education &amp; Science
---

### Post by eumetaxas on 2010-07-15
After hours of googling how to import or attach documents, video or audio files to a pdf using Latex, I came up with this guide.

These are personal notes like these ([http://ubuntuforums.org/showthread.php?t=1106025](http://ubuntuforums.org/showthread.php?t=1106025)) in the hope either to help someone or get improved by someone!

**I had no success with any of the following ways with Xetex**.
Because of the advantage of unicode against iso (personal opinion) I made templates for unicode Greek which may apply to any other language.

I am using Ubuntu 9.10, TexLive 2009 & Texmaker. The encoding of the text in TexMaker must be unicode (utf8) and package hyperref is needed in all ways.

**1: The package hyperref**

Clicking either the text or a figure the file (video, image, text) opens in an external window (works with both Evince and Adobe Reader). The file is not attached. The link refers to another file that must be located in the same folder as the pdf.

**2: The package attachfile**

Double click either the icon or text or a picture to open the files (video, image, text) again in an external window. In Ubuntu works only with Adobe Reader.
The files with this package are attached to the pdf with the advantage of being all in one file and the downside to create huge file.

**3: The package Movie15**

The link can be here either text or image. The package Movie15 also attach files. It works only with Adobe Reader on MS Windows because the Adobe Reader on Linux only supports Real Player. Some people report success with Okular (KDE). Personally I did not. As I had neither using a workaround for xetex ([http://asymptote.sourceforge.net/doc/embed.html](http://asymptote.sourceforge.net/doc/embed.html)). The Roadmaps of Okular and Evince say that they will incorporate support for multimedia.

**An example using the above mentioned packages:**

```
%Multimedia & Attachments &#956;&#949; PdfLatex &#954;&#945;&#953; Unicode


\documentclass[10pt,a4paper]{article}
\usepackage[english,greek]{babel}
\usepackage[utf8]{inputenc} 

\usepackage{ucs}
\usepackage[pdftex,colorlinks,unicode,pagebackref=true]{hyperref} % needed  for unicode pdfauthor & pdftitle names!!
\hypersetup{pdftitle={Unicode with PdfTex},
pdfauthor={me},
unicode=true} % needed for unicode bookmarks (side index)!!

\usepackage{attachfile}
\usepackage{graphics}

\usepackage{geometry}
\geometry{verbose,letterpaper}
\usepackage{movie15}
	


\begin{document}
\tableofcontents


The encoding of the text in TexMaker must be unicode (utf8).\\

\section{Inserting and attaching files}


\subsection{Using the hyperref package}

Clicking either the text  \href{run:sample.avi}{here} or a figure \href{run:sample.avi}{\includegraphics{test.jpg}} the file (video, image, text) opens in an external window (works with both Evince and Adobe Reader). The file is not attached. The link refers to another file that must be located in the same folder as the pdf.

\subsection{Using the attachfile package} 

Double click the figure \attachfile[author=me,color=0 0 0,mimetype=video/avi]{sample.avi}\\

or the text \textattachfile[author=me,color=0 0.5 0.2]{sample.odt}{here} \\

or the image \textattachfile{sample.avi}{\includegraphics{test.jpg}}\\

to open the files (video, image, text) again in an external window. In Ubuntu works only with Adobe Reader.\\

The files with this package are attached to the pdf with the advantage of being all in one file and the downside to create huge file.\\

\subsection{Using the Movie15 package}

\begin{figure}[H]
\includemovie[
poster,mimetype=video/avi, inline=true,
text={\small(some text to click on)}]{3cm}{3cm}{sample.avi}
\end{figure}


\begin{figure}[H]
\includemovie[
poster,mimetype=video/avi, inline=true,
text={\includegraphics{test.jpg}}]{3cm}{3cm}{sample.avi}
\end{figure}

The link can be here either text or image. The package Movie15 also attach files. It works only with Adobe Reader on MS Windows because the Adobe Reader on Linux only supports Real Player. Some people report success with Okular (KDE). Personally I did not make it. As I had neither using a workaround for xetex ([http://asymptote.sourceforge.net/doc/embed.html]("http://asymptote.sourceforge.net/doc/embed.html")). The Roadmap of Okular and Evince say that they will incorporate support for multimedia.
 
\end{document}



```

**4: The Multimedia Package**

This package does a similar job with the Movie15. Concomitant use is incompatible. Link can be here either text or image. Files are NOT attached and the media file must be located in the same folder as the pdf. The video is embedded into the pdf (like movie15). I could not get that one to work with Ubuntu. If you put the "external viewer" option the video opens in the another window (like attachfile or hyperref). This works with both Evince and with Adobe Reader. 

**An exapmle using Multimedia Package:**

```
%Only with  pdftex &#942; Latex, NOT xetex

\documentclass[10pt,a4paper]{article}
\usepackage[english,greek]{babel}
\usepackage[utf8]{inputenc} 
\usepackage{ucs}

\usepackage[pdftex,colorlinks,unicode,pagebackref=true,]{hyperref} % needed  for unicode pdfauthor & pdftitle names!!
\hypersetup{pdftitle={Unicode with PdfTex},
pdfauthor={me},
unicode=true} % needed for unicode bookmarks (side index)!!

\usepackage{graphics}
\usepackage{multimedia}


\begin{document}
\tableofcontents \en
\section{Using the multimedia package}

This package does a similar job with the Movie15. Concomitant use is incompatible. Link can be here either text or image. Embedding works with Adobe Reader in Windows. Files are NOT attached. 

\movie[width=3cm,height=2cm,poster]{\includegraphics{test.jpg}}{sample.avi}\\

If you put the "external viewer" option the video opens in the another window (like attachfile or hyperref). This works with both Evince and with Adobe Reader. The link refers to another file to be located in the same folder as the pdf.\\

\movie[externalviewer,width=3cm,height=2cm,poster]{some text to clik on}{sample.avi}\\


\movie[externalviewer,width=3cm,height=2cm,poster]{\includegraphics{test.jpg}}{sample.avi}\\

\end{document}

```

[COLOR="Red"]**[SIZE="3"]If someone had success with Xetex i'll be grateful![/SIZE]**[/COLOR]

Of course comments for improvements or mistakes are always welcome!

---

### Post by Horst_H on 2010-12-18
I've had exactly the same issue for a long time, trying to use xelatex + beamer with embedded movies. I'm on a Mac, not Ubuntu, but I don't think that this makes a difference to the problem. I'm using the TexLive 2009 installation. 

I first downloaded the patch for movie15 called "movie15_dvipdfmx.sty" issued by the makers of asymptote, [http://asymptote.svn.sourceforge.net/viewvc/asymptote/trunk/asymptote/patches/](http://asymptote.svn.sourceforge.net/viewvc/asymptote/trunk/asymptote/patches/). I placed the style file in the same folder as my source files (will move it to a better location in the TeX search path later).

The following code worked for embedding an AVI file:

```

%!TEX TS-program = xelatex 
%!TEX encoding = UTF-8 Unicode

\documentclass[dvipdfm]{beamer} 

\usepackage[dvipdfmx]{movie15_dvipdfmx}

\begin{document}

\begin{frame}
    \frametitle{Vibrating Circular Membrane - Radial Symmetry}
    
    \begin{center}
    \includemovie[poster,text={Vibrating membrane}, mouse, repeat,controls]{.5\linewidth}{.375\linewidth}{membrane_3.avi}
    \end{center}
\end{frame}

\end{document}

```

I was able to play the movie file in Adobe Acrobat.

According to the movie15 package, I should be able to use an image in the "text" option, but neither \XeTeXpicfile nor \includegraphics worked for me here. I suppose you can't have everything.

---

### Post by eumetaxas on 2010-12-19
Thank you for your response!
I have upgraded to texlive 2010 in the meantime - but I will give it a try!

Thank you again,
Eugene

---

