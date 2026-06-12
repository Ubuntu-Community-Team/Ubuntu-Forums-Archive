---
title: "LaTeX Makefile"
date: 2012-05-01
forum: Education &amp; Science
---

### Post by dankdave on 2012-05-01
Does anyone know what's wrong with this Makefile?  I thought the Makefile would be smart enough to know whether or not any of the .tex files have changed, and therefore not run pdflatex if they weren't ...

```

# List all the files that are used when producing the pdf
FILES = \
    main.tex \
    chap1.tex \
    chap2.tex \
    chap3.tex \
    chap4.tex \
    chap5.tex \
    appendix.tex

# this line should only execute when a single file from above has been altered
# The only problem is that isn't the case ...
all: $(FILES)
	pdflatex main.tex


```

Of course, that's a tab before the pdflatex command ...

---

### Post by Bachstelze on 2012-05-02
```
# List all the files that are used when producing the pdf
FILES = \
    main.tex \
    chap1.tex \
    chap2.tex \
    chap3.tex \
    chap4.tex \
    chap5.tex \
    appendix.tex

# this line should only execute when a single file from above has been altered
# The only problem is that isn't the case ...
main.pdf: $(FILES)
	pdflatex main.tex
```

If you don't say what the output file is, make can't check if a source file is more recent than it. ;)

---

### Post by dankdave on 2012-05-03
I think I'm going to run with latexmk, which is available in the repositories.  If you have a project that depends on a few different .tex files, and main.tex is your main file, you can get away with simply typing:
```

latexmk main.tex

```

I think this is the makefile I'm going to roll with:
```

TEX = latexmk

# List all the files that are used when producing the pdf
MAIN_FILE = main.tex

FILES = \
    chap1.tex \
    chap2.tex \
    chap3.tex \
    chap4.tex \
    chap5.tex \
    appendix.tex

FLAGS = -bibtex -pdf

all: $(FILES)
	$(TEX) $(FLAGS) $(MAIN_FILE)

clean:
	rm *.pdf *.aux *.log *.toc *.lof

```

[http://www.phys.psu.edu/~collins/software/latexmk-jcc/]("http://www.phys.psu.edu/~collins/software/latexmk-jcc/")

---

### Post by dankdave on 2012-05-03
> **Bachstelze said:**
> 
If you don't say what the output file is, make can't check if a source file is more recent than it. ;)

What's the order that the dependencies get resolved in?  I originally wanted to run pdflatex only when one of the .tex files gets changed.

However, with that being said, maybe that's not such a hot idea.  Sometimes you need to run pdflatex a few times in order to get all the citations and references to actually show up in your pdf.

---

### Post by Bachstelze on 2012-05-03
> **dankdave said:**
> What's the order that the dependencies get resolved in?  I originally wanted to run pdflatex only when one of the .tex files gets changed.

The command will be run if any of the files listed as a dependency was modified, so the order is unimportant. If you want to check for only one file, include only that file as a dependency. What you said about running it several times is true, though...

---

