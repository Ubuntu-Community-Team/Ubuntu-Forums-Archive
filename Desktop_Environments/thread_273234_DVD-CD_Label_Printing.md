---
title: "DVD-CD Label Printing"
date: 2006-10-07
forum: Desktop Environments
---

### Post by GuiGuy on 2006-10-07
OK, after a couple of days I finally have the Canon PIXMA ip3000 working. :)  Now, what software are people using to design & print on DVDs?

Thanks

---

### Post by manny0 on 2006-11-22
yea i would also like to know what software people are using. in windows i just used neros built in software k3b doesnt seem to have this feature.

---

### Post by IanW on 2006-11-23
I can't remember where I got it, but there's a GIMP CD template out there somewhere. (Google is your friend!)

---

### Post by linuxwizard on 2006-11-23
Hi 
I use Kover,Koverartist,glabel,hope this will help.

---

### Post by Georges on 2006-12-31
I just apt-get install koverartist
and it installed 0.3.2-0ubuntu1

no dependecies signalled so I suppose I have all needed KDE stuff on my system already (running gnome as standard)

Well, the "case" drop down menu has no choices. it's simply empty. So I cannot create a DVD cover, only CD covers.
Anyone noticed this? What could be the reason?

---

### Post by GuiGuy on 2006-12-31
> **Georges said:**
> I just apt-get install koverartist
and it installed 0.3.2-0ubuntu1


Thanks. I have that but was hoping for something a little more sophisticated so I can use the CD/ DVD printing tray on Canon ink-jet printers. 

I settled on Openoffice as I was able to set up a template for the disc tray in it. It's a bit clunky but it works.

regards

---

### Post by Georges on 2007-01-01
> **GuiGuy said:**
> Thanks. I have that but was hoping for something a little more sophisticated so I can use the CD/ DVD printing tray on Canon ink-jet printers. 

That's not a cover, that's a label. And so I use glabel for that.

There is currently no program combining both labels and covers.

And glabel cannot write text on curves. Can openoffice do that? It may be a reason for me to abandon glabel and use openoffice as well.

---

### Post by GuiGuy on 2007-01-01
> **Georges said:**
> That's not a cover, that's a label. 

That's pedantics ;) 

> Can openoffice do that? It may be a reason for me to abandon glabel and use openoffice as well.

Seriously though, yes, OOo can- use FONTWORKS - in a drawing insert a text box (FRAME). Select the box and RIGHT CLICK > PROPERTIES and then select FONTWORKS. A dialog pops up and gives a number of options. (NB In a document insert a FONTWORKS object)

I use the [TURBOPRINT]("http://www.turboprint.de/english.html") driver for the Canon printer. In the document setup you can choose a page size that reflects the CD tray. There is a bit of mucking about getting the disk circle in the right position, but once that's done and the document saved as a template the rest is easy.


regards

---

### Post by lingenfr on 2007-05-13
I tried to compile the latest koverartist, but no joy. configure complains about missing qt headers and libraries. I installed q4-core, dev and dev-tools. Don't know what else to do. Anyone?

---

