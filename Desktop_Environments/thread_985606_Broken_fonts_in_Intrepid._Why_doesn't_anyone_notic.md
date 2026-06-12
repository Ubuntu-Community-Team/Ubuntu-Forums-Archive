---
title: "Broken fonts in Intrepid. Why doesn't anyone notice?"
date: 2008-11-17
forum: Desktop Environments
---

### Post by softtower on 2008-11-17
I have installed Intrepid (8.10) at least 3 times: Ubuntu and Kubuntu and on both variants the font rendering isn't working the way it was on 8.04.

More specifically, "native" hinting with bytecode interpreter does not seem to be working anymore: I can't get those super-smooth (even without smoothing) fonts I used to have.

My favorite setting has always been "Native hinting", "Slight", "Subpixel smoothing". KDE looks like complete crap - it seems to be stuck in auto-hinting mode with ether full or no hinting (ignores slight/medium values). 

And nobody seems to be noticing... We used to have so-called "Turner patches" - deb packages with fixed version of FreeType (with BCI enabled). Has anyone heard of recompiled FreeType for Intrepid?

OpenOffice seems to suffer from this the most: version 3 looked *great* on 8.04 and it looks much, much worse on 8.10.

---

### Post by naubusan on 2008-11-18
Wondering same too.
I have installed Ibex on four different machines, and on every machine full subpixel smoothing results this.

[IMG]http://i364.photobucket.com/albums/oo87/naubusan/ubu.jpg[/IMG]

---

### Post by stinger30au on 2008-11-18
out of interest are you using nvidia cards in 8.10???

have you installed the newest drivers from nvidia at all as the ones shipped with 8.10 dont work...

thanks again nvidia for not having open source drivers, *NOT*

---

### Post by naubusan on 2008-11-18
Both ati and nvidia

---

### Post by softtower on 2008-11-18
Yes, your screen shot looks the same as mine: it looks pretty good, actually, because it is showing only Ubuntu's own fonts and they look good with auto-hinting (the setting which, I suspect, Ubuntu 8.10 is stuck with).

But to display Microsoft True Type fonts properly you need *native* hinting with byte code interpretation, which is broken. I don't use my Ubuntu laptop anymore because of this: surfing the web is a bit painful on my eyes so I'm back to OSX. (which I hate, but at least I can see things clearly there for now).

BTW: I don't mind recompiling FreeType with BCI, I just need to find time to find some docs on configuring FreeType build process and DEB packaging.

---

