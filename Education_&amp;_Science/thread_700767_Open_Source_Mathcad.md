---
title: "Open Source Mathcad?"
date: 2008-02-18
forum: Education &amp; Science
---

### Post by camdecoster on 2008-02-18
I am looking for a FOSS alternative (cross platform, preferably) for Mathcad. What I really like about Mathcad is the live worksheet interface. Console based programs aren't nearly as convenient, in my opinion. I've already looked into Maxima, Octave and Scilab, but they all use console based input. Does anyone know of any program (or GUI for the aforementioned programs) that would function as an alternative to Mathcad with the same live worksheet interface?

---

### Post by arkara on 2008-02-18
i know octave..
but it is a alternative of matlab witch i think its very similar... with mathcad
also try scilab

---

### Post by thisismalhotra on 2008-02-19
> **camdecoster said:**
> I am looking for a FOSS alternative (cross platform, preferably) for Mathcad. What I really like about Mathcad is the live worksheet interface. Console based programs aren't nearly as convenient, in my opinion. I've already looked into Maxima, Octave and Scilab, but they all use console based input. Does anyone know of any program (or GUI for the aforementioned programs) that would function as an alternative to Mathcad with the same live worksheet interface?

QtOctave and Koctave are nice GUI frontends for octave and the latest Qtoctave works just like matlab.. you might wanna give it a try ...

---

### Post by bhavi on 2008-02-19
> **thisismalhotra said:**
> QtOctave and Koctave are nice GUI frontends for octave and the latest Qtoctave works just like matlab.. you might wanna give it a try ...
Yes Koctave works just like Matlab.. I use it..

---

### Post by thisismalhotra on 2008-02-19
No offense here but I would still go with Qtoctave, as Koctave has not been updated in ages and Qtoctave is a working branch with active developers and they have added few other tools to the GUI such as EasyPlot which helps a lot.

---

### Post by ad_267 on 2008-02-20
Octave and Matlab are different to **Mathcad**, I think you want something like xMaxima ([http://packages.ubuntu.com/maxima](http://packages.ubuntu.com/maxima))

Have a look at this page there's some good links: [https://help.ubuntu.com/community/UbuntuScience](https://help.ubuntu.com/community/UbuntuScience)

---

### Post by camdecoster on 2008-02-27
Thanks for all the responses. I can't seem to find any program with a Mathcad-like interface, but I suppose Maxima or Scilab will work for the most part. If anyone finds anything, please add it to this post or PM me.

---

### Post by sg007 on 2008-09-15
> **camdecoster said:**
> Thanks for all the responses. I can't seem to find any program with a Mathcad-like interface, but I suppose Maxima or Scilab will work for the most part. If anyone finds anything, please add it to this post or PM me.
if you looking for ,,Mathcad-like interface'' program ... could be a hard task, but maybe CalcTeX could be supportive for you. this package is still developing and should be an alternative to mathcad.

[http://sg.bzip.pl/CalcTeX/](http://sg.bzip.pl/CalcTeX/)

---

### Post by brunovecchi on 2008-09-16
[**This thread**]("http://ubuntuforums.org/showthread.php?t=804254") might be useful. The bottom line is there isn't yet an alternative; MathCad seems to be quite unique.

---

### Post by xflow on 2008-09-16
You can try FreeMat:

[http://freemat.sourceforge.net/](http://freemat.sourceforge.net/)

---

### Post by janne_ph on 2008-09-16
I'm not familiar with mathCad, but if you are looking for something similar to Maxima I would recommend wxMaxima. The GUI feels much better than xMaxima, at least thats my opinion.

---

### Post by andysmith3 on 2008-09-18
helloreplica.com  provides a wide array of [Replica Watches](http://www.helloreplica.com/) and professional customer sevrice, our goal is to make every customer 100% satsfied. We are more than ready to show our unique prowess and fortes to gain our footing. And we also provide fast delivery service, we guarantee our listing price is lower than other competitor. welcome to oursite  [Replica Rolex Watches](http://www.helloreplica.com/)  [Rolex Watches](http://www.rolex2u.com/)   [replica rolex watches](http://www.rolex2u.com/) [replica rolex](http://www.rolex2u.com/)

---

### Post by I3enhamin on 2008-10-16
sagemath.org blows me away... it's very promising.  notebook and/or shell options.

---

### Post by dotnick on 2009-01-28
I'm new to this thread, and I too love MathCad.  I checked out the SMath program that was mentioned on one of these threads.  It is certainly the closest thing to MathCad that I've seen so far.  This project does still seem to be in its infancy though.  Printing doesn't seem to be supported yet and other graphical and advanced mathematical functions are still missing, but the initial interface and live worksheet is already in place.  There may be a feature to send the sheet to an image file instead of a pdf, and there is an option to send the sheet to an HTML file (for printing with a web browser).

I'm happy to see this topic make so much buzz.  I've been hoping for something like this for a long time now.  

[http://en.smath.info/forum/default.aspx?g=posts&t=73](http://en.smath.info/forum/default.aspx?g=posts&t=73)

---

### Post by muddybeemer on 2010-01-24
If you are looking for an open-source alternative to MathCad, you may want to look at CompPad: ([comppad.sourceforge.net]("http://comppad.sourceforge.net")).  Here is the description from the Sourceforge page:

"CompPad is an OpenOffice.org extension that provides live mathematical and engineering calculations within a Writer document. It is intended to provide an open-source alternative to Mathcad."

CompPad evaluates the formulas in an openoffice document and displays the results in the document.  Some of its features include:
[LIST]
[*]Units of measure
[*]Complex numbers
[*]Vectors and Matrices
[*]X-Y Plots using native OpenOffice Chart.
[*]A selection of built-in functions
[/LIST]

It is currently pre-alpha but is quite usable for basic calculations.  Check out the [CompPadDemo.odt]("http://comppad.svn.sourceforge.net/viewvc/comppad/trunk/test/CompPadDemo.odt") to see its features, and download the latest .oxt file to install the plug-in.

---

### Post by not_a_phd on 2010-01-26
I have tried CompPad (albeit 5-months ago). I found it a bit too cumbersome, primarily due to its pre-alpha state. The fact is, in order for it to be very useful to me, it is going to have to reinvent  lot of computational wheels already taken care of in octave.

I use octave extensively, and would find it exceedingly more useful if I could embed figures and symbolic equations as comments in my .m files. If I could embed tables of results and graphs in the .m file, with results fed back from octave, that would be even better. 

I prefer octave to to spreadsheets, primarily because F=m*a reads better than =$A$1*$B$1. But, the ability to embed text box notes, figures, and graphs in spreadsheets makes them extremely useful.

---

### Post by MySchizoBuddy on 2010-08-13
Smath Studio Desktop is THE alternative to Mathcad.
[http://en.smath.info/forum/default.aspx?g=posts&t=561](http://en.smath.info/forum/default.aspx?g=posts&t=561)

---

### Post by meng1usa on 2010-09-21
Tried it. It actually is the clone of mathcad, but not as functional.
But it's usable for most needs.
-------------
+1 smath studio

---

### Post by BFris on 2011-03-18
CompPad is rough around the edges, but I already find it useful for everyday use. The 0.3.x releases are the most useful.

I took day figure out if CompPad was worth the trouble. And I'm glad I did. Now I'm using it for scratch pads and reports. The big advantage it has over MathCAD is that the documents are inherently publication quality. Seriously. I already use OpenOffice/ LibreOffice Writer for all of my reports, even though Micro$oft Word is preferred where I am.

Honestly, I wouldn't call CompPad stable enough for a 20 page report. But 10 pages or less and you're set.

---

