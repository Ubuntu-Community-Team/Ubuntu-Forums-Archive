---
title: "Firefox 3 won't open"
date: 2009-03-05
forum: General Help
---

### Post by larryp on 2009-03-05
New to ubuntu--had it installed(by someone else) on a dell that previously ran Windows Millenium.

Have upgraded to Hardy Heron(and Firefox 3). FF worked okay for a while, but now whenever it is opened, the page never finishes loading. Trying to close the window eventually brings up the force quit option, which shuts it down.

Other web browsers still work. I even managed to download FF2 and it works(although it looks different than before). 

Might be an issue with a flash player, as youtube wouldn't work and I tried downloading some things, and I could have too many and from the wrong places.

Any help would be greatly appreciated. Please be patient with me--I'm just starting to find my way around and directions that include all the steps from the desktop would be helpful

Thanks!

---

### Post by Rallg on 2009-03-05
One possibility is that a program (or programs) that emulate Flash are installed, and are in conflict with the real Flash.

There is also a big difference between how this is handled on 32-bit and 64-bit systems. If you have a 64-bit system (meaning that you have the 64-bit version of Ubuntu installed, regardless of processor) then disregard what I write here:

Use the menu System > Administration > Synaptic Package Manager to un-install "gnash" if you have it. It might also un-install some related programs. Then see if flashplugin-nonfree is installed. if not, install it.

Then try Firefox. Did that help?

If not, you might consider completely uninstalling both FF2 and FF3, and flashplugin-nonfree. If you really want to be thorough, you can follow by manually removing a variety of hidden folders located here and there in your system. However, let's first see what happens without doing that.

Then re-install only FF3, and flashplugin-nonfree. Launch FF3, and Edit > Preferences > Applications, ensuring that the media types normally associated with Flash are indeed assigned to Flash, rather than to Movie Player, Totem, or something else.

Did that help?

---

### Post by jerrrys on 2009-03-05
flash player can be an issue..might get lucky..just reload..an alt..check out miro.. [http://www.getmiro.com/](http://www.getmiro.com/)

---

### Post by larryp on 2009-03-05
Not sure if I have a 32-bit or 64-bit system. How does one find out? 

I will try removing the gnash components and then install the flashplugin-nonfree...

when I get home....I'll let you know...

thanks

---

### Post by larryp on 2009-03-06
Okay, I uninstalled all gnash programs. Then installed flashplugin-nonfree. Logged out, back in, opened FF3--

and the computer crashed. Tried again--FF3 started opening 2 tabs, finished loading the page, but soon became unresponsive. Closed the window(force quit), opened FF3 again and FF3 started opening 2 tabs again but was unable to finish loading the pages and I had to force quit again.

Tried option 2-- completely uninstalled FF3, FF2, and flashplugin-nonfree. Logged out, logged back in, reinstalled FF3 and flashplugin-nonfree. Opened FF3 and

same problem--page wouldn't finish loading, tried to open 2 tabs at once.

What should I try next?

Thanks

---

### Post by larryp on 2009-03-07
Anyone have any more ideas for this problem?

---

