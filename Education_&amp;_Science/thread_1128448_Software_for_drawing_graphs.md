---
title: "Software for drawing graphs"
date: 2009-04-17
forum: Education &amp; Science
---

### Post by elvijs on 2009-04-17
I'm working on a project which requires illustrations in the form of graphs with additional lables (I need to draw a Markov chain and display the associated probabilities). Is there a good program for doing this?

---

### Post by Julian Lewis on 2009-04-17
apt-get install gnuplot

This is a very powerful and easy to use plot program for linux. I have used it from applications, command files are easy to make.

---

### Post by elvijs on 2009-04-17
Sorry, I wasn't being clear - I mean graphs as in graph theory: [http://en.wikipedia.org/wiki/Graph_(mathematics)](http://en.wikipedia.org/wiki/Graph_(mathematics))

---

### Post by Natr0n on 2009-04-17
How about [dia]("http://projects.gnome.org/dia/")?

---

### Post by unutbu on 2009-04-17
You can also generate some pretty wild diagrams using inkscape:
[http://ubuntuforums.org/showthread.php?p=6412100](http://ubuntuforums.org/showthread.php?p=6412100)

Or, if you don't mind learning a mini-language, graphviz might be a good solution: [http://www.graphviz.org/Gallery.php](http://www.graphviz.org/Gallery.php)

(To generate the pictures:

```
sudo apt-get install graphviz
```

Save the code in graph.dot. Run

```
dot -Gratio=auto -Tpng -o graph.png graph.dot
xdg-open graph.png
```

---

### Post by hubie on 2009-04-17
As is true for most things, [the answer lies with LaTeX]("http://graphtheoryinlatex.blogspot.com/"). :)

---

### Post by elvijs on 2009-04-18
Thanks for the info!

---

### Post by elvijs on 2009-04-19
For anyone interested, [_this_]("http://www.fauskes.net/code/dot2tex/documentation/") allows to add LaTeX to dot graphs.

---

