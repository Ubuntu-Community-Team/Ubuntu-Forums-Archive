---
title: "Circuit Schematic CAD Program"
date: 2008-12-08
forum: Education &amp; Science
---

### Post by fissionmailed on 2008-12-08
I'm looking for a free/opensource/etc program to draw some circuit(ADDs, NORs etc).  Does any one know of some good programs for this? I use xilinx at college but I don't want to spend 800-5000 dollars for a license to use at home. Plus I just need something to draw circuits, xilinx would be over kill anyway.  I could log into a remote desktop at college but the internet here reeks and it's really slow. 

Thanks in advance.

---

### Post by mike919 on 2008-12-12
Hey fissionmailed,

Eagle is a great circuit shematic / layout editor, and there is a linux version.  A free edition is available with some restrictions (only one schematic page per project and max 3"x4" board size), but if you're only using it for schematics it should fit your needs nicely.  It's available from cadsoft ([http://www.cadsoft.de/](http://www.cadsoft.de/)).

Mike

---

### Post by Keen101 on 2008-12-17
I second that for eagle cad, but really only if you are going to make PCB's too. It's not open souce, but had a free edition.

I would really recommend trying out DIA. It should be in the repos, and is open source. It's comparable to Altium designer i suppose, but on a cheaper scale. Should do what you need though.

[http://live.gnome.org/Dia](http://live.gnome.org/Dia)
[http://live.gnome.org/Dia/Screenshots](http://live.gnome.org/Dia/Screenshots)

the screenshots don't show the resistors and the diodes and stuff, but it has them.

---

### Post by fissionmailed on 2009-01-11
> **mike919 said:**
> Hey fissionmailed,

Eagle is a great circuit shematic / layout editor, and there is a linux version.  A free edition is available with some restrictions (only one schematic page per project and max 3"x4" board size), but if you're only using it for schematics it should fit your needs nicely.  It's available from cadsoft ([http://www.cadsoft.de/](http://www.cadsoft.de/)).

Mike

Thanks, I'll look into that!

> **Keen101 said:**
> I second that for eagle cad, but really only if you are going to make PCB's too. It's not open souce, but had a free edition.

I would really recommend trying out DIA. It should be in the repos, and is open source. It's comparable to Altium designer i suppose, but on a cheaper scale. Should do what you need though.

[http://live.gnome.org/Dia](http://live.gnome.org/Dia)
[http://live.gnome.org/Dia/Screenshots](http://live.gnome.org/Dia/Screenshots)

the screenshots don't show the resistors and the diodes and stuff, but it has them.

I actually have Dia installed.  I need to figure out how to access the resistors and all.  I wonder if they have logic gates in there too.

---

### Post by edgranholm on 2009-02-22
I'm having problems installing the newest version of Eagle.  I downloaded the .run file from their site, but can't (don't really know how) to get it to install.  I tried double clicking on it, but nothing happened.  I've already got version 4.16 installed.  I did that through the add/remove applications thing.  Can someone help me get this thing installed please?

---

### Post by hsweet on 2009-02-23
I've started using Qucs with my high school electronics class.  Simple, seems to work.
[http://qucs.sourceforge.net/screenshots.html](http://qucs.sourceforge.net/screenshots.html)

---

### Post by mike919 on 2009-02-26
edgranholm,

I just tried this myself to update to the newest version.  After you download the .run file, right click on it and click on properties.  In the permissions tab you need to check 'Allow executing file as program'.

You should be able to run by double clicking the file then clicking run at the prompt.  Or if you prefer command line, cd to the directory then 'sh eagle-lin-5.4.0.run'.  From then on its a graphical installer and pretty self explanatory.

If you want to create your own application launcher you can link it to the 'eagle' executable file in the bin folder.

Hope this helps!

Mike

---

### Post by edgranholm on 2009-03-02
Thanks for the help...  Someone else suggest I do that, so I got it to work now.  Thanks again!

---

### Post by jerrrys on 2009-03-02
has anyone ever tried:

[http://www.lis.inpg.fr/realise_au_lis/kicad/](http://www.lis.inpg.fr/realise_au_lis/kicad/)

??

---

### Post by sERAPHIM_newbie_at_linux on 2009-03-03
Thanks Keen101

Only just installed Dia, but it looks good so far. Not actually using it myself - my  brother-in-law wants to make a mechanical schem/physical drawing about some pneumatic car system or something :P

---

### Post by cb951303 on 2009-03-03
geda suite has a schematics editor.
if you only need to do schematics I recommend it over eagle because it's free. but if you also need to make PCB you just can't beat eagle.

---

### Post by kwacka on 2009-03-28
Also check out PCB & Oregano - they're both in repositories.

If you want simulation, Gspiceui is a frontend for some of the geda programs e.g. geda-gschem

---

### Post by neoflight on 2009-03-28
> **kwacka said:**
> Also check out PCB & Oregano - they're both in repositories.

If you want simulation, Gspiceui is a frontend for some of the geda programs e.g. geda-gschem

Good thread so far. Check our site too (in sig). there are some links there which might help.

---

### Post by ad_267 on 2009-03-29
[KiCAD]("http://en.wikipedia.org/wiki/Kicad")

---

