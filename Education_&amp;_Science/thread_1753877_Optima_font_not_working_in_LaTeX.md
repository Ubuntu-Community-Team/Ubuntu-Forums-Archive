---
title: "Optima font not working in LaTeX"
date: 2011-05-09
forum: Education &amp; Science
---

### Post by Abdaxz on 2011-05-09
Hi,

After installing Ubuntu 11.04 my old documents using the (in my opinion very nice) font "optima" do not compile any more -- or rather, it compiles but uses the standard CM font instead.

I have installed the texlive-extra-fonts which says that it contains optima (and it did in Ubuntu 10.10). I include optima using "\renewcommand{\sfdefault}{uop}" as I like it to be the default sans serif.

Any ideas?

Best regards,

Tobias

---

### Post by timothy_tim on 2012-01-26
This issue has been bugging me for several hours, but I eventually found out how to solve this.

The real problem here is that the due the license of the Optima clone 'classico' the package can't be included in the 'texlive-extra-fonts'-package.

To install you've to execute:
```
~$ sudo getnonfreefonts-sys classico
~$ sudo updmap-sys --enable Map=uop.map
```

Also, make sure there is no conflicting '.texmf-var/' directory in you home directory by executing 'updmap --enable Map=uop.map' if you already have this directory or remove the directory.

Note these similar problems:
[http://ubuntuforums.org/showthread.php?t=1546988](http://ubuntuforums.org/showthread.php?t=1546988)
[http://ubuntuforums.org/showthread.php?t=949293](http://ubuntuforums.org/showthread.php?t=949293)
[http://tex.stackexchange.com/questions/13661/installing-urw-classico-on-mac-os-texlive-2010](http://tex.stackexchange.com/questions/13661/installing-urw-classico-on-mac-os-texlive-2010)

---

### Post by Abdaxz on 2012-02-06
Hi,

Thanks a lot for the answer, but I am sad to say that it did not work as expected...

I have a fresh install of Ubuntu 11.10 (I did a re-installation to be sure) with texlive-full. I have executed the commands and everything _seems_ to work (I did get an error, see below) but when I try my documents I get:


kpathsea: Running mktexpk --mfmode / --bdpi 600 --mag 1+0/600 --dpi 600 uopr8r
mktexpk: don't know how to create bitmap font for uopr8r.
kpathsea: Appending font creation commands to missfont.log.
 )
!pdfTeX error: pdflatex (file uopr8r): Font uopr8r at 600 not found
 ==> Fatal error occurred, no output PDF file produced!

When looking back, I did get an error when trying to install optima:

Extracting 'uop.zip'...                                     [done]
Installing 'uop.map'...                                     [done]

texhash: Updating /usr/local/share/texmf/ls-R... 
texhash: Done.

Updating map files (updmap-sys)...                          [failed]

When trying just sudo updmap-sys no errors occur (as far as I can see).

Any suggestions on what to do?

Best regards,

Tobias

---

### Post by jlmcm on 2012-02-11
I have exactly the same problem, and I'm getting the same errors. I spent a good 3 hours trying to figure this out with no luck so far.

Someone please help!

---

### Post by timothy_tim on 2012-02-26
Apparently,
```
~$ sudo updmap-sys --enable Map=uop.map
```
is not working correct.
To overcome this problem, create a new file "/etc/texmf/updmap.d/10local.cfg" with "Map uop.map" as contents.
Now run
```
~$ sudo update-updmap
~$ sudo updmap-sys
```

That should fix it! :)

(There seems to be more issues with all of this. I got the "Updating map files (updmap-sys)... [failed]" error too. Strangely, when invoking getnonfreefonts-sys with the "--verbose" option, it will return "Updating map files (updmap-sys)... [done]")

---

### Post by Abdaxz on 2012-03-01
Hi,

Thanks a million, it works!!!

I am so happy to be able to use my optima font again!

//Tobias

---

