---
title: "Drawing a (right-angled) triangle using gnuplot"
date: 2013-11-15
forum: Education &amp; Science
---

### Post by s3a on 2013-11-15
Hello, everyone.

I would like to use gnuplot to add triangle images to a LibreOffice Writer document I'm writing. If there are, in your opinion, better tools for the job, I am interested in hearing what they are, but I still would like to know how to operate gnuplot, since it seems to be something that I will love when I master it.

I'm a complete beginner to using gnuplot, and I was hoping someone could tell me how to draw a (right-angled) triangle using gnuplot, and have the triangle have those two curvy things representing the non-90-degree angles, in addition to having that square-or-two-sides-of-a-square symbol that represents 90 degree angles.

I would REALLY appreciate it if someone could give me the most basic syntax possible to draw such a triangle!

In fact, I don't even yet know how to make gnuplot look through a file for the commands instead of me giving them manually via the command line, so please be gentle! :D

---

### Post by steeldriver on 2013-11-15
DISCLAIMER: I am only an occasional gnuplot user, I pretty much have to relearn it every time

To answer your second question, you can put any commands that you use in an interactive gnuplot session into a plain text file and simply call it in batch mode like

```
gnuplot *myfile*
```

To plot a triangle, you could simply define the vertices of your as regular points in a 2D plot e.g. create a file containing x y data pairs

```

$ cat tri.dat
1.0  1.0
1.0  4.0
5.0  1.0
1.0  1.0

```

and then plot it from the interactive gnuplot prompt as

```
gnuplot> plot [0:6] [0:6] 'tri.dat' title 'Right triangle' with lines
```

However the newer versions of gnuplot have some quite nice 'object' plotting options - since you'll probably need to use 'objects' for the angle markers, it might be easiest to plot the basic triangle as a polygon object as well. This was the best I could come up with:

```

$ cat tri.plt

set angle degrees

# use 'square' aspect ratio else calculated angles don't match display angles
set size square

# draw a 3,4,5 right triangle as a polygon - f[ill]s[tyle] empty border 1 (red)
set object 1 poly from 1,1 to 1,4 to 5,1 to 1,1 fs empty border 1

# draw a small rect[angle] to represent the rightangle
set object 2 rect from 1,1 to 1.25,1.25 fs empty border 0

# draw an arc for the upper angle
set object 3 circle center 1,4 size 0.35 arc [-90:-(90-acos(3.0/5.0))]

# draw an arc for the lower angle
set object 4 circle center 5,1 size 0.35 arc [-(180+acos(4.0/5.0)):-180]

# plot 'something' - else objects don't show
plot [0:6] [0:6] 0 title 'Right triangle', 0 notitle


```

then run it from the shell as

```
$ gnuplot -p tri.plt
```

[ATTACH=CONFIG]247859[/ATTACH]

---

### Post by tgalati4 on 2013-11-15
A web search on *gnuplot tutorial* will bring up several hits including:

[http://people.duke.edu/~hpgavin/gnuplot.html](http://people.duke.edu/~hpgavin/gnuplot.html)

*gnuplot* is worth learning.  I started using it in 1986 to plot experimental data.  Not much has changed and that is what I like about it.

---

### Post by s3a on 2013-11-16
Steeldriver, you have given me some amazing basic syntax that is specific to my situation to learn from! [nerdgasm]Oh my god![/nerdgasm] :P

Thank you both, especially steeldriver!

---

### Post by steeldriver on 2013-11-16
I forgot to mention, if you want to create embeddable files (png / gif / jpeg etc.) that you can import into your document, you can use the 'set term[inal]' command - either within the script, or passed as an expression on the command line e.g.

```
gnuplot -e "set term postscript; set output 'tri.ps'" tri.plt
```

or equivalently using stdout

```
gnuplot -e "set term postscript" tri.plt > tri.ps
```

For a complete list of available terminal types in your installation, use 'set term' with no argument at the gnuplot prompt.

---

