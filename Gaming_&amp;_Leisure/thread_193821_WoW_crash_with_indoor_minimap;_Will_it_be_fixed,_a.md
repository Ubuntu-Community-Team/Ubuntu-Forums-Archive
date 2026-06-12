---
title: "WoW crash with indoor minimap; Will it be fixed, and what can I do now?"
date: 2006-06-10
forum: Gaming &amp; Leisure
---

### Post by Brighid on 2006-06-10
Hi everyone,

I recently started WoW with Wine under Kubuntu 6.06, using the .deb package found in the Wiki (big thanks to the creator of the package!).  The framerate isn't as good as Windows, but it's tolerable.  I'm probably going to lower my settings some, anyway.

But my problem isn't with the framerate.  From what I can so far tell, WoW runs flawlessly, save for one thing that I think most of the community's become familiar with.  When I go indoors with the minimap open, the game crashes.  In the previous Wine version, it acted differently and instead of crashing just caused extreme screen tearing, that I could fix by closing the minimap and toggling Vertical Sync.  But now that I have no workaround, I need to figure out how to be able to go indoors!

I had heard of a mod that turns the minimap off by default, so you can log in not having to worry about whether you're indoors or not.  Does anyone know where to find that?  I can't seem to locate it.

To be honest, though, even *with* that mod, I'm not sure I'm ready to play WoW strictly in Linux.  I rely on the minimap rather consistently, and I don't want to have to limit myself so much, when it's possible to avoid doing so by simply booting into Windows.

I know that, in the past, things like mouse targeting and visible target circles were problems for WoW Linux players, but there have since been patches for Wine that fix these problems.  Is it unreasonable to believe that there may eventually be a patch that fixes this tearing (and now crashing) problem?  I would love to be able to stop using Windows .. at this point, WoW is pretty much all I use it for.

So, in summary:

1. **Does anyone know where to find the mod that disables the minimap on login by default?**

2. **Does anyone know if a patch to fix the crash caused by the minimap being on indoors is in the works, or will be?**

Thanks in advance to any who reply.  I was really excited to see that WoW ran so well under Linux; I look forward to the day when it runs without any problems!

Regards,
Bríghid

**Edit**: Instead of posting a new reply, I'm just going to edit this to make it more visible.  WoW no longer crashes since updating to Wine 0.9.16 (by compiling and patching myself, as instructed [here](http://appdb.winehq.org/appview.php?versionId=5109)).  I was even able to update WoW to patch 1.11.1 in Linux (though I did have to download the updater from FileFront, it wouldn't work with the normal method).  I'm still having problems with the game in Linux, but that's for another thread.

Thanks for the help, everyone.  Definitely a great community here.

---

