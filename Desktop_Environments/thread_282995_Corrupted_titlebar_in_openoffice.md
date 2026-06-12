---
title: "Corrupted titlebar in openoffice"
date: 2006-10-23
forum: Desktop Environments
---

### Post by mithion on 2006-10-23
I'm not sure if this is the appropriate category to post this but here goes.  In Xubuntu, the titlebar of openoffice looks all corrupted. It was like this in Xubuntu 6.06 which used openoffice 2.0.3. I recently upgraded to Xubuntu 6.10 which now uses openoffice 2.0.4. The same graphical problem arises. As far as I'm concerned, openoffice is the only program I have encountered in Xubuntu which has this problem. I'm not sure if this is a hardware or software problem.  Since all other windows display their titlebar correctly, I would assume it's something wrong with openoffice and thus it is software based.  It is not an ultra debilitating bug since it's still workable, but it would be nice if the titlebar looked normal. Anybody know how to fix this?  I've attached a screenshot to show you what's wrong.  As you can notice, openoffice looks corrupted while firefox looks fine.

---

### Post by theadventuresofanidealist on 2006-10-29
i have exactly the same problem. how does one fix it?

---

### Post by musper on 2006-11-10
Huh, one more with exactly the same problem.
Could it eventually be hardware problem? The machine I'm working on has an old S3Trio* 8MegAGP...Those cards aren't good enough even under their "native" winX drivers, in my experience...If I have time, I'll stick an old nVidia MX in that box, and report what I've learnd from that...

---

### Post by mithion on 2006-11-10
I would bet 100$ it's software related.  I'm 90% sure (it's a computer at my work so I have no way to certify this at this moment) the graphics card is an 8mb S3Trio on the computer with the problem.  But the reason I say it's software is that I recently decided to try out ubuntu instead of xubuntu, and open office no longer has this problem.  There is some fundamental problem with the graphical engine in xubuntu.  It is trully puzzling though since open office is the only program with this problem.  I haven't encountered any other program yet which has titlebar display problems.  I've been looking around a lot, and haven't found a solution yet.  This is probably due to the increasing rarity of computers using these cards.  Anyhow, xubuntu has failed to impress me.  I think the gnome guys are doing a fine job of cleaning and optimizing their code.  I haven't noticed a performance hit when switching to ubuntu versus using XFCE.  If you are annoyed with the open office bug, I recomend giving gnome a spin.  It's really more functional if you ask me.

---

### Post by shaulreznik on 2006-11-11
Uninstall OoO 2.0.4 and install a new snapshot ([http://download.openoffice.org/680/index.html](http://download.openoffice.org/680/index.html)) following these instructions:
[http://www.ubuntuforums.org/showpost.php?p=1617513&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1617513&postcount=2). After the installation create a launcher to /opt/ooo-dev2.1/program/swriter.

---

### Post by jeeves on 2007-03-30
I had the same problem with OpenOffice 2.2 in the Xubuntu Feisty Beta version running on old pc with an Intel 82810 graphic controller. 

Reinstalling did not seem to help. [B]I finally got if fixed by editing my /etc/X11/xorg.conf and changing the "DefaultDepth" from "24" to "16"
[/B]
I also installed the openoffice.org-gtk package, but that alone did  not fix things.

---

### Post by mithion on 2007-03-31
> I had the same problem with OpenOffice 2.2 in the Xubuntu Feisty Beta version running on old pc with an Intel 82810 graphic controller. 

Reinstalling did not seem to help. I finally got if fixed by editing my /etc/X11/xorg.conf and changing the "DefaultDepth" from "24" to "16"

I also installed the openoffice.org-gtk package, but that alone did not fix things.

I'm sorry.  I switched the computer in question to regular ubuntu.  I cannot test your fix of changing the color depth.  But that would sound like a clever thing to try.  I do invite anyone else with the problem to test the fix and post their results.  Thanks for your input.

---

### Post by joris1977 on 2007-04-03
Installing the openoffice.org-gtk package solved the problem for me. I have no idea why. 
Synaptic also installed openoffice.org-style-industrial, so it is possible this did the trick.

anyway thx mithion for pointing me to this solution (although it didn´t work for you ;) )

---

### Post by TravMan63 on 2007-06-06
Almost a quote...

 had the same problem with OpenOffice 2.2 in the Xubuntu Feisty 7.04 version running on old pc with an Intel 82810 **(E)** graphic controller.

Reinstalling **(impress)** did not seem to help. I finally got if fixed by editing my /etc/X11/xorg.conf and changing the "DefaultDepth" from "24" to "16"

I also installed the openoffice.org-gtk package, but that alone did not fix things.

Worked for me as well...

---

