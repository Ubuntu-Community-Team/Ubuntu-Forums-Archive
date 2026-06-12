---
title: "Preparing presentation with Latex and Animation"
date: 2010-11-03
forum: Education &amp; Science
---

### Post by swaprava on 2010-11-03
Hi all,

This is to those people who use scientific literature frequently and require to prepare presentations based on them or our own works. What I found to be very annoying is the conflict between animation and cool equations in preparing any presentation. It seems if you want to use mathematical symbols and equations using the power of Latex, you must use Beamer, however, it is not very easy to include animations in a beamer presentation because it is not WYSIWYG kind of editor. The other presentation preparing app like openoffice doesn't show the equations as beautifully as beamer does. Can anybody suggest an application in Ubuntu (or Linux in general) which combines the best of both worlds? I heard about Keynote in Mac, however, never used it. If there is something similar in Ubuntu, where we can prepare animations in short time and put equations as in Latex, that would be a major step forward in using Linux for scientific presentation preparation. :)

---

### Post by Warthaug on 2010-11-03
My solution is to run a virtualized version of XP and to use powerpoint for presentations.  Its the one piece of ssoftware where m$ is still ahead of the curve.

I realize that answer doesn't help you in the least...

Bryan

---

### Post by Matths87 on 2010-11-03
Despite Beamer is not the best choice if you are looking for sophisticated animations and other related stuff, LaTeX is in my opinion the unique software that allows the user to create very complicated formulas with little effort and loss of time. In this sense, M$ Office and also OpenOffice should be used only for the shopping list :P

---

### Post by agm. on 2010-11-03
I am a fan of LaTeX but have yet to master Beamer myself.  Two options are available, though neither is optimal.  One option is to make all of your equations in a LaTeX file, build it, and then copy/paste them from the pdf into an PowerPoint or Impress file.  

The other alternative is to use the formula editor in Open Office.  While it is not as elegant as LaTeX, it can do most formulas relatively well.  (A final alternative would be to use PowerPoint with the additional program "Mathtype").

In general, I agree with the post above, PowerPoint is still significantly easier and more elegant than Open Office's Impress software.

Hope that helps!

---