### Post by eqisow on 2006-06-10
1. [http://www.curse-gaming.com/en/wow/addons-4147-1-minimap-autohide.html]("http://www.curse-gaming.com/en/wow/addons-4147-1-minimap-autohide.html")

2. I've never actually had the mini-map problem, so I don't know what to tell you. 0.9.15 just came out a couple of days ago. You could try that if you haven't yet. Check the [Wine wiki]("https://wiki.ubuntu.com/Wine") under the "Latest Wine with WoW Patch" section.

---

### Post by Runner on 2006-06-10
I had the mini map problem on one computer using a old geforce 4 card , it went away right after upgrading to a geforce 6600

---

### Post by Brighid on 2006-06-10
[QUOTE=eqisow]1. [http://www.curse-gaming.com/en/wow/addons-4147-1-minimap-autohide.html]("http://www.curse-gaming.com/en/wow/addons-4147-1-minimap-autohide.html")

2. I've never actually had the mini-map problem, so I don't know what to tell you. 0.9.15 just came out a couple of days ago. You could try that if you haven't yet. Check the [Wine wiki]("https://wiki.ubuntu.com/Wine") under the "Latest Wine with WoW Patch" section.[/QUOTE]

Unfortunately, 0.9.15 is the version I'm currently using. :(  I had heard about someone that used 0.9.6 to avoid the crash or tearing, but I'm unsure what patches were added in to the source of the .deb package on the Ubuntu Wiki.  Though I wonder if there's an old .deb package of 0.9.6 somewhere that's already patched?

As I mentioned above (though I wasn't sure of version numbers before):  In 0.9.14, the screen would tear, but in 0.9.15, the game just crashes.

Anyway, thank you for the link.  I will check it out.  It will at least make WoW playable for me again.

[QUOTE=Runner]I had the mini map problem on one computer using a old geforce 4 card , it went away right after upgrading to a geforce 6600[/QUOTE]

I wish I could do that, but as of now I don't have the money to spare for a new card.  I'll keep it in mind for the future, though.  In the meantime, I'm not sure what I'll do.

Thanks to both of you!  I appreciate your help.  Still not sure where to go from here, though.

-Bríghid

---

### Post by setog3 on 2006-06-26
I replace the default depth 16 bit by 24 and now I have the mini map working

    DefaultDepth   24


so, don't need more the autohide addons

:D

Debian User

---

### Post by Brighid on 2006-06-27
[QUOTE=setog3]I replace the default depth 16 bit by 24 and now I have the mini map working

    DefaultDepth   24


so, don't need more the autohide addons

:D

Debian User[/QUOTE]

I'm not very good with xorg.conf, but I took a look at it, and from what I can tell, all instances of "depth" or "DefaultDepth" are set to 24.  Despite this, the game crashes the moment I walk indoors.  Thanks for the idea, anyway. 

I just don't know what to do .. I've been playing on Windows, and though that is a fine temporary solution, I'm really sick of using Windows in general.

There's a native OS X port of the game, and my next computer is likely to be a MacBook Pro, so it looks like I may end up using OS X over Kubuntu, unfortunately.

---

### Post by setog3 on 2006-06-28
can you post your xorg.conf ? 
because it solve the problem for me so I think you can do the same
and wich version of wine ?

---

### Post by Sandlst on 2006-06-28
Ive just read that the wine version 0.9.16 has 'Fixes crash when entering or in buildings or city when minimap is displayed. (nvidia hardware)' Ill link the page (with HOWTO at the bottom) [here]("http://appdb.winehq.org/appview.php?versionId=5109").  Hope this works, as Im tired of dealing with this too.

---

### Post by Brighid on 2006-06-28
[QUOTE=setog3]can you post your xorg.conf ? 
because it solve the problem for me so I think you can do the same
and wich version of wine ?[/QUOTE]

Seeing that 0.9.16 is out gives me some hope, so I'm going to first try updating to the new version of Wine.  If I still have problems, expect to see my xorg.conf ..

[QUOTE=Sandlst]Ive just read that the wine version 0.9.16 has 'Fixes crash when entering or in buildings or city when minimap is displayed. (nvidia hardware)' Ill link the page (with HOWTO at the bottom) [here]("http://appdb.winehq.org/appview.php?versionId=5109").  Hope this works, as Im tired of dealing with this too.[/QUOTE]

Thank you very much for informing me of this.  I haven't been keeping up with Wine updates, and I was actually hoping that the new version would fix this issue (though I honestly didn't expect it).  I hope this is the end of the problem - that means I can finally quit Windows.  I still wish I could get Yahoo! Messenger to run under Wine, though. :p

---

### Post by graigsmith on 2006-07-11
so lets see, how can we get the new version? the apt server has an old version on it? and the precompiled version im using to play wow has the minimap/texture flicker problem.

has anyone made a compile of this for ubuntu?  or do i have to compile it myself?

---

### Post by Sandlst on 2006-07-11
Its quite easy to compile yourself if you go to the link I provided above.  The howto is a bit down the page, but unfortunatly it seems the 1.11.2 update has caused the infamous mouse-bug to re-appear, unless its just my computer.....hope they update it soon to fix this.
**EDIT** It was my computer, no mousebug, although I dont know why it was doing it for a bit.

---

