---
title: "Cinnamon Menu CSS Theme Development Effort"
date: 2012-05-15
forum: Desktop Environments
---

### Post by MooseDog on 2012-05-15
Having just made my very first 'contribution' to the open source world from which I've taken so much:

[http://cinnamon-spices.linuxmint.com/themes/view/76](http://cinnamon-spices.linuxmint.com/themes/view/76)

I'd like to try and continue along this path. Specifically an effort to expand the theming capabilities by making things more readable and easier modified. As we know, documentation on this subject is pretty thin on the ground. More in a bit, but my goal is to make theming intuitive w/o plowing through pro-directed docs.

So...I've started a repo on Github to pursue this:

[http://bit.ly/JmfCa0](http://bit.ly/JmfCa0)

And here's the deal: I'm using a CSS pre-compiler to generate the final cinnamon.css file (which is long, obtuse and not at all obvious). The Compass framework is amazing, and if you do CSS, once you use it (or any of the others to be fair) you'll never look back:

[http://compass-style.org/](http://compass-style.org/)

Specifically, it's a Ruby gem that leverages the Sass pre-compiler:

[http://sass-lang.com/](http://sass-lang.com/)

Referring back up above, here's what I'm thinking: by breaking style blocks into a file structure of the end result's component parts, you have in a sense created an intuitive documentation. Sure, in-line notes will always be invaluable, but a file structure of 'partials' is faster to read and understand at a glance. Gets the themer up and running even quicker! And the whole community wins that way.

Variables, nesting and functions for CSS oh my!

---

### Post by rai4shu2 on 2012-05-15
This can be adapted to include Xfce? Anything that can help gtk theming would be a huge improvement.

---

### Post by MooseDog on 2012-05-17
xfce, afaik, uses gtk+, so unfortunately no.

however, since cinnamon is a fork of gnomeshell, this in theory should also work for a gnomeshell theme, with some tweaks (one i can think of off the top of my head is renaming the resulting css file).

---

### Post by rai4shu2 on 2012-05-17
Umm... Last I checked, Cinnamon still uses gtk 3. The same as Gnome Shell and most updated gtk apps. Xfce currently uses gtk 2, but that will change soon.

---

