---
title: "How to use maxima in Emacs?"
date: 2006-11-06
forum: Education &amp; Science
---

### Post by philyer on 2006-11-06
I'm using *Emacs cvs*, and I've installed *Maxima*. I heared that
*Maxima* can be used in emacs. I found this in the homepage of *Maxima*:
> Put something like these in your ~/.emacs:

(setq auto-mode-alist (cons '("\\.max" . maxima-mode) auto-mode-alist))
(setq load-path (cons  "/usr/share/maxima/5.9.0/emacs" load-path ))
(autoload 'maxima "maxima" "Running Maxima interactively" t)
(autoload 'maxima-mode "maxima" "Maxima editing mode" t)
I'm using ubuntu 6.10, and I haven't found the "/usr/share/maxima/5.9.3/emacs"(maxima installed is 5.9.3). 
I've add these codes into my ~/.emacs but when I input "M-x maxima" in Emacs,
I said that "can not load file maxima".
So, how can I use maxima in Emacs?
Thanks!

---

### Post by parktownprawn on 2006-11-06
install the maxima-emacs package

```
sudo apt-get install maxima-emacs
```

if you want to be more adventurous you can try imaxima which renders the maxima output using latex.

[http://members3.jcom.home.ne.jp/imaxima/Site/Welcome.html](http://members3.jcom.home.ne.jp/imaxima/Site/Welcome.html)

---

### Post by philyer on 2006-11-06
> **parktownprawn said:**
> install the maxima-emacs package

```
sudo apt-get install maxima-emacs
```

if you want to be more adventurous you can try imaxima which renders the maxima output using latex.

[http://members3.jcom.home.ne.jp/imaxima/Site/Welcome.html](http://members3.jcom.home.ne.jp/imaxima/Site/Welcome.html)
Thanks.
If I use apt-get to install maxima-emacs, emacs21 will be installed, too.
But I'm using emacs CVS, these two will coflict with each other.

---

### Post by parktownprawn on 2006-11-06
Where did you install emacs-cvs?

Did you install it in /usr/local ?

---

### Post by darrenleeweber on 2008-03-29
While it may be good to use maxima in emacs, also consider texmacs, both as a useful mathematical editor and as a front end to maxima, gnuplot, octave, etc.  

```

apt-cache search texmacs
sudo aptitude install texmacs

```
I've been using texmacs with a very useful addition called tmplot, see
[http://users.ox.ac.uk/~sedm2579/tmplot.html]("http://users.ox.ac.uk/~sedm2579/tmplot.html")
Also take a look at this useful tutorial, with great tips on getting nice mathematical rendering for input:
[http://arxiv.org/abs/cs/0504039v1](http://arxiv.org/abs/cs/0504039v1)

I can also recommend wxmaxima, it's really nice.
```

apt-cache search wxmaxima
sudo aptitude install wxmaxima

```

---

