---
title: "New version of lyx"
date: 2007-07-25
forum: Education &amp; Science
---

### Post by kleeman on 2007-07-25
The developers have just released version 1.5 which is a major step forward. The new version uses qt4 instead of qt3 and has reorganized the math panel onto menu bars. These can be dragged to either the bottom left or right of the text window. There are many other improvements....

One thing to be careful about is that 1.5 produces files that cannot be read by earlier version e.g. the 1.4 versions. I have produced some checkinstall debs (i.e. without dependencies) which you can grab here (64bit and 32bit respectively)

[http://www.math.nyu.edu/faculty/kleeman/amd64/lyxlatest_1.5.0-1_amd64.deb](http://www.math.nyu.edu/faculty/kleeman/amd64/lyxlatest_1.5.0-1_amd64.deb)
[http://www.math.nyu.edu/faculty/kleeman/amd64/lyxlatest_1.5.0-1_i386.deb](http://www.math.nyu.edu/faculty/kleeman/amd64/lyxlatest_1.5.0-1_i386.deb)

Install with

sudo dpkg -i lyxlatest_1.5.0-1_i386.deb  (or the 64bit deb)

The binary is installed in /usr/local/bin 

so can be executed with

/usr/local/bin /lyx

The old version is still in /usr/bin

Enjoy...

---

### Post by Declan on 2007-07-28
Thanks for the deb.
I've noticed that it runs a good bit slower than the lyx 1.4.4 that I have on the same computer. I suppose there's a way around that, is there? Something mysterious adjustment of some mysterious xorg setting?
By slowness, I mean that the thing lags behind my typing, which is a bit disconcerting.
Any ideas?

Declan (grateful, once again, for the deb).

---

### Post by kermy on 2007-07-28
> **Declan said:**
> Thanks for the deb.
I've noticed that it runs a good bit slower than the lyx 1.4.4 that I have on the same computer. I suppose there's a way around that, is there? Something mysterious adjustment of some mysterious xorg setting?
By slowness, I mean that the thing lags behind my typing, which is a bit disconcerting.
Any ideas?

Declan (grateful, once again, for the deb).
strange... from the changelog:
> As usual, one big task has been the ongoing code cleanup of the LyX
core. Performing this cleanup makes the code more understandable and
easier to maintain. It also leads inevitably to a more robust
application. Nonetheless, it's an unfortunate fact of life that ugly
code is sometimes faster than pretty code. We're well aware that LyX
1.4 is slower than LyX 1.3. One important goal of this 1.5 development
series has been to bring this speed back.

---

### Post by kleeman on 2007-07-28
> **Declan said:**
> Thanks for the deb.
I've noticed that it runs a good bit slower than the lyx 1.4.4 that I have on the same computer. I suppose there's a way around that, is there? Something mysterious adjustment of some mysterious xorg setting?
By slowness, I mean that the thing lags behind my typing, which is a bit disconcerting.
Any ideas?

Declan (grateful, once again, for the deb).
Hmm I haven't noticed that at all. My experience has been the opposite. The 1.4 series was definitely slower than the 1.3 series for me but 1.5 was nearly back to 1.3 speeds. I get no lag at all. What are your specs (memory, cpu and graphics card)?

This is the first version to use qt4 so you could try playing with the config for this. I used this to adjust menu fonts but there are a bunch of other options as well...

You need to install qt4-qtconfig  and launch the program with 

qtconfig-qt4

---

### Post by Declan on 2007-07-31
Thanks for this. I've installed the qt config thingy. Is there anything that might directly impact on lyx functioning? Or is it a matter of randomly changing things?
Now that I've been using lyx 1.5 for a few days, I see that this issue (the speed) varies a bit. 
I have 512 RAM and a celeron 2.8 processor.
Maybe I just have to learn to type slower?

Declan

---

### Post by kleeman on 2007-07-31
You could try playing with the gui options under the interface tab....

I noticed on the developers mailing list that some people have reported problems similar to yours when graphics hardware acceleration is not working. To check whether it is type:

glxinfo | grep render

If the first line produced says

 direct rendering: No

then it is in fact turned off. Mine says Yes. The mailing list suggests replacing the line

    DefaultDepth    24
in the [screen] section of /etc/X11/xorg.conf

with

    DefaultDepth    16

After doing that you need to restart X with

ctl-alt-backspace

---

### Post by timmie on 2007-08-09
Hello,
version 1.5.1 with some bug fixes is out.

It fixes open-document-export for Ubuntu.

@kleeman
Are you going to submit your packages to MOTU?

---

### Post by euler_fan on 2007-08-09
Is LyX still using tetex as the LaTeX distro or will it work with TeXLive?

I'd probably reinstall it if it would. TeXLive just has so many great tools built in I can't imagine going back to tetex just to get LyX.

---

### Post by timmie on 2007-08-09
It only needs latex no matter wether it is provided by tetex, miktex, texlive, etc.

See this post here:
[http://article.gmane.org/gmane.editors.lyx.general/35537/match=texlive](http://article.gmane.org/gmane.editors.lyx.general/35537/match=texlive)

BTW, I am still on tetex. How did you shift to texlive?
Using synaptics?
What is the main advantage?

---

### Post by euler_fan on 2007-08-09
> **timmie said:**
> It only needs latex no matter wether it is provided by tetex, miktex, texlive, etc.

See this post here:
[http://article.gmane.org/gmane.editors.lyx.general/35537/match=texlive](http://article.gmane.org/gmane.editors.lyx.general/35537/match=texlive)

BTW, I am still on tetex. How did you shift to texlive?
Using synaptics?
What is the main advantage?

I will look into that. Thanks.

I switched using synaptic. My question was sparked because using synaptic in order to switch I had to get rid of tetex and LyX which made it appear that it depended on it. Must just be how it is packaged for Edgy.

I have heard that tetex has more or less stopped being maintained whereas TeXLive is still under active development. Also TeXLive has aims to be a "complete" LaTeX distro and its packages include most of the commonly used packages. This is nice for me since I don't care to install packages from scratch if I don't have to.

I guess I may just have to do a checkinstall from source to get LyX to work with TeXLive in Edgy. Not a big deal, but as time goes on and I get more and more comfortable with strait LaTeX I'm not sure if I'll bother.

---

### Post by hogweed on 2007-08-10
> **euler_fan said:**
> I will look into that. Thanks.

I switched using synaptic. My question was sparked because using synaptic in order to switch I had to get rid of tetex and LyX which made it appear that it depended on it. Must just be how it is packaged for Edgy.

I have heard that tetex has more or less stopped being maintained whereas TeXLive is still under active development. Also TeXLive has aims to be a "complete" LaTeX distro and its packages include most of the commonly used packages. This is nice for me since I don't care to install packages from scratch if I don't have to.

I guess I may just have to do a checkinstall from source to get LyX to work with TeXLive in Edgy. Not a big deal, but as time goes on and I get more and more comfortable with strait LaTeX I'm not sure if I'll bother.

Yes, TeTeX is now no longer supported, and TeX-Live is essentially its replacement. There are a still a few bumps in the transition, but that should all be resolved in the next few months.

As far as LyX is concerned, it works fine with either tetex or texlive, or any other TeX distribution, in fact. When you uninstalled TeTeX, apt saw that there was not going to be any TeX discbution installed on your system, so it wanted to dump LyX as well.

You could simply do this: uninstall all of the tetex-specific packages; install all of the Tex-live packages that you want; re-install LyX. As long as you haven't touched your LyX directory, all your settings should be fine. When you have finished the installation of Tex-live, just fire up LyX, go to Tools --> Reconfigure. Restart LyX and you will be using TeX-Live.

This should be the case in Edgy as well as Feisty; Gutsy uses TeX-Live 2007.

Hope this helps...

--
hogweed

---

### Post by euler_fan on 2007-08-10
> **hogweed said:**
> Yes, TeTeX is now no longer supported, and TeX-Live is essentially its replacement. There are a still a few bumps in the transition, but that should all be resolved in the next few months.

As far as LyX is concerned, it works fine with either tetex or texlive, or any other TeX distribution, in fact. When you uninstalled TeTeX, apt saw that there was not going to be any TeX discbution installed on your system, so it wanted to dump LyX as well.

You could simply do this: uninstall all of the tetex-specific packages; install all of the Tex-live packages that you want; re-install LyX. As long as you haven't touched your LyX directory, all your settings should be fine. When you have finished the installation of Tex-live, just fire up LyX, go to Tools --> Reconfigure. Restart LyX and you will be using TeX-Live.

This should be the case in Edgy as well as Feisty; Gutsy uses TeX-Live 2007.

Hope this helps...

--
hogweed

I'll give that a try. Thanks.

---

### Post by xadder on 2007-08-13
I just installed the .deb version of the new .lyx to give it a try. I am sure this is a real noob question for lyx users, but how do I get export to LaTeX working? If I look at the export menu I have loads of options (e.g. various CJK lyx, pdf, ps, plain  text), but no LaTeX.

I'm using texlive, and lyx1.5.1.

---

### Post by xadder on 2007-08-13
Scratch my previous question, at least as a general one. I had tried the AGU article template, and that didn't provide latex export. Also seemed to rqiure jadetex which I don't have.

With other templates, latex export comes up fine. Problem solved for now, except it would be nice to use AGU articles too.

---

### Post by timmie on 2007-08-13
[QUOTE=xadder;3181781. I had tried the AGU article template, and that didn't provide latex export. Also seemed to rqiure jadetex which I don't have.

With other templates, latex export comes up fine. Problem solved for now, except it would be nice to use AGU articles too.[/QUOTE]

I tried the AGU and it didn't provide latex export on my version either.

Please report this problem directly to the user list through:

[http://news.gmane.org/gmane.editors.lyx.general](http://news.gmane.org/gmane.editors.lyx.general)

[http://www.lyx.org/internet/mailing.php](http://www.lyx.org/internet/mailing.php)

The developers and users are alway present on that list and very friendly and responsive.

Greetings, Timme

---

### Post by hogweed on 2007-08-13
To get back to the original topic of the thread, you can find a .deb of the new version of Lyx for Feisty in [the download section of the LyX Wiki]("http://wiki.lyx.org/LyX/Download").

A few notes on this binary: it will install the binary to /usr/bin/lyx1.5.1 and when invoked will create a new user directory at ~/.lyx1.5.1

This is good for installing alongside another version of LyX, but may cause confusion if you simply want to update your current installation, so heads up.

--
hogweed

---

### Post by meho_r on 2007-08-21
Anyone .deb of lyx 1.5.1 for AMD64?

EDIT: Sorry, found it.

---

