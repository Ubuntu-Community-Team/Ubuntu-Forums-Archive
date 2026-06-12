---
title: "LaTeX opening pictures piece by piece"
date: 2010-02-02
forum: Education &amp; Science
---

### Post by 7raTEYdCql on 2010-02-02
I intend to host a quiz, and one of the rounds, involves opening a unrevealed picture piece by piece, by clicking on them. Therefore revealing the underneath picture as the round progresses. 

Any idea of achieving the using LaTeX, or any other software for that matter.

---

### Post by Abdus on 2010-02-02
I doubt this is achievable using TeX engine - it was not written with user interaction in mind at all, it comes from pre-internet times. :)

The question here should be - can I embed an interactive object prepared in an external application XYZ into a LaTeX generated .pdf document?

I don't know the answers, but this tip possibly can help you find a solution.

---

### Post by 7raTEYdCql on 2010-02-02
> **Abdus said:**
> I doubt this is achievable using TeX engine - it was not written with user interaction in mind at all, it comes from pre-internet times. :)

The question here should be - can I embed an interactive object prepared in an external application XYZ into a LaTeX generated .pdf document?

I don't know the answers, but this tip possibly can help you find a solution.

Can you suggest me some tools which can make this possible.

---

### Post by Abdus on 2010-02-03
> **i.mehrzad said:**
> Can you suggest me some tools which can make this possible.

Unfortunately not, I don't know any applications for creating interactive content - I'm a typesetter. I have also never seen a truly interactive PDF document, which suggests to me that me PDF format is most probably not suitable for your project. If it was possible, we would have plenty of PDF's with interactive content, I think.

Some multimedia can be embedded into a PDF for sure, like movies, but I doubt it's your goal here.

---

### Post by xadder on 2010-02-03
A crude way to do this would be to use the ability of \includegraphics to show just part of the figure, using e.g. bburx=100,bbury=600,.....
changing the "bb" parameters for each page. This wouldn't work with a simple click, but a Page-down would do the job, effectively showing a new picture on each page.

Check out e.g. the prosper (or beamer) packages for presentations in LaTeX. Such tricks (hiding parts of the page or figure) are often used in presentations.

---

### Post by Hannes Hochreiner on 2010-02-03
> **xadder said:**
> Check out e.g. the prosper (or beamer) packages for presentations in LaTeX. Such tricks (hiding parts of the page or figure) are often used in presentations.

I agree with xadder, if you know the sequence in which the tiles of the image are revealed in advance, you could just check out a few presentation programs.

If you don't know the sequence in advance, you could, for example, use an HTML page where you define the image as the background of a table, set a background colour for the different cells (to hide the image) and apply an "onclick" handler to the cells to remove the background colour of the cells (i.e. make them transparent as to reveal the image) when you click on them.

---

### Post by QuimNuss on 2010-02-03
It's possible to make interactive pdf's with the TiKz library, however, it isn't easy at all. With the latest Adobe PDF version there are drawing options and other stuff, maybe there's something you could exploit, but I don't really think so.

Indeed, PDF it's a weird choice for an interactive quiz, there are many other languages and formats which would support what you intend to do straight away. Why you'd like to use LaTeX? Are you writing down a lot of formulae?

---

### Post by Abdus on 2010-02-03
> **QuimNuss said:**
> It's possible to make interactive pdf's with the TiKz library, however, it isn't easy at all.

The only place where it says 'interactive' in the (most excellent) PGF/TiKz documentation is the user license (and 1 irrelevant footnote). "Click" was found 2 times, irrelevant to our discussion as well. :) Are you sure TiKz is really capable of producing interactive content? I wuold be most interested, it would really suit a project I'm doing rifgt now using TiKz.

---

