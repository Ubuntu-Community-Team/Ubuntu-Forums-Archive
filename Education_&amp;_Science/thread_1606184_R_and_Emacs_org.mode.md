---
title: "R and Emacs org.mode"
date: 2010-10-26
forum: Education &amp; Science
---

### Post by Axolotl9250 on 2010-10-26
Hi All, I've been trying to get into writing documents with R code in org.mode with emacs, as I already have ESS, and sql-sqlite mode, so I could do my entire collection, analysis, and inserting into and writing up paper, all with Emacs. 

I got some code from the net to try out for myself (all taken from: [http://repo.or.cz/w/Worg.git/blob_plain/HEAD:/org-contrib/babel/examples/foo.org](http://repo.or.cz/w/Worg.git/blob_plain/HEAD:/org-contrib/babel/examples/foo.org)) 

```
Well, we can now include =R= in our document.  Here's a simple example
#+begin_src R :exports both
  2 + 2
#+end_src

```An an Image, through use of code block-reuse (DRY principle):
```

#+begin_src R :results output :exports both
  n <- 50
  x <- seq(1, n)
  a.true <- 3
  b.true <- 1.5
  y.true <- a.true + b.true * x
  s.true <- 17.3
  y <- y.true + s.true * rnorm(n)
  out1 <- lm(y ~ x)
  summary(out1)
#+end_src

#+source: fig1
#+begin_src R :exports results :noweb yes :file fig1.pdf
  <<fig1plot>>
#+end_src

```I do this in my .org file and export through latex to PDF and I don't get any images.
I just get the code or <<fig1plot>> printed.

I even tried the code that followed:

```

#+attr_latex: width=0.8\textwidth,placement=[p]
#+label: fig:one
#+caption: Scatter Plot with Regression Line
#+results: fig1
[[[[file:fig1.pdf]]]]

```But still no luck.

I also did some R code where I assigned the numbers 1 2 3 4 5 6 7 8 9 10 to the object
"data" and then called data to have it return those numbers , and it doesen't - it just displays the command on the pdf, with no processing done. So I'm assuming commands are not being sent to R and results retrieved.

I'm confident that I'm doing these code chunks correctly. I was told this would work with emacs straight away,
providing I have R, and ESS also installed too, and would be able to try it instantly.
Does anybody know what I'm doing wrong? I've attached the PDF and the .org file if any further information is needed.

Thanks,
Ben.

(Note the .org file has the .txt extension to allow upload, normally it has the .org extension)

---

### Post by Axolotl9250 on 2010-10-26
I've made a development, in that it may be a problem with org-babel. Now I have not installed anything onto 
Ubuntu and Emacs other than the basic Emacs from Synaptic.
My Lecturer instructed me to add this to my .emacs file:

(org-babel-do-load-languages
      'org-babel-load-languages
      '((emacs-lisp . nil)
        (R . t)))

Which I did, but now upon starting Emacs I get this error: 

Warning (initialization): An error occurred while loading `/home/ben/.emacs':

Symbol's function definition is void: org-babel-do-load-languages

To ensure normal operation, you should investigate and remove the
cause of the error in your initialization file.  Start Emacs with
the `--debug-init' option to view a complete error backtrace.

Now without that bit in my .emacs Emacs runs fine. I stress I haven't done anything else to Emacs.
Is there something else I need to do or install to use babel?

Cheers, 
Ben.
[EDIT] Everything's fixed now, I updated Org mode through downloading a package and installing it as opposed to using the built in version.



&#834;

---

