---
title: "texlive 2008 paper size"
date: 2009-04-11
forum: General Help
---

### Post by tramir on 2009-04-11
Hey everybody,

I have the following problem: I installed TeXLive 2008 from source using [these instructions]("http://neoarch.wordpress.com/2008/08/16/tex-live-in-ubuntu-without-the-packages/") (except for the PATH thing, where I used the last comment on the same page). I chose "letter" as the default paper size for everything and checked that all the configuration files in  /usr/local/texlive/2008/texmf-config/ have the paper size defined as letter. I also have /etc/papersize = letter. I checked and overchecked all the settings, ran "sudo tlmgr paper letter" and so on, but whatever I do, my LaTeX documents get compiled as A4. Anybody has any idea how I could solve it?

TIA...

---

### Post by tramir on 2009-04-12
Nevermind, figured it out. I was loading the "anysize" package, which has the (bad) habit of setting the paper size to A4. Problem solved...

---

