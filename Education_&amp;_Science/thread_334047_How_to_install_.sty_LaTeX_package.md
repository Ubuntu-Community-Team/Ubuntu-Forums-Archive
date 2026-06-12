---
title: "How to install .sty LaTeX package"
date: 2007-01-08
forum: Education &amp; Science
---

### Post by LJM on 2007-01-08
I'm trying to install the calrsfs.sty calligraphy package for LaTeX. 

The problem is that, although I have superuser priviledges (I'm the main and only Ubuntu user), the machine doesn't let me extract the files in the right folder, namely, /usr/local/share/texfm-texlive/tex/latex. If I try using the Terminal, it won't even show me all the existing folders past /usr/local/share (only fonts, games, and a few others); if I try using the Gnome interface and get to the latex folder, it won't let me paste any files in there due to "lack of permission." 

Does this make any sense? Thank you in advance. --LJM

---

### Post by kleeman on 2007-01-09
Are you root when this happens?
At the terminal type
sudo su
and put in your password.
Try again after this...

---

### Post by Toufik on 2007-01-10
```
sudo latex calrsfs.sty
```
should work

Even if you are the only user of your computer, you have to type "sudo" and your password each time you want to modify your system (like installing something)

---

### Post by LJM on 2007-01-10
Thank you for your replies. Before I had had a chance to read them, I solved the problem using brute force.

I installed texlive-full, which is incredibly bulky, took quite some time, and probably gave me packages I'll never ever need, but now all packages I need seem to be there, including calrsfs.sty.

But thank you for your help. I wrote it down for trying out with possible similar problems in the future.

LJM

---

### Post by neoflight on 2007-01-10
> **LJM said:**
> Thank you for your replies. Before I had had a chance to read them, I solved the problem using brute force.

I installed texlive-full, which is incredibly bulky, took quite some time, and probably gave me packages I'll never ever need, but now all packages I need seem to be there, including calrsfs.sty.

But thank you for your help. I wrote it down for trying out with possible similar problems in the future.

LJM

yes texlive-full is bulky. :mrgreen: make sure that you run 'texhash' and  'texconfig' after you copy a sty file in the appropriate places, to use it.

---

### Post by timmie on 2007-01-19
I made a small tutorial for the handy miktex package manager for linux on
[http://wiki.ubuntuusers.de/MiKTeX_Package_Manager](http://wiki.ubuntuusers.de/MiKTeX_Package_Manager)

Even if you donno German the commands will be the same ;-)

---

### Post by parktownprawn on 2007-01-24
For those of you with "kein deutsch" i've posted a short howto for installing miktex package manager on the ubuntu wiki

[https://help.ubuntu.com/community/MiktexPackageManager](https://help.ubuntu.com/community/MiktexPackageManager)

---

### Post by cogumbreiro on 2007-02-04
I have blogged about this:

[http://irrepupavel.blogspot.com/2007/02/installing-latex-style-files-sty-on.html](http://irrepupavel.blogspot.com/2007/02/installing-latex-style-files-sty-on.html)

Afterwards I found this forum. Someone might find it useful.

---

### Post by ahmatti on 2007-03-16
Miktex package manager is great! Much easier and faster than separately downloading and extracting packages of ctan servers :)

---

### Post by timmie on 2007-03-16
> **parktownprawn said:**
> For those of you with "kein deutsch" i've posted a short howto for installing miktex package manager on the ubuntu wiki

[https://help.ubuntu.com/community/MiktexPackageManager](https://help.ubuntu.com/community/MiktexPackageManager)

Please add a option install via [CheckInstall]("https://help.ubuntu.com/community/CheckInstall") which would keep the system clean.

Greetings, Tim

---

### Post by ahmatti on 2007-03-16
Thanks for the checkinstall tip. I have been wondering if there is a way to do that!

And thanks for Miktex howtos! It is just what I needed, work perfectly with texlive :)

---

### Post by underwater on 2007-12-10
If you do all of the instructions and then sudo checkinstall instead of make install, it will fail at installing.

---

### Post by timmie on 2007-12-10
Please tell us exactly where it fails for you. Then we may be able to help.

For me it worked.

---

### Post by PhDP on 2008-06-01
> **cogumbreiro said:**
> I have blogged about this:

[http://irrepupavel.blogspot.com/2007/02/installing-latex-style-files-sty-on.html](http://irrepupavel.blogspot.com/2007/02/installing-latex-style-files-sty-on.html)

Afterwards I found this forum. Someone might find it useful.

The problem is that I don't have the authorization to put files in usr/

---

### Post by aakaasha on 2008-11-05
I am trying for days now to install the mktex package manager.

I downloaded all files and extracted to /usr/local/miktex-2.7.3135, I installed all build-utilities, but if I type the command "./configure" the following error shows up:

```
bash: ./configure: No such file or directory
```

What is wrong with the described method? :confused:

Regards,
Florian

---

### Post by Stefan_K on 2008-11-05
Hi Florian,

have a look here for a description how to install the miktex package manager on Ubuntu: [http://texblog.net/latex-archive/linux/mpm-miktex-package-manager/]("http://texblog.net/latex-archive/linux/mpm-miktex-package-manager/")

Stefan

---

### Post by aakaasha on 2008-11-08
```
/usr/local/miktex-2.7.3135$ cmake -G "Unix Makefiles" -DMIKTEX_INSTALLROOT="/usr/share/texmf-texlive" -DMIXTEX_ROOTS="/usr/share/texmf-texlive"
CMake Error: The program lynx could not be found.
-- Configuring done
/usr/local/miktex-2.7.3135$ make
make: *** Keine Targets angegeben und keine »make«-Steuerdatei gefunden.  Schluss.
/usr/local/miktex-2.7.3135$ 
```

:confused:

Does it work the same way with Ubuntu 7.10?

---

### Post by Stefan_K on 2008-11-08
Did you install lynx? It seems to be needed.

Stefan

---

### Post by 081103jk on 2008-11-10
[**&#24405;&#38899;&#30418;**](http://www.googlejk.cn/luyinghe.htm)&#24405;&#38899;&#23453;&#21450;&#35745;&#31639;&#26426;&#30340;USB&#31471;&#21475;&#65292;&#26368;&#21518;[**&#24405;&#38899;&#31649;&#29702;**](http://www.googlejk.cn/luyinguanlixitong.htm)&#23433;&#35013;&#38468;&#36865;&#20809;&#30424;&#20869;&#30340;&#39537;&#21160;&#31243;&#24207;&#21644;&#24212;&#29992;&#36719;&#20214;&#20415;&#21487;&#24320;&#22987;&#25805;&#20316;&#20351;&#29992;&#12290;&#30005;&#35805;&#20027;&#26426;&#21518;&#20219;&#20309;&#19968;&#20010;&#20998;&#26426;&#25320;&#20986;&#25110;&#25509;&#21548;&#26469;&#30005;&#22343;&#21487;&#36827;&#34892;&#24405;&#38899;&#12290;&#12288;[**&#24405;&#38899;&#30005;&#35805;**](http://www.googlejk.cn/luyindianhua.htm)&#23545;&#20110;&#22810;&#32447;&#36335;&#25110;&#36830;&#25509;&#30005;&#35805;&#31995;&#32479;&#30340;&#29992;&#25143;&#65292;[**&#22768;&#35759;&#30005;&#35805;&#24405;&#38899;**](http://www.googlejk.cn/shexun.htm)&#22914;&#22522;&#20110;&#20010;&#21035;&#21407;&#22240;&#25110;&#29702;&#30001;&#19981;&#38656;&#35201;&#23545;&#25152;&#26377;&#30005;&#35805;&#20998;&#26426;&#36827;&#34892;&#24405;&#38899;&#25110;&#22522;&#20110;&#31169;&#38544;&#21407;&#22240;&#24819;&#20010;&#21035;&#31649;&#29702;&#24405;&#38899;&#35760;&#24405;&#65292;[**&#30005;&#35805;&#24405;&#38899;&#31995;&#32479;**](http://www.googlejk.cn/dhlyxt.htm)&#30005;&#35805;&#24405;&#38899;&#20202;&#21487;&#21442;&#32771;&#20197;&#19978;&#30340;&#25509;&#39539;&#26041;&#27861;&#65292;&#19981;&#31649;&#26377;&#22810;&#23569;&#26465;&#30005;&#35805;&#20998;&#32447;

---

### Post by aakaasha on 2008-11-12
I installed Lynx and then it worked! Thank you, Stefan!

---

