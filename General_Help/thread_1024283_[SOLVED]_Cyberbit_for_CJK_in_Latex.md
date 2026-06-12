---
title: "[SOLVED] Cyberbit for CJK in Latex"
date: 2008-12-28
forum: General Help
---

### Post by prinny42 on 2008-12-28
Okay, so I'm trying to get CJK working in Latex by installing Cyberbit following the instructions under "New Way" in /usr/share/doc/latex-cjk-common/README.Debian.gz.  I've gotten to the point where I'm supposed to do this:

```
$ for i in *.pfb
        do
         echo "$(basename $i .pfb) $(basename $i .pfb) <$i" \
         >> cyberbit.map
        done
```

However, I had trouble getting that to copy/paste properly, and the instructions said you could put it all on one line, so I did.  What I put in was this:

```
$ for i in *.pfb do echo "$basename $i .pfb) $(basename $i .pfb) <$i" >> cyberbit.map done
```

But when I do that the terminal responds

```
bash: cyberbit.map: Permission denied
```

I've tried all of the following variants:

```
sudo $ for i in *.pfb do echo "$basename $i .pfb) $(basename $i .pfb) <$i" >> cyberbit.map done

$ sudo for i in *.pfb do echo "$basename $i .pfb) $(basename $i .pfb) <$i" >> cyberbit.map done

$ for i in *.pfb sudo echo "$basename $i .pfb) $(basename $i .pfb) <$i" >> cyberbit.map done

$ for i in *.pfb do sudo echo "$basename $i .pfb) $(basename $i .pfb) <$i" >> cyberbit.map done
```

And it never even prompts me for a password; it just gives the same "permission denied" response.

If I try entering it without the dollar sign I get

```
bash: syntax error near unexpected token `>>'
```

The things I've done up till now are as follows:

1) Downloaded Cyberbit.ZIP from [ftp://ftp.netscape.com/pub/communicator/extras/fonts/windows/Cyberbit.ZIP](ftp://ftp.netscape.com/pub/communicator/extras/fonts/windows/Cyberbit.ZIP)

2) Put it in ~/Desktop/holding

3) Extracted Cyberbit.ttf and renamed it cyberbit.ttf

4) Entered these things at the command line:
```
rm -rf ~/.texmf-var/fonts/pk

sudo mkdir -p /usr/local/share/fonts/truetype/bitstream

sudo mv /home/(my username was here)/Desktop/holding/cyberbit.ttf /usr/local/share/fonts/truetype/bitstream

sudo mkdir -p /usr/src/cyberbit-fonts

sudo ln -s /usr/local/share/fonts/truetype/bitstream/cyberbit.ttf /usr/src/cyberbit-fonts/cyberbit.ttf

sudo cp /usr/share/latex-cjk-common/utils/subfonts/subfonts.pe /usr/src/cyberbit-fonts

cd /usr/src/cyberbit-fonts

fontforge -script subfonts.pe cyberbit.ttf cyberbit \
   /usr/share/texmf/fonts/sfd/Unicode.sfd

```

After fontforge did its thing I tried to continue, but that's when I hit this bump.

Does anyone know what I'm doing wrong?  I've tried Google, but all I found was repeats of the directions I was following when I got the error in the first place.

Thank you very much.

EDIT: I thought to try working around it by making cyberbit.map in my home folder and sending it to /usr/src/cyberbit-fonts afterwards, but that's not working.  If I include the dollar sign, bash now tells me that it can't find the command "$".  So if I take out the dollar sign, I'm back to getting the same syntax error I got before.  Any ideas?

---

### Post by prinny42 on 2008-12-29
Alright, I never did get Cyberbit working, but I did manage to get CJK working with Latex, sort of.  I thought I should post this in case anyone else needs to do the same.

Basically, I just did what is described at <http://fsfe.org/en/fellows/ciaran/ciaran_s_free_software_notes/japanese_pdfs_part_2_xetex>.

In case that link breaks at some point in the future, I'm going to reiterate its major points here.  All you have to do is get the texlive-xetex package and use the xelatex command instead of pdflatex or latex.  Here is a template for an input file:

> \documentclass[12pt]{article}
\usepackage{fontspec}

\setmainfont{Sazanami Mincho}

\begin{document}

\section{What I learned today}
I can write this &#31169;&#12399;&#12461;&#12521;&#12531;&#12391;&#12377; in Japanese.

\end{document}

Note that part "\setmainfont".  You might not have Sazanami Mincho; I didn't.  But that's no big deal, to check what Japanese fonts you do have, just use this command:

```
fc-list :lang=ja
```

I hope you might find this of use.

EDIT: Ah, I just noticed that I seem to be using "CJK" and "Japanese" interchangeably.  Well, Japanese is the only one I use, so I don't know if this is of any use if you need Chinese or Korean.  Sorry.

---

### Post by pauljohn32 on 2009-01-17
> **prinny42 said:**
> Okay, so I'm trying to get CJK working in Latex by installing Cyberbit following the instructions under "New Way" in /usr/share/doc/latex-cjk-common/README.Debian.gz.  I've gotten to the point where I'm supposed to do this:

```
$ for i in *.pfb
        do
         echo "$(basename $i .pfb) $(basename $i .pfb) <$i" \
         >> cyberbit.map
        done
```

However, I had trouble getting that to copy/paste properly, and the instructions said you could put it all on one line, so I did.  What I put in was this:

```
$ for i in *.pfb do echo "$basename $i .pfb) $(basename $i .pfb) <$i" >> cyberbit.map done
```

But when I do that the terminal responds

```
bash: cyberbit.map: Permission denied
```

I've tried all of the following variants:

[CODE]sudo $ for i in *.pfb do echo "$basename $i .pfb) $(basename $i .pfb) <$i" >> cyberbit.map done

....[snip]  Any ideas?


I've just finished working on this.  Recall the instructions are for Debian systems, not for the Ubuntu oriented sudo approach.  The error you are getting happens because the "root power" of sudo is,not carrying over to give you permission to create a file by diverting the output with >


To make it work, log in as root like so

# sudo su

after you give a password, then you are in a root account and the commandes they give do work.  And I'll testify that the author of that Debian help page is not lying.  On a new Lenovo T61, the fontforge work to create the type 1 fonts out of the Cyberbit.ttf file takes an eternity.  At least 90 minutes of full out use of a CPU.

After you finish that, you can write Unicode documents that include Chinese characters.  Evidence is here:

http://pj.freefaculty.org/latex/UTF8.pdf

Paul Johnson
Professor, University of Kansas

---

