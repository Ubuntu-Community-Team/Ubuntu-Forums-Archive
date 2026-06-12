---
title: "Graphics card stability test [Overclock]"
date: 2009-05-19
forum: General Help
---

### Post by XCan on 2009-05-19
I'm wondering if there are any worthwhile applications for Ubuntu dedicated to load the graphics card to its maximum for stability-testing purposes. For example, Windows has the excellent FurMark, the stability tool in Ati-tools and so forth.

Out of curiousity, I'm also looking for similar programs for the CPU, like Orthos in Windows.

---

### Post by Psycho.mario on 2009-05-19
I second this question, it would be a useful app.

---

### Post by nolliecrooked on 2009-05-19
if you have a nvidia card you can use nvclock.it lets you control fanspeed too. just search for it in synaptic. it will give you 3 options like

nvclock
nvclock qt
nvclock gtk

forget nvclock qt, its pointless. install nvclock & nvclock gtk

to launch the gui for nvclock, type nvclock_gtk in the terminal, or make a launcher with that as the command :P

---

### Post by P3t3r on 2012-04-24
Are there any such tools for AMD graphics cards? I have several AMD graphics cards in my machine and I think one of them is unstable even at stock clock. Which test should I use for this on Ubuntu?

---

### Post by Cheesemill on 2012-04-24
For CPU stress testing I use mprime.
It's not in the repos but it's easy enough to install, no need to compile.
You can register for an account if you want to join the search for large prime numbers but there is no need if you only want to use it for stress testing.

[LIST]
[*]Download mprime from [here]("http://www.mersenne.org/freesoft/").
[*]Extract the files anywhere you want (I create a folder called mprime in my home folder).
[*]cd into the appropriate directory and run:
[/LIST]
```
./mprime -m
```

---

### Post by P3t3r on 2012-04-24
> **Cheesemill said:**
> For CPU stress testing I use mprime.
Sure but this doesn't work for GPU, right?

---

### Post by Cheesemill on 2012-04-24
From the OP.
> **XCan said:**
> Out of curiousity, I'm also looking for similar programs for the CPU, like Orthos in Windows.

---

### Post by oldos2er on 2012-04-24
Old thread closed.

---

