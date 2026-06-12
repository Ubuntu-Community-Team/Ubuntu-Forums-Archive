---
title: "Fonts are messed up in KDE but OK in Gnome"
date: 2007-03-20
forum: Desktop Environments
---

### Post by bubblenut on 2007-03-20
I installed Ubuntu yesterday and today added KDE as I am primarily a KDE user. The problem I am having is that fonts are really messed up in KDE (see attached screenshot). 
I have tried changing the font to one which I know should work well from previous experience, Bitstream Vera Sans. I have also tried messing around with the anti-aliasing and dpi settings to no avail. I have restarted KDE after many of the changes as well.
My current settings are as follows:
Font: Bitstream Vera Sans (+ Mono for fixed with)
Anti-Aliasing:
  Exclude range: 8.0pt - 15.0pt
  Sub-pixel hinting: RGB
  Hinting style: Medium

Has anyone else come across this problem? What should I do to fix it?

---

### Post by Pikestaff on 2007-04-05
I have the same problem on my laptop, although I use Kubuntu and don't have Gnome installed currently.  But the fonts look just like that...

Has anyone found a fix for this?

---

### Post by iamhugeinjapan on 2007-04-05
KDE has a section in the Control Panel for controlling how GTK apps look. Have you tried tinkering with that? From memory Firefox is controlled by that section too.

---

### Post by skywatcher on 2007-04-17
Hi

My turn to ask if anyone has found a fix for this problem? I'm having the same problem with Kile on my laptop.

---

### Post by gerard67 on 2007-09-12
Althoug there should be some config file hidden somewhere to do this directly, I solve this problem by installing kcontrol and its dependencies,
then launch kcontrol -> appearance -> fonts, and set DPI settings to 96.. apply and try to start Kile again .. if its OK, you can remove Kcontrol and Co.

Mathieu Petit

---