### Post by radioboy on 2010-11-04
A better option than cutting and pasting from a pdf to an Open/Libre-Office presentation, is to use something like Ekee or Laeqed, which are small LaTeX to image renderers, appropriate for equations:
[http://rlehy.free.fr/](http://rlehy.free.fr/)
[http://www.thrysoee.dk/laeqed/](http://www.thrysoee.dk/laeqed/)

You can also use the OOoLatex extension:
[http://ooolatex.sourceforge.net/old_release/main.html](http://ooolatex.sourceforge.net/old_release/main.html)

However, I still prefer typesetting slides with LaTeX, so I'd love better support of multimedia content with native applications, and hopefully a Beamer-compatible WYSIWYG editor.

We are nonetheless restricted by the pdf format. I have tried watching slides with embedded video/animations using Acrobat Reader in Linux, but it hasn't worked well, besides installing nspluginwrapper, which wreaks havoc on my system.
But well, that's just me, really.

Edit: the package movie15 for LaTeX has never worked for me.

---

### Post by radioboy on 2010-11-04
I was thinking that a LaTeX+Beamer to HTML5 viewer could be a solution, hopefully making visualisation more platform independent (assuming a compatible browser is present) and rich.

Check this:
[http://mathdl.maa.org/images/upload_library/55/steinertthrelkeld/canvas/canvas.html](http://mathdl.maa.org/images/upload_library/55/steinertthrelkeld/canvas/canvas.html)
[http://philip.html5.org/demos/mathml/svg.xhtml](http://philip.html5.org/demos/mathml/svg.xhtml)
[http://www.canvasdemos.com/](http://www.canvasdemos.com/)

This would make presentations even more awesome.
And if we add this...
[http://wiki.sagemath.org/interact](http://wiki.sagemath.org/interact)

---

### Post by Chronon on 2010-11-04
> **radioboy said:**
> A better option than cutting and pasting from a pdf to an Open/Libre-Office presentation, is to use something like Ekee or Laeqed, which are small LaTeX to image renderers, appropriate for equations:
[http://rlehy.free.fr/](http://rlehy.free.fr/)
[http://www.thrysoee.dk/laeqed/](http://www.thrysoee.dk/laeqed/)

You can also use the OOoLatex extension:
[http://ooolatex.sourceforge.net/old_release/main.html](http://ooolatex.sourceforge.net/old_release/main.html)

LatexDraw is another option.  It offers a bit more than just rendering equations as images but it can do that as well.

I have never played with movie15 but I found a useful page by someone I know here: [http://pages.uoregon.edu/noeckel/PDFmovie.html](http://pages.uoregon.edu/noeckel/PDFmovie.html)

It says that Linux acroread does not work but Okular (a KDE4 app) should.

---

### Post by luisito on 2010-11-04
It is true that Beamer is not the easiest to use presentation software. I personally voted that I wish there was a better alternative but I don't think there is.

By the way, I am a mathematician. I run the applied math seminar at my university and I go to conferences all the time. I would say that 90% of the people use Beamer and about 10% use PowerPoint. The rest is negligible in my world. To my taste, Beamer presentations are way better than PowerPoint. To a great extent that is because people who use PowerPoint tend to abuse on the special effects that only distract the audience and make everyone roll their eyes.

Let me point out that you can include animations and movies on Beamer. There are two ways to do it and they are well documented in Beamer's manual. It is not as easy as drag and drop, but the result is acceptable at the end. Look at this presentation (you need to open it with Adobe reader and go fullscreen): [http://math.uchicago.edu/~luis/preprints/comp-pres.pdf](http://math.uchicago.edu/~luis/preprints/comp-pres.pdf)

On the other hand, I don't know of a simple way to move text smoothly from one place to another. Technically everything is possible including javascript, but it is certainly not easy.

Hopefully some day there is going to be something better than Beamer, or Beamer will be improved. But I don't think there is any option now.

---

### Post by gunksta on 2010-11-05
Powerpoint is nothing more than a digital version of transparent slides. It is true, Powerpoint, Impress, etc. can do things that would be impossible with traditional slides like play movies, include blinking text, etc. But fundamentally, the structure of a Powerpoint presentation is exactly like the structure of a presentation made 25 years ago with pieces of clear plastic and an overhead projector.

Beamer is an even more literal progression of the old-fashioned slide idea. Because Beamer is based on LaTeX, it is arguably even more "slide" based than something like Powerpoint, since LaTeX is a type-setting instrument (albeit a very powerful one).

I'm not sure anyone can create a "better Powerpoint". Someone can implement something similar and it may or may not have a nicer UI (Keynote?) but a Powerpoint clone will still be based on the idea of slides. Unfortunately, slides tend to be boring and may or may not really explain the topic. They also encourage people to simply read crap off the over-head/slide. This is nice for people who are illiterate or have limited vision but tends to be excruciating for everyone else.

We need a fundamentally new paradigm for presentations. I rather like this one:
[INDENT][Hans Rosling blows your mind]("http://www.ted.com/talks/hans_rosling_shows_the_best_stats_you_ve_ever_seen.html")
[/INDENT]If you haven't seen the classic Ted Talk with Hans Rosling showing off global development data, you should go watch it right now. While not every presentation lends itself to this sort of dynamic presentation, I think it would be useful in many many situations. Hans also proves that you don't have to be a dynamic personality to deliver a dynamic presentation.

We need tools to enable this sort of presentation. The last thing I want is another Powerpoint+1 clone.

---

### Post by Warthaug on 2010-11-05
> **gunksta said:**
> Unfortunately, slides tend to be boring and may or may not really explain the topic. They also encourage people to simply read crap off the over-head/slide. This is nice for people who are illiterate or have limited vision but tends to be excruciating for everyone else.
I think you are placing the blame in the wrong direction.  A well prepared, good speaker can make any presentation interesting - regardless of what tools are used.  The opposite is also true.  Powerpoint is simply a tool - you can use it well, or poorly, but in either case its the user, not the tool, which is the good/bad part of the issue. 

Powerpoint remains my tool of choice as its animatableness is far superior to the alternate choices, and it handles media fairly well.  Open Office present sucks - animation abilities are minimal, support for media like videos is pretty much non-existent (the last time I used it, it had the controls for videos, but couldn't actually play them!).

> **gunksta said:**
> We need a fundamentally new paradigm for presentations. I rather like this one:
[INDENT][Hans Rosling blows your mind]("http://www.ted.com/talks/hans_rosling_shows_the_best_stats_you_ve_ever_seen.html")
Nothing new there - he just has animated slides which he is well rehearsed in interacting with.  Like I said above - powerpoint isn't the problem, its the way people use it.  Rosling is interacting with his slides; but they are still nothing more than animated powerpoint  (or some other program) slides.

I use animations in most of my presentations, to breakdown complex processes/math*, and to try and spice up my talk.  I think it works - at least the feedback I get suggests it does.

*in my field (cell biology) complex math for most people is anything beyond SD, SEM and means/medians...

Bryan

EDIT: found it - a good video on making your powerpoints better.  Generally, good advice:
[http://www.youtube.com/watch?v=d04w4vvByDI&feature=player_embedded](http://www.youtube.com/watch?v=d04w4vvByDI&feature=player_embedded)

---

### Post by gunksta on 2010-11-05
@Warthaug
I'm not trying to say that slides are necessarily bad, I just think we should and could do better. Rather than find yet another way to shoe-horn modern style computing into a slide-show, I'd rather use something that inherently works in a dynamic, graphical manner.

Regarding his presentation. It was of course rehearsed and prepped. Any good presentation will be. But, if you watch him in this and in other videos you will see that he is not using slides. He is using a series of pre-defined programs, which create the animations he wants, during the presentation. He is actually controlling the output as it happens.(according to some pre-defined units/methods)

That's what I like about it. I would like to see something more generic, which allows the user to have complete control over a segment of the presentation. When appropriate, allowing the presenter to interact with the system, live. Current presentation tools allow you to pre-record everything but they aren't as effective if you want to deliver a more flexible presentation.

---

### Post by gunksta on 2010-11-11
While perusing the web on my lunch break, I stumbled onto this yesterday. It is, interesting. From a logic/organizational standpoint, it is still very much slide based, but I really do like the fact that it runs in the browser.
[INDENT][_S5_]("http://meyerweb.com/eric/tools/s5/")  

[/INDENT]Pros:

[LIST]
[*]Minimal software requirement because it runs on any modern browser.
[*]Can embed web-content (locally or actually on the web)
[*]Can use Javascript to create animations, etc.
[/LIST]
In essence your presentation becomes a web-site. You could, for example, enable non-linear logic into your presentation through links and allow your audience to decide what you will focus on (By linking to separate S5 presentations) without needing to interact with the actual filesystem directly. You can use javascript to create any kind of graph or animation that you can think of / develop.

Cons:

[LIST]
[*]Steep learning curve - This is more attractive to programmers than to non-programmers.
[*]No compatibility with existing Powepoint slides, etc.
[*]Limited options for themes, unless you want to/can roll your own.
[*]No GUI (see first con)
[*]Still based on the logic of slides
[/LIST]

---

### Post by PC_load_letter on 2010-11-11
I did this once and it seems to work, the end result is closer (even better IMHO) to what you get from OSX Keynote. 
1- Write and compile your beamer presentation, output in pdf.

2- Use the command 'convert' from the terminal to change the presentation into a collection of high quality PNG or JPEG slides. 

3- One by one (the only tedious part of this), embed each slide in OOo Impress, then save the presentation in the OOo presentation format.

4- Now you have total control to animate any parts of a slide, and with countless transitions effects. Still you need Impress to do the presentation.

**Or:**
Download this neat little program called "Impressive" and use it to run your beamer presentation. "Impressive" has a few nice transitional effects that you could use to make the beamer presentation less boring. 

**EDIT: **Here is a link to the man page: 
[http://manpages.ubuntu.com/manpages/lucid/man1/impressive.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/impressive.1.html)

**Or:** 
Just read about this yesterday, here: 
[http://www.omgubuntu.co.uk/2010/11/ease-clutter-presentation-app-linux-ubuntu/](http://www.omgubuntu.co.uk/2010/11/ease-clutter-presentation-app-linux-ubuntu/)

It's still a beta but it looks very promising.

---

### Post by perroazul on 2010-11-12
you can actually embed a movie in a beamer presentation. the code for doing that is below
```
\usepackage{multimedia}
\begin{document}
 \movie[width=6cm, height=6cm, poster]{}{animation.avi}

```
now, that will only work with acrobat reader. Since I prefer using ubuntu's default pdf viewer, I instead opt for using this code
```
\href{run:animation.avi}{\beamergotobutton{My movie}}

```
which does not require any extra package. That will create a clickable button that will open your movie file. After I discuss the movie, I go back to the full screen presentation.

---

### Post by gunksta on 2010-11-12
That is a good trick. Thanks for sharing.

---

### Post by Chronon on 2010-11-13
> **perroazul said:**
> you can actually embed a movie in a beamer presentation. the code for doing that is below
```
\usepackage{multimedia}
\begin{document}
 \movie[width=6cm, height=6cm, poster]{}{animation.avi}

```
now, that will only work with acrobat reader. Since I prefer using ubuntu's default pdf viewer, I instead opt for using this code
```
\href{run:animation.avi}{\beamergotobutton{My movie}}

```
which does not require any extra package. That will create a clickable button that will open your movie file. After I discuss the movie, I go back to the full screen presentation.

Thank you!

---

