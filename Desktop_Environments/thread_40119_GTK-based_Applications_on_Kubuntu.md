---
title: "GTK-based Applications on Kubuntu"
date: 2005-06-07
forum: Desktop Environments
---

### Post by Zunino on 2005-06-07
Hello.

I have recently switched to Kubuntu and I must say I have never been so pleased by any other Linux distro I have tried. Apart from a few, really annoying issues (e.g. the irritating window placement algorithm and the infamous cedilla mapping for US keyboards), I have managed to arrange things to my taste.

This post is about one such issue. It concerns the appearance of Gnome/GTK-based applications on Kubuntu. Basically, what happens is that, upon starting Kubuntu, any GTK-based application looks terrible (to my taste), with huge fonts and widgets that are not in accordance to my settings. I have found that, by running *gnome-theme-manager*, the problem is corrected and the applications show the fonts as I wish. However, upon starting a new Kubuntu session, the issue is there again.

I have prepared a web page [1] in order to better illustrate the problem. I hope to get some helpful advice on this.

[1] [http://zunino.eti.br/kubuntu/](http://zunino.eti.br/kubuntu/)

Thank you very much.

-- 
Ney André de Mello Zunino

---

### Post by SGC on 2005-06-07
Did you try using gtk2-engines-gtk-qt,  it uses kde theme and font for gtk applications.

See a before and after screenshots for synaptic (gtk-based):

---

### Post by André on 2005-06-08
If gtk-qt doesn't work probably for you (it doesn't for me) than i suggest installing a nice theme for the gtk2 apps like clearlooks. This one integrates pretty well with plastik (just my opinion :-)).

Greetings
André

/edit:
When you installed the gtk-qt theme you can change the default theme for gtk apps in the control center. Nice thingy: You can set fonts and theme. You can also choose to use the KDE stuff but that doesn't work too well for me.

---

### Post by sinbad782 on 2005-06-09
For OpenOffice.org try installing the openoffice.org-kde or openoffice.org2-kde packages. 

Also, for apps like update-manager that run with root privileges you may need to copy your ~/.gtkrc file into /root in order to get the same effect as for apps that run with regular user privileges. 

This is what I do, and seems to work pretty well, but if anyone else has a better way of doing this then please post.

---

