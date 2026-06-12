---
title: "Why does OpenOffice 3.1 look like this? (8.10)"
date: 2009-05-11
forum: General Help
---

### Post by Minipalmer on 2009-05-11
Hey there,

Was a 9.04 user, my card was blacklisted and I switched back to 8.10.

I got a little giddy and starting vamping up 8.10 with several 9.04 goodies, OOo 3.1 being one of them.

I've installed it three different ways, every time it looks just like this, not fitting my theme at all. What gives?

*EDIT: Is there anyway to just revert back to 2.4? 3.1 just look ugly all around, fonts and everything.

Here's what it's looking like:

[http://i42.tinypic.com/33fc8sj.png](http://i42.tinypic.com/33fc8sj.png)

---

### Post by pytheas22 on 2009-05-12
Which repository did you add to get OO 3.1 in Ubuntu 8.10?  Whoever built the packages probably just didn't customize them to mesh with the Ubuntu theme, as the ones in the official Ubuntu repository are, which is why OO 3.1 looks the way it does on your computer.  It's also possible that the problem results from the theme you're using--if you switch back to the default Ubuntu theme, does OO look normal?

You would probably have better luck (with both looks and performance) if you installed OO using an Ubuntu-specific repository, like the one used in [these instructions]("http://chrisjohnston.org/2008/how-to-install-openoffice-30-on-ubuntu-810-intrepid-ibex").

That said, if you really want to go back to OO 2.4, go to System>Administration>Software Sources, click on the 'Thirty-Party Software' tab, and remove the repositories you added for OO 3.  Then update your system and the OO 2.4 packages should be reinstalled; if not, try removing and reinstalling OO.

---

### Post by tjwoosta on 2009-05-12
From the picture it looks like OO is using the QT interface instead of the GTK interface. Try to start it with this command and see if it helps.

```
OOO_FORCE_DESKTOP=gnome soffice

```

or for the writer specifically you can use this command

```
OOO_FORCE_DESKTOP=gnome soffice -writer
```

---

### Post by Minipalmer on 2009-05-12
Thanks or the replies fellas.

@ pytheas22: I actually installed it through the specific repository twice, and both times it looked this bad. So then I did it through synaptic.

@ tjwoosta: From the first code you listed, it did bring up a new splash for Open Office I hadn't seen yet. But the theme still looks like trash, haha.

It's strange, because I have done complete removals and reinstalls several times, and it always ends up like this.

---

### Post by ezsit on 2009-05-12
I did a custom, command line install of Ubuntu 8.10 and added everything I wanted. I then went to openoffice.org and downloaded the tarball containing the DEBs and installed OpenOffice 3.1 that way, directly from openoffice.org and it looks fine. I am using XFCE and installed a bunch of Gnome and KDE apps, so some programs do not look like they belong, but I have all the functionality I need. My point is that if you can get over the slight differences in widget styles, you can have all the programs you want and all the functions you need.

Also, try installing directly from openoffice.org and see what you get. It might just work out fine.

---

### Post by Minipalmer on 2009-05-12
Thanks ezsit.

Though, the people who wrote the tutorials I used had it worked out just fine. But I will try this later.

I'm not overly concerned about matching themes or anything. OOo has never matched anything anyway. This is just a little too terrible for me, haha.

---

### Post by Benzjaminz on 2009-05-21
Hi Minipalmer

I had exactly the same prob as you on jaunty. Upgraded to 3.1 and got that horrible theme then downgraded to office 3.0.1 and was still stuck with the horrible theme. 

The thing which seemed to fix it for me was to add openoffice.org-gtk in synaptic package manager. The theme went right back to normal ubuntu. Hope this helps you.

---

### Post by Minipalmer on 2009-05-21
You, sir, are a gentleman and a scholar. Worked like a charm.

---

### Post by Kareeser on 2009-05-21
Good to see this solved.

Does openoffice.org-gtk work with the non-Ubuntu version downloaded from the OpenOffice.org website?

---

### Post by fig_wright on 2009-07-16
Genius! That was driving me mad...  :popcorn:

---

### Post by zevans on 2009-07-17
Is there, or are there plans for, an openoffice-kde? So it looks right in Kubuntu?

---

### Post by jmszr on 2009-07-17
zevans,

There is an openoffice.org-kde in the Synaptic Package Manager. I would think that Adept would also have it.

---

