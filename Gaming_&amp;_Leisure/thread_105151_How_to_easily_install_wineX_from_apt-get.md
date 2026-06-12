---
title: "How to easily install wineX from apt-get ?"
date: 2005-12-17
forum: Gaming &amp; Leisure
---

### Post by patrick295767 on 2005-12-17
How to easily install wineX from apt-get ?
(for newbies)
Could it be possible to make repositories ??

thank you !!

pat

---

### Post by vininim on 2005-12-17
WineX is a commercial 'version' of Wine , wich means you have to pay a subscription service to have access to it. Its name is now Cedega, and you could have more info on how to do that in their site.

---

### Post by Toxicity on 2005-12-17
I would recommend installing wine

(I think I may be missing something but it should work... heh?)
Install things in this order:
Xdialog
Wine
winetools

just run a search with synaptic after getting your repositories sorted out.

once all of thats going, if/when you get to that point, type wt2 in command line. This will launch a graphical program for getting wine up and going. Once you have your fake windows system installed, and have run through whats listed for base (or whatever else you happen to need.) you can assign exes to automaticall run through wine by right clicking on an exe selecting run with other application, or the like. In the custom prompt type wine and then ok. Now all Exes are routed through wine.

(yea, yea, I'm very vague here but I figured it out alone so with my crappy instruction you should do better than my first few times heh)

and if your actually willing to pay for Cedega (WineX) Then completely ignore everything I just said I guess as I'm not sure how much different it really is.

---

### Post by CDN MILLWRIGHT32 on 2005-12-18
Toxicity!
I am getting a message " This software depends on dcom98.exe" it is not installed yet.
How do I do this, or do i need it? Also should I install all the files listed in the windows system software list?

---

### Post by CDN MILLWRIGHT32 on 2005-12-18
never mind, got it.

---

### Post by Burgundavia on 2005-12-18
It is unlikely WineX/Cedega will be packaged for Ubuntu/Debian. The last time somebody tried, the Transgaming people threatened to pull the cvs access.

That being said, the new vanilla wine stuff is very good, not quite there but comign along. And of course, completely free.

Corey

---

### Post by leech on 2005-12-19
Actually in a lot of cases, Wine will run something much better than Cedega.  Cedega is good for Direct3D only games and ones that are directly supported by it.  Usually games that aren't directly supported by Transgaming have lots of issues, if they work at all.  

For a good example, I tried grand theft auto 1 and 2 with Cedega.  The first one worked, the second one would play the videos, and then crash to the desktop.  With normal Wine, both of them worked (though I never got sound working in the first one, with cedega or wine)

Leech

---

### Post by lysis on 2005-12-20
[QUOTE=Toxicity]I would recommend installing wine

(I think I may be missing something but it should work... heh?)
Install things in this order:
Xdialog
Wine
winetools

just run a search with synaptic after getting your repositories sorted out.

once all of thats going, if/when you get to that point, type wt2 in command line. This will launch a graphical program for getting wine up and going. Once you have your fake windows system installed, and have run through whats listed for base (or whatever else you happen to need.) you can assign exes to automaticall run through wine by right clicking on an exe selecting run with other application, or the like. In the custom prompt type wine and then ok. Now all Exes are routed through wine.

(yea, yea, I'm very vague here but I figured it out alone so with my crappy instruction you should do better than my first few times heh)

and if your actually willing to pay for Cedega (WineX) Then completely ignore everything I just said I guess as I'm not sure how much different it really is.[/QUOTE]

I can't find Xdialog.  i did apt-get install Xdialog.  where is this?

---

### Post by lysis on 2005-12-20
ahh nm; i forgot it's case sensitive . . . i did xdialog and it worked fine.

---

