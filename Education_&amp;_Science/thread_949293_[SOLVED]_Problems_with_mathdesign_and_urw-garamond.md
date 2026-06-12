---
title: "[SOLVED] Problems with mathdesign and urw-garamond in latex"
date: 2008-10-16
forum: Education &amp; Science
---

### Post by jazzgossen on 2008-10-16
I want to \usepackage[urw-garamond]{mathdesign} in a document that I'm writing, but it just doesn't work. When I use it, I get a number of errors from latex, such as:

LaTeX Font Warning: Encoding `T1' has changed to `OT1' for symbol font
(Font)              `operators' in the math version `normal' on input line 114.

LaTeX Font Warning: Encoding `U' has changed to `OML' for symbol font
(Font)              `letters' in the math version `normal' on input line 115.

And the fonts in my document look strange, both math and text fonts (fi ligatures exchanged with \Phi, for example).

I have installed the texlive-fonts-extra package, which includes both mathdesign and the Garamond font.

Has anyone successfully used this package?

---

### Post by pedrogl on 2008-10-16
Hi,
the actual font files aren't installed with texlive-fonts-extra package, you need to install them manually.
Try the getnonfreefonts-sys command:
```
sudo getnonfreefonts-sys garamond
```

---

### Post by jazzgossen on 2008-10-16
I ran getnonfreefonts-sys, and now the pfb files are in /usr/local/share/texmf/fonts/type1/urw/garamond/. I also ran updmap-sys. But I still get the same errors and symptoms from Latex. 

What else do I need to do to make Latex find the files?

---

### Post by pedrogl on 2008-10-16
mmm, that's the downside of latex, it's hell to install new fonts/packages ...
have you tried:```

sudo texhash
```

---

### Post by jazzgossen on 2008-10-17
This is strange... Now the main text of my document is Garamond, but the math looks "broken", with several strange characters:

[IMG]http://www.eyra.se/temp/screenshot-17okt08-749760523.png[/IMG]

I thought that mathdesign would influence the math fonts only, and not the normal text font. This is how it looks without matdesign, using Sabon as the main font, and with the mathfont package to use the same characters for math:

[IMG]http://www.eyra.se/temp/screenshot-17okt08-190583654.png[/IMG]

---

### Post by pedrogl on 2008-10-17
strange, please post the complete output from latex, do you use mathdesign in combination with other packages?

---

### Post by jazzgossen on 2008-10-17
Yes I do. I just tried it on a minimal test document, and there it looks better. Sorry, should have done that first. Thanks for your help.

Just a note to anyone else who tries to mix another text font (Sabon in my case) with mathdesign: the \renewcommand{\rmdefault} must come after \usepackage{mathdesign}

---

### Post by jaguarviajero on 2009-08-30
> **pedrogl said:**
> Hi,
the actual font files aren't installed with texlive-fonts-extra package, you need to install them manually.
Try the getnonfreefonts-sys command:
```
sudo getnonfreefonts-sys garamond
```

I executed the command, but it fails because it cannot find  garamond.zip file in [http://ctan.org/tex-archive/nonfree/fonts/urw/garamond.zip](http://ctan.org/tex-archive/nonfree/fonts/urw/garamond.zip) 

Looking for the location of the file, I found it in [http://tug.ctan.org/get/fonts/urw/garamond.zip](http://tug.ctan.org/get/fonts/urw/garamond.zip)

How can i install the font with the new URL?

thanks in advance

---

### Post by pedrogl on 2009-08-30
This seems like a bug.

Quick fix:

1. copy the script to your home:
```
cp /usr/bin/getnonfreefonts-sys ~/getnonfreefonts-sys
```

2. open the file with gedit and replace line 14 with this:
```
my $TL_version='2009';
```

3. execute the modified script:
```
sudo ~/getnonfreefonts-sys garamond
```

---

### Post by jaguarviajero on 2009-08-31
Thank you very much, the script ran perfectly and the font was installed. However, on compiling my .tex file, an error occurs because the .sty file is not found. I find this strange as the font *was* installed, right?

this is my minimal .tex file header
```

\documentclass[10pt,a4paper]{article}
\usepackage[T1]{fontenc}
\usepackage{lmodern}
\usepackage{garamond}
...

```

i know this is more into the LaTex domain.

thanks again.

---

### Post by XCan on 2009-08-31
Although I dunno much about installing new packages, I just wanted to say that you should avoid ```
 \usepackage[T1]{fontenc} 
``` unless you like pixelated fonts when read on a computer. Use, for example, ```
 \usepackage[latin1]{inputenc} 
``` instead.

---

### Post by pedrogl on 2009-08-31
Hi
Install the texlive-fonts-recommended package. Also, if you want to use mathdesign fonts, install texlive-fonts-extra
```
sudo apt-get install texlive-fonts-recommended texlive-fonts-extra
```

---

### Post by jaguarviajero on 2009-08-31
> **pedrogl said:**
> Hi
Install the texlive-fonts-recommended package. Also, if you want to use mathdesign fonts, install texlive-fonts-extra
```
sudo apt-get install texlive-fonts-recommended texlive-fonts-extra
```

hey, thanks for the suggestion, but the texlive-fonts-recommended package does not contain the garamond font. what do i install it for?

i installed it anyway, and i still cannot get latex to use garamond, i get this warning message: "LaTeX Font Warning: Some font shapes were not available, defaults substituted."

furthermore, what is the point of installing the texlive-fonts-extra package if you still have to download each font? (as suggested [here]("http://ubuntuforums.org/showthread.php?p=7867890")) why doesn't the package contain the .sty files? is it a bug?

---

### Post by pedrogl on 2009-08-31
texlive-fonts-recommended contains the garamond.sty file. texlive-fonts-extra has extra mathematical fonts (for use with garamond).

I think that the actual font cannot be redistributed in the package because of licensing issues. That's why it's "extra" or "recommended".

It's worth to say that installing fonts is hell in latex, because of latex itself, not linux, not ubuntu.

---

