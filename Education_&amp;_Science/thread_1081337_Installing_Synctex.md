---
title: "Installing Synctex"
date: 2009-02-26
forum: Education &amp; Science
---

### Post by TheAxeR on 2009-02-26
Has anybody had any success installing synctex?

---

### Post by thomaslundgaard on 2009-05-25
Hi!

If you want to use synctex, you need a pdfviewer and a text editor that supports it. To my knowlege, only texworks supports this on linux. I don't like texworks, so I patched the gnome pdfviewer evince and the editor geany, to support synctex. You can get the patches and a guide on howto get it working on my site:

[http://lundgaard.wep.dk/?page=synctex](http://lundgaard.wep.dk/?page=synctex)

---

### Post by lucius.antonius on 2010-03-15
it would be great to get this accepted upstream. have you proposed that?

i saw that there's an old feature request in evince's bugzilla, but nothing got accepted so far. 

[http://bugzilla.gnome.org/show_bug.cgi?id=543503](http://bugzilla.gnome.org/show_bug.cgi?id=543503)

---

### Post by frabjous on 2010-04-09
> **thomaslundgaard said:**
> Hi!

If you want to use synctex, you need a pdfviewer and a text editor that supports it. To my knowlege, only texworks supports this on linux. I don't like texworks, so I patched the gnome pdfviewer evince and the editor geany, to support synctex. You can get the patches and a guide on howto get it working on my site:

[http://lundgaard.wep.dk/?page=synctex](http://lundgaard.wep.dk/?page=synctex)

Thomas,

Thanks for the info. I don't know if you're still checking this thread, but so far  I've got it half-working, following the instructions on your website.

Working on Ubuntu 9.10 64 bit...

In addition to what's listed there, I also had to install the packages:
intltool
libgnome-keyring-dev
libpoppler-glib-dev
to correctly compile evince.

Even though I had a full install of TeXlive 2009 already, I also had to install the texinfo in my attempts to get texi2pdf to work, though I ended up mostly giving up on that.

After compiling both evince and geany, I still couldn't make them work together using your script at first. I wasn't sure whether it was texi2pdf or synctex that was the problem. (My synctex seems to want to segfault a lot of the time, especially when the -x option is used.)

I ended up changing your compilation script, removing a lot of stuff I didn't need (for the purpose of debugging), like BibTeX support and finding the "main" file, and ended up just using straight pdflatex rather than involving texi2pdf (--I didn't really understand the syntax of that line in the bash file--), and getting the necessary info from synctex in a different way.

My modified script is as follows. I apologize for what I'm sure are amateurish steps. I'm quite noobish with bash. (I'm not a programmer; I'm a philosophy professor, so cut me some slack...)

```

#!/bin/bash
# Compile latex document and open viewer at specified location via synctex
LINE=$1
COLUMN=$2
FILE=$3
MAINFILE=${FILE%.tex}

LATEX_LOG="${MAINFILE}.log"
BIBTEX_LOG="${MAINFILE}.blg"
SYNCTEX_FILE="${MAINFILE}.synctex.gz"

## Compile
########################################
pdflatex -halt-on-error --synctex=1 "${MAINFILE}.tex"

    ####################################
    ## Check for warnings in latex log
    ####################################
    # Get warnings from latex logfile
    IGNORED_WARNINGS=$( echo -e "LaTeX Warning: Label \`' multiply defined.\nLaTeX Warning: There were multiply-defined labels." )
    WARNINGS=$( cat "$LATEX_LOG" | grep --ignore-case "LaTeX Warning" | grep --invert-match -F "$IGNORED_WARNINGS" )

    # For each warning
    IFS="
"
    for warning in $WARNINGS; do
        echo ":1:${warning}"
    done
    unset IFS
   
    ## View with synctex
    LINE=$( expr ${LINE} - 1 )

page=""
page=`synctex view -i "$LINE:$COLUMN:$FILE" -o "${MAINFILE}.pdf" | grep "Page:" | sed 's@Page:@@'`
x=`synctex view -i "$LINE:$COLUMN:$FILE" -o "${MAINFILE}.pdf" | grep "h:" | sed 's@h:@@'`
y=`synctex view -i "$LINE:$COLUMN:$FILE" -o "${MAINFILE}.pdf" | grep "v:" | sed 's@v:@@'`
width=`synctex view -i "$LINE:$COLUMN:$FILE" -o "${MAINFILE}.pdf" | grep "W:" | sed 's@W:@@'`
height=`synctex view -i "$LINE:$COLUMN:$FILE" -o "${MAINFILE}.pdf" | grep "H:" | sed 's@H:@@'`

height=$( expr $( echo ${height} | grep -o ^[0-9] ) \* 2 )

if [ "$page" ]; then
        evince --use-absolute-page --page-label "$page" --highlight-rect "${x}:${y}:${width}:${height}" "${MAINFILE}.pdf" 2>/dev/null &
    else
        echo "Synctex did not return usable results, viewing without synctex"
        evince "${MAINFILE}.pdf" 2>/dev/null &
    fi

```With this, I can get forward search working from geany to evince, but so far I've had no luck getting backward search from evince to geany working at all. Double clicking inside evince has no discernible effect whatever, and I don't even know where to begin diagnosing the problem.

---

### Post by witwicki on 2010-04-16
I've been using synctex successfully (with Forward Search and Inverse Search) for the last couple of months in Ubuntu 9.10 using the following...

1. Kile, a KDE editor that I run under Gnome
2. Okular, a KDE PDF viewer that I run under Gnome
3. texlive (2009) installed from a ppa
4. A simple python script that I wrote

Instructions on how to set everything up can be found here: [http://comments.gmane.org/gmane.comp.kde.devel.kile/1340](http://comments.gmane.org/gmane.comp.kde.devel.kile/1340)
(See posts "Stefan Witwicki | 12 Feb 00:39", "Stefan Witwicki | 12 Feb 05:14", "Stefan Witwicki | 12 Feb 23:44")

Let me know if you have any trouble setting things up this way.    I have to say that I much prefer Okular to Evince.  It has some very useful functionality that Evince lacks.

-Stefan

---

### Post by MaraShylaStewart on 2010-04-19
SyncTex is not yet released in current TeX distributions (TeXLive 2007), but you can install it by following these steps:
1- install the TexLive distribution
2- replace the following three files:
C:\TeXLive2007\bin\win32\pdftex.exe
C:\TeXLive2007\bin\win32\pdftex.dll
C:\TeXLive2007\bin\win32\kpathsea356.dll
by pdftex.dll, pdftex.exe, and kpathsea356.dll.
3- Regenerate the format files using the setup program from the TexLive CD

Using SyncTex

Now to generate .synctex files you just need to specify the --synctex command-line argument to pdftex as follows:
pdflatex --synctex=-1 test.tex

---

### Post by witwicki on 2010-04-19
> **frabjous said:**
> Thomas,

Thanks for the info. I don't know if you're still checking this thread, but so far  I've got it half-working, following the instructions on your website.

...

With this, I can get forward search working from geany to evince, but so far I've had no luck getting backward search from evince to geany working at all. Double clicking inside evince has no discernible effect whatever, and I don't even know where to begin diagnosing the problem.

Frabjous,

It just occurred to me that double-clicking may not be the correct way to invoke inverse (a.k.a. backward) search from evince.  Try [Shift]-[leftclick].  That's what it is in Okular.

-Stefan

---

### Post by frabjous on 2010-04-19
> **witwicki said:**
> I've been using synctex successfully (with Forward Search and Inverse Search) for the last couple of months in Ubuntu 9.10 using the following...

Thanks for the suggestions. I used to use Kile and Okular awhile back, but (1) it bothered me having to install half of KDE to use it, (2) Kile seemed far less lightweight compared to the other text editors I use for other purposes, though it's definitely very capable, and (3) the font-rendering and antialiasing in Okular looks simply terrible on my setup compared to evince--which is somewhat of a mystery since both are based on the poppler libraries. (It also loaded slower.)

Still, it might not hurt to try it again. 

> **MaraShylaStewart said:**
> SyncTex is not yet released in current TeX distributions (TeXLive 2007), but you can install it by following these steps:

As I already noted, I'm using TeXlive 2009, which I installed through the online install script. Synctex is definitely installed, and is working fine with TeXworks.

> C:\TeXLive2007\bin\win32\pdftex.exe
C:\TeXLive2007\bin\win32\pdftex.dll
C:\TeXLive2007\bin\win32\kpathsea356.dll
by pdftex.dll, pdftex.exe, and kpathsea356.dll.
Those look like Windows files. What does this have to do with this thread? I appreicate efforts to help, but why do I have a feeling I'm communicating with a bot, or something?


> **witwicki said:**
> 
It just occurred to me that double-clicking may not be the correct way to invoke inverse (a.k.a. backward) search from evince.  Try [Shift]-[leftclick].  That's what it is in Okular.


Believe me, I tried every variant of clicking, shift-clicking, control-clicking, left/right/middle, you name it. No luck. Thanks for the suggestion, though.

Perhaps I should wait until there's an official patch for evince.

---

### Post by witwicki on 2010-04-19
> **frabjous said:**
> Thanks for the suggestions. I used to use Kile and Okular awhile back, but (1) it bothered me having to install half of KDE to use it, (2) Kile seemed far less lightweight compared to the other text editors I use for other purposes, though it's definitely very capable, and (3) the font-rendering and antialiasing in Okular looks simply terrible on my setup compared to evince--which is somewhat of a mystery since both are based on the poppler libraries. (It also loaded slower.)

Still, it might not hurt to try it again. 



I agree that the rendering of Okular looks a little odd, but I find it acceptable for the purposes of LaTeX development.  
(I'm not sure why it would look "terrible", though.  Viewing my PDFs in my environment, it just looks different.  It is as if text is displayed in a slightly different but equally-sized font.  I've never noticed anti-aliasing artifacts.)

And while, as you note, Kile and Okular are not all that lightweight,
personally, I find that the inverse search capability far outweighs any such issues.

---

### Post by Stefanie on 2010-04-30
I also had font rendering issues with Okular in Jaunty and Karmic, but everything is fine under Lucid. 

Getting Synctex to work is much more straightforward now, I installed texlive-full and okular and all I had to do was 

- configure Okular to use gVim as text editor ("gvim --remote-wait +%l "+normal %c|" %f" in my case)
- configure vim-latexsuite's forward search function to use Okular instead of kdvi (see this helpful wiki [https://facwiki.cs.byu.edu/nlp/index.php/Vim%2BLaTeX_on_Linux](https://facwiki.cs.byu.edu/nlp/index.php/Vim%2BLaTeX_on_Linux)) 
- run pdflatex with the option "-synctex=1" 

It's not 100% out of the box (unless maybe you use Kile instead of vim), but it's a lot easier than compiling a patched version of evince :-)

---

### Post by frabjous on 2010-04-30
Thanks for the input everyone.

Since I was upgrading to Lucid anyway, I thought I'd try again with a relatively fresh install. I decided to go with the Lubuntu 10.04 RC for a very lightweight and fast system. 

This time, using Thomas's patched versions of geany and evince, I've gotten it to work (albeit using my bash script instead of Thomas's). So far so good. 

Not sure what the problem was last time. It may have been that I hadn't completely wiped free my old install of evince before compiling his version. (The problem was that evince is a dependency of ubuntu-desktop and I didn't want to uninstall that previously  -- but lubuntu-desktop doesn't come with evince, but with epdfview, so this time I started fresh.)

I've got Kubuntu installed on my work computer, and so I'll probably try getting Kile<>Okular working on there, and try with each until I decide which one I like better. I may even find that I like TeXworks more than either. SyncTeX works on there without a hitch: I was just disappointed by the lack of other features.

---

### Post by frabjous on 2010-05-06
For those following this thread, it's worth noting that if you install TeXlive (2009) and Okular and Kile from the Lucid repos, you not only get inline spellchecking in Kile, but SyncTeX forward/inverse search between it and Okular works out of the box, and you don't even need to follow the instructions Stefan linked to, or use a special compilation script. (All you need to do is make sure the PDFLaTeX output routine is set-up to use SyncTeX: it comes with a "modern" choice that does this.)

I still don't think Okular looks quite as nice as evince, but it does have nice features, and it looks better than I remember it (I last used it back in Jaunty). (At least as good as the PDF preview inside TeXworks, and you can actually print from it!.)

Indeed, you can pretty easily set up Okular to do foward/reverse search with any editor. Indeed, I just got it working with gedit. For inverse search, in Okular just go into Settings > Configure Okular > Editor, and then put in "Custom Text Editor" and put in:

gedit +%l

For forward search, you can just enable the external tools plugin for gedit (under plugins in the Preferences dialogue), and then Tools > Manage External Tools. Define a new one. Put it to use:

```

#!/bin/bash
pdflatex -interaction=nonstopmode -synctex=1 "$GEDIT_CURRENT_DOCUMENT_PATH"
okular --unique "${GEDIT_CURRENT_DOCUMENT_PATH%.tex}.pdf#src:$GEDIT_CURRENT_LINE_NUMBER$GEDIT_CURRENT_DOCUMENT_PATH" &

```You'll probably want to set it to save the current document, and perhaps define a shortcut key. 

This could be tweaked in various ways, and perhaps be made to work with rubber/the gedit LaTeX plugin, master/documents, XeLaTeX, etc.. I'll play around with it some more. Consider also just defining one with just the Okular line so you do  forward search post-compilation without recompiling, and so on.

I imagine getting it to work with geany or most other editors is about as easy.

---

### Post by nortexoid on 2010-07-25
Wow, this is awesome.

I'm running Kubuntu and all I did was configure Okular to use Kile instead of Kate (default) by opening Okular, going to Configure Okular -> Editor, and choosing Kile.

Then open Kile, go to Configure Kile -> Tools -> Build, select PdfLaTeX and make sure the options are "-interaction=nonstopmode -synctex=1 '%source'" (without outer quotes).

When using Kile, there is a ForwardPDF option under Build -> View. (I have it set as a view button in the toolbar.) It takes you from source to PDF. From PDF to source, in Okular hold down the left shift key and click in the document.

---

### Post by juanmah on 2010-11-04
Thx nortexoid. The last gnome update, evince got synctex capabilities, but I was not able to set it up.

I use kile with okular regularly, and your explanation opened me a boost of productivity.

---

### Post by nortexoid on 2010-11-11
One thing I noticed about synctex with Kile and Okular is that it only takes you to the LINE and not the WORD like texshop and mactex do. This can be really unhelpful because often one has lengthy-sized lines (i.e. paragraphs).

Mactex is just a customized version of texlive and I doubt there's anything special about texshop, so why doesn't synctex on okular + kile work like it does on mactex + texshop? Any way of getting the mac effect on linux?

---

