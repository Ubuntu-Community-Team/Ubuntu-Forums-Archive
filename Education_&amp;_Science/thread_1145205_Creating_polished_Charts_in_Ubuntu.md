---
title: "Creating polished Charts in Ubuntu"
date: 2009-05-01
forum: Education &amp; Science
---

### Post by lodp on 2009-05-01
I'm looking for a way to create nice polished charts in Ubuntu or online. I'm trying to help a friend spruce up her dissertation. She's writing it in MS Word 97, and the charts look like they're from '93.

The graphs in Oo look OK, but I'm looking for something a little more stylish, while still simple.

I ran into the Google Charts API and had some nice results:

[IMG]http://chart.apis.google.com/chart?chs=500x250&chg=20,12.5&chf=bg,s,ffffff|c,s,ffffff&chxt=x,y&chxl=0:|0|35-45J.|45-55J.|55-65J.|65-75J.|75-85J.|85u.mehr|1:|0|2000|4000|6000|8000|1000|12000|14000|16000&cht=lc&chd=t:0.00,1.66,9.32,17.32,37.99,21.99|0.00,.32,1.32,9.32,41.99,77.99|0.00,1.99,10.66,26.66,79.99,100.00&chdl=M%C3%A4nner|Frauen|Gesamt&chco=3333ff,cc3333,333300&chls=2,1,0|2,1,0|2,1,0&chm=o,3333ff,0,-1.0,7|o,cc3333,1,-1.0,7|o,333300,2,-1.0,7[/IMG]

However, creating charts that way is a real pain (there are no really good web-GUIs that control all aspects), and the charts don't look very good in print since they aren't vector graphics.

Any ideas?

---

### Post by Gilabuugs on 2009-05-01
Take a look at gnuplot it is command based though, but has a large community if you can google.

If you know python matplotlib is a step up in quality I think.

Edit: You might want to look into google charts some more I was looking and there is a size part of the charts in pixels I didn't see if there was a limit but you don't need that big for good charts.

---

### Post by halocaridina on 2009-05-02
You may also want to try ploticus:

[http://ploticus.sourceforge.net/doc/welcome.html](http://ploticus.sourceforge.net/doc/welcome.html)

The "prefabs handbook" has many examples of creating publication quality graphs using files with a simple data structure.

Ploticus can also output much more sophisticated graphs using scripts.

We (my colleagues and I) have utilized ploticus in several recent peer-reviewed publications without having to do any modifications to the output, so it might be exactly what you need.

halocaridina

---

### Post by jbrefort on 2009-05-02
You might give a try to gnumeric. Its charts are highly customizable and can be exported as svg or eps.

---

### Post by lodp on 2009-05-02
Thank you guys so much!

Gnumeric turns out to be exactly what I was looking for. The interface is very intuitive, and you can customize every aspect of the chart.
I was having problems with the .svg exports though -- the resulting files would display fine in gthumb and firefox, but when I inserted the file in an openoffice document, all the labels were missing. I guess I'll have to file a bug for that..

---

### Post by gunksta on 2009-05-03
SVG support in OOo is faily new and the problem could be in OpenOffice, rather than in Gnumeric. Try opening the plot in a dedicated SVG viewer such as Inkscape, or you could even use FireFox, which has pretty good support for SVG graphics. If the graph looks right in these tools, then the bug is probably in OOo. If it looks weird in these apps, the problem is probably in gnumeric.

---

### Post by NikoC on 2009-05-04
Qtiplot also has a nice GUI and offers a lot of customization options (available via the repos: sudo apt-get install qtiplot)

---

