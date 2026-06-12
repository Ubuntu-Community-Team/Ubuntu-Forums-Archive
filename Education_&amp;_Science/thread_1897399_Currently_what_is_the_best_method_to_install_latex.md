---
title: "Currently what is the best method to install latex in Ubuntu?"
date: 2011-12-19
forum: Education &amp; Science
---

### Post by arroy_0209 on 2011-12-19
I am asking because there are conflicting views and technical complications related to installation of latex in Ubuntu 10.04 LTS-2.

One suggestion is to use the command
```

sudo apt-get install texlive-latex-base

```but many people say this version is too old. In that case one case download directly from texlive but the entire package is huge (size is more than 1Gb, if I am not wrong) and contains so many unnecessary applications which I will never use. What I need is a basic latex compiler and as need arises, install specific packages and use them. For example, I will need amsmath, amsfont, etc and some aps (for americal physical society related publications) packages, and special packages for drawing diagrams and writing symbols etc. The texlive package contains many things but there is limitation on volume of download that I am allowed by my ISP and that exceeds the limit. Can anybody please explain which way I should proceed? It would be nice (though not absolutely necessary) that pdflatex is attached. Should I just download and install kile? Your suggestions are welcome.

---

### Post by gunksta on 2011-12-19
LaTeX, R, Python, etc. are all produced "upstream" from Ubuntu. This means Ubuntu uses and provides the software to users like you and me, but they do not actually employ the hackers writing the software. If you really need the latest / greatest bleeding edge features, you should install LaTeX using the upstream version which is usually much newer than what is in the Ubuntu repos. But most of us don't need those features. I certainly don't. When I use LaTeX, I prefer to use the packages in the repos because I know they work and I know I know they will automatically upgrade when I upgrade my computer in a few months.

Normally I would recommend texlive-latex-recommended but if you are under a restrictive bandwidth cap, this is probably a bad idea. Its a big download. I think you should just search the repos manually looking for what you need and install the packages you want and need. They will pull in the necessary dependencies automatically. If you can go somewhere where you can use a wifi connection to get around your provider's bandwidth cap, it might pay off and you can just install everything and be done with it.

---

### Post by FreeTheBee on 2011-12-20
I always install manually, I never bothered with the texlive in the repositories since I consider it obsolete most of the time. At the moment they still seem to be using texlive 2009 which was frozen a bit more than 1.5 years ago.  To me this is not a matter of bleeding edge vs stability, but more lack of attention from Ubuntu. I also prefer to use the texlive package manager over synaptic for my latex installation. 

As gunksta pointed out though, for many people it will not matter that much. If you're not using any packages that are actively developed tl2009 will do just fine. If you are using kile this will be easier as well, since then you don't have to mess about fixing dependencies. In some cases it could even be beneficial to use an old one, since for example elsevier is also still on tl2009 for submission of papers.

---

### Post by ssam on 2011-12-21
if you want quick and easy use the repos. This is probably fine for most people. ubuntu and debian have texlive 2009, fedora has 2007.

you can have a look at what has change in more recent versions.
[http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-770009.1.5](http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-770009.1.5)

---

