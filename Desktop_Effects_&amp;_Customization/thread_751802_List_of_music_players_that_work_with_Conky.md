---
title: "List of music players that work with Conky?"
date: 2008-04-10
forum: Desktop Effects &amp; Customization
---

### Post by SomeGuyDude on 2008-04-10
A big thing for me is making sure I can get conky to play nice with my music player of choice, and I'm curious how many actually do work. So far I know of:

1) Amarok
2) Exaile
3) Audacious
4) XMMS
5) MPD
6) XMMS2
7) Rhythmbox

Still looks like we got nothing from Quod Libet, Banshee, or Songbird. Do any of them work, but I'm unaware of it?

---

### Post by morgengenuss on 2008-04-11
there's also [gmusicbrowser]("http://gmusicbrowser.sourceforge.net"), which can be used in combination with conky

---

### Post by worntreads on 2008-05-08
bump

I've looked for quod libet info in conky, no dice.  QL and Songbird are the ones I'd like to see working in conky, if anyone has managed this or knows anything about it the news would be much appreciated.

---

### Post by cl0ckwork on 2008-06-04
i would love to have support for banshee.
previously had conky configured perfectly with amarok
but amarok wasnt really the best IMO
i prefer the full library veiw over the playlist veiw due to my 7000+ song library

ive been tinkering with the code but everything ive tried hasnt worked

---

### Post by SomeGuyDude on 2008-06-04
Banshee/Quod Libet would be awesome, but currently lacking far as I know.

---

### Post by jjgomera on 2008-07-07
> **morgengenuss said:**
> there's also [gmusicbrowser]("http://gmusicbrowser.sourceforge.net"), which can be used in combination with conky
how can i do it?

i find this [patch](http://squentin.free.fr/gmusicbrowser/dokuwiki/doku.php?id=third_party_apps:conky) for conky, but its for old version

---

### Post by Prefix100 on 2008-07-09
Ive got conky working with banshee by getting conky to query banshee.

```
${color #5c1f1f}Banshee${hr 2}${color #b23d3d}
${exec banshee-1 --query-artist}
${exec banshee-1 --query-title}
${exec banshee-1 --query-track-number}
${exec banshee-1 --query-album}
${exec banshee-1 --query-position}
```

---

