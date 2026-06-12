---
title: "A ton of Latex/Kile questions"
date: 2010-10-16
forum: Education &amp; Science
---

### Post by Super Nade on 2010-10-16
Folks,

I'm a Windows user who has recently migrated to Ubuntu. So, please bear with me if these questions appear silly.

Texlive 2009, Kile v2 beta 4 (Kubuntu) 

**Question #1: Springer Templates**

I would like to start writing up my lecture notes in a book format. I would like to do so in the Springer format. ([http://www.springer.com/authors/book+authors?SGWID=0-154102-12-417900-0](http://www.springer.com/authors/book+authors?SGWID=0-154102-12-417900-0))

So, I downloaded the svmono.zip file which contains several .tex files and the svmono stylesheet. Where do I put these so that I can use them with kile? I would also like to create a template called "springer" which would show up in kile's default template list.
[B]
Question #2: Texlive 2010[/B]

I installed TexLive2010 from the source. How can I ensure that kile uses this instead of the default 2009 version? I did a bit of reading and edited /etc/environment which looks like this:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/tex$
#PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/sbin:/bin:/usr/games:/usr/local/texlive/2010$
  MANPATH=/usr/local/texlive/2010/texmf/doc/man:$MANPATH; export MANPATH
  INFOPATH=/usr/local/texlive/2010/texmf/doc/info:$INFOPATH; export INFOPATH 
```

Yet, when I check the version of tex being used I see
```
septimus@laptop:~$ tex -v
TeX 3.1415926 (TeX Live 2009/Debian)
kpathsea version 5.0.0
Copyright 2009 D.E. Knuth.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the TeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the TeX source.
Primary author of TeX: D.E. Knuth.

```

What am I missing? 

**Question #3: tlmgr**
Where can I find tlmgr for both 2009 and 2010 versions? I am spoiled by miktex. :)

Thanks!

S-N

---

### Post by PC_load_letter on 2010-10-18
For Question #1:
Unzip the package and put the tex files anywhere (they are templates I guess). As for the style files (.sty), put them in **/usr/share/texmf-texlive/tex/latex/**
Then from the terminal, type:
```
sudo texhash
```
And everything should work then. 


As for Question #3: what is timgr? Is it a Latex package, or a Windows program?

---

### Post by Super Nade on 2010-10-18
Thank you! #sudo texhash worked! As for "tlmgr" (texlive manager), it is an update tool to texlive. Sort of like the update tool in MikTex. I am using the Linux version (running ku/u buntu 10.10).

---

### Post by PC_load_letter on 2010-10-18
> **Super Nade said:**
> Thank you! #sudo texhash worked! As for "tlmgr" (texlive manager), it is an update tool to texlive. Sort of like the update tool in MikTex. I am using the Linux version (running ku/u buntu 10.10).

I googled and it seems that timegr has been included in TeXlive since the 2008 version. So maybe there is nothing that needs to be done. It'd be great someone else could confirm this.

---

### Post by Super Nade on 2010-10-19
I found it, but I don't know why it is not executing?

```
septimus@laptop:/usr/local/texlive/2010/bin/i386-linux$ locate tlmgr
/usr/local/texlive/2010/bin/i386-linux/tlmgr
/usr/local/texlive/2010/texmf/doc/man/man1/tlmgr.1
/usr/local/texlive/2010/texmf/doc/man/man1/tlmgr.man1.pdf
/usr/local/texlive/2010/texmf/doc/texlive/texlive-common/tlmgr-general-options.png
/usr/local/texlive/2010/texmf/doc/texlive/texlive-common/tlmgr-gui.png
/usr/local/texlive/2010/texmf/doc/texlive/texlive-common/tlmgr-paper-options.png
/usr/local/texlive/2010/texmf/doc/texlive/texlive-sr/images/tl2010-tlmgr-main-screen-freebsd-sr.png
/usr/local/texlive/2010/texmf/doc/texlive/texlive-sr/images/tl2010-tlmgr-options-freebsd-sr.png
/usr/local/texlive/2010/texmf/doc/texlive/texlive-sr/images/tl2010-tlmgr-paper-options-freebsd-sr.png
/usr/local/texlive/2010/texmf/scripts/texlive/tlmgr.pl
/usr/local/texlive/2010/texmf/scripts/texlive/tlmgrgui.ico
/usr/local/texlive/2010/texmf/scripts/texlive/tlmgrgui.pl
/usr/local/texlive/2010/texmf-var/web2c/tlmgr.log
septimus@laptop:/usr/local/texlive/2010/bin/i386-linux$ sudo tlmgr
sudo: tlmgr: command not found
septimus@laptop:/usr/local/texlive/2010/bin/i386-linux$ tlmgr
No command 'tlmgr' found, did you mean:
 Command 'vlmgr' from package 'qdbm-util' (universe)
 Command 'rlmgr' from package 'qdbm-util' (universe)
tlmgr: command not found
septimus@laptop:/usr/local/texlive/2010/bin/i386-linux$ 

```

---

### Post by spinoza666 on 2010-10-19
This tlmgr-thing sounds very interesting, so I googled and found this:

[http://old.nabble.com/sudo-tlmgr-of-TL-2009-td26997519.html]("http://old.nabble.com/sudo-tlmgr-of-TL-2009-td26997519.html")

Near the end, this is offered as a makeshift solution:

> Assuming you installed in the default location, you can do

sudo chown -R chrisp /usr/local/texlive

and then, without changing anything to root's environment, simply run tlmgr as
chris (without sudo). This way, the user crhisp is the administrator of the TL
installation.

That's what I recommend (and personnaly use) for single-user machines.

Manuel. 

So, basically what they are saying is that tlmgr is not executable since it's not in the correct path, but that if you make yourself (here username chrisp - exchange for your own username) the owner of the texlive directory, then you can execute tlmgr in the usual manner. I'm no expert, sounds a bit unsafe to me, but may work.

With regards to question 2, have you made sure that you do not have two versions of tex installed? I'm guessing you installed tex through the package manager first, and then installed the 2010 version from source, without fully removing the 2009 version? A crude solution would perhaps be to purge the 2009 version, and then reinstall the 2010 version if needed:

sudo apt-get purge texlive

Then reinstall from source if you need to.

Cheers:)

---

### Post by Super Nade on 2010-10-20
Thank you spinoza. Do I have to reinstall kile and other tex front ends as well? If not, how to ensure that kile does not misbehave?

---

### Post by spinoza666 on 2010-10-21
I'm unsure. Kile depends on texlive, so purging texlive would normally remove kile as well I think. But you have the 2010 version installed from source as well, so perhaps not. As I said, I'm no expert.

Personally, I would purge kile, and all other front ends, together with texlive. Then I would reinstall texlive 2010 from source, just to make sure it is properly installed, and subsequently reinstall kile, and whatever front ends you want. Again, I'm no expert, and this is probably a crude solution to some, but I think that this may work.

Kile depends on texlive, so if you reinstall kile first, texlive 2009 will also be installed automatically. But if you install texlive 2010 from source, and then kile, I think that kile should identify this, and not install texlive 2009.

Why do you want the 2010 version in the first place? Why not use the 2009 version, I mean are they that different?

---

### Post by Azrael3000 on 2010-10-22
sorry if I missunderstand your question #3 but is it correct that you are only concerned about updating?

Well in case you have installed TexLive from the repositories (see also post above) it will be updated just like every other program through the update manager. Of course if you do require the 2010 version this holds no longer true.

---

### Post by Super Nade on 2010-10-22
Re Texlive 2010 vs 2009:

You are probably right. I'm just a noob who likes shiny new things. :) I am taking your advice and sticking with the 2009 version. After all, it is not hindering my writing. Then there is the "if it aint broke..." paradigm (although I personally prefer..."the enemy of good is better").

Thanks spinoza and Azrael. You guys are champs!

PS# I am going through a kernel tweaking spree at the moment. Compiled 4 version of the kernel that are progressively smaller. Perhaps it won't actually help anything, but I just want to see at what point things break. :)

---

### Post by Azrael3000 on 2010-10-23
well you see the good thing about ubuntu is that it just works. That's the reason why a lot of people use it. Of course this has to come with the downside of not being bleeding edge. But for me personally I rather have a system which I do not have to take care of and concentrate on my real work.
Of course if you want to fiddle around with your OS and go all bleeding edge then you might want to consider other distributions like Gentoo.
Anyhow have fun in the Linux world. Most people don't know it, but it's really nice here :)

---

