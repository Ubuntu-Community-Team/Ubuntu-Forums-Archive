---
title: "Help on customizing"
date: 2005-01-18
forum: General Help
---

### Post by Roberto Rosselli on 2005-01-18
Hi all, I'm a long time GNOME fan and contributor (translations, documentation
and some articles for an Italian magazine) and I would like to create a
LiveCD optimized for TEI ([http://www.tei-c.org/](http://www.tei-c.org/)) XML text editing and
processing; I would also like to include GTK+/GNOME programs that might
be useful to academic people like me (Pybliographic, for instance).
Unfortunately my programming skills are next to nil, so I hope it's not
too hard.

Where do I start to create a customized version of the Ubuntu Live CD? After
looking on the Ubuntu site, I found a LiveCdCustomizationHowTo which is
unfortunately empty, perhaps because you're moving from a "standard"
morphix LiveCD system to a different one?

Any help welcome, many thanks in advance.

Roberto

---

### Post by jobdrb on 2005-01-19
[QUOTE=Roberto Rosselli]Hi all, I'm a long time GNOME fan and contributor (translations, documentation
and some articles for an Italian magazine) and I would like to create a
LiveCD optimized for TEI ([http://www.tei-c.org/](http://www.tei-c.org/)) XML text editing and
processing; I would also like to include GTK+/GNOME programs that might
be useful to academic people like me (Pybliographic, for instance).
Unfortunately my programming skills are next to nil, so I hope it's not
too hard.

Where do I start to create a customized version of the Ubuntu Live CD? After
looking on the Ubuntu site, I found a LiveCdCustomizationHowTo which is
unfortunately empty, perhaps because you're moving from a "standard"
morphix LiveCD system to a different one?

Any help welcome, many thanks in advance.

Roberto[/QUOTE]

Hi Roberto,

The new Ubuntu LiveCD is now Working process by the people of Gnoppix,
For some reasons, the people from Gnoppix are making a new live cd but not based from Morphix.

if your wish you could get the last incarnation on Gnoppix.org 0.8.2.2 (Warty) that is based on the current stable release and use Morphix structure,
read the Morphix docs and make your remastered cd, its not difficult.

May be, you could found a script that help to make this work done, I know some for KDEbased and one for Mandrake that make based in what is configured in your PC.

---

### Post by Roberto Rosselli on 2005-01-20
Hi jobdrb,
thanks for your reply. I've read of the Gnoppix/Ubuntu LiveCD relation on other parts of the forum, but I confess it's not at all clear to me. Furthermore, if the morphix system will be abandoned, I would have to start again for the next version(s) of the LiveCD. So I think I'll patiently wait until the wiki tutorial will get a little more flashy, or someone else will englighten me ;)

Thanks again, and happy computing.

Roberto

---

### Post by xpt on 2005-01-23
Hi, 

I'm new to Ubuntu. This is my 1st post.

I too want to know the Ubuntu LiveCD customizing very much. Hope the wiki on it will out soon. 

Also, I notice there is an "Install From Knoppix Howto", whereas Installation from Ubuntu LiveCD is stated impossible on the Ubuntu main page. I personally think that if Install from Knoppix is possible, then Install from Ubuntu LiveCD is definitely possible, and should not be much different from that of Knoppix. 

Am I right? If so, hope someone can cover that ("Install From Ubuntu LiveCD Howto") in th wiki too. 

Thanks

xpt

---

### Post by amu on 2005-01-24
[QUOTE=Roberto Rosselli]Hi all, I'm a long time GNOME fan and contributor (translations, documentation
and some articles for an Italian magazine) and I would like to create a
LiveCD optimized for TEI ([http://www.tei-c.org/](http://www.tei-c.org/)) XML text editing and
processing; I would also like to include GTK+/GNOME programs that might
be useful to academic people like me (Pybliographic, for instance).
Unfortunately my programming skills are next to nil, so I hope it's not
too hard.

Where do I start to create a customized version of the Ubuntu Live CD? After
looking on the Ubuntu site, I found a LiveCdCustomizationHowTo which is
unfortunately empty, perhaps because you're moving from a "standard"
morphix LiveCD system to a different one?

Any help welcome, many thanks in advance.

Roberto[/QUOTE]

probably the easiest way to mater your own CD

1.) extract the cloop image you'll find it at casper/filesystem.cloop
2.) loop-mount the resulting file
3.) chroot into
4.) make any changes you need...
5.) re-compress the cloop image
6.) place it back the cd to casper/filesystem.cloop
7.) burn you own liveCD 

Cheers,
amu

P.S.
If you want more detail, pls mail me, send you question to the ubuntu-devel maillinglist or check the wiki pages. I read this forum not regularly

---

### Post by Roberto Rosselli on 2005-01-26
[QUOTE=amu]probably the easiest way to mater your own CD

1.) extract the cloop image you'll find it at casper/filesystem.cloop
2.) loop-mount the resulting file
3.) chroot into
4.) make any changes you need...
5.) re-compress the cloop image
6.) place it back the cd to casper/filesystem.cloop
7.) burn you own liveCD 

Cheers,
amu

P.S.
If you want more detail, pls mail me, send you question to the ubuntu-devel maillinglist or check the wiki pages. I read this forum not regularly[/QUOTE]
 Hi amu,
thanks for the info. I also see the wiki is now online, so that's going to help too.

Problem is, I'm not a Debian user and the wiki is really thought for a debian user :) Will look into it, though.

Ciao

---

