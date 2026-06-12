---
title: "acroread 8, beamer and movies"
date: 2007-10-26
forum: Education &amp; Science
---

### Post by fmytreberg on 2007-10-26
I am a physics professor and use LateX-beamer with Acrobat Reader for presentations.  Previously (until gusty) I could customize how my movies played in  Acrobat Reader by changing the ~/.mailcap file.  For example, this is the relevant feisty ~/.mailcap entry.

```
video/*; mplayer -fps 20 -loop 0 -fixed-vo -vo x11 '%s'
```

I upgraded my laptop to gutsy recently, and thus also upgraded to acroread 8.1.1 from the Medibuntu repos.  Now, when I try to open a movie in Acrobat Reader it no longer uses MPlayer with the options specified in the ~/.mailcap file.  In fact, I cannot figure out how to change the default player and options for acroread.  Did Acrobat Reader start looking elsewhere for mime types?  If so, where is it looking?  Any thoughts about how to solve this issue would be greatly appreciated.

-Marty

---

### Post by hugmenot on 2007-10-26
They had the ingenious idea to make RealPlayer handle the media types in AR8. 
Unfortunately RealPlayer doesn't ship with any useful format support. .avi, .mpg, .wmv and .mov all cannot be played with it. 

There's a support forum at adobe.com. They have quite a bunch of Indian hackers working on it, and they seem quite responsive. 
You might want to add your thought to this thread if you fell like it:
[http://www.adobeforums.com/webx/.3bca21c1](http://www.adobeforums.com/webx/.3bca21c1)

---

### Post by fmytreberg on 2007-10-29
Thanks hugmenot, that is a useful link.  From reading another post [http://www.adobeforums.com/webx/.3bc2ff18/1](http://www.adobeforums.com/webx/.3bc2ff18/1) it appears that, in the absence of RealPlayer, it uses Nautilus to make MIME decisions.  This will make it difficult to use command line options.  I may just need to try installing RealPlayer and then embedding the movies.

-Marty

---

### Post by hugmenot on 2007-10-29
Then please report afterwards, which type of movie you were able to embed and play. I'm really interested.

---

### Post by fmytreberg on 2007-10-30
First of all I was not able to embed video into the PDF document, even with Real Player installed.  However, I was able to control how Acrobat Reader links to movies.  Basically, what I did was created a new MIME type called video/texmpg, and then used Nautilus to choose how to play this type.  Specific instructions follow.

1. Rename all movies from .mpg to .texmpg.  Create PDF document that contains links to these .texmpg files.

2. Create the new texmpg MIME type.  First backup the old xml file and open it in your favorite editor.
```
sudo cp /usr/share/mime/packages/freedesktop.org.xml /usr/share/mime/packages/freedesktop.org.xml_back
sudo vi /usr/share/mime/packages/freedesktop.org.xml
```
Add the following lines to this .xml file.
```
  <mime-type type="video/texmpg">
    <comment>TEXMPEG video</comment>
    <expanded-acronym>LaTeX Moving Picture Experts Group</expanded-acronym>
    <magic priority="50">
      <match value="\x47\x3f\xff\x10" type="string" offset="0"/>
      <match value="0x000001b3" type="big32" offset="0"/>
      <match value="0x000001ba" type="big32" offset="0"/>
    </magic>
    <glob pattern="*.texmpg"/>
  </mime-type>
```
Save and exit the file.

3. Update MIME.
```
sudo update-mime-database /usr/share/mime/
```

4. Now you have defined the new MIME type, but Acrobat Reader will not know how to open it.  So, open Nautilus, find one of your .texmpg files and right click on it, choose Properties -> Open With -> Add -> Use a custom command.  You may enter whatever you wish, this was my choice
```
/usr/bin/mplayer -fps 20 -loop 0 -fixed-vo -vo x11
```

5.  To test that it is working correctly.  You should be able to double-click on any .texmpg file in Nautilus and it will run using the command defined in the last step.  If you double-click any .mpg file it should run using whatever the default application is (VLC on my system).   Now open up your PDF document in Acrobat Reader and your movie should play using the custom command.

-Marty

---

### Post by benjamin.lereverend on 2007-11-09
Hi, I tried to use the following method but Acroread 8 keeps saying the video is not readable, could you reexplain the procedure from scratch.

Cheers, Ben

---

### Post by rosencrantz on 2008-07-25
I got it to work with a shell script (at least on opensuse).

Latex code: 

\href{run:script.sh}{\includegraphics{film still}}

Script: 

#!/bin/sh
mplayer ...Options... movie.avi

Add "application/x-shellscript;/bin/bash %s" in ~./mailcap
One can even remove the window borders (at least in compiz-emerald), do exact scaling and positioning in mplayer (scale and geometry options) and start mplayer on top (window rules) to exactly simulate embedding. 
I don't want to paste the whole [step-by-step how-to]("http://eumenidae.blogspot.com/2008/07/embedded-movies-in-latex-pdf-workaround.html") here, it's a bit long.

---

### Post by electricsbm on 2009-02-21
> **fmytreberg said:**
> 
5.  To test that it is working correctly.  You should be able to double-click on any .texmpg file in Nautilus and it will run using the command defined in the last step.  If you double-click any .mpg file it should run using whatever the default application is (VLC on my system).   Now open up your PDF document in Acrobat Reader and your movie should play using the custom command.

-Marty

Thanks for above pointer. I got konqueror to identify the MIME type and play the movie in mplayer. But the acrobat reader doesn't recognize the MIME type and still complaints about need for extra plugin. The acrobat reader plays the movie ONLY after double clicking on the movie and asking whether I really want to open the file. Is it possible to get the movie to play 'in-situ'? Here is my sample latex file to see if something should be done at latex level.

```

\documentclass[12pt,landscape]{article}
\usepackage{geometry}
\geometry{verbose,letterpaper}
\usepackage[]{movie15}
\usepackage{hyperref}
\usepackage{graphicx}
\begin{document}
\begin{figure}[ht]
\includemovie[
poster,
label=cells,
  text={\small Test mplayer with acroread},
  mimetype=video/texmpg,
]{12cm}{6cm}{test.texmpg}

\end{figure}

\end{document}


```

best
shalin

---

### Post by rosencrantz on 2009-03-31
Just a quick update: Okular/KDE4 plays embedded movies by now. Some hitches:
poster images are not shown, movie keeps running even if you change the page, but the rest works OK. So KDE users are more or less out of trouble ;-)

---

### Post by rosencrantz on 2009-03-31
Sorry, duplicate posting because of connection troubles

---

### Post by dfmalh on 2009-10-25
Hi, I am struggling to get a movie (.avi) into my thesis (PDF) containing about 80 EPS images.

Here is my problem.

To get hyperref to work with my images (80) in my thesis as .eps (for publication) I did the following:

> \usepackage[dvipdfm, pagebackref]{hyperref}

It works when I compile it like this: latex --> dvi --> ps --> pdf

So to include my small movie (.avi) I did the following:

> \usepackage[dvipdfm, pagebackref]{hyperref}
\usepackage{movie15}

This does not work, because movie15 does not work with dvipdfm.

I did not want to use PDFLATEX because it does not include .eps, and if I want to use it, it would mean that I would have to change 80 images to .eps

I read somewhere that there is a package...

> \usepackage{epstopdf}

...that will convert EPS to PDF on demand... So I tried to insert it, and take dvipdfm out, ran PDFLATEX, but then I run into other problems...

Is there anybody who have figured a way out to create a PDF containing and EPS image and a movie? I really need help on this problem.

---

### Post by dfmalh on 2009-10-27
The only way that seems to work well is to convert the EPS images to PDF.

---

### Post by vevo on 2011-07-19
in this post [http://tex.stackexchange.com/questions/12790/can-xelatex-luatex-import-movies](http://tex.stackexchange.com/questions/12790/can-xelatex-luatex-import-movies)
they say that
```
\usepackage[dvipdfmx]{movie15_dvipdfmx}
```
works. But they do not mention the pdf reader.

It does not work for me with ubuntu 11.04 and okular.

---

