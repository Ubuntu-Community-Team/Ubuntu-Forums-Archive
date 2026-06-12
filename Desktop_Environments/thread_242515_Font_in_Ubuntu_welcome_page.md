---
title: "Font in Ubuntu welcome page"
date: 2006-08-23
forum: Desktop Environments
---

### Post by QuantumCaffeine on 2006-08-23
Hi all,

(If you can't stand nitpickers, stop reading now.) 

I've never been keen on the font used in the welcome page that's used as the default Firefox home page (the one headed "Welcome to Ubuntu 6.06 LTS"), so I had a look at the source and discovered that it's set to use the following fonts:

font-family: "Lucida Grande", Verdana, Lucida, Helvetica, Arial, sans-serif;

(From /usr/share/ubuntu-artwork/home/ubuntu.css.)

What's up with this? If memory serves, *none* of the named fonts are installed as standard, meaning most people will see the standard sans-serif font (or Verdana if they install the standard Windows fonts later on). Furthermore, Lucida Grande is a commercial font that only Mac users get for free.

Since this page is one of the first things most people see on installing Ubuntu, it would be nice if we could sort this out. For my money, we should either remove all options but sans-serif, or we should replace the named fonts with one that's usually installed. (For example, Luxi Sans is not dissimilar in feel to Lucida Grande. Personally, I like it a lot better than the default Sans.)

Sorry to rant, but it's been niggling at me for a while (pathetic, I know).

QC

---

### Post by fragos on 2006-08-23
Which fonts to use are very subjective.  You are very correct the fonts used aren't part of the standard install.  And why use Windows fonts rather than open source.  Thankfully, browsers and other applications are able to display readable text even when the specefied font isn't availble.

---

### Post by QuantumCaffeine on 2006-08-24
> **fragos said:**
> Which fonts to use are very subjective.  You are very correct the fonts used aren't part of the standard install.  And why use Windows fonts rather than open source.  Thankfully, browsers and other applications are able to display readable text even when the specefied font isn't availble.

The point isn't so much about readability -- that's a given -- but about attractiveness, given that this page is one of the first things a new user will see. Attractiveness is obviously a subjective matter, but it's obvious that the current stylesheet has simply been taken from somewhere else and used without much thought. All I'm asking is that someone think about it and adjust the stylesheet accordingly. 

This is one of those (extremely rare) occasions when the author of a stylesheet can be sure exactly what fonts should be available, so it's just a matter of either picking one or using 'sans-serif' to pick up the default Firefox sans serif font. It's an easy fix to a small problem.

Cheers,

QC

---