### Post by Mazin on 2008-11-18
Out of curiosity, does [https://help.ubuntu.com/community/MacBook#Fonts%20like%20Mac%20OS%20X%20(optional](https://help.ubuntu.com/community/MacBook#Fonts%20like%20Mac%20OS%20X%20(optional)) do anything?

---

### Post by softtower on 2008-11-18
I run Ubuntu on Thinkpads and keep Macbooks under OSX for Adobe software.

---

### Post by softtower on 2008-11-18
I haven't tried this on Intrepid, but on previous releases this style (without any hinting but with super-aggressive smoothing) doesn't work well at all. And I definitely wouldn't call it "similar to OSX" :) To get similar rendering on Ubuntu 8.04 you had to enable "native" hinter + "slight" hinting mode + gray (instead of sub-pixel) smoothing. This combination isn't achievable anymore because BCI seems to be broken and, therefore, slight native hinting isn't available.

---

### Post by Brebs on 2008-11-18
For KDE, it is/was a [bug in QT4](http://trolltech.com/developer/task-tracker/index_html?method=entry&id=195256) apparently.

For Gnome's simplistic font options versus the flexibility of freetype, see my [cairo-respect-fontconfig.patch](http://www.fedoraforum.org/forum/showthread.php?t=186789&page=4)

---

### Post by softtower on 2008-11-18
Brebs, this is something, thank you! 

I also sent you a personal message via this forum, can you please check? ... knowing how hard it is to notice new messages (I've missed a few in the past) I'm posting this here.

---

### Post by Brebs on 2008-11-18
Just ask the questions publicly, rather than "ask to ask".

---

### Post by softtower on 2008-11-18
Allright, where do I begin...

I've been googling for a most complete "fonts on Linux" programmers manual but could never find anything comprehensive, but from the pieces that I was able to collect, here is my understanding of how it works, and I only wanted to make sure I'm correct:

On Gnome fonts are rendered by FreeType library, but Cairo is also somehow involved [cairo uses freetype?]. But on KDE Qt alone does everything.

Also it's possible for some applications, like Open Office, to use their own private builds of badly configured FreeType, running with screwed fonts for years without any hope of fixing it by editing common config files. 

Fonts are configured in 3 different places: in /etc/fonts (via fontconfig-config package or manually), in your own ~/.fonts.conf file, which overrides those settings, and via "X database" (xrdb). Gnome uses the latter, while Qt prefers the former although there are some corner cases when they're get mixed up???

When it comes to font configuration, there are 3 hinting possibilities: *none* (which basically means you're screwed since no modern TT font can be rendered this way), *native* hinting which works great but uses patented techniques such as bytecode interpretation (BCI) and *auto*, the famous "autohinter" which tries really hard to avoid patent issues by not employing BCI, but rarely produces results comparable to native/BCI hinter. "Hinting", by the way, is a process of helping the renderer to map smooth curves into a grid of pixels, hence "hinting".

Hinting can be applied at different levels: slight/medium/full but I am not sure if that's applicable to both hinting algorithms: native/auto... 

Then there is another somewhat separate issue of "smoothing". There are two options - subpixel/LCD and grayscale, with the former being split into "new" and "legacy" sub-types that I don't know much about. But somehow smoothing can also be very misconfigured, like in the case of OpenOffice 3, which enables smoothing when you allow it in Gnome, but makes it look much worse than the rest of your desktop.

Now... the questions:

How's my understanding of "fonts on linux" world? Did I miss anything and how many mistakes did I make? 

And where do I begin if I want to "fix" font issues in KDE/Gnome? What is the web site/forum/bug database or an IRC channel where programmers who work on font rendering hang out? Perhaps I will figure out how to recompile OpenOffice properly, to be 100% Gnome/KDE compliant when it comes to font configuration.

Something is clearly going on with Intrepid since Gnome font settings no longer produce the results I was previously getting using the same Appearance/Font dialog on Hardy. Also, I want to be able to fix KDE without waiting for brave souls like yours to release patches, I'm pretty sure I can do that.

---

### Post by Brebs on 2008-11-19
Sounds like a reasonable summary. Linux is a mess :(

> no longer produce the results I was previously getting
Saying that is useless, because it's too general. I'm using Ubuntu Intrepid's font rendering in [Fedora 9](http://www.fedoraforum.org/forum/showthread.php?t=186789) with Gnome and cairo-respect-fontconfig.patch, and it *works*.

Try checking the patch on [Ubuntu bug](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/293643), which the reporter of the bug is obviously too lazy to do himself.

Don't forget that KDE and Gnome use different libraries. Also, individual apps (e.g. firefox and openoffice) can be compiled with their own internal versions of cairo, separate to the "system" cairo, which will act differently. This is done solely to confuse the hell out of newbies, as far as I can tell :(  If you're getting weird rendering in apps, then check how the apps were compiled. E.g. in firefox, you want to see "--enable-system-cairo".

---

### Post by AlexeiM on 2008-11-20
The bug in Qt4 is not going to be fixed until 4.5 next year
which will be most probably not backported to Intrepid.

See
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/217729](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/217729)
and blog post on Trolltech.com.

However the patches proposed by B. Lin seem to improve
the situation slightly: [http://imagebin.ca/view/AFUdqlH.html](http://imagebin.ca/view/AFUdqlH.html)

---

### Post by AlexeiM on 2008-11-20
Ok there was no single qt app on that screenshot,
here is one: [http://imagebin.ca/view/bk0jjR5t.html](http://imagebin.ca/view/bk0jjR5t.html)

---

### Post by JuanChanKane on 2009-02-08
Hi there,

About why nobody notices this: 

I do think this font mess is not something casual. Crisp fonts consistently across different apps are mandatory for any OS, but strangely its been an issue for Linux like for [[COLOR="Blue"]ever[/COLOR]]("http://jeremy.zawodny.com/blog/archives/000773.html"). Surely some will chime in saying that their fonts rock, to those I's ask to try freetype with BCI enabled and *then* speak. 

But think about it...if you were the major player in the OS market, with lots of resources at hand to be 1st...wouldn't you do whatever is necessary to remain 1st? 

IMHO this is not casual...this happens because somebody with resources wants it to happen.

---

### Post by Brebs on 2009-02-08
> **JuanChanKane said:**
> IMHO this is not casual...this happens because somebody with resources wants it to happen.
Er yeah, very mysterious :rolleyes: 

Presumably you're talking about the potential for infringing on Microsoft's ClearType patents. Well, Ubuntu know what they're doing, and I expect they've had some extremely well-paid lawyer-scum look at the risk of being sued. It's obviously an acceptable risk, due to the font-rendering code that's used in Ubuntu.

Lots of other distros include font-rendering-improvement patches also, these days.

So, this *is* casual. The blog you linked to is from 2003 - waaay out of date.

---

