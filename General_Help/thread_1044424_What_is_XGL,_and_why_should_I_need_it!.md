---
title: "What is XGL, and why should I need it!?"
date: 2009-01-19
forum: General Help
---

### Post by emshains on 2009-01-19
I know that the basic gui system is X.org. It also takes care of input/output and audio on the system. But does this use openGL for desktop rendering ? 

I am just asking about XGL, because when I saw one video about compiz, it said it was all about XGL, and how it is the future of linux eye-candy. I am running ubuntu 8.04 on an old system, basically  1.6ghz and a 7300GT, and it deals with compiz and emerald quite well, although firefox starts to lag with about 20 tabs open, with metacity it lags with 25-30, sometimes it depends on what page I am. What I want to know is, shoild I use xgl over the usual X, and if I do,  will installing &/or running XGL will make my system use more of my GPU. 


Any help will be appreciated.

---

### Post by emshains on 2009-01-20
Is there anybody who could explain the difference ?

---

### Post by ajcham on 2009-01-20
As I understand it, XGL was part of X.org - I'm not sure if it was fully integrated with X, or if it was an extension of X.  Nevertheless, it was never a matter of choosing between XGL and X.org - they came together.

In any case, XGL is no longer required - it was replaced by AIGLX in the X Server last Summer.  Also, the Nvidia drivers for your 7300 are capable of performing all the features of XGL.

---

### Post by mcduck on 2009-01-20
XGL was used at some point to enable redirection of all display output, it was required with some graphics cards to be able to use Compiz at all. Current Ati & nVidia drivers suppport all features required by Compiz and thus XGL isn't needed for anything any more.

If you are able to use Compiz without it, you don't need it for anything. It doesn't have any benefits over currently used solution (AIGLX) but instead creates some annoying problems.

---

### Post by emshains on 2009-01-20
Well, I thought I could get a performance boost, but ok :D

---

