---
title: "Screen tearing in browser videos (and sometimes in pictures and when scrolling)"
date: 2016-04-01
forum: Desktop Environments
---

### Post by foxj.1994 on 2016-04-01
So I'm running Kubuntu 15.10, and I'm having problems with screen tearing.

Currently I'm using Chrome as I want to be able to use Netflix, but the problem persists in other browsers too, I don't think it's a Chrome specific issue.
The graphics driver I'm using is the proprietary one (fglrx-updates) for an AMD HD7870. The driver seems fine, I noticed a great performance increase when I selected it with window effects etc. And it's running my screen at 144Hz completely fine.

Anyway, as the title suggests, I'm quite frequently getting laggy screen tearing in videos. Not only does this occur in videos, but sometimes even in pictures (until I refresh) and even when scrolling. It's usually diagonal tearing from bottom left to top right, but not always. Sometimes there's a lot of it.
It doesn't always happen, but does probably 60-70% of the time. It seems to get worse when I have multiple tabs open etc.

I was looking up online for solutions and many people said it could be the compositor, but I couldn't find any fixes that work with the current version of KDE/plasma. I added an exception for firefox and chrome to something for the compositor but I think that was only for fullscreen video, when the problem I'm getting is not only just fullscreen videos, but videos in general and even pictures and text when scrolling (and it didn't seem to work anyway).

Any help at all would be greatly appreciated.

Cheers :)

[edit]
OK so I just tried out Netflix, and I get screen tearing when it's not fullscreen but not any once it's been fullscreen for a couple of seconds. So I guess it must be the compositor? How can I exclude a whole browser from the compositor?

---

### Post by mörgæs on 2016-04-02
Have you tried a lighter desktop environment like LXDE / Lubuntu?

---

### Post by mc4man on 2016-04-02
If you have an nvidia gpu then maybe look into using triple buffering, done in xorg.conf
```
Option  "TripleBuffer" "true"
```

---

### Post by foxj.1994 on 2016-04-03
> **mörgæs said:**
> Have you tried a lighter desktop environment like LXDE / Lubuntu?
No I've not, I don't really want to, whole reason I chose KDE was because I enjoy its UI and configurability. I don't think it's an issue of my PC not being powerful enough for it; it's not been upgraded in a few years but it's still decent enough (Quad core 3.5GHz, 4GB RAM, 7870 -- can run triple A games from say 3-4 years ago on max settings easily).

> **mc4man said:**
> If you have an nvidia gpu then maybe look into using triple buffering, done in xorg.conf
```
Option  "TripleBuffer" "true"
```
I don't, I'm afraid :(
My card's an AMD (back when it was ATI) HD7870

---

### Post by mörgæs on 2016-04-03
Testing other desktop environments is often a valuable step in troubleshooting, also if you decide to stay with KDE.

---

### Post by foxj.1994 on 2016-04-04
> **mörgæs said:**
> Testing other desktop environments is often a valuable step in troubleshooting, also if you decide to stay with KDE.

Alright I'll do that when I get the chance :) I'll edit this post with my results

---

### Post by him610 on 2016-04-05
Experienced a similar problem a couple of months ago. Resolved it by by reducing the display resolution. Have experienced no recurrence since.

---

### Post by QIII on 2016-04-05
Reducing the resolution does not solve the problem.  It replaces one undesirable condition with another.

---

### Post by light_yagami2 on 2016-04-05
Does it only happen in chrome?

---

