---
title: "Metapost does not recognize commands that work under windows. + TexMaker-Theme clash"
date: 2009-02-21
forum: Education &amp; Science
---

### Post by cthulhu_54 on 2009-02-21
METAPOST-PROBLEM
I just migrated from Windows to Ubuntu. In Windows I use mpost to produce graphics to my documents that I compile using LaTeX. In Ubuntu I use TexMaker, which also has a nice mpost build/compile option, which means that I now can do both my LaTeX documents and Metapost using the same editor, nice. Or at least it would be if it worked. I've tried several times, but the Linux/TexLive version of Metapost does not recognize commands that work when I use them in my Windows/MikTex-distribution. Why?

For instance when I build the following simple file:
```

beginfig(1);
a=0.5cm;
pickup pencircle scaled 1pt

draw (0,8a)--(8a,8a);
label.rt(btex $\left.|1\right>$ etex, (8a,7a));
drawarrow (4a,7a)--(4a,8a);

evenly=dashpattern(on 5 off 5);
drawarrow (6a,8a)--(6a,2a) dashed evenly withcolor 0.5white;

endfig;
end;

```

It freaks out at the "evenly=dashpattern..." stuff. When I delete this line (and the following) everything seems to work. At least I get a "File.1" output but is this a PS-file? I does not seem to be readable. When I did this in windows I had a button that converted the *.1 file to PS and EPS. how can I do this in Linux? Does anyone have a clue as to why some commands wont work in Linux, when they do so in Windows?


TEXMAKER THEME-PROBLEM
My second problem is a clash of themes using TexMaker. In ubuntu I use a dark theme which makes background black and text bright, which I really like but in the "editor"-window the line bing typed is white with black text, which is OK, but everything else, i.e. the entire document is black background with black text --> unreadable! Does anyone know a way around this? Configuring the qt4 options does not help, neither is there any option for the text color in Texmaker (just for "commands", "math", and "keyword"). I really like my theme and I really like TexMaker and when changing to Linux I thought I could get everything just as I wanted it, was I wrong?

I've also tried Kile but this does not go well with my theme, since it is KDE and I use Gnome.

---

### Post by cthulhu_54 on 2009-02-26
Anyone?

---

