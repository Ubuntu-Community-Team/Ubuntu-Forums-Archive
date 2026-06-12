---
title: "Enlightenment: probably themost silly problem ever..."
date: 2009-11-11
forum: Desktop Environments
---

### Post by Tickborn on 2009-11-11
HI,
I was interested in having a  look to e17, so i installed it form repository.
Everything worked fine. I set it up in the scalable version, log in it and start to enjoy.
But the fonts were definitly to small and i started to play with  the scalabel menu. Unfortunately  i clicked on the ok button by accident when my scale was set to a huge ratio. Result: fonts are so big that i visualize only minimal part of the menu, and therefore i'm unable to reselect the options and change it back.:(
No problem, i thought. I unistall e17  from synaptic , reinstall, re-open.. and there are my fonts in huge dimension again!
I kept trying to  uninstall whatever seems related to e17, but eventually i miss something.
Can anybody tell me how to do completely get rid of e17 before reinstalling? or how to reset the fonts?

Thanx!

---

### Post by earthpigg on 2009-11-11
hi!

you like synaptic, so we will go with a method using synaptic to solve your problem.

you are on the right track.

try again, but right click and select 'completely remove'. this will remove your personal config settings, as well as the software itself.

there is another "more correct" geektastic method involving dotfiles and whatnot, but the solution you where driving towards works just as well.

---

### Post by Tickborn on 2009-11-12
Hi,
Thanx for your answer and advice.
I thought i did check on remove completely, but i went through the procedure again. Keeping inmind what you said, when Synaptic asked if i want to remove also the configuration files, i clicked on Details, to find out  that some of the libreries were not going to be removed with  config. So i  look for them manually in Synaptic and reselect. Finallyi removed everything. Re-install E17.. and again everything in huge scale!:o
What do i miss?
Would you be so kind to explainme also how to do it without Synaptic? Maybe that will work better, and for sure is soemthing i would like to learn.
Thanx again!

---

### Post by earthpigg on 2009-11-12
ok, lets try it super nerd way instead:
```

rm -r ~/.e16
```

log out, and back in

---

### Post by VCoolio on 2009-11-12
The above post is almost correct; just delete the config in ~/.e (perhaps even find the right file for your wrong settings). Login again and the folder will be recreated with default settings.
This shouldn't be necessary though, but it is the fastest way, except if you have a lot of customized settings that are going to be lost. But I don't really understand what problem we're talking about, so I can't come up with another solution.

---

### Post by Tickborn on 2009-11-14
> **earthpigg said:**
> ok, lets try it super nerd way instead:
```

rm -r ~/.e16
```log out, and back in

Uhm... i try, changing e16 to e17 (that is what i installed) but seems like it does not exist
](*,)
I also try to check through Synaptic witch dependences hadthe package e17. I went directory by directory with Nautilus and delete them all.. reinstall e17.. and.. guess.. :( :( :(

Finally i looked for .e, found it, and within it the scalable config files... And now i'm finally writing to you from a working Enlightenment desktop :)

Thank everybody for the help!

---

