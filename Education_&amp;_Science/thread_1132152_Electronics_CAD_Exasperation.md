---
title: "Electronics CAD Exasperation"
date: 2009-04-21
forum: Education &amp; Science
---

### Post by oldchris on 2009-04-21
I'm strictly a hobbyist who makes the occasional electronic gizmo in support of other hobbies. I used to make schematics/pcbs with a DOS application and I don't recall ever getting as aggravated as I have been lately.

a) does anybody have any tricks/hints on getting gEDA/gschem to link nets to pins?  It seems to be very hit or miss - sometime they link fine, other times I get the no-connectivity red square no matter what I try.  I'm sure there must be some simple setting/option/technique that I'm not grasping. 

b) other than Eagle (which drives me crazy every time I have to find a component in the libraries) can somebody recommend a relatively non-frustrating schematic/PCB layout solution (kicad?). 

c) if gEDA is as good as I'm going to get, can somebody direct me to a support community?  My googling has been very unhelpful. 

TIA,
Chris

---

### Post by hubie on 2009-04-22
I can't give you any direct help because I haven't used any of the programs, but I did dig up a couple of links I hope you might find useful:  a [Slashdot question]("http://ask.slashdot.org/article.pl?sid=06/02/24/222212") (2006), and a [Linux Journal article]("http://www.linuxjournal.com/article/8438") (2005).

If you find anything more recent, please post here because I would find it interesting.

---

### Post by oldchris on 2009-04-23
Don't really have much to add to the 2005/2006 opinions.  In 2009 the advice seems to be "use Eagle" or "try Kicad".  There appear to be people using gEDA/gschem/PCB etc, but they don't seem to have a "community" with fora where noobs can ask dumb questions.  There is a "mailing list" that seems quite active, but I'm not sure I want to wade through dozens of emails every day.  

As for my gschem issues, here's what I've figured out so far: 

- gschem doesn't do "close".  If you're off just a bit, the net won't connect to the pin.  You need to be right at the end of the red bit or just (1 snap max) into the background colour and colinear to the pin. 
- zoom (z/Z or mouse wheel) is your friend.  You really have to zoom in to find the right point on the symbol to link the net. 
- don't mess too much with snap grid. If you change the interval, and the new interval isn't an even multiplier/divisor of the old interval, nothing will connect.  This is also a problem if you use symbols built on a different snap.

Have managed to get a simple schematic connected and moved into PCB for layout/artwork. 

C.

---

